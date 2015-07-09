## Content

* [User Profile](#user-profile) - *GET /users/1* - **DONE**
* [Get Users with Emails](#get-users-with-emails) - *GET /users?emails=jan@cincoapp.com,...* - **DONE**
* [Top5s for User](#top5s-for-user) - *GET /users/1/top5s*
* [Add Friendship](#add-friendship) - *POST /users/1/friendships* - **DONE**
* [Remove Friendship](#remove-friendship) - *DELETE /users/1/friendships* - **DONE**


## User Profile

Required authentication.

### Request

~~~HTTP
GET /users/1 HTTP/1.1
~~~

Parameter            | Optional | More info
-------------------- | -------- | ---------
uset_id              | no       |

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": {
    "user_id": 16,
    "email": "j.zimandl@email.cz",
    "first_name": "Jenda",
    "last_name": "Zimandl",
    "photo_url": "https://fbcdn-profile-a.akamaihd.net/hprofile-ak-xpa1/v/t1.0-1/p200x200/10478732_10202373702691704_1664910723578270453_n.jpg?oh=7245129fb32f031d584201550dbae7ce&oe=561D9A0F&__gda__=1444685726_5ec7160787a0cc26ff657bc1ae153fa1",
    "location_name": "Vlasim, Czech Republic",
    "is_tastemaker": false,
    "is_friend": false,
    "score": 0,
    "friends": 1,
    "lists": 1
  }
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
user_id | no
email | no
first_name | no     
last_name | no 
photo_url | no
location_name | no
is_tastemaker | no
is_friend | no
score | no
friends | no
lists | no   



## Get Users with Emails

Required authentication. Enables pagination.

### Request

~~~HTTP
GET /users?emails=jan@cincoapp.com,evan@cincoapp.com,bruce@cincoapp.com HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
emails    |  | no       | list of emails separated by commas

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": [
    {
      "user_id": 1,
      "first_name": "Jan",
      "last_name": "Zimandl",
      ...
    }, 
    ...
  ]
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
user_id | no
first_name | no     
last_name | no 
... |  




## Top5s for User

Required authentication.

### Request

~~~HTTP
GET /users/1/top5s HTTP/1.1
~~~

Parameter  | Length        | Optional | More info
---------- | ------------- | -------- | ---------
user_id    |               | no

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": [
    {
      "category_id": 1,
      "user": {
        "user_id": 1,
        "name": "Jan Zimandl",
        "picture": "http://image.jpg",
        "is_tastemaker": true,
        "is_friend": false
      },
      "last_activity_date": "2015-06-10T10:23:52Z",
      "places": [
        {
          "place_id": 1,
          "title": "Canter's Deli",
          "lat": 14.1234,
          "lon": 50.213,
          "news": true
        },
        {
          "place_id": 2,
          "title": "Joe's Pizza",
          "lat": 14.1234,
          "lon": 50.213,
          "news": false
        }
      ]
    },
    ...
  ]
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
category_id | no
user                 | no       | author of the top 5
_user_id             | no
_name                | no
_picture             | no       | url
_is_tastemaker       | no
_is_friend           | no
last_activity_date | no       
places | no       | list of places
_place_id | no       | 
_title | no       | place title
_lat, _lon | no       | location
_news | yes      | news for place



## Add Friendship

Follow another user as a friend.
Required authentication.

### Request

~~~HTTP
POST /users/1/friendships HTTP/1.1
~~~

Parameter  | Length        | Optional | More info
---------- | ------------- | -------- | ---------
user_id    |               | no 


### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~



## Remove Friendship

Required authentication.

### Request

~~~HTTP
DELETE /users/1/friendships HTTP/1.1
~~~

Parameter  | Length        | Optional | More info
---------- | ------------- | -------- | ---------
user_id    |               | no 

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~
