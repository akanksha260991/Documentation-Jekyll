### Get the JUnit report in XML format
View the executions details of all the test cases(in your test-suite) on a device in the XML format
> Note: Each device execution is regarded as a session

#### USAGE
```
$ ./browserstack app-automate espresso sessions junit-report [flags]
```

#### FLAGS
```
  -b, --build-id       [*] Build ID
  -s, --session-id     [*] Session ID
```

#### Example
```bash
 ./browserstack app-automate espresso sessions junit-report --build-id="16ded045d014bafca58b1d16de80d340de6bcd3c" --session-id="9617605fd06f74bc6e2e703617851bf946ded264"
```

#### Sample Response
```bash
 <?xml version="1.0"?>
 <testsuites>
   <testsuite name="com.example.tipcalculator.SimpleFailTest2" tests="1" failures="1" skipped="0" timedout="0" time="2.648" timestamp="2020-01-28 12:18:17 +0000">
     <properties>
       <property session_id="9617605fd06f74bc6e2e703617851bf946ded264"/>
       <property devicename="Samsung Galaxy S8"/>
       <property os="Android"/>
       <property version="7.0"/>
     </properties>
     <testcase name="simpleFailTest2" classname="com.example.perfecto.tipcalculator.SimpleFailTest2" result="failed" test_id="9617605fd06f74bc6e2e703617851bf946ded26401445118" time="2.648" video_url="https://www.browserstack.com/s3-upload/bs-video-logs-usw/s3-us-west-1/9617605fd06f74bc6e2e703617851bf946ded264/video-9617605fd06f74bc6e2e703617851bf946ded264.mp4#t=0,4">
       <failure>android.support.test.espresso.NoActivityResumedException: Pressed back and killed the app
  at dalvik.system.VMStack.getThreadStackTrace(Native Method)
  at java.lang.Thread.getStackTrace(Thread.java:1567)
  at android.support.test.espresso.base.DefaultFailureHandler.getUserFriendlyError(DefaultFailureHandler.java:92)
  at android.support.test.espresso.base.DefaultFailureHandler.handle(DefaultFailureHandler.java:56)
  at android.support.test.espresso.ViewInteraction.runSynchronouslyOnUiThread(ViewInteraction.java:184)
  at android.support.test.espresso.ViewInteraction.doPerform(ViewInteraction.java:115)
  at android.support.test.espresso.ViewInteraction.perform(ViewInteraction.java:87)
  at android.support.test.espresso.Espresso.pressBack(Espresso.java:189)
  at com.example.perfecto.tipcalculator.SimpleFailTest2.simpleFailTest2(SimpleFailTest2.java:69)
  at java.lang.reflect.Method.invoke(Native Method)
  at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:50)
  ....
```
