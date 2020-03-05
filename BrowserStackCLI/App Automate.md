## App Automate
Run your automated Mobile app tests on the real mobile devices offeref by BrowserStack. We currently support Appium, Espresso and XCUITest automation frameworks.

#### USAGE
```
$ ./browserstack app-automate [commands] [flags]
```

 #### COMMANDS
```
  apps                Manage your uploaded mobile apps on BrowserStack
  testsuite           Manage your TestSuite for different Frameworks (Espresso/XCUITest)
  espresso            Run your Espresso mobile app tests
  xcuitest            Run your XCUITest mobile app tests
  appium              View and manage your appium tests executed on BrowserStack's real devices.
  plan-status         Get plan details - Number of parallels allowed, currently running and queued
  devices             List of all Devices available for Testing
```

 #### FLAGS
```
    --config          Config file for your tests. Default: $HOME/.browserstack-cli.yaml
-h, --help            Help for  Browserstack CLI
```
