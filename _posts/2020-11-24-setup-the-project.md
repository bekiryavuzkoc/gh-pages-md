---
title: Set up the Project
description: 5
---

You can download the codelab project from: [https://github.com/huaweicodelabs/VideoKit/tree/master/PlayVideosWithVideoKit](https://github.com/huaweicodelabs/VideoKit/tree/master/PlayVideosWithVideoKit).



**Creating a Project**
----------------------

**Step 1**: Start Android Studio.

**Step 2**: Choose **File** \> **Open**, go to the directory where the
sample project is decompressed, and click **OK**.

<img style="width: 376.00px" src="https://raw.githubusercontent.com/bekiryavuzkoc/testRepo/gh-pages/assets/videokitcodelab.PNG" onclick="imageclick(src)">

**Step 3**: Configure the AppGallery Connect plug-in, Maven repository
address, build dependencies, obfuscation scripts, and permissions.
(These items have been configured in the sample code. If any of them
does not meet your requirements, change it in your own project.)
**1. Configure the Maven repository address and AppGallery Connect
plug-in in the project's build.gradle file.**

- Go to **allprojects** \> **repositories** and configure the Maven
  repository address for the HMS Core SDK.

  
  
  ```
  allprojects {
          repositories {
              maven { url 'https://developer.huawei.com/repo/' }
            ...
          }
      }
  ```
  
- Go to **buildscript** \> **repositories** and configure the Maven
  repository address for the HMS Core SDK.

      buildscript {
              repositories {
                 maven {url 'https://developer.huawei.com/repo/'}
                  ...
              }
              ...
          }

- Go to **buildscript** \> **dependencies** and add build
  dependencies.

      buildscript {
              dependencies {
                              //Replace {agconnect_version} with the actual AGC plugin version number.
                              //Example: classpath 'com.huawei.agconnect:agcp: 1.4.1.300'
                  classpath 'com.huawei.agconnect:agcp:{agconnect_version}'
              }
          }

**2. Configure the dependency package in the app's build.gradle file.**

- Add a dependency package to the **dependencies** section in the
  **build.gradle** file.

      dependencies {
              ...
                      //Video Kit
              implementation 'com.huawei.hms:videokit-player:1.0.1.300'
              ...
          }


  For Video Kit, please refer to [latest
  version](https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/version-change-history-0000001050199403).

- Add the following information under **apply plugin:
  'com.android.application'** in the file header:

      apply plugin: 'com.huawei.agconnect'

**3. Configure obfuscation scripts.**

- Configure the following information in the
  **app/proguard-rules.pro** file:

              -ignorewarnings
              -keepattributes *Annotation*
              -keepattributes Exceptions
              -keepattributes InnerClasses
              -keepattributes Signature
              -keepattributes SourceFile,LineNumberTable
              -keep class com.hianalytics.android.**{*;}
              -keep class com.huawei.updatesdk.**{*;}
              -keep class com.huawei.hms.**{*;}

- If you are using AndResGuard, add it to the allowlist in the
  obfuscation script file.

              "R.string.hms*",
              "R.string.connect_server_fail_prompt_toast",
              "R.string.getting_message_fail_prompt_toast",
              "R.string.no_available_network_prompt_toast",
              "R.string.third_app_*",
              "R.string.upsdk_*",
              "R.layout.hms*",
              "R.layout.upsdk_*", 
              "R.drawable.upsdk*",
              "R.color.upsdk*", 
              "R.dimen.upsdk*",
              "R.style.upsdk*",
              "R.string.agc*"

**4. Configure permissions in the AndroidManifest.xml file.**

    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
    <uses-permission android:name="com.huawei.permission.SECURITY_DIAGNOSE"/>


**Step 4**: In the Android Studio window, choose **File** \> **Sync
Project with Gradle Files** to synchronize the project.