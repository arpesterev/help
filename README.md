# Help: Spring Boot chat prototype

A Java 8 / Spring Boot prototype with registration, form authentication, JSP pages and WebSocket-based chat messaging. Data is stored in PostgreSQL through Spring Data JPA.

## Code map

- `src/main/java/com/boots/controller/`: registration, administration and chat endpoints.
- `src/main/java/com/boots/service/`: domain operations.
- `src/main/java/com/boots/config/`: security, MVC and WebSocket configuration.
- `src/main/webapp/WEB-INF/jsp/`: JSP views.
- `src/main/resources/application-dev.properties`: development configuration without embedded credentials.

## Local setup

Prerequisites: Java 8, Maven and a locally accessible PostgreSQL database with the schema expected by the application.

```sh
cp .env.example .env
# Edit .env with your own local database settings. Never commit it.
set -a
. ./.env
set +a
mvn spring-boot:run
```

The default Spring profile is `dev`. Its datasource URL, username and password are read from `SPRING_DATASOURCE_URL`, `SPRING_DATASOURCE_USERNAME` and `SPRING_DATASOURCE_PASSWORD`. These variables must be defined before launching the application.

## Security and support status

This is a historical development project, **not a production-ready authentication or messaging service**. Its security configuration permits broad CORS access and disables CSRF protection, so it requires review and hardening before any deployment beyond local testing.

Older commits contained datasource credentials and local log files. Removing them from the latest revision does not remove their contents from Git history. Rotate any credentials that were valid and inspect whether the log history contains personal data.

The Maven build is checked in, but a full deployment and security assessment have not been performed in this documentation update.
