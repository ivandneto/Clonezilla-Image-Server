# Parte 2 – DRBL e Clonezilla Server Edition (SE)

## Introdução

Esta é a segunda parte do guia completo sobre Clonezilla.  
Aqui focaremos no **Clonezilla Server Edition (SE)** e no **DRBL**, que é a base necessária para o funcionamento do Clonezilla SE.

Se ainda não leu a Parte 1, recomenda-se ler antes.

---

# 🖥️ DRBL – Diskless Remote Boot in Linux

**DRBL (Diskless Remote Boot in Linux)** é um software livre, licenciado sob GPL.  
Ele fornece:

- Boot remoto sem disco (diskless)
- Instalação de sistemas pela rede
- Clonezilla Server Edition (SE)

O DRBL funciona de forma parecida com LTSP, usando:

- **NFS** → fornece sistema e diretórios aos clientes  
- **NIS** → autenticação e identificação  
- Clientes processam localmente, servidor apenas fornece o sistema

---

# 📦 Clonezilla Server Edition (SE)

O Clonezilla SE permite:

- Clonar máquinas pela rede  
- Restaurar imagens em unicast, multicast ou broadcast  
- Trabalhar com grupos específicos de clientes  
- Automatizar clonagens em massa

### Modos de operação:

| Modo | Descrição |
|------|-----------|
| **Unicast** | Comunicação 1:1 entre servidor ↔ cliente |
| **Broadcast** | Envio do servidor para *todas* máquinas |
| **Multicast** | Envio para um *grupo* específico de máquinas |

Nesta parte do guia, trataremos exclusivamente do Clonezilla SE.

---

# 🛠️ Instalação do DRBL (Debian/Ubuntu)

## 1️⃣ Adicionar repositório do DRBL

Edite:

