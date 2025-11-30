# Clonezilla Server Edition (SE) — Parte 2  
## Página 3 — Configurando o DRBL para trabalhar com o Clonezilla SE

Após preparar o ambiente básico do servidor DRBL, o próximo passo é configurar especificamente o **Clonezilla Server Edition**, que será responsável por clonar e restaurar máquinas pela rede.

Para isso, utilizamos o script:

````
/usr/sbin/drblpush -i
````

Esse modo interativo permite que o administrador aprove ou personalize cada etapa da configuração.

🛠️ Iniciando a Configuração com **drblpush -i**

Execute como root:
````
/usr/sbin/drblpush -i
````

A partir deste ponto, o assistente iniciará uma série de perguntas.
Veja abaixo cada etapa com orientações

1️⃣ Definição do domínio DNS

O sistema pedirá:

| Informe o domínio DNS do servidor.

Se você não usa domínio, pode usar algo fictício, por exemplo:

````
clonebkp.net
````

Ou simplesmente aceitar o padrão:

````
drbl.name
````
![Clonezilla inicial](../images/pagina-2/pag3-image1.png)

2️⃣ Nome NIS e prefixo dos clientes

Será solicitado:

  Nome do domínio NIS

  Prefixo para hostname dos clientes

Sugestões:

  NIS: **penguinzilla** (ou deixe o padrão)

  Prefixo de host: **clientzilla**

![Clonezilla inicial](../images/pagina-2/pag3-image2.png)
  
3️⃣ Interface conectada à Internet

Informe qual interface do servidor é a interface externa (acesso à internet).

Exemplo do artigo: 
````
eth0
````
A outra interface (ex.: eth1) será usada para atender os clientes via PXE.

![Clonezilla inicial](../images/pagina-2/pag3-image3.png)

4️⃣ Coleta de endereços MAC

O script perguntará:

| Deseja coletar os MAC addresses dos clientes agora?

Responda:
````
N
````
Essa tarefa é trabalhosa e não necessária neste momento.

Em seguida:

| Deseja associar IPs aos MAC addresses no DHCP?

````
N
````
Você poderá fazer essa configuração manualmente mais tarde.

![Clonezilla inicial](../images/pagina-2/pag3-image4.png)


5️⃣ Definindo faixa de IPs para os clientes

Informe o primeiro IP da faixa:
````
192.168.56.10
````
Depois, informe quantos clientes serão atendidos:
````
40
````
O script calculará automaticamente a faixa.
Confirme com:
````
Y
````
![Clonezilla inicial](../images/pagina-2/pag3-image5.png)

6️⃣ Exibição do layout da rede

Uma representação será exibida mostrando o fluxo:
````
Servidor DRBL <--> Clientes
````
Pressione ENTER para continuar.

![Clonezilla inicial](../images/pagina-2/pag3-image6.png)

7️⃣ Escolha do modo de operação

O assistente perguntará:

Qual modo o servidor DRBL irá operar?

Escolha:
````
2 – Clonezilla Server (sem diskless mode)
````
![Clonezilla inicial](../images/pagina-2/pag3-image7.png)

8️⃣ Selecionando o modo de imagem do cliente

Escolha:
````
1 – Modo box
````
Isso otimiza espaço no servidor.

Depois, será pedido o diretório onde as imagens serão armazenadas:
````
/home/partimag
````
Você pode apenas pressionar ENTER para aceitar o padrão.

![Clonezilla inicial](../images/pagina-2/pag3-image8.png)

9️⃣ Senha para iniciar o serviço nos clientes

O sistema perguntará:

| Deseja exigir senha ao iniciar o cliente?

Escolha:
````
N
````
Mas, se quiser segurança extra, pode escolher **Y**.

![Clonezilla inicial](../images/pagina-2/pag3-image9.png)


🔟 Configuração da tela de boot dos clientes

**1. Responda:**

````
Y
````
**2. Informe o tempo de espera (em décimos de segundo)**
````
60
````
**3. Escolha se deseja fundo gráfico:**
````
Y
````
**4. E se deseja habilitar NAT para clientes::**
````
N
````

![Clonezilla inicial](../images/pagina-2/pag3-image10.png)

1️⃣1️⃣ Verificação final e criação da configuração

O script verificará se o kernel possui suporte a NFS.

Depois perguntará:

| Deseja continuar e gerar toda a configuração?

Responda:
````
Y
````
![Clonezilla inicial](../images/pagina-2/pag3-image11.png)

Pronto!
O servidor Clonezilla está configurado — mas ainda não iniciado.
