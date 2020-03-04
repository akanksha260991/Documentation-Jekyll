# BrowserStack CLI - App Automate (Beta)

#### Set of simple commands to upload apps, manage your test executions and much more. Setup and use BrowserStack CLI for your automated mobile app testing


## Introduction
BrowserStack App Automate allows you to manage your app testing on our cloud-based infrastructure by providing full integration with the command-line interface (CLI). Follow the steps below to setup BrowserStack CLI on your machine:

1. Download the BrowserStack binary for CLI

  * [OS X 32-bit (10.7 and above)](https://browserstack.com/browserstack-cli/download?arch=386&file=browserstack&os=darwin&version=1.0.0)
  * [OS X 64-bit (10.7 and above)](https://browserstack.com/browserstack-cli/download?arch=amd64&file=browserstack&os=darwin&version=1.0.0)
  * [Linux 32-bit](https://browserstack.com/browserstack-cli/download?arch=386&file=browserstack&os=linux&version=1.0.0)
  * [Linux 64-bit](https://browserstack.com/browserstack-cli/download?arch=amd64&file=browserstack&os=linux&version=1.0.0)
  * [Windows 32-bit (XP and above)](https://browserstack.com/browserstack-cli/download?arch=386&file=browserstack.exe&os=windows&version=1.0.0)
  * [Windows 64-bit (XP and above)](https://browserstack.com/browserstack-cli/download?arch=amd64&file=browserstack.exe&os=windows&version=1.0.0)

2. Open your terminal and navigate to the folder containing the BrowserStack CLI binary.

3. Make the BrowserStack CLI executable. For MAC and Linux machines run the following command: 
   <br>
   ```bash
   chmod +x browserstack
   ```

<br> 

## Getting Started
Give your users a seamless experience by testing on 2000+ real devices.  To get started, run the command below to explore the list of available options.

#### USAGE
```
$ ./browserstack [commands] [flags]
```

#### COMMANDS
```
  authenticate        Set/Update your BrowserStack credentials
  app-automate        Automated mobile app testing on Real Mobile devices
  update              Update browserstack-cli to the latest version
  version             Print the version number of BrowserStack CLI
  help                Help about any command
```

#### FLAGS
```
      --config        Config file for your tests. Default: $HOME/.browserstack-cli.yaml
  -h, --help          help for browserstack
```

> **Note**: To know more about any specific command, use the help flag as shown below:
```
$ ./browserstack [command] --help
```
<br>

### Authenticate
Before you can upload an app or manage your test executions, you first need to authenticate yourself with your BrowserStack ```Username``` and ```Access-Key```. You can view your credentials on App Automate dashboard or [Account Summary](https://www.browserstack.com/accounts/settings)

#### USAGE
```
$ ./browserstack authenticate [flags]
```

#### FLAGS
```
      --username      To identify you as a unique user on BrowserStack account. You can fetch the info from https://www.browserstack.com/accounts/settings
      --access-key    Private BrowserStack key associated with your account. You can fetch the info from https://www.browserstack.com/accounts/settings
  -h, --help          help for authenticate
```

#### Example
```bash
$ ./browserstack authenticate --username=your_username --access-key=your_access_key
```
<br>

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
<br>
<br>

## Upload and manage your apps
Manage your apps uploaded on BrowserStack. Upload, delete or view the list of uploaded apps.
> **Note**: We will delete the uploaded app after 30 days from the date of upload

#### USAGE
```
$ ./browserstack app-automate apps [commands] [flags]
```

#### COMMANDS
```
  upload               Upload app on BrowserStack
  list                 List apps uploaded on BrowserStack
  delete               Delete app uploaded on BrowserStack
```
<br>
<br>

### Upload your app
Upload your app on BrowserStack using the required flags `path`/ `url` and `framework`. 
> Note:  App upload will take few seconds to about a minute depending on the size of your app. If you upload an iOS app, we will resign the app with our own provisioning profile to be able to install your app on our devices during test execution. We delete the uploaded app after 30 days from the date of upload
 
#### USAGE
```
$ ./browserstack app-automate apps upload [flags]
```

#### FLAGS
```
  -p, --path          [*] Local path to your app
  -u, --url           [*] Public URL of app
      --custom-id     Set a custom ID to the uploaded app. It allows to upload multiple apps under same name
  -h, --help          help for upload
```

#### Example
```bash
# Upload from local system
$ ./browserstack app-automate apps upload --path="/Users/steve/Desktop/WikipediaSample.apk" --custom-id="MyApp"

# Upload from URL
$ ./browserstack app-automate apps upload --url="https://www.browserstack.com/app-automate/sample-apps/android/WikipediaSample.apk" --custom-id="MyApp"
```

#### Sample Response
```bash
{ 
  "app_url": "bs://24488aa367ec83fd95a6079e3d7e26134277e48d",
  "custom_id": "MyApp",
  "shareable_id": "steve/MyApp" 
}
```
> **Note:** custom_id is optional. You can upload multiple builds under same custom_id. Use custom_id in `app` capability for Appium to always pick the last uploaded build. 
<br>
<br>

### Delete your app
Delete an app using the required flag `app`. The `app` is the app_url (bs://...) of the app uploaded on BrowserStack.
 
#### USAGE
```
$ ./browserstack app-automate apps delete [flags]
```

#### FLAGS
```
-a, --app              [*] app_url (bs://....) of the app the user want to delete
-h, --help                 help for delete
```

#### Example
```bash
$ ./browserstack app-automate apps delete --app="bs://de6cc2c44ddb49efbb48c775387b9832fec5c2bb"
```
<br>
<br>

### List your apps
Get the list of uploaded apps on Browserstack. The response is presented in the JSON format
 
#### USAGE
```
$ ./browserstack app-automate apps list
```

#### Sample Response
```bash
[
  {
    "app_id": "d176369c9a01870f255f421c4f43998819a05252",
    "app_name": "BrowserStack-SampleApp.apk",
    "app_url": "bs://d176369c9a01870f255f421c4f43998819a05252",
    "app_version": "1.0",
    "uploaded_at": "2020-03-03 12:36:29 UTC"
  },
  {
    "app_id": "fcda17ab57e090aac278092c45a4d2b8431a2f34",
    "app_name": "BrowserStack-SampleApp.ipa",
    "app_url": "bs://fcda17ab57e090aac278092c45a4d2b8431a2f34",
    "app_version": "1.0",
    "custom_id": "SampleApp",
    "shareable_id": "steve/MyApp",
    "uploaded_at": "2020-02-26 10:30:56 UTC"
  },
  ....
]
```
<br>
<br>

## Manage your test-suite
Upload and manage your test-suite for testing your apps using Espresso or XCUITest framework. Espresso test-suite has .apk format and XCUITest has .ipa format. 
 
#### USAGE
```
$ ./browserstack app-automate testsuite [commands] [flags]
```

#### COMMANDS
```
  upload            Upload test suite on BrowserStack
  list              List the recent test suites uploaded on BrowserStack
  delete            Delete test suite uploaded on BrowserStack
```

#### FLAGS
```
  --config      Config file for your tests. Default: $HOME/.browserstack-cli.yaml
  -h, --help    help for testsuite
```
<br>
<br>

### Upload your test-suite
Upload TestSuite to BrowserStack using the required flags `path`/`url` and `framework`.
 
#### USAGE
```
$ browserstack app-automate testsuite upload [flags]
```

#### FLAGS
```
  -p, --path          [*] Local path of test suite
  -u, --url           [*] Public URL of test suite
  -f, --framework     [*] test suite framework. Values: espresso/xcuitest
      --custom_id     Set a custom_id to uploaded test suite. It allows to upload multiple apps under same name
  -h, --help          help for upload
```

#### Example
```bash
# Upload from local system
$ ./browserstack app-automate testsuite upload --path="/path/to/my/testsuite/directory/apps-debug-Test.apk" --framework="espresso"  --custom_id="MyTest"

# Upload from URL
$ ./browserstack app-automate testsuite upload --url="https://www.browserstack.com/app-automate/sample-apps/android/CalculatorTest.apk" --framework="espresso"  --custom_id="MyTest"
```
#### Sample Response
```bash
{
  "test_url": "bs://74beb90e8e32710ddddd2c1d684898e0434a4dd1",
  "custom_id": "MyTest",
  "shareable_id": "akanksha48/MyTest"
}
```
<br>
<br>

### Delete your test-suite
Delete a test-suite using the required flag `testsuite`. The `testsuite` is the test_url (bs://...) of the test-suite uploaded on BrowserStack.
 
#### USAGE
```
$ ./browserstack app-automate testsuite delete [flags]
```

#### FLAGS
```
  -f, --framework       [*] test suite framework. Values: espresso/xcuitest
      --testsuite       [*] test_url (bs://...) of the uploaded test on the BrowserStack servers
  -h, --help                help for delete
```

#### Example
```bash
$ ./browserstack app-automate testsuite delete --testsuite="bs://f946e972e7d0cdd394ada763f13ab14628a1b5fd" --framework "espresso"
```
<br>
<br>

### List your test suites
Get the list of uploaded test-suites on Browserstack. The response is presented in the JSON format
 
#### USAGE
```
$ ./browserstack app-automate testsuite list [flags]
```

#### FLAGS
```
  -f, --framework       [*] test suite framework. Values: espresso/xcuitest
  -h, --help            help for list
```

#### Sample Response
```bash
[
  {
    "custom_id": "MyTest"
    "framework": "espresso",
    "test_suite_id": "f946e972e7d0cdd394ada763f13ab14628a1b5fd",
    "test_suite_name": "CalculatorTest.apk",
    "test_suite_url": "bs://f946e972e7d0cdd394ada763f13ab14628a1b5fd",
    "uploaded_at": 1582702377
  },
  {
    "custom_id": null,
    "framework": "espresso",
    "test_suite_id": "c8d72e7be2b0b0174b9cf492187dc549708540bc",
    "test_suite_name": "app-debug-androidTest.apk",
    "test_suite_url": "bs://c8d72e7be2b0b0174b9cf492187dc549708540bc",
    "uploaded_at": 1582634949
  }
  ...
]
```
<br>
<br>


## List of devices
BrowserStack allows you to choose from a wide range of [physical mobile and tablets devices](https://www.browserstack.com/list-of-browsers-and-platforms/app_automate) for maximum market coverage. 

a. View all the devices (in JSON format) supported on BrowserStack:

#### USAGE
```
$ ./browserstack app-automate devices
```

#### Sample Response
The output will be a list of devices in JSON object array: 

```bash
[
  {
    "device": "iPhone XS",
    "os": "ios",
    "os_version": "13",
    "realMobile": true
  },
   {
    "device": "Samsung Galaxy S9 Plus",
    "os": "android",
    "os_version": "9.0",
    "realMobile": true
  },
  {
    "device": "Samsung Galaxy S8 Plus",
    "os": "android",
    "os_version": "9.0",
    "realMobile": true
  },
  ...
]
 ```
 <br>
 <br>

b. View all the devices (in Tabular format) supported on BrowserStack:

#### USAGE
```
$ ./browserstack app-automate devices -t
```
#### Sample Response
```
  +-----------------------------+---------+------------+------------+
  |           DEVICE            |   OS    | OS VERSION | REALMOBILE |
  +-----------------------------+---------+------------+------------+
  |                   iPhone XS |     ios |         13 |       true |
  |           iPhone 11 Pro Max |     ios |         13 |       true |
  |               iPhone 11 Pro |     ios |         13 |       true |
  |                   iPhone 11 |     ios |         13 |       true |
  |                   iPhone XS |     ios |         12 |       true |
  |               iPhone XS Max |     ios |         12 |       true |
  |                   iPhone XR |     ios |         12 |       true |
  |      Samsung Galaxy S9 Plus | android |        9.0 |       true |
  |      Samsung Galaxy S8 Plus | android |        9.0 |       true |
  |         Samsung Galaxy S10e | android |        9.0 |       true |
  |     Samsung Galaxy S10 Plus | android |        9.0 |       true |
  |          Samsung Galaxy S10 | android |        9.0 |       true |
  | Samsung Galaxy Note 10 Plus | android |        9.0 |       true |
  |      Samsung Galaxy Note 10 | android |        9.0 |       true |
  |          Samsung Galaxy A10 | android |        9.0 |       true |
  |       Samsung Galaxy Note 9 | android |        8.1 |       true |
  |     Samsung Galaxy J7 Prime | android |        8.1 |       true |
```
 
> **Note:** The first column of the command output, `DEVICE`, contains the name of the devices that you can use later to run tests on a specific model. The `OS_VERSION` column lists the operating system versions supported by that device. 
You need to specify both the `DEVICE` and `OS_VERSION` for running tests on BrowserStack.
<br>
<br>

## View the plan status
Get the information about your group's App Automate plan, including your plan name, maximum number of parallel sessions allowed, the number of parallel sessions currently running and the number of parallel sessions queued.
 
#### USAGE
```
$ ./browserstack app-automate plan-status
```

#### Sample Response
 The output will be in JSON format: 

```bash
 {
  "automate_plan": "App Automate",
  "parallel_sessions_max_allowed": 25,
  "parallel_sessions_running": 0,
  "queued_sessions": 0,
  "queued_sessions_max_allowed": 25,
  "team_parallel_sessions_max_allowed": 25
}
 ```
> **Note**: The plan-status can be helpful for polling how many parallels are being used at any given point and add more tests once your used parallels get available.
<br>
<br>
<br>


## Manage your Appium test executions
Run your Appium test scripts on BrowserStack [App Automate](https://www.browserstack.com/app-automate/rest-api?framework=appium) by updating the code snippets with the BrowserStack's authentication keys and desired capabilities. View and manage your Appium test automation scripts executed on BrowserStack's real devices using the following command:

#### USAGE
```
$ ./browserstack app-automate appium [commands] [flags]
```

#### COMMANDS
```
  projects            View and Manage all the projects associated with your account
  builds              View and Manage all the builds associated with your account
  sessions            View and Manage all the sessions associated with your builds
  debug               Range of debugging tools provided by BrowserStack to easily debug your test automation for native and hybrid mobile apps
```
<br>
<br>

## View and manage the projects
Projects are organizational structures for builds executed on BrowserStack. Fetch the list of all the projects and manage them.
#### USAGE
```
$ browserstack app-automate appium projects [command]
```

 #### COMMANDS
```
list                     List of recent projects
info                     Get info about a project                             
delete                   Delete a project
```
<br>
<br>

### View the list of projects
List all the recent projects of your account. Once the list of projects is available, more specific information about a specific project can be queried using project ID.
 
#### USAGE
```
$ ./browserstack app-automate appium projects list
```

#### Sample Response
```bash
[
  {
    "created_at": "2020-03-03T08:22:42.000Z",
    "group_id": 2,
    "id": 124114,
    "name": "RunSampleTests",
    "sub_group_id": 0,
    "updated_at": "2020-03-03T16:44:22.000Z",
    "user_id": 3934023
   },
  {
    "created_at": "2020-03-03T11:01:54.000Z",
    "group_id": 2,
    "id": 124133,
    "name": "RunLocalTest",
    "sub_group_id": 0,
    "updated_at": "2020-03-03T11:01:54.000Z",
    "user_id": 788534
  }
  ....
]
```
<br>
<br>

### Get project info
Get info about a project of your account using the required flag `Project ID`.
 
#### USAGE
```
$ ./browserstack app-automate appium projects info [flags]
```

#### FLAGS
```
-p, --project-id=project-id        [*] Project ID
```

#### Example
```bash
 ./browserstack app-automate appium projects info --project-id=124133
```

#### Sample Response
```bash
 {
  "project": {
    "builds": [
      {
        "automation_project_id": 124133,
        "created_at": "2020-03-03T11:01:54.000Z",
        "delta": true,
        "duration": 122,
        "framework": "appium",
        "group_id": 2,
        "hashed_id": "a0aa593ce24797665cad15d00b3dca8fc278f50c",
        "id": 844509,
        "name": "Appium Sample Test",
        "status": "timeout",
        "sub_group_id": 0,
        "tags": null,
        "test_data": {},
        "updated_at": "2020-03-03T11:03:56.000Z",
        "user_id": 788534
      },
      {...}
      ....
    ],
    "created_at": "2020-03-03T11:01:54.000Z",
    "group_id": 2,
    "id": 124133,
    "name": "RunSampleTests",
    "sub_group_id": 0,
    "updated_at": "2020-03-03T11:01:54.000Z",
    "user_id": 788534
  }
}
```
<br>
<br>

### Delete a project
Delete a project of your account using the required flag `Project ID`. 
> Note that to delete a project, it needs to be empty of builds and sessions

#### USAGE
```
$ ./browserstack app-automate appium projects delete [flags]
```

#### FLAGS
```
-p, --project-id=project-id        [*] Project ID
```
<br>
<br>

## View and manage builds
Builds are organizational structures for tests. Fetch the list of all the builds and manage them. 
 
#### USAGE
```
$ ./browserstack app-automate appium builds [commands] [flags]
```

#### COMMANDS
```
list                       List the recent builds
delete                     Delete a build
session-list               List of all sessions within a build
```
<br>
<br>

### View the list of builds
List the recent builds of your account.

#### USAGE
```
$ ./browserstack app-automate appium builds list
```

#### Sample Response
 ```bash
 [ 
  {
     "automation_build": {
       "duration": 1731351,
       "hashed_id": "83ba386a86e081e94e3727354839ea89ed928214",
       "name": "Mobile OPS",
       "status": "failed"
     }
   },
   {
     "automation_build": {
       "duration": 8992929,
       "hashed_id": "da09a401ee0750d8b4d7701475e2929b160dbf65",
       "name": "Hitesh - Android",
       "status": "failed"
     }
   }
   ...
   ..
 ]
 ```
<br>
<br>

### Delete a build
Delete a build of your account using the required flag `Build ID`.
> Note: Deleting a build will delete all the sessions contained within it.

#### USAGE
```
$ ./browserstack app-automate appium builds delete [flags]
```

#### FLAGS
```
 -b, --build-id=build-id       [*] Build ID
```
<br>
<br>

### Get the list of sessions inside a build
Retrieve a list of sessions under a particular build using the required flag `Build ID`

#### USAGE
```
$ ./browserstack app-automate appium builds sessions-list [flags]
```

#### FLAGS
 ```
 -b, --build-id=build-id        [*] Build ID
 ```

#### Example
```
 ./browserstack app-automate appium builds sessions-list --build-id=83ba386a86e081e94e3727354839ea89ed928214
```

#### Sample Response
```bash
 [
  {
    "automation_session": {
      "app_details": {
        "app_custom_id": null,
        "app_name": "org.wikipedia.alpha",
        "app_url": "bs://c700ce60cf13ae8ed97705a55b8e022f13c5827c",
        "app_version": "2.5.194-alpha-2017-05-30",
        "uploaded_at": "2019-09-25T10:02:11.000Z"
      },
      "appium_logs_url": "https://api.browserstack.com/app-automate/builds/.......",
      "browser": null,
      "browser_url": "https://app-automate.browserstack.com/builds.......",
      "browser_version": "app",
      "build_name": "Mobile OPS",
      "device": "Google Pixel 4",
      "device_logs_url": "https://api.browserstack.com/app-automate/builds/.../sessions/.../devicelogs",
      "duration": 38,
      "hashed_id": "379f2d097119cce908ed71ce6bd862ebedb4e0c0",
      "logs": "https://app-automate.browserstack.com/builds/.../sessions/.../logs",
      "name": "Pixel 4 Play Store Login",
      "os": "android",
      "os_version": "10.0",
      "project_name": "Untitled Project",
      "public_url": "https://app-automate.browserstack.com/builds/.../sessions/...?auth_token=...",
      "reason": "start-error",
      "status": "error",
      "video_url": "https://app-automate.browserstack.com......."
    }
  },
  {
    "automation_session": {
      "app_details": {
        "app_custom_id": null,
        "app_name": "org.wikipedia.alpha",
        "app_url": "bs://c700ce60cf13ae8ed97705a55b8e022f13c5827c",
        "app_version": "2.5.194-alpha-2017-05-30",
        "uploaded_at": "2019-09-25T10:02:11.000Z"
      },
      "appium_logs_url": "https://api.browserstack.com/app-automate/builds/.../sessions/.../appiumlogs",
      "browser": null,
      "browser_url": "https://app-automate.browserstack.com/builds/.../sessions/...",
      "browser_version": "app",
      "build_name": "Mobile OPS",
      "device": "Google Pixel 4",
      "device_logs_url": "https://api.browserstack.com/app-automate/builds/.../sessions/.../devicelogs",
      "duration": 39,
      "hashed_id": "21366a38df449d17b2eacf72d240a6cd4cfca9a7",
      "logs": "https://app-automate.browserstack.com/builds/.../sessions/.../logs",
      "name": "Pixel 4 Play Store Login",
      "os": "android",
      "os_version": "10.0",
      "project_name": "Untitled Project",
      "public_url": "https://app-automate.browserstack.com/builds/.../sessions/...?auth_token=...",
      "reason": "start-error",
      "status": "error",
      "video_url": "https://app-automate.browserstack.com/....."
    }
  },
  ...
]
```
<br>
<br>
<br>

## View and manage sessions
Session is one device execution on BrowserStack. Fetch all the sessions associated with your different builds.

#### USAGE
```
$ ./browserstack app-automate appium sessions [command] [flags]
```

#### COMMANDS
```
info                  Get info of a session
api-status            Mark your session/test as Passed/Failed. You can also pass a reason for failure if required
delete                Delete a session
 ```
<br>
<br>

### Get session info
Once the list of sessions is available, more specific information about a particular session can be queried by using the required flag `Session ID`

#### USAGE
```
$ ./browserstack app-automate appium sessions info [flags]
```

#### FLAGS
```
-s,  --session-id=session-id   [*] Session ID
 ```
<br>
<br>

### Set status for a session
Mark your Appium sessions as Passed/Failed. The required flags are `Session ID` and `Status`. Also `reason`(optional) for failure can be specified e.g "Element Not Found"

#### USAGE
```
$ ./browserstack app-automate appium sessions set-status [flags]
```

#### FLAGS
```  
  -s, --session-id     [*] Session ID.
      --status         [*] Set the status as passed/failed
      --reason             Pass a reason for the failure/success
```

#### Example
```
 ./browserstack app-automate appium sessions set-status --session-id=379f2d097119cce908ed71ce6bd862ebedb4e0c0 --status="passed" --reason="Assertion failed"
```

#### Sample Response
```bash
  {
   "automation_session": {
     "browser": null,
     "browser_version": "app",
     "build_name": "Mobile OPS",
     "device": "Google Pixel 4",
     "duration": 38,
     "hashed_id": "379f2d097119cce908ed71ce6bd862ebedb4e0c0",
     "name": "Pixel 4 Play Store Login",
     "os": "android",
     "os_version": "10.0",
     "project_name": "Untitled Project",
     "reason": "Assertion failed",
     "status": "passed"
    }
  }
```
<br>
<br>


## Debug your Appium tests
You can debug your Appium script executions on BrowserStacks using range of debugging options available. 

#### USAGE
```
$ ./browserstack app-automate appium debug [commands] [flags]
```

#### COMMANDS
```
 text-logs         Session Logs in text format.
 device-logs       Device Logs of your session execution.
 appium-logs       Appium Logs of your session execution.
 network-logs      Network Logs in HAR (HTTP Archive) format
```
<br>
<br>

### Debug - Text logs
Get the logs for all your requests and responses for the session executed on BrowserStack's real devices

#### USAGE
```
$ ./browserstack app-automate appium debug text-logs  [flags]
```

#### FLAGS
```
-b, --build-id=build-id        [*] Build ID 
-s, --session-id=session-id    [*] Session ID
```
  
#### Example
```bash
 $ ./browserstack app-automate appium debug text-logs --build-id="8a46fdeb1dfssdd11a168292ac0925be06yy19e8" --session-id="e015915c695bn76dcbbebc26d566t489916e53ae"
 ```
 
 #### Sample Response
```bash
   2020-3-4 9:23:35:394 SESSION_SETUP_TIME {"initialising_device":6134}
   2020-3-4 9:23:35:394 SESSION_SETUP_TIME  {"downloading_app":892,"installing_app":26344,"setting_up_appium":5441,"setting_up_network_connection":4189}
   2020-3-4 9:23:47:423 SESSION_SETUP_TIME {"launching_app":12029}
   2020-3-4 9:23:47:429 REQUEST [2020-3-4 9:23:47:429] POST /session {"desiredCapabilities":{"build":"Appium Sample","name":"single_test","device":"Google Pixel","osVersion":"7.1","platformName":"android","browserstack.debug":true,"browserstack.networkLogs":true,"app":"sample_app","acceptSslCert":false,"detected_language":"appium/ruby_lib_core/3.5.0 (selenium/3.141.0 (ruby macosx))"}}
   2020-3-4 9:23:47:429 START_SESSION
   2020-3-4 9:23:47:429 REQUEST [2020-3-4 9:23:47:430] GET /session/bf6379b137d93539b516beb07a0fa50be731cb03
   2020-3-4 9:23:47:430 RESPONSE {"status":0,"value":{"device":"google pixel","osVersion":"7.1","platformName":"Android","browserstack.debug":"true","browserstack.networkLogs":"true","acceptSslCert":true........"chromeOptions":{"w3c":false},"browserstack.minOSVersion":"4.1","appPackage":"org.wikipedia.alpha","appActivity":"org.wikipedia.main.MainActivity","bundleID":"org.wikipedia.alpha","browserstack.deviceLogs":"true","nativeWebScreenshot":true,"version":"","mobile": {"browser":"mobile","version":"Google Pixel-7.1"},
 ....
 ...

```
<br>
<br>

### Debug - Device Logs
Get the device level logs for the session executed on the BrowserStack's real devices

#### USAGE
```
$ ./browserstack app-automate appium debug device-logs [flags]
```

#### FLAGS
```
-b, --build-id=build-id        [*] Build ID 
-s, --session-id=session-id    [*] Session ID
```

#### Example
```bash
 $ ./browserstack app-automate appium debug device-logs --build-id="8a46fdeb1dfssdd11a168292ac0925be06yy19e8" --session-id="e015915c695bn76dcbbebc26d566t489916e53ae"
```
#### Sample Response
```bash
 03-04 09:23:46.540 I/art     ( 4400): Starting a blocking GC Explicit
 03-04 09:23:46.553 I/art     ( 4400): Explicit concurrent mark sweep GC freed 3427(191KB) AllocSpace objects, 0(0B) LOS  objects, 40% free, 4MB/7MB, paused 227us total 12.511ms
 03-04 09:23:46.608 D/ApplicationLoaders( 4400): ignored Vulkan layer search path /data/app/com.android.chrome-1/lib/arm64:/data/app/com.android.chrome-1/base.apk!/lib/arm64-v8a for namespace 0x77ea77e0f0
 03-04 09:23:46.610 I/WebViewFactory( 4400): Loading com.android.chrome version 78.0.3904.62 (code 390406237)
 03-04 09:23:46.673 I/cr_LibraryLoader( 4400): Time to load native libraries: 2 ms
 03-04 09:23:46.689 I/chromium( 4400): [INFO:library_loader_hooks.cc(51)] Chromium logging enabled: level = 0, default verbosity = 0
 03-04 09:23:46.690 I/cr_LibraryLoader( 4400): Expected native library version number "78.0.3904.62", actual native library version number "78.0.3904.62"
 03-04 09:23:46.691 W/System  ( 4400): ClassLoader referenced unknown path:
 03-04 09:23:46.692 D/ApplicationLoaders( 4400): ignored Vulkan layer search path /data/app/com.android.chrome-1/lib/arm64:/data/app/com.android.chrome-1/base.apk!/lib/arm64-v8a for namespace 0x77ea77e160
 03-04 09:23:46.744 I/cr_BrowserStartup( 4400): Initializing chromium process, singleProcess=true
 03-04 09:23:46.750 W/ResourceType( 4400): Failure getting entry for 0x7f130537 (t=18 e=1335) (error -2147483647)
 03-04 09:23:46.789 E/chromium( 4400): [ERROR:filesystem_posix.cc(89)] stat /data/user/0/org.wikipedia.alpha/cache/WebView/Crashpad: No such file or directory (2)
 03-04 09:23:46.789 E/chromium( 4400): [ERROR:filesystem_posix.cc(62)] mkdir /data/user/0/org.wikipedia.alpha/cache/WebView/Crashpad: No such file or directory (2)
 .....
 ...
```
<br>
<br>

### Debug - Network logs 
Get the Network Logs in HAR (HTTP Archive) format for the session executed on the BrowserStack's real devices

#### USAGE
```
$ ./browserstack app-automate appium debug network-logs [flags]
```
 
#### FLAGS
```
-b, --build-id=build-id          [*] Build ID 
-s, --session-id=session-id      [*] Session ID 
```

#### Example
```bash
 $ ./browserstack app-automate appium debug network-logs --build-id="8a46fdeb1dfssdd11a168292ac0925be06yy19e8" --session-id="e015915c695bn76dcbbebc26d566t489916e53ae"
```
#### Sample Response
```bash
....
[
 log": {
    "version": "1.2",
    "creator": {
      "name": "mitmproxy har_dump",
      "version": "0.1",
      "comment": "mitmproxy version mitmproxy 4.0.4"
    },
    "entries": [
        .....
        "startedDateTime": "2020-03-04T09:58:56.423053+00:00",
        "time": 284,
        "request": {
          "method": "GET",
          "url": "https://en.wikipedia.org/w/api.php?.....",
          "httpVersion": "HTTP/2.0",
          "cookies": [
            {
              "name": "GeoIP",
              "value": "US:FL:Miami:25.85:-80.18:v4",
              "httpOnly": false,
              "secure": false
            },
            {
              "name": "WMF-Last-Access-Global",
              "value": "04-Mar-2020",
              "httpOnly": false,
              "secure": false
            },
            {
              "name": "WMF-Last-Access",
              "value": "04-Mar-2020",
              "httpOnly": false,
              "secure": false
            }
          ],
          "headers": [
            {
              "name": ":authority",
              "value": "en.wikipedia.org"
            },
            {
              "name": "accept-encoding",
              "value": "gzip"
            },
            {
              "name": "user-agent",
              "value": "WikipediaApp/2.5.194-alpha-2017-05-30 (Android 7.1; Phone) Alpha Channel"
            },
            ....
    ]
]

```
<br>
<br>

## Debug - Appium logs 
Get the Logs for your Appium Sessions executed on the BrowserStack's real devices

#### USAGE
```
$ ./browserstack app-automate appium debug appium-logs [flags]
```
 
#### FLAGS
```
  -b, --build-id=build-id          [*] Build ID 
  -s, --session-id=session-id      [*] Session ID
```

#### Example
```bash
 $ ./browserstack app-automate appium debug appium-logs --build-id="8a46fdeb1dfssdd11a168292ac0925be06yy19e8" --session-id="e015915c695bn76dcbbebc26d566t489916e53ae"
```

#### Sample Response
```bash
 2020-03-04 09:58:38:322 - [Appium] Creating new AndroidUiautomator2Driver (v0.5.2) session
 2020-03-04 09:58:38:322 - [Appium] Capabilities:
 2020-03-04 09:58:38:323 - [Appium]   device: 'google pixel'
 2020-03-04 09:58:38:323 - [Appium]   osVersion: '7.1'
 2020-03-04 09:58:38:324 - [Appium]   platformName: 'Android'
 2020-03-04 09:58:38:324 - [Appium]   browserstack.debug: 'true'
 2020-03-04 09:58:38:324 - [Appium]   browserstack.networkLogs: 'true'
 2020-03-04 09:58:38:324 - [Appium]   acceptSslCert: true
 2020-03-04 09:58:38:324 - [Appium]   detected_language: 'appium/ruby_lib_core/3.5.0 (selenium/3.141.0 (ruby macosx))'
 2020-03-04 09:58:38:324 - [Appium]   os_version: '7.1'
 2020-03-04 09:58:38:325 - [Appium]   deviceName: 'Android'
 2020-03-04 09:58:38:325 - [Appium]   sessionName: 'single_test'
 2020-03-04 09:58:38:325 - [Appium]   buildName: 'Ruby Appium Sample'
 2020-03-04 09:58:38:325 - [Appium]   browserstack.useChromeDriver: 'true'
 ...
```
<br>
<br>
<br>



## Test your Espresso builds
BrowserStack supports Espresso automated mobile app tests using Java , and running your tests on our cloud setup of Real Devices

#### USAGE
```
$ ./browserstack app-automate espresso [commands] [flags]
```

 #### COMMANDS
 ```
 run                     Execute your Espresso tests on Browserstack's Real Devices
 ```
 <br>
 <br>
  
## browserstack app-automate espresso run
 
 #### DESCRIPTION
 Run your [Espresso Tests on BrowserStack](https://www.browserstack.com/app-automate/rest-api?framework=espresso) using the required flags `app`, `testSuite`, `device`

 #### USAGE
```
$ browserstack app-automate espresso run [flags]
```
 #### FLAGS
```
     --app                     [*] Local path of app or app_url(bs://<hashed_id>) of app uploaded on BrowserStack
     --testSuite               [*] Local path of test app or test_url(bs://<hashed_id>) of app uploaded on the BrowserStack
 -d, --device                  [*] Device name. Format: devicename-os_version. Values: -d = Google Nexus 6-6.0.
     --projectname                 Set project name to group your test executions under one build
     --devicelogs                  Device Logs for your tests. Value: true/false
     --numShards                   Break test cases into shards
     --shardIndex                  Specify the shard number to run a specific shard. Values: 0 to (numShards-1)
     --local                       Enable local testing. Value: true/false (Default Value = false)
     --video                       Enable/Disable the video of the test run. Value: true/false (Default Value = true) 
     --orientation                 Change screen orientation of mobile. Value: portrait/landscape (Default Value = portrait)
     --help
 ```
> Note: In order to shard your tests, both `numShards` and `shardIndex` are required flags. E.g To break test cases into four shards and run only the first shard the flag values will be --numShards 4 and --shardIndex 0
<br>

> Note: For executing the test in multiple devices, use the `device` flag multiple times.

 #### Example
```bash
$ browserstack app-automate espresso run --app "app-debug.apk" --testSuite "app-debug-Test.apk" --device "Google Nexus 6-6.0" --device "Samsung Galaxy S9-8.0" --projectname "MyEspressoTest" --numShard 4 --shardIndex 0
```
<br>
<br>
<br>

## RUN XCUITEST ON BROWSERSTACK
Run your XCUITests for iOS on BrowserStack [App Automate](https://www.browserstack.com/app-automate/rest-api?framework=espresso). You can run your XCUITest via the CLI using the following set of commands:


 #### DESCRIPTION
BrowserStack supports XCUITest framework for iOS mobile app testing, and running your tests on our cloud setup is simple and straightforward.
 
 #### USAGE
```
$ browserstack app-automate xcuitest [command]
```
#### COMMANDS
 ```
 run                     Execute your XCUITests on Browserstack's Real Devices
 ```
 <br>
 <br>
 
 ## browserstack app-automate xcuitest run
 
 #### DESCRIPTION
 Run your [XCUITests on BrowserStack](https://www.browserstack.com/app-automate/xcuitest/get-started) using the required flags `app`, `testSuite`, `device`. The test suite needs to be a zip file.

 #### USAGE
```
$ browserstack app-automate xcuitest run [flags]
```
 #### FLAGS
```
     --app                     [*] Local path of app or app_url(bs://<hashed_id>) of app uploaded on BrowserStack
     --testSuite               [*] Local path of test app or test_url(bs://<hashed_id>) of app uploaded on the BrowserStack
 -d, --device                  [*] Device name. Format: devicename-os_version. Values: -d = Google Nexus 6-6.0.
     --projectname                 Set project name to group your test executions under one build
     --devicelogs                  Device Logs for your tests. Value: true/false
     --only-testing                Specify the selected classes to be tested. Multiple values allowed
     --local                       Enable local testing. Value: true/false (Default Value = false)
     --video                       Enable/Disable the video of the test run. Value: true/false (Default Value = true) 
     --orientation                 Change screen orientation of mobile. Value: portrait/landscape (Default Value = portrait)
     --help
 ```
<br>

> Note For executing the test in multiple devices, use the `device` or `d` flag multiple times.  

 #### Example
```bash
$ browserstack app-automate xcuitest run --app "app-debug.ipa" --testSuite "app-debug-Test.zip" --device "
iPhone 7-12.0" --device "iPhone X-11" --projectname "MyXCUITest" --only-testing "SampleXCUITestsClass/SampleXCUITestsPackage"
```

