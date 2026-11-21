# Help: Spring Boot chat prototype

A Java 8 / Spring Boot prototype with registration, form authentication, JSP pages and WebSocket-based chat messaging. User/registration data is stored in PostgreSQL through Spring Data JPA; chat messages and rooms use Spring Data MongoDB.

## Code map

- `src/main/java/com/boots/controller/`: registration, administration and chat endpoints.
- `src/main/java/com/boots/service/`: domain operations.
- `src/main/java/com/boots/config/`: security, MVC and WebSocket configuration.
- `src/main/webapp/WEB-INF/jsp/`: JSP views.
- `src/main/resources/application-dev.properties`: development configuration without embedded credentials.

## Local setup

Prerequisites: Java 8-compatible tooling (CI uses JDK 11), Maven, a locally accessible PostgreSQL database and MongoDB.

```sh
cp .env.example .env
# Edit .env with your own local database settings. Never commit it.
set -a
. ./.env
set +a
mvn spring-boot:run
```

MongoDB settings are in `src/main/resources/application.yml` and must also be appropriate for your local setup. The default Spring profile is `dev`. Its datasource URL, username and password are read from `SPRING_DATASOURCE_URL`, `SPRING_DATASOURCE_USERNAME` and `SPRING_DATASOURCE_PASSWORD`. These variables must be defined before launching the application.

## Security and support status

This is a historical development project, **not a production-ready authentication or messaging service**. Its security configuration permits broad CORS access and disables CSRF protection, so it requires review and hardening before any deployment beyond local testing.

Older commits contained datasource credentials and local log files. Removing them from the latest revision does not remove their contents from Git history. Rotate any credentials that were valid and inspect whether the log history contains personal data.

The Maven build is checked in, but a full deployment and security assessment have not been performed in this documentation update.
