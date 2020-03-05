### View the builds in a project
You can group all the builds under the same project using the `project` parameter while executing the build. Use the command below to fecth all the builds under a project.
 
#### USAGE
```
$ ./browserstack app-automate espresso projects [flags]
```

#### FLAGS
```
      --project     [*] Project Name specified to group your builds
  -h, --help            help for project
```

#### Example
```bash
 ./browserstack app-automate espresso projects --project="SampleEspresso"
```

#### Sample Response
```bash
{
  "builds":  [
    {
      "app_details": {
        "bundle_id": "com.example.tipcalculator",
        "custom_id": null,
        "name": "app-debug.apk",
        "url": "bs://7115de2070fe63b213f8be8a91fc0225d2eb8eb0",
        "version": "1.0"
      },
      "build_id": "69697232ccf53b65c6ebc8a911aad3bde062823f",
      "device_statuses": {
        "error": {},
        "success": {
          "Google Pixel 3,10.0": "Success",
          "Samsung Galaxy S8,7.0": "Success"
        }
      },
      "devices": {
        "Google Pixel 3-10.0": {
          "session_details": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/...",
          "session_id": "c947477dba4eabbf3e226640591f1b364cd87dd2",
          "status": "done",
          "test_report": "https://app-automate.browserstack.com/...",
          "test_status": {
            "FAILED": 2,
            "IGNORED": 0,
            "SUCCESS": 2,
            "TIMEDOUT": 0
          }
        },
        "Samsung Galaxy S8-7.0": {
          "session_details": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/7a0b613a9dd91a35398c71eee2cfebc44744fd03",
          "session_id": "7a0b613a9dd91a35398c71eee2cfebc44744fd03",
          "status": "done",
          "test_report": "https://app-automate.browserstack.com/...",
          "test_status": {
            "FAILED": 2,
            "IGNORED": 0,
            "SUCCESS": 2,
            "TIMEDOUT": 0
          }
        }
      },
      "duration": "127 seconds",
      "framework": "espresso",
      "input_capabilities": {
        "app": "bs://7115de2070fe63b213f8be8a91fc0225d2eb8eb0",
        "devices": [
          "Samsung Galaxy S8-7.0",
          "Google Pixel 3-10.0"
        ],
        "project": "SampleEspresso",
        "testSuite": "bs://8df3f698cf7678cf61d5cf85bb514e456a429346"
      },
      "start_time": "2020-01-28 12:06:53 UTC",
      "status": "failed",
      "test_suite_details": {
        "bundle_id": "com.example.tipcalculator.test",
        "custom_id": null,
        "name": "app-debug-androidTest.apk",
        "url": "bs://8df3f698cf7678cf61d5cf85bb514e456a429346",
        "version": ""
      }
    },
    {
      "app_details": {
        "bundle_id": "com.example.perfecto.tipcalculator",
        ....
        ..
        
    }
    .....
  ]
}
```
<br>

### Get the build summary
View the overall status of your build execution and its summary e.g. app details, device executions in the build, test status on each device etc. Make use of the `Build ID` to fetch the build summary.

#### USAGE
```
$ ./browserstack app-automate espresso builds [flags]
```

#### FLAGS
```
      --build-id string     [*] Build ID
  -h, --help                    help for project
```

#### Example
```bash
 ./browserstack app-automate espresso builds --build-id="69697232ccf53b65c6ebc8a911aad3bde062823f"
```

#### Sample Response
```bash
 {
  "app_details": {
    "bundle_id": "com.example.tipcalculator",
    "custom_id": null,
    "name": "app-debug.apk",
    "url": "bs://7115de2070fe63b213f8be8a91fc0225d2eb8eb0",
    "version": "1.0"
  },
  "build_id": "69697232ccf53b65c6ebc8a911aad3bde062823f",
  "device_statuses": {
    "error": {},
    "success": {
      "Google Pixel 3,10.0": "Success",
      "Samsung Galaxy S8,7.0": "Success"
    }
  },
  "devices": {
    "Google Pixel 3-10.0": {
      "session_details": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/...",
      "session_id": "c947477dba4eabbf3e226640591f1b364cd87dd2",
      "status": "done",
      "test_report": "https://app-automate.browserstack.com/....",
      "test_status": {
        "FAILED": 2,
        "IGNORED": 0,
        "SUCCESS": 2,
        "TIMEDOUT": 0
      }
    },
    "Samsung Galaxy S8-7.0": {
      "session_details": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/...",
      "session_id": "7a0b613a9dd91a35398c71eee2cfebc44744fd03",
      "status": "done",
      "test_report": "https://app-automate.browserstack.com/...",
      "test_status": {
        "FAILED": 2,
        "IGNORED": 0,
        "SUCCESS": 2,
        "TIMEDOUT": 0
      }
    }
  },
  "duration": "127 seconds",
  "framework": "espresso",
  "input_capabilities": {
    "app": "bs://7115de2070fe63b213f8be8a91fc0225d2eb8eb0",
    "devices": [
      "Samsung Galaxy S8-7.0",
      "Google Pixel 3-10.0"
    ],
    "project": "SampleEspresso",
    "testSuite": "bs://8df3f698cf7678cf61d5cf85bb514e456a429346"
  },
  "start_time": "2020-01-28 12:06:53 UTC",
  "status": "failed",
  "test_suite_details": {
    "bundle_id": "com.example.tipcalculator.test",
    "custom_id": null,
    "name": "app-debug-androidTest.apk",
    "url": "bs://8df3f698cf7678cf61d5cf85bb514e456a429346",
    "version": ""
  }
}
```
