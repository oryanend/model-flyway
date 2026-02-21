## 🔍 O que é `migration`?

**Migrations**, ou **Database Migrations**, são técnicas e ferramentas que auxiliam no versionamento da base de dados durante o desenvolvimento. Elas normalmente evitam a escrita direta de scripts SQL no banco de dados, permitindo que as atualizações no banco de dados sejam realizadas por meio da própria linguagem de programação e dos frameworks que estão sendo utilizados.

Ou seja, **migrations** permitem que você use a linguagem do seu sistema para modificar o banco de dados, controlando quando cada mudança é aplicada e podendo desfazê-la sempre que necessário.

## 💻 O que é `Flyway`?

O **Flyway** é uma ferramenta usada para versionar o banco de dados e é responsável pela criação das **migrations**. Ele permite controlar as mudanças no schema por meio de scripts versionados, garantindo segurança e integridade durante as atualizações.

Para isso, o **Flyway** cria uma tabela própria no banco de dados, onde registra o histórico das versões aplicadas e o status de cada migração. Com base nesse controle, ele executa apenas as mudanças necessárias, de forma rápida e confiável.

Existem outras ferramentas para versionamento de banco de dados, mas uma das principais vantagens do **Flyway** é sua forte integração com o ecossistema Java. No **Spring Boot**, sua configuração é simples: basta adicionar a dependência ao projeto para começar a utilizá-lo.

## 👣 Passo a Passo
### 1️⃣ Adicionar a dependência do Flyway

No arquivo `pom.xml`, adicione:

```xml
<dependency>
  <groupId>org.flywaydb</groupId>
  <artifactId>flyway-core</artifactId>
</dependency>
```

### 2️⃣ Criar a pasta de migrações
Crie a seguinte estrutura dentro de `resources`:

```
src/main/resources/db/migration
```
### 3️⃣ Configurar os arquivos de propriedades

**📄 application.properties**
```properties
spring.application.name=flyway
spring.profiles.active=test
spring.jpa.open-in-view=false

spring.jpa.properties.hibernate.cache.use_second_level_cache=false
spring.jpa.properties.hibernate.cache.use_query_cache=false

spring.datasource.hikari.maximum-pool-size=10
spring.datasource.hikari.pool-name=MainPool
spring.datasource.hikari.connection-timeout=20000
```

**📄 application-test.properties**
```properties
# DATASOURCE
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

# H2 CONSOLE
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# JPA / HIBERNATE
spring.jpa.hibernate.ddl-auto=validate
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

### 4️⃣ Criar o arquivo de migração

Crie um arquivo `.sql` dentro da pasta `migration`:

```
src/main/resources/db/migration/V01__migration_test_flyway.sql
```
### 📌 Importante:
O nome deve seguir o padrão do **Flyway**:

```
V<versão>__<descrição>.sql
```

Exemplo:

```
V01__create_table_user.sql
```
## 🔗 Fontes

- 🔹 [Migrations com Flyway no Spring Boot – Medium](https://medium.com/@ryanalmeidaend/migrations-com-flyway-no-spring-boot-2564f715f00e)
- 🔹 [Getting Started With Flyway – Medium](https://medium.com/@david_haylock/getting-started-with-flyway-8e945a0777bd)
- 🔹 [Database Migrations With Flyway – Baeldung](https://www.baeldung.com/database-migrations-with-flyway)

## ⚙️ Tecnologias utilizadas

![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white) ![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white) ![Postgresql](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white) 
# 👥 Autor
| [<img src="https://avatars.githubusercontent.com/u/135620793?v=4" width=115><br><sub>Ryan Oliveira</sub>](https://github.com/oryanend) |
| :---: |



