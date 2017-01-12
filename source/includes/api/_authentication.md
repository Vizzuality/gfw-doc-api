# Authentication

The RW API uses JWT Tokens to identify and authenticate to the users.

## Generate your own Oauth Token

For generate your own token, follow the next steps:

1- Enter in Control Tower Application
Navigate to [http://api.resourcewatch.org:82](http://api.resourcewatch.org:82)

If you don't login before, the application will redirect you to the login page.
You will see:
<img src="images/authentication/login.png" class="screenshot"/>
You can login with Email/Password or with your account of Google, Facebook, Twitter. If you don't remember your password, it happens to all of us, you can restart your password by clicking on 'Recover password'.

2- When you login correctly, you will be redirected to Control Tower Application and you will see:
<img src="images/authentication/control-tower.png" class="screenshot"/>

3- To obtain your token, you click in Profile menu item and you will see:
<img src="images/authentication/profile.png" class="screenshot"/>


4- Copy your token clicking in Copy button. Remember to use it, add the header `Authorization: Bearer: <yourToken>`


