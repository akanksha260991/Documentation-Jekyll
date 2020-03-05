## List of devices
BrowserStack allows you to choose from a wide range of [physical mobile and tablets devices](https://www.browserstack.com/list-of-browsers-and-platforms/app_automate) for maximum market coverage. 

a. View all the devices (in JSON format) supported on BrowserStack:

#### USAGE
```
$ ./browserstack app-automate devices
```

#### Sample Response
The output will be a list of devices in JSON object array: 

```bash
[
  {
    "device": "iPhone XS",
    "os": "ios",
    "os_version": "13",
    "realMobile": true
  },
   {
    "device": "Samsung Galaxy S9 Plus",
    "os": "android",
    "os_version": "9.0",
    "realMobile": true
  },
  {
    "device": "Samsung Galaxy S8 Plus",
    "os": "android",
    "os_version": "9.0",
    "realMobile": true
  },
  ...
]
 ```
 <br>
 <br>

b. View all the devices (in Tabular format) supported on BrowserStack:

#### USAGE
```
$ ./browserstack app-automate devices -t
```
#### Sample Response
```
  +-----------------------------+---------+------------+------------+
  |           DEVICE            |   OS    | OS VERSION | REALMOBILE |
  +-----------------------------+---------+------------+------------+
  |                   iPhone XS |     ios |         13 |       true |
  |           iPhone 11 Pro Max |     ios |         13 |       true |
  |               iPhone 11 Pro |     ios |         13 |       true |
  |                   iPhone 11 |     ios |         13 |       true |
  |                   iPhone XS |     ios |         12 |       true |
  |               iPhone XS Max |     ios |         12 |       true |
  |                   iPhone XR |     ios |         12 |       true |
  |      Samsung Galaxy S9 Plus | android |        9.0 |       true |
  |      Samsung Galaxy S8 Plus | android |        9.0 |       true |
  |         Samsung Galaxy S10e | android |        9.0 |       true |
  |     Samsung Galaxy S10 Plus | android |        9.0 |       true |
  |          Samsung Galaxy S10 | android |        9.0 |       true |
  | Samsung Galaxy Note 10 Plus | android |        9.0 |       true |
  |      Samsung Galaxy Note 10 | android |        9.0 |       true |
  |          Samsung Galaxy A10 | android |        9.0 |       true |
  |       Samsung Galaxy Note 9 | android |        8.1 |       true |
  |     Samsung Galaxy J7 Prime | android |        8.1 |       true |
```
 
> **Note:** The first column of the command output, `DEVICE`, contains the name of the devices that you can use later to run tests on a specific model. The `OS_VERSION` column lists the operating system versions supported by that device. 
You need to specify both the `DEVICE` and `OS_VERSION` for running tests on BrowserStack.
