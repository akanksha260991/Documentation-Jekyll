# Gradle Plugin
### Documentation for running Espresso test using BrowserStack's Gradle Plugin.

### Getting Started
You can easily build your app and execute the test using [BrowserStack Gradle Plugin](https://github.com/browserstack/browserstack-gradle-plugin). In order to configure the plugin add below snippet in your app's build.gradle file.

#### Specify the device
```bash
plugins {
  id: com.browserstack.gradle
}

runDebugBuildOnBrowserstack {
  username = "akanksha48"
  accessKey = "mUsSYL3azt9pLzEYLPaX"
  devices = ['Samsung Galaxy S8-7.0']
}
```
>Note: You can view the [supported device](https://www.browserstack.com/list-of-browsers-and-platforms/app_automate) on BrowserStack

Execute below command to build your app and run your Espresso test
```
gradle runDebugBuildOnBrowserstack
```

This will execute the following:

1. Build debug and test apks, as dependencies are declared on assembleDebug and assembleDebugAndroidTest tasks.
2. Find the latest app apk and test apk in the app directory recursively.
3. Upload both the apks on BrowserStack server.
4. Execute Espresso test using the uploaded apps on the devices mentioned in the configuration.


#### Manadatory parameters

| Name      	| Description                                                                                                                                                           	|
|-----------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| username  	| Your BrowserStack username                                                                                                                                            	|
| accessKey 	| Your BrowserStack accessKey                                                                                                                                           	|
| devices   	| List of Device and OS version you want to run your tests on. Acceptable format is -. <br><br>**Example:**<br>```devices: ["Google Pixel-8.0", "Samsung Galaxy S8-7.1"]``` 	|

> Note: View the complete list of parameters supported

#### Optional parameters

| Name                	  | Description                                                                                                                                                                          	|
|-----------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| project               	| Your BrowserStack username                                                                                                                                                           	|
| projectNotifyURL      	| Your BrowserStack accessKey                                                                                                                                                          	|
| numShards             	| List of Device and OS version you want to run your tests on. Acceptable format is -. <br>Example:<br>```devices: ["Google Pixel-8.0", "Samsung Galaxy S8-7.1"]<br>```                	|
| shardIndex            	| Set this parameter if you want to enable the device logs                                                                                                                             	|
| class                 	| Test only some selected classes. Ex: "com.browserstack.class1,com.browserstack.class2"                                                                                               	|
| package               	| Test only some selected packages. Ex: "com.browserstack,com.browserstack1"                                                                                                           	|
| enableSpoonFramework  	| Capture the screenshots of your tests using the Spoon framework. Values: "true/false". (Default: false)                                                                              	|
| video                 	| Enable the video of the test run. Values: "true/false". Default: true                                                                                                                	|
| deviceLogs            	| Enable the device logs. Values: true/false                                                                                                                                           	|
| otherApps             	| Install apps in addition to the main app. Ex: "bs://9617605fd06f74bc6e2e703617851bf946ded26496e49ed8, bs:////8df3f698cf7678cf61d5cf85bb514e456a429346"                               	|
| uploadMedia           	| Test uploaded images/videos. Upload media using REST API and use the **media_url** returned. Ex: "media://06f74bc6e2e703617851bf946ded2649, media://698cf7678cf61d5cf85bb514e456a42" 	|
| locale                	| Change the locale to test localization of your App. Ex: "fr"                                                                                                                         	|
| language              	| Change the language to test localization of your App. Ex: "fr"                                                                                                                       	|
| geoLocation           	| Test how your app behaves in specific countries. Ex: "US"                                                                                                                            	|
| gpsLocation           	| Simulate the location of the device to a particular GPS location. Ex: "40.730610,-73.935242"                                                                                         	|
| deviceOrientation     	| Change screen orientation of mobile device. Value: "landscape/portrait". Default: Portrait                                                                                           	|
| callbackURL           	| Receive a confirmation once your test execution is completed on this url                                                                                                             	|
| annotation            	| Run tests only for particular annotations. Ex: "P1, P2"                                                                                                                              	|
| size                  	| Run tests that have @SmallTest, @MediumTest and @LargeTest annotations. Ex: "SmallTest, MediumTest"                                                                                  	|
| timezone              	| Configure tests to run on a custom time zone. Ex: "UTC" or "New_York" etc                                                                                                            	|
| local                 	| Enable local testing. Ex: "false". (Default: false)                                                                                                                                  	|
| localIdentifier       	| If you are using same account to test multiple applications, you can setup named connection using the localIdentifier option. Ex: "Test123"                                          	|
| appStoreConfiguration 	| Login to your google account on the devices in order to test the functionalities like Google Pay. Format: "{"username": "play-store-email", "password": "play-store-password"}"      	|
| disableAnimations     	| Disable animations on the device. Values: "true/false"                                                                                                                               	|
| allowDeviceMockServer 	| Set to 'true' if you are using Mock server. Local, NetworkLogs, IP geoLocation will not work if you enable this capability                                                           	|
| networkLogs           	| Set this parameter if you want to enable the Network Logs. By default it's false.                                                                                                    	|
| networkProfile        	| Simulate different network conditions from the list of existing network profiles. Ex: "2g-gprs-good"                                                                                 	|
| customNetwork         	| Simulate the custom network conditions. Format: "download speed (kbps), upload speed (kbps), latency (ms), packet loss (%)" . Ex: "1000,1000,100,1"                                  	|
