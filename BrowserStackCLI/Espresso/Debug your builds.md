## Debug your Espresso builds
You can debug your Espresso builds on BrowserStack using the range of debugging options available. 

#### USAGE
```
$ ./browserstack app-automate espresso debug [commands] [flags]
```

#### COMMANDS
```
 network-logs          Get the network Logs
 device-logs           Get the device logs
 app-profiling         Device Logs of your session execution
```
<br>

### Debug - Network logs
Get the Network Logs in HAR (HTTP Archive) format for the session executed on the BrowserStack's real devices

#### USAGE
```
$ ./browserstack app-automate espresso debug network-logs [flags]
```

#### FLAGS
```
  -b, --build-id      [*] Build ID
  -t, --test-id       [*] Test ID
```
  
#### Example
```bash
 $ ./browserstack app-automate appium debug text-logs --build-id="8a46fdeb1dfssdd11a168292ac0925be06yy19e8" --session-id="e015915c695bn76dcbbebc26d566t489916e53ae"
 ```
 
 #### Sample Response
```bash
 {
    "log": {
      "creator": {
        "comment": "mitmproxy version mitmproxy 4.0.4",
        "name": "mitmproxy har_dump",
        "version": "0.1"
      },
      "entries": [............],
      "version": "1.2"
   }
 }
```
<br>

### Debug - Device logs
Get the device level logs for the session executed on the BrowserStack's real devices

#### USAGE
```
$ ./browserstack app-automate espresso debug device-logs [flags]
```

#### FLAGS
```
-b, --build-id=build-id        [*] Build ID 
-s, --test-id=test-id          [*] Test ID
```

#### Example
```bash
 $ ./browserstack app-automate espresso debug device-logs --build-id="8a46fdeb1dfssdd11a168292ac0925be06yy19e8" --session-id="e015915c695bn76dcbbebc26d566t489916e53ae"
```
#### Sample Response
```bash
   03-04 12:51:07.815 E/Zygote  ( 5306): isWhitelistProcess - Process is Whitelisted
   03-04 12:51:07.816 E/libpersona( 5306): scanKnoxPersonas
   03-04 12:51:07.816 E/libpersona( 5306): Couldn't open the File - /data/system/users/0/personalist.xml - No such file or directory
   03-04 12:51:07.817 W/SELinux ( 5306): SELinux selinux_android_compute_policy_index : Policy Index[2],  Con:u:r:zygote:s0 RAM:SEPF_SM-G960F_8.0.0_0001, [-1 -1 -1 -1 0 1]
   03-04 12:51:07.817 I/SELinux ( 5306): SELinux: seapp_context_lookup: seinfo=untrusted, level=s0:c512,c768, pkgname=com.example.calculator
   03-04 12:51:07.820 I/zygote64( 5306): Late-enabling -Xcheck:jni
   03-04 12:51:07.833 I/zygote64( 5306): SuspendAllInternal: 1. proc_name -
   03-04 12:51:07.833 I/zygote64( 5306): SuspendAllInternal: 2.proc_name - zygote64
   03-04 12:51:07.856 D/TimaKeyStoreProvider( 5306): TimaKeyStore is not enabled: cannot add TimaSignature Service and generateKeyPair Service
   03-04 12:51:07.856 D/ActivityThread( 5306): Added TimaKeyStore provider
   03-04 12:51:07.892 W/System  ( 5306): ClassLoader referenced unknown path:
   03-04 12:51:07.921 I/MonitoringInstr( 5306): Instrumentation started on process com.example.calculator
   03-04 12:51:07.923 I/MonitoringInstr( 5306): Setting context classloader to 'dalvik.system.PathClassLoader[DexPathList[[zip file "/system/framework/android.test.runner.jar", zip file "/data/app/com.example.calculator.test-FT-E3kCbEbzZ0GIi_BFfeA==/base.apk", zip file "/data/app/com.example.calculator-cH9566uwUH0fROfaRugB5Q==/base.apk"],nativeLibraryDirectories=[/data/app/com.example.calculator.test-FT-E3kCbEbzZ0GIi_BFfeA==/lib/arm64, /data/app/com.example.calculator-cH9566uwUH0fROfaRugB5Q==/lib/arm64, /system/lib64, /vendor/lib64]]]', Original: 'dalvik.system.PathClassLoader[DexPathList[[zip file "/system/framework/android.test.runner.jar", zip file "/data/app/com.example.calculator.test-FT-E3kCbEbzZ0GIi_BFfeA==/base.apk", zip file "/data/app/com.example.calculator-cH9566uwUH0fROfaRugB5Q==/base.apk"],nativeLibraryDirectories=[/data/app/com.example.calculator.test-FT-E3kCbEbzZ0GIi_BFfeA==/lib/arm64, /data/app/com.example.calculator-cH9566uwUH0fROfaRugB5Q==/lib/arm64, /system/lib64, /vendor/lib64]]]'
```
<br>

### Debug - App profiling
The profiling logs help to identify where your app is making inefficient use of resources, such as the CPU, memory etc. Also, you can inspect the network traffic and helps you optimize the underlying code.

#### USAGE
```
$ ./browserstack app-automate espresso debug app-profiling [flags]
```

#### FLAGS
```
-b, --build-id=build-id        [*] Build ID 
-s, --test-id=test-id          [*] Test ID
```

#### Example
```bash
 $ ./browserstack app-automate espresso debug app-profiling --build-id="dc7a173b21f68f3c5e112fbf8f04b7f494eb6de9" --test-id="2847b9126eaf4255cb50cc048259a795dd5842760dfe00e7"
```
#### Sample Response
```bash
 [
    {
      "batt": 100,
      "comexamplecalculator_cpu": null,
      "comexamplecalculator_mem": null,
      "comexamplecalculator_netr": null,
      "comexamplecalculator_nets": null,
      "cpu": 61,
      "mem": 3396.71,
      "mema": 1549.83,
      "temp": 29,
      "ts": 1583326267
    },
    {
      "batt": 100,
      "comexamplecalculator_cpu": null,
      "comexamplecalculator_mem": null,
      "comexamplecalculator_netr": null,
      "comexamplecalculator_nets": null,
      "cpu": 50,
      "mem": 3396.71,
      "mema": 1544.87,
      "temp": 29,
      "ts": 1583326268
    },
    ...
 ]

```
