# Capture screenshots
#### Capture the screenshots of your tests to help debug better

Spoon has the ability to take screenshots during your tests. This allows for visual inspection of test executions across devices.
If you want to capture the screenshots of your tests using the Spoon framework, use `enableSpoonFramework` while executing the espresso test on BrowserStack:

| Param               	| Values          | Description                                               |
|----------------------	|---------------- | --------------------------------------------------------- |
| enableSpoonFramework 	| true/false(**Default:** false)            | Set the parameter if you want to capture the screenshots of your tests 	|


### View Screenshots on App Automate dashboard 
You can view the screenshots under **Screenshots** tab inside the **Test Details** Page in [App Automate Dashboard](https://app-automate.browserstack.com/dashboard)


![screenshots](https://github.com/akanksha260991/Documentation-Jekyll/blob/master/Screenshot%202020-03-09%20at%2012.59.51%20PM.png)
<br>
Example:
```
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/build" \
-d '{"enableSpoonFramework" : true, "devices": ["Samsung Galaxy S8-7.0"], "app": "bs://f7c874f21852ba57957a3fdc33f47514288c4ba4", "testSuite": "bs://e994db8333e32a5863938666c3c3491e778352ff"}' \
-H "Content-Type: application/json" 
```

>Note: See the [espresso-app-browserstack](https://github.com/browserstack/espresso-browserstack) sample app for more details on integrating Spoon framework. Render the screenshots for your build using the [Espresso API](https://www.browserstack.com/app-automate/rest-api?framework=espresso#sessions).


