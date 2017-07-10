---
title: Android
header: Android Integration
category: Integration
order: 5
---

It is a Gradle build plugin capable to load related to configuration resources and include their as strings resource files according to android localization specification on pre-compile phase.

Include in project
```groovy
buildscript {
   repositories {
       mavenCentral()
   }
   dependencies {
       classpath 'ws.l10n:l10n-android-gradle-plugin:1.0.3'
   }
}
apply plugin: 'l10n-android-gradle-plugin'
```

#### Usage
````groovy
l10nOptions {
   serviceUrl = "https://l10n.ws/api/v1"
   accessToken = "YOUR_ACCESS_TOKEN"
   bundleKey = "YOUR_BUNDLE_KEY"
   version = "YOUR_BUNDLE_VERSION"

   fileName = "strings.xml"
   resourcePath = "./src/main/res"
   rewriteExisted = true // rewrite existed files, be aware that delete current content
   useRegion = true // if true directories will be in "values-en-US" style
}
````

#### Run
````groovy
gradle loadMessages
````


#### Source Code
For more details source code you can find here [https://github.com/l10nws/l10n-java](https://github.com/l10nws/l10n-java)