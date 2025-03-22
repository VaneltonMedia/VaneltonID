# Vanelton ID
Welcome to the complete documentation for using Vanelton ID modules and APIs for your applications, games, services and more. First, you should consult the Vanelton Media console and create your project so that everything works perfectly.

If you already have your **appID** and your **appKey**, you are ready to take the first steps towards implementing the Vanelton ID authentication system in your project.

> [!TIP]
> In these first steps you will learn the basics of using cURL, but we recommend that you first check if there is direct compatibility with modules or frameworks for your language.

## Quickstart
The Vanelton ID authentication system is simple and practical, and also very secure. You can quickly implement it in your project, whether it is a website, a game or an application, it may be enough for what your project needs. The Vanelton ID system is easy to implement and use.

Make your first login call using cURL below. This call will return a JSON with information about the user logging in, along with updated application information.

```bash
curl -X POST \
     -H "Authorization: $YOUR_APPID:$YOUR_APPKEY" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "email=$USER_EMAIL&password=$USER_PASSWORD" \
     https://www.vaneltongamedev.com/appdbvs/vaneltonid-dbvs/app-login.php
```

The JSON output should look something like this:

```json
{
  "vaneltonid": {
    "logged": 1,
    "id": 1,
    "userkey": "28rufj2u8rh8732hrj9r328jr32r1",
    "email": "johnpepo@gmail.com",
    "username": "JohnPepo",
    "name": "John Pepo",
    "profileimg": "/source/users/profile-photos/JohnPepo/Profile.png?t=1741270652",
    "token": "9a03957d1ee011893fce8673583e44c8aecd093a3235301a8017d79e4827e389"
  },
  "app": {
    "authorized": 1,
    "packageid": "-21",
    "packagename": "com.vgd.pepogame",
    "appname": "Pepo Game",
    "appcompany": "Vanelton Media",
    "appicon": "/source/apps/com.vgd.pepogame/icon.png",
    "appversion": "1.0.0",
    "appsite": "#"
  }
}
```

You can temporarily store all this JSON to manipulate on the page. However, the most important thing for you to store is the VANELTONID TOKEN.

This token is how you will always recover the user's session without it appearing that the user is logging in multiple times. You can store this token in localStorage, PHP session, among other alternatives to keep the token always available to recover the session.

It is important to note that misuse of this function (such as multiple login calls for the same account) may result in the temporary blocking of new sessions in your project. This may temporarily harm your project and compromise the authentication system.