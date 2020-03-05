## Execute your XCUI build
 Run your [XCUITests on BrowserStack](https://www.browserstack.com/app-automate/xcuitest/get-started). You need to pass the `app`, `testSuite` along with the `devices` on which you want to run your XCUI build.

 #### USAGE
```
$ ./browserstack app-automate xcuitest run [flags]
```
 #### FLAGS
```
  -a, --app string                   [*] Local path / Public url to .ipa OR app_url(bs://<hashed_id>) of app uploaded on BrowserStack
  -t, --testSuite string             [*] Path to the .zip OR test_url(bs://<hashed_id>) of test uploaded on BrowserStack
  -d, --device strings               [*] List of Devices for test execution. Ex: "Google Nexus 6-6.0"
      --project string               Group your test executions. Ex: "MySampleTest"
      --projectNotifyURL             Notify url for projects where we can send a confirmation once execution of all the builds under the project are completed
      --debugscreenshots string      Save the screenshots automatically captured by XCode. Ex: "true"
      --only-testing strings         To test only some selected classes or tests. Ex: "XCUITestsPackage/XCUITestsClass","XCUITestsPackage/XCUITestsClass/testAlert"
      --skip-testing strings         Skip particular classes or tests from testing. Ex: "SampleXCUITestsPackage/SampleXCUITestsClass/testAlertTest"
      --callbackURL string           Receive a confirmation once your test execution is completed
      --setEnvVariables string       Pass key and value pairs to be set in the environment variable. "{"key1": "value1", "key2": "value2"}"
      --local string                 Enable local testing. Default: "false"
      --localIdentifier              If you are using same account to test multiple applications, you can setup named connection using the localIdentifier option. Ex: "Test123"
      --acceptInsecureCerts          Avoid invalid certificate errors while using self-signed certificate to test your app. Value: "true/false". Default: false"
      --video string                 Enable the video of the test run. Values: "true/false". Default: true
      --deviceLogs string            Enable the device logs. Values: true/false
      --networkLogs                  Set this parameter if you want to enable the Network Logs. By default it's false.
      --geoLocation                  Test how your app behaves in specific countries. Ex: "US"
      --gpsLocation                  Simulate the location of the device to a particular GPS location. Ex: "40.730610,-73.935242"
      --uploadMedia                  Test uploaded images/videos. Upload media using REST API and use the hashed url returned. Ex: "media://hashedid, media://hashedid"
      --locale                       Change the locale to test localization of your App. Ex: "fr"
      --language                     Change the language to test localization of your App. Ex: "fr"
      --networkProfile               Simulate different network conditions from the list of existing network profiles. Ex: "2g-gprs-good"
      --customNetwork                Simulate the custom network conditions. Format: "download speed (kbps), upload speed (kbps), latency (ms), packet loss (%)" . Ex: "1000,1000,100,1"
      --deviceOrientation string     Change screen orientation of mobile device. Values: "portrait/landscape". Default: "portrait"
  -h, --help                         help for run
 ```

 #### Example
```bash
$ ./browserstack app-automate xcuitest run --app "app-debug.ipa" --testSuite "app-debug-Test.zip" --device "
iPhone 7-12.0" --device "iPhone X-11" --projectname "MyXCUITest" --only-testing "SampleXCUITestsClass/SampleXCUITestsPackage"
```
