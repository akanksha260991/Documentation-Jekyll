# Upload and test custom media
#### Test the custom media files in your test. The guide helps you with the following:

1. Upload the media on BrowserStack
2. Use the uploaded media in your tests

### Upload the media
The API to upload the media file(images/videos) on BrowserStack:
```
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/upload-media" \
-F "file=@/path/to/media/file/mediaFile.jpg" \
-F "data={\"custom_id\": \"MyMedia\"}"
```

**Sample Response:**
```
{"media_url":"media://21d66a8a0471097bbf5789330129e9ab97e467e3","custom_id":"MyMedia","shareable_id":"USERNAME/MyMedia"}
```

### Use the uploaded media in your tests
After uploading the custom media files, you can use it while executing XCUI tests on BrowserStack. In order to use your uploaded images or videos in the test, make use of uploadMedia parameter in the API request to start XCUI test execution.

**REST API endpoint :**
POST /app-automate/espresso/build
| Capability  	| Description                                    	| Values                                                                                              	|
|-------------	|------------------------------------------------	|-----------------------------------------------------------------------------------------------------	|
| uploadMedia 	| Use your uploaded images or videos in the test 	| The media_url returned on the upload response.<br>Example: ["media://hashedid", "media://hashedid"] 	|

Example
```
curl -u "USERNAME:ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/build" \
-d '{"project" : "Dashboard-v2", "upload Media" : "["media://21d66a8a0471097bbf5789330129e9ab97e467e3", "media://97bbf578938a04730129e9ab921d66a98t7d89v77"]", "devices": ["iPhone 8 Plus-11.0"], "app": "bs://f5L3azt9pLzE995f49376eb1fa3c284dc321f8d", "testSuite": "bs://6eb1fa3c284ddbe9971b2d1aee0d52943b9c081"}' \
-H "Content-Type: application/json"
```

> Note: 1. Only 5 files are allowed to be passed(per test).<br>
        2. Supported format for images are JPG, JPEG, PNG, GIF, BMP
        3. Max file size allowed for images is 10MB
        4. Supported format for videos are .mp4, .mov and .3gp - Max file size allowed for videos is 50MB
 
