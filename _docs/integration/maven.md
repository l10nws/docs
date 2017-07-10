---
title: Maven 
header: Maven Build Integration
category: Integration
order: 4
---

It is a Maven build plugin that load related to configuration and include message properties files to classpath at pre-compile phase.

#### Include in project

Library published in maven central repository.
````xml
<plugin>
    <groupId>ws.l10n</groupId>
    <artifactId>l10n-maven-plugin</artifactId>
    <version>1.0.3</version>
    <configuration>
        <serviceUrl>https://l10n.ws/api/v1</serviceUrl>
        <accessToken>YOUR_ACCESS_TOKEN</accessToken>
        <bundleKey>YOUR_BUNDLE_KEY</bundleKey>
        <version>YOUR_BUNDLE_VERSION</version>
        <baseName>messages</baseName>
        <path>./src/main/resources</path>
    </configuration>
    <executions>
        <execution>
            <phase>compile</phase>
            <goals>
                <goal>loadMessages</goal>
         </goals>
        </execution>
    </executions>
</plugin>
````
#### Run
````groovy
mvn l10n-maven-plugin:loadMessages
````


#### Source Code
For more details source code you can find here [https://github.com/l10nws/l10n-java](https://github.com/l10nws/l10n-java)