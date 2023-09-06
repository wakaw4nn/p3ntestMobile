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
