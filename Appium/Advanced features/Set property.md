# Set the propoerty for session

If you are trying to set some arguments for an Instrumentation test, you can make use of `setProp` parameter. If you pass `key1` and `value1` in the params, we set the key as *debug.test.key1 = value1*.
> **Note:** For setprop, we limit the keys to **debug.test** namespace.

<br>

| Capability       | Description                                    | Values                      |
|-------------|----------------------------------------------- | ------------------------|
| browserstack.android.setprop     | Set the property name and its associated value for your session | Format: {key1: value1, key2: value2}                         |  

Example:
```
 "browserstack.android.setprop" : "{"logKey":"DEBUG_APP"}"
```

### How to use the values set
For reading the values set in `key1`, use the `debug.test.key1` and not only `key1` in your appium test script.


> **Note:** In order to get the capability enabled for your tests, please [Contact Support](https://www.browserstack.com/contact#technical-support)

