## Content

* [Get All Categories](#get-all-categories) - *GET /categories*



## Get All Categories

### Request

~~~HTTP
GET /categories HTTP/1.1
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
      "title": "Pizza",
      "icon_url": "http://icon-cat-pizza.png",
      "image_url": "http://image-cat-pizza.jpg"
    }, 
    ...
  ]
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
id                   | no
title                | no     
icon_url             | no       | url to png image
image_url            | no       | url to jpeg image

