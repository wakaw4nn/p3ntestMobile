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

Explorar isso é muito fácil, através do logcat - um utilitário para monitorar os logs do sistema no android.
 
[insecure-logging.webm](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/89466cde-37bc-40a7-8c13-8aaf5186d67a)

### Hardcoding Inssues 
Este problema ocorre quando o desenvolvedor escreve alguma credencial em texto plano (ou com criptografia fraca) diretamente no código. Neste caso, o desenvolvedor utiliza um método de autenticação inseguro, comparando o input do usuário com a credencial declarada no código.
![hardcoding-inssues](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/7c1ef254-746f-45b1-9d45-311b777b6678)

### Armazenamento Inseguro de Dados
Informações senssíveis devem ser armazenadas de forma adequada, fazendo uso de criptografia e controle de acesso. Quando tais controles de segurança não existem, temos vulnerabilidades de armazenamento inseguro. Abaixo vou abordar alguns cenários de armazenamento inseguro. 

#### Shared Preferences  
Shared Preferences são arquivos que contém pares de chave-valor e fornece métodos simples para leitura e gravação. Podemos observar no código, obtido através de engenharia reversa, que a função saveCredentials() faz a gravação das credenciais em um arquivo Shared Preferences sem criptografia e sem implementar técnicas de controle de acesso ao arquivo.  
![insecure-data-storage-1](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/f526a9d3-20fd-4233-be73-4aef8aebebe7)

Neste exemplo de exploração inserimos as credenciais no aplicativo, e logo após elas serem gravadas, acessamos diretamente o arquivo jakhar.aseem.diva_preferences.xml no caminho /data/data/jakhar.aseem.diva/shared_prefs, e logo em seguida exibimos o seu conteúdo com o utilitário cat.

[insecure-data-storage.webm](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/4ee18cf5-e6d0-48a6-bcfe-0e30940cc36d)

#### Banco de Dados - SQLite
Outro utilitário bastante utilizado para registro de dados são os bancos de dados SQLite, pelo fato de serem leves e versáteis. Banco de dados são estruturas mais robustas que Shared Preferences, porém ainda se deve tomar os mesmos cuidados ao registrar informações em DBs, que se resumem em fazer uso de criptografia forte e aplicar métodos de controle de acesso. 
Observando código fonte, podemos notar que estes controles de segurança não foram aplicados, as informações estão sendo salvas em texto claro e não há nenhum controle de acesso ao DB.
![insecure-data-storage-2](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/d80bc3a2-a1ae-4ee0-8269-9318171cedfb)

Para exploração dessa vulnerabilidade, acessamos diretamente o banco de dados (após inserir as credenciais no aplicativo) no caminho /data/data/jakhar.aseem.diva/shared_prefs. O DB está nomeado como IDS2, e como ele não tem nenhum controle de acesso, podemos ler o mesmo através do utilitário sqlite3. Já dentro do sqlite3, utilizamos o comando .tables para listas todas as tabelas do banco de dados. Identificamos a tabela "myuser" que é de nosso endereço. Podemos ler o conteúdo da tabela facilmente com o seguinte comando: select * from myuser;

[insecure-data-storage-sqlite.webm](https://github.com/wakaw4nn/p3ntestMobile/assets/143054074/2e802fbe-db7d-4e68-a381-3ee752e2a50e)








