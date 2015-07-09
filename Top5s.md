## Content

* [Get Top5](#get-top5) - *GET /top5s/1* - **DONE**
* [Get Top5 By Category](#get-top5-by-category) - *GET /top5s?category_id=1* - **DONE**
* [Top5s for Tastemakers](#top5s-for-tastemakers) - *GET /top5s/tastemakers* - **DONE**
* [Top5s for Tastemakers in Category](#top5s-for-tastemakers-in-category) - *GET /top5s/tastemakers?category_id=1* - **DONE**
* [Top5s for Friends](#top5s-for-friends) - *GET /top5s/friends* - **DONE**
* [Top5s for Friends in Category](#top5s-for-friends-in-category) - *GET /top5s/friends?category_id=1* - **DONE**
* [Top5s for Recent Friends Activity](#top5s-for-recent-friends-activity) - *GET /top5s/friends/recent?category_id=1* - DONE without pagination
* [Add Place to Top5](#add-place-to-top5) - *POST /top5s/1/places*
* [Move Place in Top5](#move-place-in-top5) - *PUT /top5s/1/places/1*
* [Remove Place from Top5](#remove-place-from-top5) - *DELETE /top5s/1/places/1*



## Get Top5

I can get only my Top5.
Required authentication.

### Request

~~~HTTP
GET /top5s/1 HTTP/1.1
~~~

Parameter            | Optional | More info
-------------------- | -------- | ---------
top5_id              | no       |


### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": {
    "top5_id": 1,
    "category_id": 1,
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
  }
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
top5_id              | no
category_id          | no
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place




## Get Top5 By Category

I can get only my Top5.
Required authentication.

### Request

~~~HTTP
GET /top5s?category_id=1&access_token={{access_token}} HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
category_id |  | no | 

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": {
    "top5_id": 1,
    "category_id": 1,
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
  }
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
top5_id              | no
category_id          | no
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place


## Top5s for Tastemakers

Required authentication.

### Request

~~~HTTP
GET /top5s/tastemakers HTTP/1.1
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
      "category_id": 1,
      "tastemakers_count": 2,
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
    {
      "text": "What is your favorite Burger",
      "action": "cincoapp://profile-detail/1"
    },
    ...
  ]
}
~~~

#### Top5s
Parameter            | Optional | More info
-------------------- | -------- | ---------
category_id          | no
tastemakers_count    | no     
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place

#### Actions
Parameter            | Optional | More info
-------------------- | -------- | ---------
text                 | no
action               | yes      | url scheme for action 





## Top5s for Tastemakers in Category

Required authentication. Enables pagination.

### Request

~~~HTTP
GET /top5s/tastemakers?category_id=1 HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
category_id |  | no | 

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
category_id          | no
user                 | no       | author of the top 5
_user_id             | no
_name                | no
_picture             | no       | url
_is_tastemaker       | no
_is_friend           | no
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place



## Top5s for Friends

Required authentication.

### Request

~~~HTTP
GET /top5s/friends HTTP/1.1
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
      "category_id": 1,
      "friends_count": 2,
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
    {
      "text": "What is your favorite Burger",
      "action": "cincoapp://profile-detail/1"
    },
    ...
  ]
}
~~~

#### Top5s
Parameter            | Optional | More info
-------------------- | -------- | ---------
category_id          | no
friends_count        | no     
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place

#### Actions
Parameter            | Optional | More info
-------------------- | -------- | ---------
text                 | no
action               | yes      | url scheme for action   




## Top5s for Friends in Category

Required authentication. Enables pagination.

### Request

~~~HTTP
GET /top5s/friends?category_id=1 HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
category_id |  | no | 

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
        "is_tastemaker": false,
        "is_friend": true
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
category_id          | no
user                 | no       | author of the top 5
_user_id             | no
_name                | no
_picture             | no       | url
_is_tastemaker       | no
_is_friend           | no
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place



## Top5s for Recent Friends Activity

Required authentication. Enables pagination.

### Request

~~~HTTP
GET /top5s/friends/recent?category_id=1 HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
category_id |  | yes      | category filter - return all if null

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
        "is_tastemaker": false,
        "is_friend": true
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
category_id          | no
user                 | no       | author of the top 5
_user_id             | no
_name                | no
_picture             | no       | url
_is_tastemaker       | no
_is_friend           | no
last_activity_date   | no       
places               | no       | list of places
_place_id            | no       | 
_title               | no       | place title
_lat, _lon           | no       | location
_news                | yes      | news for place



## Add Place to Top5

Required authentication.

### Request

~~~HTTP
POST /top5s/1/places HTTP/1.1
Content-Type: application/json
~~~

~~~JSON
{
  "place_id": 1,
  "position": 1
}
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
top5_id    |               | no
place_id   |               | no
position   |               | yes      | if null add to last free position

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~



## Move Place in Top5

Required authentication.

### Request

~~~HTTP
PUT /top5s/1/places/1 HTTP/1.1
Content-Type: application/json
~~~

~~~JSON
{
  "position": 1
}
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
top5_id    |               | no
place_id   |               | no
position   |               | no

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~



## Remove Place from Top5

Required authentication.

### Request

~~~HTTP
DELETE /top5s/1/places/1 HTTP/1.1
~~~

Parameter  | Length        | Optional | More info
---------- | ------------- | -------- | ---------
top5_id    |               | no
place_id   |               | no

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~