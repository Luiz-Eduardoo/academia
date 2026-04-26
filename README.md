🎯 Objetivo da atividade
Desenvolver a base inicial do projeto Academia utilizando Spring Boot no VS Code, preparando corretamente o ambiente de execução com SQL Server e MySQL, configurando o arquivo application.properties, criando o banco de dados e garantindo que a aplicação consiga iniciar com sucesso por meio do comando:

mvnw.cmd spring-boot:run
O foco desta entrega é consolidar os passos fundamentais para que o projeto esteja estruturalmente correto e executável, servindo como base para a continuidade do manual e das próximas implementações.

Ao final da atividade, o(a) estudante deverá ser capaz de:

✔ criar um projeto Spring Boot no VS Code
✔ configurar corretamente o application.properties
✔ compreender a diferença entre SQL Server e MySQL no contexto da conexão com Spring Boot
✔ criar o banco de dados academia
✔ criar as tabelas iniciais do projeto
✔ executar a aplicação com sucesso
✔ evidenciar visualmente o Spring Boot em funcionamento

🧱 Escopo obrigatório da entrega
Nesta etapa, o(a) aluno(a) deverá obrigatoriamente realizar:

1. Criação do projeto no VS Code
O projeto deverá ser criado no VS Code, utilizando o Spring Initializr ou a estrutura iniciada em sala.

2. Configuração do application.properties
O arquivo deverá ser preparado com:

nome da aplicação

configurações comuns do JPA/Hibernate

configuração ativa para MySQL

comentários/orientações para SQL Server

porta da aplicação

3. Criação do banco de dados academia
O banco deverá ser criado:

em MySQL

e compreendido também em SQL Server, como ambientação da disciplina

4. Criação das tabelas iniciais
Devem ser criadas as tabelas:

planos

alunos

com relacionamento entre elas.

5. Execução do Spring Boot
A aplicação deverá subir com sucesso via terminal.

6. Evidência obrigatória
O(a) aluno(a) deverá apresentar print do Spring rodando no terminal.

⚙️ Requisitos técnicos obrigatórios
O projeto deverá utilizar:

Java

Spring Boot

Maven

Spring Web

Spring Data JPA

Banco relacional

VS Code

application.properties configurado corretamente

MySQL funcional

ambientação para SQL Server

🧩 Estrutura mínima esperada do projeto
academia
│
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com/facens/academia
│   │   │       └── AcademiaApplication.java
│   │   └── resources
│   │       └── application.properties
│
├── pom.xml
└── mvnw / mvnw.cmd
Nesta entrega, o foco ainda não é implementar toda a API completa, mas sim garantir que a base do projeto esteja correta, funcional e pronta para evolução.

🚀 Guia de desenvolvimento (passo a passo)
Etapa 1 — Preparação do ambiente
Verifique a instalação do Java:

java -version
Verifique também se o Maven Wrapper está disponível no projeto.

Instalar e/ou validar no VS Code:

Extension Pack for Java

Spring Boot Extension Pack

Etapa 2 — Criação do projeto no VS Code
No VS Code:

1️⃣ Abrir a paleta de comandos
Ctrl + Shift + P
2️⃣ Executar:
Spring Initializr: Create a Maven Project
Configurações sugeridas do projeto:
Language: Java

Group: com.facens

Artifact: academia

Packaging: Jar

Java: conforme ambiente configurado em sala

Dependências mínimas:
Spring Web

Spring Data JPA

MySQL Driver

Lombok (opcional)

Spring Boot DevTools (opcional)

Como ambientação da disciplina, o projeto também deverá considerar a futura utilização com SQL Server, mesmo que a execução atual esteja priorizada em MySQL.

Etapa 3 — Configuração do application.properties
O arquivo deverá refletir o que foi orientado em sala, incluindo:

spring.application.name

configurações JPA comuns

logs

porta da aplicação

profile ativo em MySQL

comentários orientativos para SQL Server

Modelo base trabalhado em sala
spring.application.name=academia

# spring.datasource.url=jdbc:sqlserver://localhost:1433;databaseName=academia;encrypt=true;trustServerCertificate=true
# spring.datasource.username=sa
# spring.datasource.password=sa
# spring.datasource.driver-class-name=com.microsoft.sqlserver.jdbc.SQLServerDriver
# spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.SQLServerDialect

# Também é aplicável em MySQL
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.open-in-view=false

logging.level.root=INFO
logging.level.com.facens.academia=DEBUG

server.port=8081

# Configuração MySQL
# spring.profiles.active=sqlserver
spring.profiles.active=mysql

spring.datasource.url=jdbc:mysql://localhost:3306/academia?useSSL=false&serverTimezone=America/Sao_Paulo&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=Facens@123
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
Atenção importante
Observe com cuidado:

jdbc:mysql:// → precisa ter ://

hibernate.format_sql → escrever corretamente

driver-class-name → deve estar correto para o banco escolhido

Etapa 4 — Criação do banco de dados
O banco academia deverá ser criado no MySQL.

CREATE DATABASE academia;
USE academia;
Como parte da ambientação da disciplina, o(a) aluno(a) também deverá compreender que, no SQL Server, a ideia é semelhante, mas a sintaxe e a conexão possuem diferenças.

Etapa 5 — Criação das tabelas iniciais
Executar os comandos abaixo no MySQL:

CREATE TABLE planos (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    modalidade VARCHAR(80) NOT NULL,
    valor_mensal DECIMAL(10,2) NOT NULL,
    ativo BIT NOT NULL DEFAULT 1
);

CREATE TABLE alunos (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(120) NOT NULL,
    email VARCHAR(120) NOT NULL UNIQUE,
    idade INT NOT NULL,
    telefone VARCHAR(20),
    situacao VARCHAR(20) NOT NULL,
    data_cadastro DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    plano_id BIGINT NOT NULL,
    CONSTRAINT fk_alunos_planos
        FOREIGN KEY (plano_id) REFERENCES planos(id)
);
Etapa 6 — Execução do projeto
No terminal do VS Code, executar:

Windows
mvnw.cmd spring-boot:run
Resultado esperado
A aplicação deverá iniciar corretamente e exibir no terminal as mensagens de subida do Spring Boot, incluindo a inicialização do Tomcat/servidor embutido.

Etapa 7 — Validação obrigatória
O(a) aluno(a) deverá comprovar que conseguiu:

criar o projeto

configurar o application.properties

criar o banco

criar as tabelas

subir o Spring Boot com sucesso

📦 Entregáveis
O(a) aluno(a) deverá entregar:

1️⃣ Link do repositório GitHub do projeto
2️⃣ Código-fonte do projeto contendo:
estrutura criada no VS Code

application.properties

projeto Spring Boot funcional

3️⃣ Evidências visuais obrigatórias
🖼️ Evidências obrigatórias (screenshots)
Capturas mínimas exigidas:

estrutura do projeto no VS Code

arquivo application.properties configurado

criação do banco academia

criação das tabelas planos e alunos

print do terminal com o Spring Boot rodando com sucesso

Este último print é obrigatório.

🧪 Critérios de avaliação
Serão considerados:

✔ criação correta do projeto no VS Code
✔ organização mínima do projeto Spring Boot
✔ configuração correta do application.properties
✔ coerência entre MySQL e ambientação SQL Server
✔ banco academia criado corretamente
✔ tabelas criadas corretamente
✔ aplicação iniciando com sucesso
✔ evidências visuais completas e legíveis

🚨 Regras importantes
A atividade corresponde ao que foi construído em sala.

O objetivo principal desta entrega é consolidar a base funcional do projeto.

Entregas sem evidência do Spring rodando poderão ser consideradas incompletas.

Configurações copiadas sem entendimento poderão ser questionadas em correção presencial.

A continuidade do projeto será guiada posteriormente com base no manual em construção.

💡 Dica estratégica
Nesta etapa, o foco é garantir que o projeto:

abra corretamente

conecte ao banco

reconheça a configuração

e execute com sucesso o spring-boot:run

Quem domina essa base terá muito mais facilidade nas próximas etapas de:

entidades

repositories

services

controllers

validações

tratamento de erros
