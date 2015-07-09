## Content

* [Facebook Sign Up](#facebook-sign-up) - *POST /signup/facebook* - **DONE**



## Facebook Sign Up

### Request

~~~HTTP
POST /signup/facebook HTTP/1.1
Content-Type: application/json
~~~

~~~JSON
{
  "facebook_token": "sadkjfhaskdzjfiasz"
}
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
facebook_token |  | no | fb access token

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": {
    "user_id": 1,
    "access_token": "NFSAjOHIgqvMAkRIwjQKk2Dp",
    "photo_url": "http://image.jpg",
    "first_name": "Jan",
    "last_name": "Zimandl",
    "just_created": true
  }
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
user_id              | no       |
access_token         | no       |
photo_url            | no       | 
first_name           | no       | 
last_name            | no       | 
just_created         | yes      | 

### Errors

Name                       | Description
-------------------------- | -----------
InvalidFacebookAccessToken | Invalid facebook access token.



