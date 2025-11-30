# 📘 Guia Completo — Clonezilla - Server Edition (Parte 2)
Documentação revisada, reorganizada e completamente reestruturada sobre **Clonezilla SE (Server Edition)** e **DRBL (Diskless Remote Boot in Linux)**, originalmente publicada na comunidade **Viva o Linux**.

O objetivo deste repositório é facilitar o acesso ao conteúdo, melhorar a legibilidade, organizar o passo a passo e preservar informações importantes para estudo técnico, uso profissional e futuras consultas.



# 📁 Estrutura da Documentação

A documentação está organizada em páginas individuais dentro de `/docs`, com imagens correspondentes em `/images`.


```
## 📘 Estrutura da Documentação
Clonezilla-Image-Server/
├── README.md
├── LICENSE.md
├── docs/
│ ├── parte2-pagina-1.md   (DRBL e Clonezilla SE — Introdução)
│ ├── parte2-pagina-2.md   (Preparando o Servidor Clonezilla SE)
│ ├── parte2-pagina-3.md   (Configuração DRBL + Clonezilla SE)
│ ├── parte2-pagina-4.md   (Clonagem de discos pela rede — PXE)
│ ├── parte2-pagina-5.md   (Restauração de imagens pela rede)
└── images/
└── pagina-X/ (imagens organizadas por capítulo)
```

---

# 📌 Conteúdo da Parte 2

Esta parte cobre:

### ✔ DRBL e Clonezilla SE  
- Funcionamento do servidor DRBL  
- Boot remoto sem disco  
- Arquitetura PXE, TFTP, DHCP, NFS  
- Diferenças entre unicast, multicast e broadcast  

### ✔ Preparação do Servidor  
- Configuração da rede  
- Instalação completa do DRBL  
- Atualização de kernel  
- Geração do ambiente para clientes PXE  

### ✔ Configuração Avançada do Clonezilla SE  
- drblsrv -i  
- drblpush -i  
- Criação dos ambientes de boot  
- Configuração do serviço DHCP  
- Modo box vs full clonezilla  

### ✔ Clonagem em Massa  
- save-disk pela rede  
- queue de clientes  
- uso de parâmetros avançados (-j2, -rescue, -q2)  

### ✔ Restauração via Multicast  
- restore-disk  
- restauração simultânea  
- seleção por MAC e IP fixo  

### ✔ Backup/Restore via SSH  
- savedisk e restore via servidor remoto  
- autenticação segura  
- partição de destino e parâmetros  

### ✔ Backup/Restore via Samba  
- Integração com ambiente Windows  
- salvamento remoto em SMB/CIFS  


---

## 🔗 Fonte Original

Conteúdo original (revisado e reestruturado) da comunidade:  
👉 https://www.vivaolinux.com.br

Clonezilla Official:  
👉 https://clonezilla.org  

DRBL Official:  
👉 https://drbl.org  


Todo o conteúdo foi reorganizado e reformatado, mantendo crédito e referência conforme diretrizes do site.

---

## 📝 Licença

A documentação deste repositório é distribuída sob a **Licença de Documentação Livre do Viva o Linux**, conforme os termos definidos no arquivo **LICENSE.md**.

---

## 💬 Contribuições

Pull Requests são bem-vindos para:

- correções  
- reorganização  
- melhorias de formatação  
- adição de conteúdo complementar  

---

## ✨ Autor

Documentação reorganizada por **Ivan (GitHub)** com auxílio de inteligência artificial para preservação histórica e uso profissional.

