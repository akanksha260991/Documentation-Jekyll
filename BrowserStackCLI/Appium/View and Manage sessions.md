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
