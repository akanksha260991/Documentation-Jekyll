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

### Debug - Appium logs 
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
 2020-03-04 09:58:38:322 - [Appium]   Creating new AndroidUiautomator2Driver (v0.5.2) session
 2020-03-04 09:58:38:322 - [Appium]   Capabilities:
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
