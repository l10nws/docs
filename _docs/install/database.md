---
title: Install Database
category: Installation 
order: 9
---

# Install Database

L10n.ws Portal uses [PostgreSQL](https://www.postgresql.org/) database.

After installation first you need to create user owner 
 
```sql
DO
$body$
BEGIN
  IF NOT EXISTS(
      SELECT *
      FROM pg_catalog.pg_user
      WHERE usename = 'l10n-portal')
  THEN

    CREATE ROLE "l10n-portal" LOGIN PASSWORD '1';
  END IF;
END
$body$;
```
Do not forget to change default password.

Next create database with created owner

```sql
CREATE DATABASE "l10n-portal" OWNER "l10n-portal";
```

## Liquibase

For database versioning we are using [Liquibase](http://www.liquibase.org/).

Run liquibase changeset scripts from [l10n-app](https://github.com/l10nws/l10n-app)

 ```sql
gradlew :liquibase:update -PrunList=portal
```

### Updating database version
For existing database 

```sql
gradlew :liquibase:changelogSync
```