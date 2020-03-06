# Test your App Center Builds on BrowserStack
#### Use BrowserStack to seamlessly test your latest app versions on our Real Device Cloud.

### Getting Started
BrowserStack allows you to directly install the apps on the BrowserStack devices using the App Center's public download URL. Below are the steps you need to follow to generate and configure your app's public link in the test.

**Step 1: Get API token from App Center**<br>
To get started, you need to get API token from App Center. Follow these steps to generate the API token:
1. Sign in to your App Center account.
2. Visit **Account Settings** → [API Token](https://appcenter.ms/settings/apitokens)
3. Click on **New API token**
4. Name your token(eg: Integrate App Automate) and click **Create**
5. Select the **Access** as **Read only**
6. Generate and copy the API token

![AppCenter](https://d2ogrdw2mh0rsl.cloudfront.net/production/images/static/docs/app-automate/app-center/api_token@2x.jpg)

<br>
<br>

**Step 2: List all the app projects for the API Token** <br>
Use the API token generated in the previous step to get all the app projects(for the token) using the API call below:
```
curl -sX GET  "https://api.appcenter.ms/v0.1/apps" \
-H "Content-Type: application/json" \
-H "X-Api-Token: {your_api_token}"
```
Sample Response of the above API call:
```bash
[
  {
    "id": "4b563137-7f40-1er5-98e8-3e5dg66f67f3",
    "app_secret": "645b01-f6dd-40b8-a05b-49997afc098",
    "description": null,
    "display_name": "Test App",
    "name": "TestApp-3",
    "os": "iOS",
    "platform": "Objective-C-Swift",
    "origin": "appcenter",
    "icon_url": "https://rink.hockeyapp.net/api/2/apps/645b01f6dd40b8a05b49997fc098?format=png",
    "created_at": "2019-05-15T06:35:32.000Z",
    "updated_at": "2019-05-15T06:37:14.000Z",
    "release_type": "Alpha",
    "owner": {
      "id": "3b5c3438-5272-4fd9-bd1a-c13bdf48cde3",
      "avatar_url": null,
      "display_name": "Peter",
      "email": "peter@xyz.com",
      "name": "peter",
      "type": "user"
    },
    "azure_subscription": null,
    "member_permissions": [
      "manager"
    ]
  },
  {
   .......
  }
]
```
<br>
<br>

**Step 3: Fetch the latest app build information for a particular project** <br>
Use the "name" and "owner.name" (obtained in response in Step 2) to fetch the latest app build information for a particular project using the API call below:
```
curl -sX GET  "https://api.appcenter.ms/v0.1/apps/{owner.name}/{name}/releases/latest" \
-H "Content-Type: application/json" \
-H "X-Api-Token: {your_api_token}"
```

Sample Response of the above API call:
```bash
{
  "app_name": "TestApp",
  "app_display_name": "TestApp",
  "app_os": "iOS",
  "owner": {
    "name": "peter",
    "display_name": "Peter Evans"
  },
  "is_external_build": false,
  "origin": "appcenter",
  "id": 1,
  "version": "1",
  "short_version": "1.0",
  "size": 37277,
  "min_os": "9.2",
  "device_family": "iPhone/iPod/iPad",
  "bundle_identifier": "com.browserstack.sample",
  "fingerprint": "2f90a9hr4547fge8b22bde1189341a",
  "uploaded_at": "2019-05-13T12:49:11.000Z",
  "download_url": "https://rink.hockeyapp.net/api/2/apps/6efdff88d................",
  "mandatory_update": false,
  "enabled": true,
  "is_latest": true,
  "provisioning_profile_name": "match Development *",
  "provisioning_profile_type": "adhoc",
  "release_notes": "",
  "package_hashes": [
    "8cf914033f56e41d88210e2d5fee4ae860da",
    "edec0708588beaa68f16e3b05da1eb77420a"
  ],
  "destination_type": "group",
  "status": "available",
  "distribution_group_id": "5236b9-6c01-4dba-96ec-fc6d18186",
  "distribution_groups": [
    {
      "id": "5236b9-6c01-4dba-96ec-fc6d18186",
      "name": "BetaTesters",
      "origin": "appcenter",
      "display_name": "BetaTesters",
      "is_public": true
    }
  ]
}
```
The download_url (eg. https://rink.hockeyapp.net/api/2/apps/6efdff88d................) from the above API response will be used to upload your app build on BrowserStack
<br>
<br>

**Step 4: Upload the build on BrowserStack** <br>
Upload your app on BrowserStack using the API call below:
```
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/upload" \
-F "data={\"url\": \"{download_url}\"}"
```

Sample Response:
```
{ "app_url": "bs://f7c874f21852ba57957a3fdc33f47514288c4ba4" }
```
The **app_url** obtained in the response will be required in the next step to run the test on BrowserStack.

> Note: App upload will take few seconds to about a minute depending on the size of your app. Do not interrupt the curl command until you get the response back.
If you upload an iOS app, we will resign the app with our own provisioning profile to be able to install your app on our devices during test execution.
We will delete the uploaded app after 30 days from the date of upload.
<br>
<br>

**Step 5: Execute the test** <br>
For executing the test on BrowserStack, update your Appium scripts as mentioned below:

1. The app capability with the app_url obtained in the Step 4 above
   Example
   ```
   "app": "bs://f7c874f21852ba57957a3fdc33f47514288c4ba4"
   ```
2. The `device` and `os_version` capability with the device name and OS version on which you want to run the test. View the list of the available Real Mobile & Tablet Devices for automated app testing on BrowserStack.
   Example
   ```
   "device": "Samsung Galaxy S8"
   "os_version": "7.0"
   ```
3. To initialize the instance of Appium driver on BrowserStack, use the following URL:
   ```bash
   // Update your USERNAME and ACCESS_KEY
   "https://USERNAME:ACCESS_KEY@hub-cloud.browserstack.com/wd/hub"
   ```
   > Note: The BrowserStack credentials (username and accesskey) can be obtained from Settings page
   
BrowserStack supports automated mobile app tests using Appium/Espresso/XCUI frameworks, and running your tests on our cloud setup is simple and straightforward. To get started, refer to the BrowserStack documentation for [Appium](https://www.browserstack.com/docs?product=app-automate), [Espresso](https://www.browserstack.com/app-automate/espresso/get-started) and XCUITest(https://www.browserstack.com/app-automate/xcuitest/get-started). Once you run the test, you will be able to view the test result on the App Automate dashboard.
