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
