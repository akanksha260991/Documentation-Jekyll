# Delete media files
We automatically delete your uploaded media files after 30 days from the day of upload. You can also use our REST API to explicitly delete any file before that. Here is an example API request that uses the uploaded media file's media_id to delete it :

```
curl -u "USERNAME:ACCESS_KEY" \
-X DELETE "https://api-cloud.browserstack.com/app-automate/custom_media/delete/<MediaId>"
```

If the media_id passed is correct, we will delete the uploaded file as shown in the sample response below :
```
{"success":true}
```
