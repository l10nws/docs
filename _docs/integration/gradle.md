---
title: Gradle 
header: Gradle Build Integration
category: Integration
order: 5
---

Gradle build plugin that load related to configuration and include message properties files to classpath at pre-compile phase.

#### Include in project
   
````groovy
buildscript {
   repositories {
       mavenCentral()
   }
   dependencies {
       classpath 'ws.l10n:l10n-gradle-plugin:1.0.3'
   }
}
apply plugin: 'l10n-gradle-plugin'
````

#### Usage
````groovy
l10nOptions {
   serviceUrl = "https://l10n.ws/api/v1"
   accessToken = "YOUR_ACCESS_TOKEN"
   bundleKey = "YOUR_BUNDLE_KEY"
   version = "YOUR_BUNDLE_VERSION"
   path = "./src/main/resources"
}
````

#### Run
```groovy
gradle loadMessages
```

#### Source Code

For more details source code you can find here [{{ site.data.links.git_source_link }}]({{ site.data.links.git_source_link }})