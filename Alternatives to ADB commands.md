# Alternatives to ADB commands on BrowserStack

ADB provides users a CLI to communicate with Android devices, like installing apps, granting permissions, copying files, profiling for performance etc., Learn how to achieve what the most commonly used ADB commands do on BrowserStack.

## Managing Applications

### 1. Install packages

**Using ADB**
```bash
adb install [options] package_name
adb install-multiple [options] packages
adb shell pm install [options] path
```

**Using BrowserStack**<br>
Installing packages on devices you want to run your tests on is simple.

First, you must upload your apps and obtain the app_url. Refer to [upload app section](https://www.browserstack.com/app-automate/rest-api#app-upload) to see how this can be done.

Second, mention the **app_url** of the apps you want to install, in your test scripts. The app you want to test will be your main app, and the apps your main app depends on will be the `otherApps`.
<br>

### 2. Uninstall packages

**Using ADB**
```bash
adb uninstall package
```

**Using BrowserStack**
You don't have to explicitly uninstall an app after you're done with your tests. We automatically uninstall your apps, delete the data that was added/modified during your tests and clean up the device before running another session on that device.

If you want to uninstall and reinstall a package within the same session, we recommend you to reset the app instead.
<br>

### 3. Reset the app or clear package data

**Using ADB**
```bash
adb shell pm clear package
```

**Using BrowserStack**
You can use [Appium's reset package](https://appium.io/docs/en/commands/device/app/reset-app/) functionality to clear all the data associated with the app.
<br>
<br>
<br>
## File Transfers

### 1. Copy a file or directory and its sub-directories to the device.

**Using ADB**
```bash
adb push local remote
```

**Using BrowserStack**<br>
By default, BrowserStack provides a set of images & videos you can use to test whether file uploads work fine in your app. Also, you can upload your custom media and use them in your tests.

First, [upload your custom media](https://www.browserstack.com/app-automate/rest-api?framework=appium#media-upload) to BrowserStack and obtain the **media_url**

Second, specify the **media_url** in the `browserstack.uploadMedia`' capability in your test scripts. Refer to our [capability builder](https://www.browserstack.com/app-automate/capabilities) for more details.

You can also use Appium's push file functionality, but you can only [push files](https://appium.io/docs/en/commands/device/files/push-file/) into the /data/tmp/ folder, and can pull the file from that location using Appium's pull functionality.
<br>

### 2. Copy a file or directory and its sub-directories from the device.

**Using ADB**
```bash
adb pull remote local
```

**Using BrowserStack**	
At the moment, we don't support pulling a file from the device to your local system.

If you want to take a screenshot, store it locally on the device, and retrieve it using pull command, you can use [Appium's screenshot functionality](https://appium.io/docs/en/commands/session/screenshot/) to get the screenshot in base64 or PNG format that you can write to a file locally on your machine.

You can also use BrowserStack's Screenshots functionality to generate screenshots. Just pass the `browserstack.debug` capability in your test scripts, and BrowserStack will automatically generate screenshots at various steps in your test.

You can also use Appium's pull file functionality, but you can only pull files from the /data/tmp folder. You can also [push files](https://appium.io/docs/en/commands/device/files/push-file/) to the same location using Appium's push functionality.
<br>
<br>
<br>

# Granting Permissions to Apps

### 1. Grant a permission to an app

**Using ADB**
```bash
adb shell pm grant package_name permission
```

**Using BrowserStack**	
You can auto-grant permissions passing the autoGrantPermissions capability while starting the test.

You can also handle with the permission alerts, and click the allow button during the test.
<br>


### 2. Revoke a permission from an app
**Using ADB**
```bash
adb shell pm revoke package_name permission
```

**Using BrowserStack**	
You cannot do this on BrowserStack at the moment.

If you need to perform your tests with limited permissions, we recommend you to run a new test session and allow / disallow the required permissions during the test by handling the permission alerts.
<br>
<br>
<br>

## Debugging Options

### 1. Print log data to the screen

**Using ADB**
```bash
adb logcat [options]
```

**Using BrowserStack**	
You can access these logs in the Device Logs section of the test session page in your [App Automate dashboard](https://app-automate.browserstack.com/)

You can also retrieve these logs via the [REST API](https://www.browserstack.com/app-automate/rest-api?framework=appium#sessions)
<br>
<br>
<br>

## Working with Android Activity & Animations

### 1. Start an Activity specified by intent

**Using ADB**
```bash
adb shell am start [options] intent
```

**Using BrowserStack**	
You can use [Appium's start activity](https://appium.io/docs/en/commands/device/activity/start-activity/) functionality to start an Android activity by providing package name and activity name.
<br>

### 2. Force stop everything associated with package

**Using ADB**
```bash
adb shell am force-stop package
```

**Using BrowserStack**	
You can use [Appium's close app functionality](https://appium.io/docs/en/commands/device/app/close-app/) to force stop and close your application.

Remember that you can only force stop your main application (specified by the app capability ), but not the applications your main application depends on (the ones specified in otherApps capability).
<br>

### 3. Disable system animations to speed up your tests and improve stability

**Using ADB**
```bash
adb shell am instrument --no-window-animation [options]
```

**Using BrowserStack**	
You can now use Appium's capability disableWindowAnimation to disable system's window animations.

Remember that you need to also set the browserstack.appium_version capability to 1.9.1 or later because this capability is not available in the older versions of Appium.
<br>
<br>
<br>

## Screen Capture & Recording

### 1. Capture a screenshot and save it to file

**Using ADB**
```bash
adb shell screencap filename
```

**Using BrowserStack**	
You use BrowserStack's Screenshots functionality to generate screenshots. Just pass the browserstack.debug capability in your tests' desired capabilities, and BrowserStack will automatically generate screenshots at various steps in your test so that you can consume them / debug using them later.

You can use Appium's screenshot functionality to get the screenshot in base64 or PNG format that you can write to a file locally on your machine.

### 2. Record display of devices

**Using ADB**
```bash
adb shell screenrecord [options] filename
```

**Using BrowserStack**	
You can use `browserstack.video` capability in your tests scripts if you want to enable video recording during your test.

Remember that you need to also set the `browserstack.appium_version` capability to 1.9.1 or later because this capability is not available in the older versions of Appium.
<br>
<br>
<br>

## App Profiling

### Get the battery consumption, memory/CPU utilization and network performance

**Using ADB**
```bash
adb dumpsys [options]
```

**Using BrowserStack**	<br>
You can get this information from your App Automate dashboard on the test session page.
> **Note:** App profiling is only available for Android.

