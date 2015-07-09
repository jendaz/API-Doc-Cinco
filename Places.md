## Content

* [Get place with ID](#get-place-with-id) - *GET /places/1*
* [Get place with Factual ID](#get-place-with-factual-id) - *GET /places?factual_id=*
* [Search](#search) - *GET /places/search?q=&lat=&lng=&category_ids=*
* [Add High5](#add-high5) - *POST /places/1/high5s*
* [Remove High5](#remove-high5) - *DELETE /places/1/high5s*



## Get place with ID

Required authentication.

### Request

~~~HTTP
GET /places/1 HTTP/1.1
~~~

Parameter            | Optional | More info
-------------------- | -------- | ---------
place_id | no      

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": /PLACE_OBJECT/
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
place_id                   | no
factual_id           | no
title                | no     
address              | no       | string address
lat                  | no       | latitude
lon                  | no       | longitude
... |



## Get place with Factual ID

Required authentication.

### Request

~~~HTTP
GET /places?factual_id=2b4466d7-df2f-467a-99e6-fdef1f321475 HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
factual_id |  | no | 

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": /PLACE_OBJECT/
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
place_id                   | yes  
factual_id           | no
title                | no     
address              | no       | string address
lat                  | no       | latitude
lon                  | no       | longitude
...  |



## Search

Required authentication. Enables pagination.

### Request

~~~HTTP
GET /places/search?q=pizza&lat=34.098117&lng=-118.32764&category_ids=1,2,3 HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
q |  | yes      | search term - all places without term
lat, lon |  | yes      | location latitude and longitude - search is ordered by distance
category_ids |  | yes      | category filter - no filter without ids


### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "total_count": 75,
  "result": [
    {
      "palce_id": 1,
      "factual_id": "0b891fda-074a-4d47-a021-e6fbec68207b",
      "title": "Pizza Hut",
      "address": "2724 Hyperion Ave",
      "lat": 34.1073,
      "lon": -118.271892,
      ...
    }, 
    ...
  ]
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
place_id | yes      | internal db id
factual_id | no
title | no     
address | no       | string address
lat | no       | latitude
lon | no       | longitude



## Add High5

Required authentication.

### Request

~~~HTTP
POST /places/1/high5s HTTP/1.1
~~~


Parameter  | Length        | Optional | More info
---------- | ------------- | -------- | ---------
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



## Remove High5

Required authentication.

### Request

~~~HTTP
DELETE /places/1/high5s HTTP/1.1
~~~

Parameter  | Length        | Optional | More info
---------- | ------------- | -------- | ---------
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



