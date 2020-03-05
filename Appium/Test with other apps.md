## Test with other apps
You can test the scenario in which your main app interacts with some other app

BrowserStack allows you to sepcify an app or list of apps (as an array) to install prior to starting your test execution. Follow the steps below:

a. Upload the app(s) on BrowserStack <br>
<br>
API to upload the app:
```
  curl -u "akanksha48:mUsSYL3azt9pLzEYLPaX" \
  -X POST "https://api-cloud.browserstack.com/app-automate/upload" \
  -F "file=@/path/to/app/file/Application-debug.apk"
```
Sample Response:
```
 {"app_url":"bs://6fh4s8da9c5efh6fb3t2a44s6r7nc"}
```

b. Use the app_url in the `otherApps' capability in your script
```java
   "device", "Samsung Galaxy S8 Plus"
   "os_version", "7.0"
   "app", "bs:////7115de2070fe63b213f8be8a91fc0225d2eb8eb0" # Main app
   "otherApps", "bs://c947477dba4eabbf3e226640591f1b364cd87dd2","bs://7a0b613a9dd91a35398c71eee2cfebc44744fd03" # Other apps
```




