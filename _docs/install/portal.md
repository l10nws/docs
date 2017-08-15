---
title: Install Portal and API
category: Installation
order: 10
---

# Install Portal and API

To install L10n Portal need any servlet container. We recommend to use [Tomcat 7+](https://tomcat.apache.org/download-70.cgi).
Download zip artifact from our [download]({{site.baseurl}}/download) page.

Unzip and you will see

* l10n-api.war - API application, web archive
* l10n-portal.war - portal application, web archive
* l10n-config.xml - configuration for L10n Portal
* l10n_create_db.sql - sql script to create database in PostgreSQL
* l10n_schema_db.sql - sql script to create database schema and initialize data

To deploy API and Portal applications copy wars in **webapps** folder
of web container and run it.

## Configuration

Setup configuration use l10n-config.xml file.

### Database configuration
For database configuration find database xml element in config file

```xml
 <datasource>
        <url>jdbc:postgresql://localhost:5432/l10n-portal</url>
        <username>postgres</username>
        <password>1</password>
        <driverClassName>org.postgresql.Driver</driverClassName>
</datasource>
```

### Superusers configuration

To have pre-installed supersusers checked section

```xml
 <superusers>
    <user>
        <email>admin@yourcompany.com</email>
        <password>admin</password>
    </user>
</superusers>
```

Multiple superuser might be declared.

### Mail server configuration

If you want to use emails in Portal, need to describe SMTP and mail list sections.

```xml
    <!--
        smtp server configuration
        default: disable, enable = false
        -->
    <smtp enable="false">
        <host></host>
        <port></port>
        <username></username>
        <password></password>
    </smtp>
    <!--
        Mail list is using if smtp enabled, set email for your company here
        noreply: email for notifications
        -->
    <mail-list>
        <item name="noreply">noreply@yourcompany.com</item>
    </mail-list>
```

## Set path of configuration file

l10n-config.xml configuration file might be placed whatever you want location.

Setup system property or environment property with name **L10N_CONFIG_DIR** and with value
path to directory where l10n-config.xml



