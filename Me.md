## Content

* [My Profile](#my-profile) - *GET /me* - **DONE**
* [Search Friends](#search-friends) - *GET /me/friends?q=jan* - DONE without pagination
* [My Top5s](#my-top5s) - *GET /me/top5s*




## My Profile

Required authentication.

### Request

~~~HTTP
GET /me HTTP/1.1
~~~

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





## Search Friends

Required authentication. Enables pagination.

### Request

~~~HTTP
GET /me/friends?q=jan HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
q |  | yes      | search term, all friends if it is null

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "total_count": 10,
  "result": [
    {
      "user_id": 17,
      "first_name": "Jan",
      "last_name": "Zimandl",
      "photo_url": "https://fbcdn-profile-a.akamaihd.net/hprofile-ak-xpa1/v/t1.0-1/p200x200/10478732_10202373702691704_1664910723578270453_n.jpg?oh=7245129fb32f031d584201550dbae7ce&oe=561D9A0F&__gda__=1444685726_5ec7160787a0cc26ff657bc1ae153fa1",
      "location_name": "Prague, Czech Republic",
      "is_tastemaker": false,
      "score": 0,
      "friends": 1,
      "lists": 1
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
photo_url | no
location_name | no
is_tastemaker | no
score | no
friends | no
lists | no




## My Top5s

Required authentication.

### Request

~~~HTTP
GET /me/top5s HTTP/1.1
~~~

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": [
    {
      "top5_id": 1,
      "category_id": 1,
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
top5_id | no
category_id | no
last_activity_date | no       
places | no       | list of places
_place_id | no       | 
_title | no       | place title
_lat, _lon | no       | location
_news | yes      | news for place



