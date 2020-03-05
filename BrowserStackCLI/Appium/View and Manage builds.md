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
