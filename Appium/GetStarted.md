# Appium with Python
#### Your guide to running mobile app tests using Appium with Python on BrowserStack real device cloud.

BrowserStack gives you instant access to 2000+ real devices. Running your Appium test automation for native and hybrid mobile apps on BrowserStack is simple. This guide helps you to get started and run your first test.

## Run your first test
>Note: Running your Appium tests on BrowserStack requires a username and an access key.To obtain your username and access keys, sign up for a Free Trial or purchase a plan.

Follow 3 easy steps to get started with your first Appium test on BrowserStack cloud.

### 1. Upload your app
Upload your Android app (.apk file) or iOS app (.ipa file) to the BrowserStack servers using the REST API.

```
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/upload" \
-F "file=@/path/to/app/file/Application-debug.apk" \
-F "data={\"custom_id\": \"MyApp\"}"
```

Sample Response:
```
{"app_url":"bs://f7c874f21852ba57957a3fdc33f47514288c4ba4", "custom_id":"MyApp","shareable_id":"username/MyApp"}
```

	
**Custom Id for your app**

The custom_id is above request is optional. It enables you to set a constant value in your 'app' capability instead of updating your test code to change the App URL every time you upload an app. Use the same Custom Id for every build you upload. 


>**Note:**<br>
	1. App upload will take a few seconds to about a minute depending on the size of your app. Do not interrupt the curl command until you get the response back.<br>
	2. If you upload an iOS app, we will resign the app with our own provisioning profile to be able to install your app on our devices during test execution.<br>
	3. We will delete the uploaded app after 30 days from the date of upload.<br>

<br>

If you do not have an .apk or .ipa file and are looking to simply try App Automate, you can download our [Android sample app](https://www.browserstack.com/app-automate/sample-apps/android/WikipediaSample.apk) or [iOS sample app](https://www.browserstack.com/app-automate/sample-apps/ios/BStackSampleApp.ipa) and upload it to the BrowserStack servers using the above API.

### 2. Setup environment

//Same as current



### 3. Configure and run test
	
Copy the sample code provided in %python% for Android and iOS. Update the desired capability "app" with the App URL returned from the above API call.

//Same as the current content

<br>

### View Test Results - Dashboard

//Same as current

