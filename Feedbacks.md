## Content

* [Add Feedback](#add-feedback) - *POST /feedbacks*



## Add Feedback

Required authentication.

### Request

~~~HTTP
POST /feedbacks HTTP/1.1
Content-Type: application/json
~~~

~~~JSON
{
  "place_id": 1,
  "top5_id": 1,
  "type": 1,
  "reason": 1,
  "note": "The place became awful"
}
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
place_id |  | no | 
top5_id |  | no | 
type |  | no | 1 - delete
reason |  | no | 
note |  | yes | 

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~




