# Clonezilla Server Edition (SE) — Parte 2  
## Página 1 — DRBL e Introdução ao Clonezilla SE

Esta é a segunda parte da documentação sobre Clonezilla.  
Aqui abordamos exclusivamente a instalação e configuração do **Clonezilla Server Edition (SE)**, utilizado para realizar clonagens e restaurações de discos pela rede de forma centralizada e automatizada.

Caso ainda não tenha visto a Parte 1:  
👉 *Clonezilla - Gerando e Restaurando Backups Completos (Parte I)*

---

## 🧩 O que é DRBL?

**DRBL** significa **Diskless Remote Boot in Linux**.

Ele é um conjunto de ferramentas em software livre (licença GPL) que permite:

- Inicializar máquinas clientes **sem uso de disco local**, via rede.
- Inicializar sistemas Linux remotamente usando NFS + NIS.
- Oferecer o ambiente necessário para o funcionamento do **Clonezilla SE**.

### Como o DRBL funciona?

O servidor DRBL fornece:

- **NFS (Network File System)** → exporta diretórios necessários para o boot do cliente.
- **NIS (Network Information Service)** → fornece autenticação e ambiente.

O processamento é feito **no cliente**, não no servidor — algo diferente de LTSP, onde o servidor faz mais trabalho.

---

## 🧰 Clonezilla Server Edition

O Clonezilla SE é a versão do Clonezilla voltada para clonagem em massa, utilizada principalmente em:

- laboratórios de informática  
- escritórios  
- salas de aula  
- empresas com muitos computadores  

Ele opera em 3 modos:

| Modo | Descrição |
|------|-----------|
| **Unicast** | Comunicação 1:1 entre cliente e servidor. |
| **Broadcast** | Servidor envia dados para *todos* os clientes conectados. |
| **Multicast** | Servidor envia dados apenas para um *grupo específico* de máquinas. |

O **multicast** é o grande diferencial do SE, ideal para restaurar/clonar dezenas de máquinas ao mesmo tempo com uso mínimo de banda.

---

🛠️ Instalação do DRBL (Debian/Ubuntu)

1️⃣ Adicionar repositório do DRBL

Edite o arquivo: /etc/apt/sources.list


Adicione:

```text
deb http://drbl.sourceforge.net/drbl-core drbl stable
```

2️⃣ Importar a chave GPG do repositório

Método recomendado:
```
wget -q http://drbl.nchc.org.tw/GPG-KEY-DRBL -O- | apt-key add -
```

3️⃣ Instalar o DRBL (que inclui Clonezilla SE)
```
apt-get update
apt-get install drbl
```

🔄 (Opcional) Atualizar kernel via Backports

Só necessário se o servidor for muito antigo.

Adicione ao final do arquivo: 
```
echo "deb http://backports.debian.org/debian-backports squeeze-backports main contrib non-free" >> /etc/apt/sources.list
```

Aplique atualizações:

```
apt-get update
apt-get -t squeeze-backports install linux-image-3.2.0-0.bpo.4-amd64 firmware-linux-nonfree
```
Reinicie o servidor e selecione o novo kernel.

💡 Esta etapa é opcional.
O Clonezilla SE funciona normalmente com o kernel padrão do Debian.

➡ **[Próxima Página → Clonagem de Dispositivos](parte2-pagina-2.md)**  

