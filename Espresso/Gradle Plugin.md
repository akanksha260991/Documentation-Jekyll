# Gradle Plugin
#### Documentation for running Espresso test using BrowserStack's Gradle Plugin.

> Note: The new major version of Browserstack espresso gradle plugin 3.0.0 is released. User now needs to create a json config file and specify it in the configFilePath as mentioned in the steps below. Also, the command runDebugBuildOnBrowserstack has now been deprecated.


### Getting Started
The plugin allows to build your app, debug-app and execute the Espresso tests on BrowserStack. Github: [BrowserStack Gradle Plugin](https://github.com/browserstack/browserstack-gradle-plugin).

#### Step 1: Add to build.gradle
In order to configure the plugin, add the following dependencies and parameters in your app-level build.gradle file:

**a.Add the BrowserStack plugin dependencies**
Add the dependency and the lines that defines the plugin task as shown:

```bash
buildscript {
  repositories {
    ...
    maven {
      url "https://plugins.gradle.org/m2/"
    }
  }
  dependencies {
    classpath "gradle.plugin.com.browserstack.gradle:browserstack-gradle-plugin:3.0.0"
  }
}
...
apply plugin: "com.browserstack.gradle"
...
```

**b. Add browserStackConfig parameters**
Add the following lines to authenticate user and load configurations from the json configuration file(details about the config file explained in next step):

```bash
browserStackConfig {
    username = "akanksha48"
    accessKey = "mUsSYL3azt9pLzEYLPaX"
    configFilePath = "path/to/your/json/configFile"
}
```
> Note: username, accessKey and configFilePath are mandatory for starting tests using gradle plugin for espresso
<br>


#### Step 2: Create an Espresso configuration file
In this step, you need to create JSON text file that contains all espresso related parameters for configuring your test execution on BrowserStack. These parameters include specifying the devices, debugging options, using device features and so on.

**Select a device**

{Add device seletor widget}

**Sample configuration file**

```bash
{
    "devices":
    ['Google Pixel 3-9.0'],

    "project": "EspressoGradleTest"
    "deviceLogs": true,
    "networkLogs": true,
    .....
}
```
> Note: To view the list of all supported parameters for Espresso tests on BrowserStack, visit complete list of API parameters section inside our Espresso Get Started documentation

#### Step 3: Execute

To build your app and run your Espresso test, execute the command below:

```bash
gradle clean executeDebugTestsOnBrowserstack
```

This will execute the following:

1. Build debug and test apks, as dependencies are declared on assembleDebug and assembleDebugAndroidTest tasks.
2. Find the latest app apk and test apk in the app directory recursively.
3. Upload both the apks on BrowserStack server.
4. Execute Espresso test using the uploaded apps on the devices mentioned in the configuration.

On successful task execution, the test results will be available on the command-line interface, as well as the App Automate dashboard.

**Sample command-line output:**

```bash
Most recent DebugApp apk: /Users/{username}/AndroidStudioProjects/espresso-browserstack/app/build/outputs/apk/debug/app-debug.apk
Most recent TestApp apk: /Users/{username}/AndroidStudioProjects/espresso-browserstack/app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk

App upload Response Code : 200
{"app_url":"bs://83c5dab1adac36004b5f6fc72d9d3136c17e3b5c"}

TestSuite upload Response Code : 200
{"test_url":"bs://83c5dab1adac36004b5f6fc72d9d3136c17e3b5c"}

Response Code : 200
{"message":"Success","build_id":"5a2bac8e53d4786bc2895316badc92299ee22fb9"}
View build status at https://app-automate.browserstack.com/builds/5a2bac8e53d4786bc2895316badc92299ee22fb9
```

**Note:**
For running tests on a project with no variants, you can simply run following command for uploading and running tests on the debug apk:

```bash
gradle clean execute${buildVariantName}TestsOnBrowserstack
```

For projects with productFlavors, replace ${buildVariantName} with your build variant name, for example if your productFlavor name is "phone" and you want to test debug build type of this variant then command will be:

```bash
gradle clean executePhoneDebugTestsOnBrowserstack
```
