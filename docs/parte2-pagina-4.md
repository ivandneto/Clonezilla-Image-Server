# Clonezilla Server Edition (SE) — Parte 2  
## Página 4 — Clonagem de Discos pela Rede

Agora que o servidor Clonezilla está configurado, chegou o momento de habilitar o serviço e realizar clonagens pela rede.  
Antes de tudo, certifique-se de que as máquinas clientes estão configuradas para **boot via PXE** (inicialização pela rede).

---

# 🚀 Habilitando o Servidor Clonezilla

Para iniciar o serviço no servidor Clonezilla, execute:

```
/usr/sbin/dcs clonezilla-start
````
A primeira tela exibida será semelhante à imagem abaixo:


1️⃣ Selecionando os clientes que serão clonados

Escolha:

````
All
````
Isso fará com que todas as máquinas que inicializarem pela rede sejam clonadas.

![Clonezilla inicial](../images/pagina-4/pag4-image1.png)


2️⃣ Escolha o modo de execução

Selecione o modo:
````
Expert
````
Para acessar configurações avançadas.

![Clonezilla inicial](../images/pagina-4/pag4-image2.png)

3️⃣ Definindo o tipo de operação

Escolha:
````
save-disk
````
Pois queremos clonar um disco inteiro das máquinas clientes.

![Clonezilla inicial](../images/pagina-4/pag4-image3.png)

4️⃣ Escolhendo onde nomear a imagem

Selecione:
````
Later_in_client
````
Assim, o cliente informará o nome da imagem e qual disco deve ser clonado.

![Clonezilla inicial](../images/pagina-4/pag4-image4.png)

5️⃣ Prioridade de aplicativos usados

Selecione:
````
-q2
````
Isso fará o servidor priorizar:
  - Partclone
  - Partimage
  - dd (como último recurso)

![Clonezilla inicial](../images/pagina-4/pag4-image5.png)

6️⃣ Definindo parâmetros importantes

Habilite:
  -j2 → copia dados ocultos da MBR

  -rescue → ignora setores defeituosos

![Clonezilla inicial](../images/pagina-4/pag4-image6.png)

7️⃣ Ignorar verificação do sistema de arquivos

Selecione:
````
Skip checking/repairing source file system
````

![Clonezilla inicial](../images/pagina-4/pag4-image7.png)

8️⃣ Verificação final e ação após backup

Escolha:
````
Sim, verificar a imagem salva
````

E:
````
-p reboot
````

Para reiniciar o cliente ao final.

![Clonezilla inicial](../images/pagina-4/pag4-image8.png)

![Clonezilla inicial](../images/pagina-4/pag4-image9.png)

9️⃣ Escolhendo o compactador

Selecione:
````
-z1p
````
(Gzip com boa compactação)

![Clonezilla inicial](../images/pagina-4/pag4-image10.png)

🔟 Tamanho máximo por arquivo

Defina:
````
4096 MB
````
![Clonezilla inicial](../images/pagina-4/pag4-image11.png)

🖥️ Máquinas Clientes

Agora reinicie as máquinas clientes e inicialize via rede

1️⃣ Tela inicial do cliente

Escolha:
````
Clonezilla: save-disk
````
![Clonezilla inicial](../images/pagina-4/pag4-image12.png)

![Clonezilla inicial](../images/pagina-4/pag4-image13.png)

2️⃣ Nome da imagem de backup

Informe o nome desejado:

![Clonezilla inicial](../images/pagina-4/pag4-image14.png)

3️⃣ Escolha o disco a ser clonado

Exemplo:
````
sda
````
![Clonezilla inicial](../images/pagina-4/pag4-image15.png)

4️⃣ Clonagem em andamento

![Clonezilla inicial](../images/pagina-4/pag4-image16.png)

![Clonezilla inicial](../images/pagina-4/pag4-image17.png)

⛔ Parando o Servidor Clonezilla - apos conclusão

Após concluir a clonagem, execute:
````
/usr/sbin/dcs clonezilla-stop
````

Selecione novamente:
````
All
````

A clonagem de partições também é possível usando:
````
save-parts
````
