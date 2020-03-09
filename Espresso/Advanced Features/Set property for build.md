# Set the property for build

If you are trying to set some arguments for Instrumentation test, you can make use of `setProp` parameter. If you pass `key1` and `value1` in the params, we set the key as *debug.test.key1 = value1*.
> **Note:** For setprop, we limit the keys to **debug.test** namespace.

<br>

| Param       | Description                                    | Values                      |
|-------------|----------------------------------------------- | ------------------------|
| setProp     | Set the property name and its associated value | Format: {key1: value1, key2: value2}                         |  

**REST API endpoint :**
<br>
POST /app-automate/espresso/build
```bash
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/build" \
-d '{"setprop" : "{key1: value1, key2: value2}", "devices": ["Samsung Galaxy S8-7.0"], "app": "bs://f7c874f21852ba57957a3fdc33f47514288c4ba4", "testSuite": "bs://e994db8333e32a5863938666c3c3491e778352ff"}' \
-H "Content-Type: application/json" 
```

### How to use the values set
For reading the values set in the execution API above, use the `debug.test.key1` and not only `key1` in your test script.

> **Note:** In order to get the capability enabled for your tests, please [Contact Support](https://www.browserstack.com/contact#technical-support)


