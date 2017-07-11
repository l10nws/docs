---
title: Java
header: Java Integration Libraries
category: Integration
order: 3
---

Lightweight Java libraries that allow perform low-level calls to access messages of L10n account.

HTTP Client
-------
This Java library provides general functionality related to HTTP v1 API, includes HTTP transport, error handling, authentication, JSON parsing.

#### Include in project

Library published in maven central repository.

#### Maven
````xml
<dependency>
    <groupId>ws.l10n</groupId>
    <artifactId>l10n-client-http</artifactId>
    <version>1.0.3</version>
</dependency>
````
#### Gradle

````groovy
compile 'ws.l10n:l10n-client-http:1.0.3'
````

#### Usage

Create client
````java
String serviceUrl = "https://l10n.ws/api/v1";
String accessToken = "YOUR_ACCESS_TOKEN";

MessageBundleService client = new HttpMessageBundleClient(serviceUrl, accessToken);
````

Load messages

````java
String bundleKey = "YOUR_BUNDLE_KEY";
String bundleVersion = "YOUR_BUNDLE_VERSION";
MessageBundle messageBundle = client.loadMessageBundle(bundleKey, bundleVersion);

MessageBundleContext messageBundleContext = new SimpleMessageBundleContext(messageBundle);

messageBundleContext.getMessage("login.username", Locale.US);
````

Core Library
------
Core Library provides a configurable messages contexts. Context uses L10n Java Client Library for getting message from a service.

#### Maven
````xml
<dependency>
    <groupId>ws.l10n</groupId>
    <artifactId>l10n-core</artifactId>
    <version>1.0.3</version>
</dependency>
````

#### Gradle
````groovy
compile 'ws.l10n:l10n-core:1.0.3'
````

#### Usage
Create reloadable context

````java
ReloadableMessageBundleContext reloadableMessageBundleContext =
    new ReloadableMessageBundleContext(messageBundleService, bundleKey, bundleVersion);
````
Initialize context
````java
reloadableMessageBundleContext.init(); // load all message
````
Reload messages

````java
reloadableMessageBundleContext.reload();
````


#### Source Code
For more details source code you can find here [{{ site.data.links.git_source_link }}]({{ site.data.links.git_source_link }})