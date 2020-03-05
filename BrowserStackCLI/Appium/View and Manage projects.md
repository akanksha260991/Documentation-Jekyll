## View and manage the projects
Projects are organizational structures for builds executed on BrowserStack. Fetch the list of all the projects and manage them.
#### USAGE
```
$ browserstack app-automate appium projects [command]
```

 #### COMMANDS
```
list                     List of recent projects
info                     Get info about a project                             
delete                   Delete a project
```
<br>
<br>

### View the list of projects
List all the recent projects of your account. Once the list of projects is available, more specific information about a specific project can be queried using project ID.
 
#### USAGE
```
$ ./browserstack app-automate appium projects list
```

#### Sample Response
```bash
[
  {
    "created_at": "2020-03-03T08:22:42.000Z",
    "group_id": 2,
    "id": 124114,
    "name": "RunSampleTests",
    "sub_group_id": 0,
    "updated_at": "2020-03-03T16:44:22.000Z",
    "user_id": 3934023
   },
  {
    "created_at": "2020-03-03T11:01:54.000Z",
    "group_id": 2,
    "id": 124133,
    "name": "RunLocalTest",
    "sub_group_id": 0,
    "updated_at": "2020-03-03T11:01:54.000Z",
    "user_id": 788534
  }
  ....
]
```
<br>
<br>

### Get project info
Get info about a project of your account using the required flag `Project ID`.
 
#### USAGE
```
$ ./browserstack app-automate appium projects info [flags]
```

#### FLAGS
```
-p, --project-id=project-id        [*] Project ID
```

#### Example
```bash
 ./browserstack app-automate appium projects info --project-id=124133
```

#### Sample Response
```bash
 {
  "project": {
    "builds": [
      {
        "automation_project_id": 124133,
        "created_at": "2020-03-03T11:01:54.000Z",
        "delta": true,
        "duration": 122,
        "framework": "appium",
        "group_id": 2,
        "hashed_id": "a0aa593ce24797665cad15d00b3dca8fc278f50c",
        "id": 844509,
        "name": "Appium Sample Test",
        "status": "timeout",
        "sub_group_id": 0,
        "tags": null,
        "test_data": {},
        "updated_at": "2020-03-03T11:03:56.000Z",
        "user_id": 788534
      },
      {...}
      ....
    ],
    "created_at": "2020-03-03T11:01:54.000Z",
    "group_id": 2,
    "id": 124133,
    "name": "RunSampleTests",
    "sub_group_id": 0,
    "updated_at": "2020-03-03T11:01:54.000Z",
    "user_id": 788534
  }
}
```
<br>
<br>

### Delete a project
Delete a project of your account using the required flag `Project ID`. 
> Note that to delete a project, it needs to be empty of builds and sessions

#### USAGE
```
$ ./browserstack app-automate appium projects delete [flags]
```

#### FLAGS
```
-p, --project-id=project-id        [*] Project ID
```
