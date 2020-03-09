# Set IdleTimeout for test executions

You can set the idle timeout duration for the Espresso test. In order to set the timeout value, you need to pass the `idleTimeout` parameter as shown in the table below.

REST API endpoint :
POST /app-automate/espresso/build
| Parameter   	| Description                                                                                        	| Values                                                                           	|
|-------------	|----------------------------------------------------------------------------------------------------	|----------------------------------------------------------------------------------	|
| idleTimeout 	| <br>Set this parameter to specify the maximum time limit for which your tests can remain idle.<br> 	| Accepted values are between 60 sec to 900 sec. <br>The default value is 900 sec. 	|

Example :
```bash
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/xcuitest/build" \
-d '{"idleTimeout" : "800", "devices": ["Samsung Galaxy S8-7.0"], "app": "bs://f5L3azt9pLzE995f49376eb1fa3c284dc321f8d", "testSuite": "bs://6eb1fa3c284ddbe9971b2d1aee0d52943b9c081"}' \
-H "Content-Type: application/json" 
```
