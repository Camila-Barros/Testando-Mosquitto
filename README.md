# Testando-Mosquitto
Projeto testando Mosquitto pela primeira vez, com Prompt de Comando, no Windows 11.

## Dispositivos:

  Consumidor (subscriber):
  - Cria e recebe mensagens ao tópico assinado.
  
  Produtor (publisher):
  - Envia mensagens ao tópico assinado.

## Teste 1 - SEM autenticação

  Em "mosquitto_conf" deixar:
  
  ```bash
    allow_anonymous true
  ```
 
  Subscriber 1:
  
  ![image](https://github.com/Camila-Barros/Testando-Mosquitto/blob/main/subscriber1.png)
  
  Publisher 1:
  
  ![image](https://github.com/Camila-Barros/Testando-Mosquitto/blob/main/publisher1.png)



## Teste 2 - COM autenticação

Em "mosquitto_conf" deixar:

  ```bash
    allow_anonymous false
    password_file C:\Program Files\mosquitto\passwd.txt
    #colocar o caminho do local onde está o arquivo de senhas criado
  ```

  Subscriber 2:
  
  IMAGEM
  
  Publisher 2:
  
  IMAGEM
