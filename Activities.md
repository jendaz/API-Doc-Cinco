## Content

* [Get Activities for Category](#get-activities-for-category) - *GET /activities?category_id=1*
* [Add Activity](#add-activity) - *POST /activities*



## Get Activities for Category

Required authentication.

### Request

~~~HTTP
GET /activities?category_id=1 HTTP/1.1
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
category_id | | no | filter by category ID

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true,
  "result": [
    {
      "id": 1,
      "date": "2015-06-20T12:00:00Z",
      "type": 1,
      "user": {
        "id": 1,
        "name": "John Doe"
      },
      "category_id": 1,
      "place": {
        "id": 1,
        "title": "Pizza Hut"
      },
      "additional_value": null
    }, 
    ...
  ]
}
~~~

Parameter | Optional | More info
--------- | -------- | ---------
id                   | no
date                 | no     
type                 | no       | 1...5
user                 | no
category_id          | no
place                | yes      | no place for types: 1
additional_value     | yes      | value for moving to post


#### Activity Types
* 1 - Someone created a list for that category
* 2 - Someone added a place to their list in this category
* 3 - Someone moved a place up in their list in this category 
* 4 - Someone moved a place down in their list in this category 
* 5 - Someone removed a place from their list in this category


## Add Activity

Required authentication.

### Request

~~~HTTP
POST /activities HTTP/1.1
Content-Type: application/json
~~~

~~~JSON
{
  "type": 1,
  "category_id": 1,
  "place_id": 1,
  "additional_value": 1
}
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
type |  | no
category_id |  | no
place_id |  | yes
additional_value |  | yes

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~



