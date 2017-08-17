# Authentication

The GFW API uses JWT Tokens to identify and authenticate users.

## How to generate your own Oauth Token

To generate your own token, follow the next steps:

1. Navigate to [http://ui.resourcewatch.org:82](http://ui.resourcewatch.org:82)
If you aren't logged in yet, the application will redirect you to the login page.
You will see:
![Control Tower login page](images/authentication/login.png)

You can login with your WRI credentials (email and password), or with your Google, Facebook, or Twitter account. If you don't remember your password (don't worry! it happens to everyone!), you can reset your password clicking on 'Recover password'.

2. After logging in you will be redirected to the Control Tower application and you will see:
![Control Tower Dashboard](images/authentication/control-tower.png)

3. To obtain your token, click in the Profile menu item and you will see:
![Control Tower Profile](images/authentication/profile.png)

4. Copy your token clicking the Copy button. Remember to add the header `Authorization: Bearer: <yourToken>` in order to use it.


## Create a new user

To create a new user do the following:

- Allowed role values: USER, MANAGER, ADMIN
- Apps: rw, gfw, prep, etc...


```shell
curl -X POST https://production-api.globalforestwatch.org/auth/user \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
 '{
    "email":"<email>",
    "role":"<role>",
    "extraUserData": {
      "apps": [
        "<apps>"
      ]
    }
}'
```
