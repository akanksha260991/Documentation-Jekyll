# Notify on test/project completion

You can order notify when the execution of a project(or any test within a project) has completed. The callback will have the data related to your executions - status, duration etc. 

### Notify test completion
You can make use of the `callbackURL` where we can send a confirmation once your single test execution is completed. To use callback URL, you need to pass the `callbackURL` parameter in the REST API request to start Espresso test execution.

| Param       | Description                                                                                 	|
|-------------|---------------------------------------------------------------------------------------------	|
| callbackURL | Set the callback url where we can send a confirmation once your test execution is completed 	|

Example:
```bash
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/build" \
-d '{"callbackURL" : "https://jenkins.xyz.test.update.url", "devices": ["Samsung Galaxy S8-7.0"], "app": "bs://f7c874f21852ba57957a3fdc33f47514288c4ba4", "testSuite": "bs://e994db8333e32a5863938666c3c3491e778352ff"}' \
-H "Content-Type: application/json" 
```


### Notify project completion
You can make use of the `projectNotifyURL' url where we can send a confirmation once your entire build/project execution is completed on BrowserStack. To use notify URL, you need to pass the `projectNotifyURL` parameter in the REST API request to start Espresso test execution.

| Param            | Description                                                                                 	|
|------------------|---------------------------------------------------------------------------------------------	|
| projectNotifyURL |  Set the the notify url where we can send a confirmation once execution of all the builds under the project are completed|

>Note: The callback will be sent if there are no builds triggered for 5 mins with the same `project` post previous execution. Set this parameter along with `project` parameter.
Example:
```bash
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/build" \
-d '{"projectNotifyURL" : "https://jenkins.xyz.project.update.url", "devices": ["Samsung Galaxy S8-7.0"], "app": "bs://f7c874f21852ba57957a3fdc33f47514288c4ba4", "testSuite": "bs://e994db8333e32a5863938666c3c3491e778352ff"}' \
-H "Content-Type: application/json" 
```


Response:
```bash
[
  "custom_build_name": project_name,
  "project": project_name,
  "Status": "Completed"
  "builds": 
  [
      {
          "build_id": "ad38fa1b6e335192b61fe8b529656486a1bce035",
          "build_name": "Espresso App.apk",
          "status": "Error",
          "duration": "50 sec",
          "dashboard_url": "https://app-automate.browserstack.com/dashboard/v2/builds/ad38fa1b6e335192b61fe8b529656486a1bce035",
          "api_endpoint": "https://api-cloud.browserstack.com/app-automate/espresso/builds/ad38fa1b6e335192b61fe8b529656486a1bce035"    
      },
      {
          "build_id": "977660e3df7846433838a9e9224737b38de5f9a6",
          "build_name": "Espresso App.apk",
          "status": "Error",
          "duration": "50 mins",
          "dashboard_url": "https://app-automate.browserstack.com/dashboard/v2/builds/977660e3df7846433838a9e9224737b38de5f9a6",
          "api_endpoint": "https://api-cloud.browserstack.com/app-automate/espresso/builds/977660e3df7846433838a9e9224737b38de5f9a6"    
      }
      .....
      .......
  ]
]
```
