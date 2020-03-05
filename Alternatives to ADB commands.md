# Alternatives to ADB commands on BrowserStack

ADB provides users a CLI to communicate with Android devices, like installing apps, granting permissions, copying files, profiling for performance etc., Learn how to achieve what the most commonly used ADB commands do on BrowserStack.

### Managing Applications

#### Install packages

**Using ADB**
```bash
adb install [options] package_name
adb install-multiple [options] packages
adb shell pm install [options] path
```

**Using BrowserStack**
Installing packages on devices you want to run your tests on is simple.

First, you must upload your apps and obtain the app_url. Refer to [upload app section](https://www.browserstack.com/app-automate/rest-api#app-upload) to see how this can be done.

Second, mention the **app_url** of the apps you want to install, in your test scripts. The app you want to test will be your main app, and the apps your main app depends on will be the `otherApps`.

#### Uninstall packages

**Using ADB**
```bash
adb uninstall package
```

**Using BrowserStack**
You don't have to explicitly uninstall an app after you're done with your tests. We automatically uninstall your apps, delete the data that was added / modified during your tests and clean up the device before running another test session on that device.

If you want to uninstall the package, and reinstall it during the same session, we recommend you to reset the app instead.

