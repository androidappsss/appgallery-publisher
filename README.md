# Gallery Publisher Gradle Plugin
[![CircleCI](https://circleci.com/gh/yamilmedina/appgallery-publisher.svg?style=shield&circle-token=4fac8f5649a93768e700226e7943e9eaa9995ff2)](https://circleci.com/gh/yamilmedina/appgallery-publisher)

<img src="content/logo.png" width=180 />

`Gallery Publisher` is a Gradle plugin that allows the publication of an artifact to Huawei's App Gallery store, inspired by [AutoPlay][3] plugin.

## Assumptions and features

* The plugin assumes that you previously assemble your APK.
* You also have the `com.android.application >= 3.0.1` plugin applied to your project.

## Configuration and requirements

1. Create an API Client: Please refer to Huawei's [HMS Core API Documentation][1] 'Creating an API Client' section.

2. Add the repository to your buildscript block:
```
buildscript {
  repositories {
    maven {
        url "https://plugins.gradle.org/m2/"
    }
  }
  dependencies {
    classpath "com.yamilmedina:gallery-publisher:<version>"
  }
}
```

3. Then, add your configuration accordingly in your app module `build.gradle` file:
```
apply plugin: 'com.android.application'
apply plugin: 'com.yamilmedina.gallery-publisher'

galleryPublisher {
    appId = "YOUR_APP_ID_FROM_CONSOLE"
    clientId = "YOUR_CLIENT_ID_FROM_CONSOLE"
    clientSecret = "YOUR_CLIENT_SECRET_FROM_CONSOLE"
    artifactPath = "PATH_TO_YOUR_APK_LOCATION"
}
```
## [appgallery](https://apkapp.gallery/)

## Usage

When you execute `./gradlew tasks` you will see a new publishing task `appGalleryPublish<BuildVariant>` in the list. 

```
./gradlew appGalleryPublishProdRelease
```

## License

Free use of Gallery Publisher Gradle is permitted under the guidelines and in accordance with the [Apache License 2.0][2] 

[1]: https://developer.huawei.com/consumer/en/service/hms/catalog/AGCConnectAPI.html?page=hmssdk_appGalleryConnect_getstarted#Creating%20an%20API%20Client
[2]: https://opensource.org/licenses/Apache-2.0
[3]: https://github.com/beworker/autoplay
