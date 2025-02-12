# Testando-Mosquitto
Projeto testando Mosquitto pela primeira vez, com Prompt de Comando, no Windows 11.


## Ferramentas

- [Eclipse Mosquitto](https://mosquitto.org/download/)

  
## Dispositivos:

  Consumidor (subscriber):
  - Cria e recebe mensagens ao tópico assinado.
  
  Produtor (publisher):
  - Envia mensagens ao tópico assinado.


## Teste 1 - SEM autenticação

### <b> IMPLEMENTAÇÃO </b>

  No arquivo "mosquitto_conf" (geralmente fica em C:\Program Files\mosquitto\mosquitto.conf) deixar:
  
  ```bash
    allow_anonymous true
  ```

  Em uma janela (1) do Prompt de Comando:

  ```bash
    net start mosquitto
    mosquitto_sub -h localhost -t "topico"
  ```

  Em outra janela (2) do Prompt de Comando:

  ```bash
    mosquitto_pub -h localhost -t "topico" -m "texto da mensagem"
  ```
  
 
### <b> TELAS </b>

<b>Subscriber:</b>
  
  ![image](https://github.com/Camila-Barros/Testando-Mosquitto/blob/main/subscriber1.png)
  
<b>Publisher:</b>
  
  ![image](https://github.com/Camila-Barros/Testando-Mosquitto/blob/main/publisher1.png)



## Teste 2 - COM autenticação

### <b> IMPLEMENTAÇÃO </b>

  No arquivo "mosquitto_conf" (geralmente fica em C:\Program Files\mosquitto\mosquitto.conf) deixar:
  
  ```bash
    allow_anonymous false
    password_file C:\Program Files\mosquitto\passwd.txt
    #colocar o caminho do local onde está o arquivo de senhas criado
  ```

  Em uma janela (1) do Prompt de Comando:

  ```bash
    net start mosquitto
    mosquitto_sub -h localhost -t "topico" -u USUARIO -P "sua_senha"
  ```

  Em outra janela (2) do Prompt de Comando:

  ```bash
    mosquitto_pub -h localhost -t "topico" -m "texto da mensagem" -u USUARIO -P "sua_senha"
  ```
  
 
### <b> TELAS </b>

<b>Subscriber:</b>
  
  ![image](https://github.com/Camila-Barros/Testando-Mosquitto/blob/main/subscriber2.png)
  
<b>Publisher:</b>
  
  ![image](https://github.com/Camila-Barros/Testando-Mosquitto/blob/main/publisher2.png)


## Nova autenticação:

Para criar um novo usuário, abra o Prompt de Comando e entre na pasta do msoquitto:

  ```bash
    cd "C:\Program Files\mosquitto"
    #colocar o caminho do local onde está a pasta
  ```

Criar o novo usuário e senha:

  ```bash
    mosquitto_passwd -b passwd.txt USUARIO2 "nova_senha"
    #conferir se o nome do arquivo de senhas é passwd
  ```

Verificar se o novo usuário foi criado, listando todos os usuários cadastrados:

  ```bash
    type passwd.txt
  ```

Depois de adicionar o usuário, reinicie o Mosquitto para aplicar as mudanças:

  ```bash
    net stop mosquitto
    net start mosquitto
  ```


## Autora

Eng. Camila Cabral de Barros

Mestranda em Inovação Tecnológica pela UNIFESP

[Lattes](http://lattes.cnpq.br/2066462797590469)
