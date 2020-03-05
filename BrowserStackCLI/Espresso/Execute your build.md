### Execute your Espresso build
Run your [Espresso Tests on BrowserStack](https://www.browserstack.com/app-automate/rest-api?framework=espresso). You need to pass the `app`, `testSuite` along with the `devices` on which you want to run your Espresso build.

#### USAGE
```
$ ./browserstack app-automate espresso run [flags]
```
 #### FLAGS
```
  -a, --app                     [*] Local path / Public url to .apk OR app_url(bs://<hashed_id>) of app uploaded on BrowserStack
  -t, --testSuite               [*] Local path / Public url to test .apk OR test_url(bs://<hashed_id>) of test uploaded on BrowserStack
  -d, --devices                 [*] Device(s) name. Multiple Values allowed. Format: "device_name-os_version". Ex: "Google Nexus 6-6.0,OnePlus 7-9.0"
      --project                 Group your test executions under one build. Ex: "LoginTest"
      --projectNotifyURL        Notify url for projects where we can send a confirmation once execution of all the builds under the project are completed
      --numShards               Number of shards to divide your test suite. Use shardIndex flag along with this
      --shardIndex              Specify the shard number to run a specific shard. Format: 0 to (numShards-1)
      --class                   Test only some selected classes. Ex: "com.browserstack.class1,com.browserstack.class2"
      --package                 Test only some selected packages. Ex: "com.browserstack,com.browserstack1"
      --enableSpoonFramework    Capture the screenshots of your tests using the Spoon framework. Values: "true/false". (Default: false)
      --video                   Enable the video of the test run. Values: "true/false". Default: true
      --deviceLogs              Enable the device logs. Values: true/false
      --otherApps               Install apps in addition to the main app. Ex: "bs://hashed-id-1, bs://hashed-id-2"
      --uploadMedia             Test uploaded images/videos. Upload media using REST API and use the hashed url returned. Ex: "media://hashedid-1, media://hashedid-2"
      --locale                  Change the locale to test localization of your App. Ex: "fr"
      --language                Change the language to test localization of your App. Ex: "fr"
      --geoLocation             Test how your app behaves in specific countries. Ex: "US"
      --gpsLocation             Simulate the location of the device to a particular GPS location. Ex: "40.730610,-73.935242"
      --deviceOrientation       Change screen orientation of mobile device. Value: "landscape/portrait". Default: Portrait
      --callbackURL             Receive a confirmation once your test execution is completed on this url
      --annotation              Run tests only for particular annotations. Ex: "P1, P2"
      --size                    Run tests that have @SmallTest, @MediumTest and @LargeTest annotations. Ex: "SmallTest, MediumTest"
      --timezone                Configure tests to run on a custom time zone. Ex: "UTC" or "New_York" etc
      --local                   Enable local testing. Ex: "false". (Default: false)
      --localIdentifier         If you are using same account to test multiple applications, you can setup named connection using the localIdentifier option. Ex: "Test123"
      --appStoreConfiguration   Login to your google account on the devices in order to test the functionalities like Google Pay. Format: "{"username": "play-store-email", "password": "play-store-password"}"
      --disableAnimations       Disable animations on the device. Values: "true/false"
      --allowDeviceMockServer   Set to 'true' if you are using Mock server. Local, NetworkLogs, IP geoLocation will not work if you enable this capability
      --networkLogs             Set this parameter if you want to enable the Network Logs. By default it's false.
      --networkProfile          Simulate different network conditions from the list of existing network profiles. Ex: "2g-gprs-good"
      --customNetwork           Simulate the custom network conditions. Format: "download speed (kbps), upload speed (kbps), latency (ms), packet loss (%)" . Ex: "1000,1000,100,1"
  -h, --help                    help for run
 ```

#### Example
```bash
# Execute build using the local path in `app` and `testSuite`
$ ./browserstack app-automate espresso run --app="/Users/steve/Desktop/Execute/Espresso/app-debug.apk" --testSuite="/Users/steve/Desktop/Execute/Espresso/app-debug-androidTest.apk" --devices="Samsung Galaxy S9-8.0, Google Pixel-7.1" --project="MyEspressoTest"


# Execute build using the app_url and test_url in `app` and `testSuite`
$ ./browserstack app-automate espresso run --app="bs://ca57ff53abc947d571e77c613d08cb7753bb9fad" --testSuite="bs://c8d72e7be2b0b0174b9cf492187dc549708540bc" --devices="Samsung Galaxy S9-8.0, Google Pixel-7.1" --project="MyEspressoTest"
```

#### Sample Response
```bash
 {
  "build_id": "43d43117159595ec41a018776f26e6679f3f223c",
  "message": "Success"
 }
```
