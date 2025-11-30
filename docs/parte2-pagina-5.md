# Clonezilla Server Edition (SE) — Parte 2  
## Página 5 — Restauração de Imagens de Discos pela Rede

Agora que você já realizou backup de discos pela rede utilizando o Clonezilla SE, é hora de ver como restaurar essas imagens em máquinas específicas.  
Nesta etapa, usaremos **endereços MAC** e **endereços IP fixos** para determinar exatamente quais clientes receberão a restauração.

---

# 🛠️ Configurando Clientes Específicos no DHCP

Para controlar quais máquinas serão restauradas, edite o arquivo:
````
/etc/dhcp/dhcpd.conf
````

E adicione entradas como estas:

````
host winxp-1 {
hardware ethernet 08:00:27:64:89:B1;
fixed-address 192.168.56.20;
}

host winxp-2 {
hardware ethernet 08:00:27:19:4E:AA;
fixed-address 192.168.56.21;
}
````

Essas máquinas agora terão IP fixo baseado no endereço MAC.

Após editar, reinicie o serviço DHCP:

```
service isc-dhcp-server stop
service isc-dhcp-server start
````

🚀 Habilitando o Servidor Clonezilla para Restauração

Para iniciar o serviço, execute:
````
/usr/sbin/dcs clonezilla-start
````
A primeira tela será semelhante a esta:

1️⃣ Selecionar clientes que serão restaurados

Escolha:
````
Part
````
Isso indica que somente alguns clientes selecionados receberão a restauração.

![Clonezilla inicial](../images/pagina-5/pag5-image1.png)

2️⃣ Selecionar os clientes pelo endereço MAC

Escolha:
````
by_MAC_addr_list
````
Somente os clientes cadastrados anteriormente no DHCP serão exibidos

![Clonezilla inicial](../images/pagina-5/pag5-image2.png)

3️⃣ Selecionar os hosts desejados

Marque os clientes que receberão a restauração:

![Clonezilla inicial](../images/pagina-5/pag5-image3.png)

4️⃣ Escolha o modo de execução

Selecione:
````
Expert
````
![Clonezilla inicial](../images/pagina-5/pag5-image4.png)

5️⃣ Escolha o tipo de operação

Escolha:
````
restore-disk
````
![Clonezilla inicial](../images/pagina-5/pag5-image5.png)

6️⃣ Selecionar/desabilitar parâmetros

Desabilite:

  - g auto → Reinstala o GRUB

  - e2 → Usa SFdisk (melhor desabilitar)

![Clonezilla inicial](../images/pagina-5/pag5-image6.png)

7️⃣ Criar nova tabela de partição proporcional ao disco de destino

Escolha:
````
-k1
````
Isso criará partições adaptadas ao tamanho do disco da máquina cliente.

| ⚠️ Atenção: Apenas cria tabela MBR — se o equipamento não suportar, não funcionará

![Clonezilla inicial](../images/pagina-5/pag5-image7.png)

8️⃣ Tipo padrão de operação

Escolha:
````
-y1
````
![Clonezilla inicial](../images/pagina-5/pag5-image8.png)

9️⃣ Ação após finalização

Escolha:
````
-p reboot
````
![Clonezilla inicial](../images/pagina-5/pag5-image9.png)

🔟 Escolher a imagem de backup no servidor

Todas as imagens salvas aparecerão:

![Clonezilla inicial](../images/pagina-5/pag5-image10.png)

1️⃣1️⃣ Escolher o disco de destino no cliente

Informe o disco que será sobrescrito:

![Clonezilla inicial](../images/pagina-5/pag5-image11.png)


1️⃣2️⃣ Selecionar método de restauração via rede

Escolha:
````
multicast
````
![Clonezilla inicial](../images/pagina-5/pag5-image12.png)


1️⃣3️⃣ Escolhendo o tipo de multicast

Selecione:
````
client+time-to-wait
````
![Clonezilla inicial](../images/pagina-5/pag5-image13.png)


1️⃣4️⃣ Número de clientes e tempo de espera

Exemplo:

Clientes: 2

Tempo de espera: 300 segundos

![Clonezilla inicial](../images/pagina-5/pag5-image14.png)

![Clonezilla inicial](../images/pagina-5/pag5-image15.png)


1️⃣5️⃣ Processo de restauração

Confirme todas as mensagens com ENTER e y quando solicitado.

![Clonezilla inicial](../images/pagina-5/pag5-image16.png)


🖥️ Máquinas Clientes

Reinicie as máquinas clientes e inicialize pela rede.

A tela será semelhante a:

Selecione:
````
Clonezilla: multicast restore
````
![Clonezilla inicial](../images/pagina-5/pag5-image17.png)

Restauração acontecendo:

Após finalizado, cada máquina será reiniciada.

![Clonezilla inicial](../images/pagina-5/pag5-image18.png)

⛔ Parando o Servidor Clonezilla

Execute:
````
/usr/sbin/dcs clonezilla-stop
````
Selecione:
````
All
````
Para não disponibilizar mais nenhum serviço às máquinas da rede



🏁 Conclusão

O Clonezilla SE é extremamente poderoso para replicação e restauração em massa, sendo perfeito para:

  -laboratórios
  -escolas
  -empresas
  -ambientes de homologação

E uma excelente alternativa livre ao Symantec Ghost Solution Suite.
