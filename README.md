# README - Microservices Java

![image](https://github.com/IgorCastilhos/Java-RabbitMQ-Microservice/assets/101683017/4bbbc2af-74fe-4d67-83be-9c67f9ac562b)

Este projeto implementa uma arquitetura de microservices usando Java, focando na comunicação assíncrona e não bloqueante entre microservices. Ele consiste em dois microservices principais:

- **User Microservice:** Gerencia os usuários da plataforma.
- **Email Microservice:** Envia e-mails automáticos para os usuários.

## Comunicação Assíncrona e Fluxo de Trabalho
![image](https://github.com/IgorCastilhos/Java-RabbitMQ-Microservice/assets/101683017/eb4cfbb5-a816-4243-9079-81a359015622)

A comunicação entre os microservices é realizada de forma assíncrona utilizando o protocolo de mensagens. O fluxo de trabalho é descrito abaixo:

1. **Cadastro de Usuário:**
    - Um cliente envia uma requisição POST /USERS para cadastrar um novo usuário.
    - O User Microservice recebe a requisição, salva os dados do usuário na base de dados e publica uma mensagem de comando em um canal de mensagens (Broker).

2. **Processamento de E-mail:**
    - O Email Microservice, conectado ao mesmo canal de mensagens, aguarda as mensagens.
    - Ao receber uma mensagem, o Email Microservice envia um e-mail de boas-vindas ao usuário cadastrado e salva os dados do e-mail.

3. **Broker - RabbitMQ:**
    - O RabbitMQ atua como broker, facilitando a comunicação assíncrona.
    - O User Microservice atua como Producer, enviando mensagens ao RabbitMQ.
    - O RabbitMQ encaminha as mensagens para as filas apropriadas, onde o Email Microservice, atuando como Consumer, as processa.

## Tecnologias Utilizadas

- **Java 17:** Linguagem de programação.
- **Maven:** Ferramenta de gerenciamento de projetos.
- **Spring Boot:** Framework para facilitar a configuração e execução de aplicações Java.
- **Spring Web:** Para criar endpoints da API.
- **Spring Data JPA:** Para transações com a base de dados.
- **Spring Validation:** Para validações na entrada da API.
- **Spring AMQP:** Protocolo de mensageria para comunicação assíncrona.
- **Spring Mail:** Para enviar e-mails.
- **PostgreSQL:** Sistema de gerenciamento de banco de dados.
- **Rabbit MQ:** Sistema de mensageria para comunicação entre microservices.
- **Cloud AMQP:** Serviço cloud para Rabbit MQ.
- **SMTP Gmail:** Serviço de e-mail para envio de mensagens.




## Conclusão

Este projeto demonstra uma implementação eficaz de uma arquitetura de microservices utilizando Java e Spring Boot, com foco na comunicação assíncrona e não bloqueante entre os serviços. A utilização do RabbitMQ como broker de mensagens permite um fluxo de trabalho eficiente e escalável.
