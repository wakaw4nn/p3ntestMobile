# p3ntestMobile

Anotações de estudo sobre pentest em aplicações mobile: Andoird (e quem sabe futuramente IOS) - Por @wakaw4nn

## Seções
- [0. Ferramentas]()
  - [0.0 APK retrieval]()
  - [0.1 Apktool]()
  - [0.2 Dex2jar]()
  - [0.3 JD-GUI]()
  - [0.4 Jadx]() 
- [1. Vulnerabilidades]()
  - [1.1 Insecure logging]()
  - [1.2 Hardcoding inssues]()
  - [1.3 Armazenamento inseguro de dados]()
    - [1.3.1 Shared Preferences]()
    - [1.3.2 Banco de dados - SQLite]()
    - [1.3.4 Arquivos temporários I]()
    - [1.3.5 Arquivos temporários II]()
   
## Ferramentas
Aqui se encontra um inventário de ferramentas voltadas para pentest mobile.
### APK retrieval
https://apps.evozi.com/apk-downloader/    
### Apktool
Engenharia reversa em arquivos APK 
https://apktool.org/
### Dex2jar
Converte .dex em .jar e arquivos smali 
https://github.com/pxb1988/dex2jar
### JD-GUI
"Yet another fast Java decompiler"
https://java-decompiler.github.io/
### Jadx
Converte arquivos .dex e apk em código Java
https://github.com/skylot/jadx


## Vulnerabilidades
Para estudo teórico e exploração das vulnerabilidades aqui listadas, usaremos o App [Diva](https://github.com/payatu/diva-android) - Um aplicativo intencionalmente vulnerável que servirá como cobaia. 

### Insecure Logging
Algumas vezes, intencionalmente ou não, programadores registram em log informações sensíveis. 
 <img src="https://github.com/wakaw4nn/p3ntestMobile/blob/main/img/insecure-logging-code.png"/>

Explorar isso é muito fácil, através do lotcat - um utilitário para monitorar os logs do sistema no emulador android.
 
[insecure-logging.webm](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/89466cde-37bc-40a7-8c13-8aaf5186d67a)

### Hardcoding Inssues 
Este problema ocorre quando o desenvolvedor escreve alguma credencial em texto plano (ou com criptografia fraca) diretamente no código. Neste caso, o desenvolvedor utiliza um método de autenticação inseguro, comparando o input do usuário com a credencial declarada no código.
![hardcoding-inssues](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/7c1ef254-746f-45b1-9d45-311b777b6678)

### Armazenamento Inseguro de Dados
Informações senssíveis devem ser armazenadas de forma adequada, fazendo uso de criptografia e controle de acesso. Quando tais controles de segurança não existe, temos vulnerabilidades de armazenamento inseguro. Abaixo vou abordar alguns cenários de armazenamento inseguro. 

#### Shared Preferences  

#### Banco de Dados - SQLite






