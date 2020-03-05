### View device executions for your build
View the overall status of your build execution and device executions in the build. Also, view the JUnit report for each device execution.

#### USAGE
```
$ ./browserstack app-automate espresso sessions [flags]
```

#### COMMANDS
```
  info                Get the info about the sessions executions on device
  junit-report        Access test reports in the standard JUnit XML format. Reports available for each session inside a build
```
<br>

### Get info about a device execution of a build
View the executions details of all the test cases(in your test-suite) on a device.
> Note: Each device execution is regarded as a session

#### USAGE
```
$ ./browserstack app-automate espresso sessions info [flags]
```

#### FLAGS
```
  -b, --build-id       [*] Build ID
  -s, --session-id     [*] Session ID
```

#### Example
```bash
 ./browserstack app-automate espresso sessions info --build-id="16ded045d014bafca58b1d16de80d340de6bcd3c" --session-id="9617605fd06f74bc6e2e703617851bf946ded264"
```

#### Sample Response
```bash
 {
  "acceptInsecureCerts": "false",
  "app_details": {
    "bundle_id": "com.example.tipcalculator",
    "custom_id": null,
    "name": "app-debug.apk",
    "url": "bs://7115de2070fe63b213f8be8a91fc0225d2eb8eb0",
    "version": "1.0"
  },
  "build_id": "16ded045d014bafca58b1d16de80d340de6bcd3c",
  "coverage": null,
  "device": "Samsung Galaxy S8-7.0",
  "deviceLogs": "true",
  "duration": "20",
  "idle_timeout": "900",
  "networkLogs": "false",
  "screenshots": null,
  "session_id": "9617605fd06f74bc6e2e703617851bf946ded264",
  "start_time": "2020-01-28 12:17:41 +0000",
  "test_count": 4,
  "test_details": {
    "com.example.tipcalculator.TestClear": {
      "simpleFailTest": {
        "device_log": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/tests/.../devicelogs",
        "duration": "1.784",
        "instrumentation_log": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/tests/.../instrumentationlogs",
        "network_log": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/tests/.../networklogs",
        "screenshots": [
          "https://s3-us-west-1.amazonaws.com/bs-selenium-logs-usw/.../.../screenshots/\"\""
        ],
        "start_time": "2020-01-28 12:18:22 +0000",
        "status": "FAILED",
        "test_id": "9617605fd06f74bc6e2e703617851bf946ded26496e49ed8",
        "video": "https://www.browserstack.com..."
      }
    },
    "com.example.tipcalculator.TestAddition": {
      "simpleFailTest2": {
        "device_log": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/tests/.../devicelogs",
        "duration": "2.648",
        "instrumentation_log": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/tests/.../instrumentationlogs",
        "network_log": "https://api.browserstack.com/app-automate/espresso/builds/.../sessions/tests/../networklogs",
        "screenshots": [
          "https://s3-us-west-1.amazonaws.com/bs-selenium-logs-usw/.../.../screenshots/\"\""
        ],
        "start_time": "2020-01-28 12:18:17 +0000",
        "status": "FAILED",
        "test_id": "9617605fd06f74bc6e2e703617851bf946ded26401445118",
        "video": "https://www.browserstack.com/..."
      }
    },
    "com.example.tipcalculator.TestButtons": {
      "simpleTest": {
        ....
      },
      "simpleTest1": {
        ....
      }
    }
  },
  "test_status": {
    "FAILED": 2,
    "IGNORED": 0,
    "QUEUED": 0,
    "SUCCESS": 2,
    "TIMEDOUT": 0
  },
  "test_suite_details": {
    "bundle_id": "com.example.tipcalculator.test",
    "custom_id": null,
    "instrumentation": "android.support.test.runner.AndroidJUnitRunner",
    "name": "app-debug-androidTest.apk",
    "url": "bs://8df3f698cf7678cf61d5cf85bb514e456a429346"
  },
  "video": "true"
}
```
