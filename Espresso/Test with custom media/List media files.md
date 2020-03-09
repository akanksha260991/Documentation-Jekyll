# List media files
You can use the REST API to fetch a list of all your uploaded media files and its details such as media_name, media_url, shareable ID and upload timestamp, etc. for each file. 

> **Note:** The response will not include the deleted Media Files. We delete the media files 30 days from the date of upload.

### List recent uploads
Here is an example API request to retrieve details about your recent Media File uploads.
```
curl -u "USERNAME:ACCESS_KEY" -X GET "https://api-cloud.browserstack.com/app-automate/recent_media_files"
```
Sample Response
```
[
  {
    "media_name": "login.png",
    "media_url": "media://215637dh571f060b1bb45330129e9ab97e467e3",
    "media_id": "215637dh571f060b1bb45330129e9ab97e467e3",
    "uploaded_at": "2019-12-23 08:57:12 UTC",
    "custom_id": "Login",
    "shareable_id": "USERNAME/Login"
  },
 {
    "media_name": "payment.png",
    "media_url": "media://346dcc23060b1bb45330129e9ab97e467e3",
    "media_id": "346dcc23060b1bb45330129e9ab97e467e3",
    "uploaded_at": "2019-12-23 08:57:12 UTC",
    "custom_id": "Payment",
    "shareable_id": "USERNAME/Payment"
   }
  .......
]
```
<br>

### List recent uploads for custom ID
Here is an example API request to retrieve details about your recent Media File uploads under a specific custom id
```
curl -u "USERNAME:ACCESS_KEY" -X GET "https://api-cloud.browserstack.com/app-automate/recent_media_files/<custom_id>"
```
Sample Response 
```
[
  {
    "media_name": "login.png",
    "media_url": "media://215637dh571f060b1bb45330129e9ab97e467e3",
    "media_id": "215637dh571f060b1bb45330129e9ab97e467e3",
    "uploaded_at": "2019-12-23 08:57:12 UTC",
    "custom_id": "Login",
    "shareable_id": "USERNAME/Login"
  }
]
```
<br>

### List recent uploads for the entire group
Here is an example API request to retrieve details about your recent Media File uploads for the entire group
```
curl -u "USERNAME:ACCESS_KEY" -X GET "https://api-cloud.browserstack.com/app-automate/recent_group_media
```
Sample Response
```
[
  {
    "media_name": "cartupdate.png",
    "media_url": "media://145dfv3437dh571f060b0129e9ab97e467e3",
    "media_id": "145dfv3437dh571f060b0129e9ab97e467e3",
    "uploaded_at": "2019-12-13 08:57:12 UTC",
    "custom_id": "CartUpdate",
    "shareable_id": "USERNAME/CartUpdate"
  },
  {
    "media_name": "login.png",
    "media_url": "media://215637dh571f060b1bb45330129e9ab97e467e3",
    "media_id": "215637dh571f060b1bb45330129e9ab97e467e3",
    "uploaded_at": "2019-12-23 08:57:12 UTC",
    "custom_id": "Login",
    "shareable_id": "USERNAME/Login"
  },
 {
    "media_name": "payment.png",
    "media_url": "media://346dcc23060b1bb45330129e9ab97e467e3",
    "media_id": "346dcc23060b1bb45330129e9ab97e467e3",
    "uploaded_at": "2019-12-23 08:57:12 UTC",
    "custom_id": "Payment",
    "shareable_id": "USERNAME/Payment"
   }
  .......
]
```

