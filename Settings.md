## Content

* [My Settings](#my-settings) - *GET /settings* - **DONE**
* [Update Settings](#update-settings) - *PUT /settings* - **DONE**



## My Settings

Required authentication.

### Request

~~~HTTP
GET /settings HTTP/1.1
~~~

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success":true,
  "result": {
    "notify_friends_activity": true,
    "notify_top5_updates": true,
    "notify_marketing": true,
    "autoshare_twitter": true,
    "autoshare_facebook": true
  }
}
~~~

Parameter               | Optional | More info
----------------------- | -------- | ---------
notify_friends_activity | no
notify_top5_updates     | no     
notify_marketing        | no
autoshare_twitter       | no
autoshare_facebook      | no




## Update Settings

Required authentication.

### Request

~~~HTTP
PUT /settings HTTP/1.1
Content-Type: application/json
~~~

~~~JSON
{
  "notify_friends_activity": true,
  "notify_top5_updates": true,
  "notify_marketing": true,
  "autoshare_twitter": true,
  "autoshare_facebook": true
}
~~~

Parameter | Length | Optional | More info
--------- | -------| -------- | ---------
notify_friends_activity |  | no | 
notify_top5_updates |  | no | 
notify_marketing |  | no | 
autoshare_twitter |  | no | 
autoshare_facebook |  | no | 

### Response

~~~HTTP
HTTP/1.1 200 OK
~~~

~~~JSON
{
  "success": true
}
~~~


