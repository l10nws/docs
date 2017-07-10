---
title: Spring 
header: Spring Framework Integration
category: Integration
order: 2
---

It is a lightweight Java library that provides quick and easy integration with the Spring Framework.

#### Include in project

Library published in maven central repository.

#### Maven
````xml
<dependency>
    <groupId>ws.l10n</groupId>
    <artifactId>l10n-spring</artifactId>
    <version>1.0.3</version>
</dependency>
````

#### Gradle
````groovy
compile 'ws.l10n:l10n-spring:1.0.3'
````

#### Usage

This example show usage of reloadable message context, implementation allow to reload messages in run-time by perform ```reload()``` method.

````xml
<!-- L10n Service Client -->
<bean id="l10nClient" class="ws.l10n.client.http.HttpMessageBundleClient">
   <constructor-arg name="serviceUrl" value="https://l10n.ws/api/v1"/>
   <constructor-arg name="accessToken" value="YOUR_ACCESS_TOKEN"/>
</bean>

<!-- Reloadable Message Bundle Context -->
<bean id="reloadableMessageBundleContext" class="ws.l10n.core.ReloadableMessageBundleContext"
    init-method="init">
   <constructor-arg name="messageBundleService" ref="l10nClient"/>
   <constructor-arg name="bundleKey" value="YOUR_BUNDLE_KEY"/>
   <constructor-arg name="bundleVersion" value="YOUR_BUNDLE_VERSION"/>
</bean>
````
Example of scheduled message context will reload messages on fixed time period by specified ```reloadPeriod``` property.

```xml
<!-- L10n Service Client -->
<bean id="l10nClient" class="ws.l10n.client.http.HttpMessageBundleClient">
   <constructor-arg name="serviceUrl" value="https://l10n.ws/api/v1"/>
   <constructor-arg name="accessToken" value="YOUR_ACCESS_TOKEN"/>
</bean>

<!-- Scheduled Message Bundle Context -->
<bean id="scheduledReloadableMessageBundleContext" class="ws.l10n.core.ScheduledReloadableMessageBundleContext"
    init-method="start" destroy-method="stop">
   <constructor-arg name="messageBundleService" ref="l10nClient"/>
   <constructor-arg name="bundleKey" value="YOUR_BUNDLE_KEY"/>
   <constructor-arg name="bundleVersion" value="YOUR_BUNDLE_VERSION"/>
   <constructor-arg name="period" value="#{60 * 60 * 1000}"/>
</bean>
```
Integration to String Framework localization and internationalization strategy.

````xml
<bean id="messageSource" class="ws.l10n.spring.L10nBundleMessageSource">
   <constructor-arg name="messageContext" ref="reloadableMessageBundleContext|scheduledReloadableMessageBundleContext"/>
</bean>
````

#### Source Code
For more details source code you can find here [https://github.com/l10nws/l10n-java](https://github.com/l10nws/l10n-java)