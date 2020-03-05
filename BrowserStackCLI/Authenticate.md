### Authenticate
Before you can upload an app or manage your test executions, you first need to authenticate yourself with your BrowserStack ```Username``` and ```Access-Key```. You can view your credentials on App Automate dashboard or [Account Summary](https://www.browserstack.com/accounts/settings)

#### USAGE
```
$ ./browserstack authenticate [flags]
```

#### FLAGS
```
      --username      To identify you as a unique user on BrowserStack account. You can fetch the info from https://www.browserstack.com/accounts/settings
      --access-key    Private BrowserStack key associated with your account. You can fetch the info from https://www.browserstack.com/accounts/settings
  -h, --help          help for authenticate
```

#### Example
```bash
$ ./browserstack authenticate --username=your_username --access-key=your_access_key
```
