---
title: API Reference

connnection
ids
quotes
addon
read specified attachment remove but leave get
attachment create
all post and puts should have bodies


includes:
  - errors

search: true
---

# Introduction

Welcome to the RangeHealth API! You can use our API to access RangeHealth's API endpoints.

You can view code examples in the dark area to the right.



# EMR API

## Reminder notifications and changes to an EMR



```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/update" \
  -H "Content-Type:application/json" \
  -d '{
		"messages": [
			{
				"key1": "value1",
				"key2": "value2"
			}
		]
	}'
```


### HTTP Request

`POST /emr/api/update`


## Recieves notification that a patient has been changed in the EMR


```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/patient_change_event" \
  -H "Content-Type:application/json" \
  -d '{
		"patientChangeEvent": [
			"patientCEvent1", "patientCEvent2"
		]
	}'
```


### HTTP Request

`POST /emr/api/patient_change_event`

# Messages API

## Create a Direct Message from an EMR Message



```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/message" \
  -H "Content-Type:application/json" \
  -d '{
		"messages": [
			"emrMessage1", "emrMessage2"
		]
	}'
```


### HTTP Request

`POST /emr/api/message`

## Read a message



```shell
curl -v GET "http://api.rangehealthpro.com/emr/api/message/557989f28f2a7a91d36b26e6" \
  -H "Content-Type:application/json"  
```


### HTTP Request

`GET /emr/api/message/:id`


## Update a message



```shell
curl -v PUT "http://api.rangehealthpro.com/emr/api/message/557989f28f2a7a91d36b26e6/?convoId=558051f9cf0d618312737e38&messageId=558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`PUT /emr/api/message/:id`

# emrEvent API

## Create emrEvent



```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/event" \
  -H "Content-Type:application/json" \
  -d '{
  		"data": ["emrEvent1", "emrEvent2"]
  	}'
```


### HTTP Request

`POST /emr/api/event`


## Read emrEvent


```shell
curl -v GET "http://api.rangehealthpro.com/emr/api/event/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /emr/api/event/:id`



# API/ATTACH

## Get profile of user



```shell
curl -v GET "http://api.rangehealthpro.com/api/user/richardwong" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/user/:user`


## Get details of logged in user



```shell
curl -v GET "http://api.rangehealthpro.com/api/userDetails/" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/userDetails`


## List direct messages



```shell
curl -v GET "http://api.rangehealthpro.com/api/direct-msg/?read=true&tags=archive" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/direct-msg`

## Read direct message



```shell
curl -v GET "http://api.rangehealthpro.com/api/direct-msg/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/direct-msg/:id`

## Create direct message



```shell
curl -v POST "http://api.rangehealthpro.com/api/direct-msg" \
  -H "Content-Type:application/json" \
  -d '{
  		"from": 558051f9cf0d618312737f68,
  		"to": [target1, target2],
  		"re": [558051f9cf0d618312737f67],
  		"text": "Hey, I am a msg"
  	}'
```


### HTTP Request

`POST /api/direct-msg`


## Archive direct message



```shell
curl -v POST "http://api.rangehealthpro.com/api/direct-msg/archive" \
  -H "Content-Type:application/json" \
  -d '{
  		"ids": [558051f9cf0d618312737f67, 456751f9cf0d618312737e86, 789051f9cf0d616452737p12]
  	}'
```


### HTTP Request

`POST /api/direct-msg/archive`

## Mark direct message as read



```shell
curl -v POST "http://api.rangehealthpro.com/api/direct-msg/markAsRead" \
  -H "Content-Type:application/json" \
  -d '{
  		"ids": [558051f9cf0d618312737f67, 456751f9cf0d618312737e86, 789051f9cf0d616452737p12]  
  	}'
```


### HTTP Request

`POST /api/direct-msg/markAsRead`



## List events



```shell
curl -v POST "http://api.rangehealthpro.com/api/event/?owner=Ash&forUser=Shawn&start=567480238&end=612349062" \
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /api/event`


## Read an event



```shell
curl -v GET "http://api.rangehealthpro.com/api/event/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/event/:id`


## Create an event



```shell
curl -v POST "http://api.rangehealthpro.com/api/event" \
  -H "Content-Type:application/json" \
  -d '{
  		"owner": "Ron",
  		"subject": "Sample Event",
  		"type": "example",
  		"description": "Hey, I am a sample event",
  		"topic": "Mysteries of the sample event",
  		"location": "Vancouver",
  		"description": "This will be a huge event"  		
  	}'
```


### HTTP Request

`POST /api/event`

## Read a person minimally



```shell
curl -v GET "http://api.rangehealthpro.com/api/person/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/person/:id`

## Read a person with options



```shell
curl -v GET "http://api.rangehealthpro.com/api/record/558051f9cf0d618312737f67/?filterBy=profile.prefs.fullname&useCached=true" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/record/:id`

## Create a record



```shell
curl -v POST "http://api.rangehealthpro.com/api/record" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": 558051f9cf0d618312737f67,
  		"message": "Hey, you are my target",
  		"attachments": [attach1, attach2]
  	}'
```

### HTTP Request

`POST /api/record/`


## List connections of logged-in user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection/?status=connected&type=pro" \
  -H "Content-Type:application/json"
 ```


### HTTP Request

`GET /api/connection/`

## List connections of specified user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection/558051f9cf0d618312737f67/?status=connected&type=pro" \
  -H "Content-Type:application/json"
 ```


### HTTP Request

`GET /api/connection/:userId`

## Create a new pro connection for the logged in user



```shell
curl -v POST "http://api.rangehealthpro.com/api/connection" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": 55805e90cf0d618312737e39
  	}'
 ```


### HTTP Request

`POST /api/connection/`

## Confirm a new pro connection for the logged in user



```shell
curl -v PUT "http://api.rangehealthpro.com/api/connection/55805e90cf0d618312737e39" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/connection/:userId`


## Deletes the specified connection of any type from the logged in user



```shell
curl -v DELETE "http://api.rangehealthpro.com/api/connection/55805e90cf0d618312737e39" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/connection/:userId`


## List the connection requests of logged-in user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection-request/?status=pending&type=pro" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/connection-request`



## List the connection requests of specific user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection-request/55805e90cf0d618312737e39/?status=pending" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/connection-request/:id`


## Create a connection request for logged-in user to specified target



```shell
curl -v POST "http://api.rangehealthpro.com/api/connection-request" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": 67543e90cf0d618312737q31,
  		"subject": "Sample connRequest",
  		"text": "Hey, I am a sample!"
  	}'
 ```


### HTTP Request

`POST /api/connection-request`


## Confirm a connection request and make logged-in user fully connected with specified user



```shell
curl -v PUT "http://api.rangehealthpro.com/api/connection-request/72839e90cf0d618312737q31" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/connection-request/:id`



## Delete a connection request and make logged-in user fully disconnected with specified user



```shell
curl -v DELETE "http://api.rangehealthpro.com/api/connection-request/75039e90cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/connection-request/:id`


## Read Addon

```shell
curl -v GET "http://api.rangehealthpro.com/api/addon/?emrobject1" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/addon`


## Get specified attachment

```shell
curl -v GET "http://api.rangehealthpro.com/attach/774059e90cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /attach/:fileId`


## Read specified attachment

```shell
curl -v GET "http://api.rangehealthpro.com/attach/991759e90cf0d618312737f24/testFile.txt" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /attach/:fileId/:fileName`


## Create an attachment

```shell
curl -v POST "http://api.rangehealthpro.com/attach" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`POST /api/attach`


## Delete an attachment

```shell
curl -v DELETE "http://api.rangehealthpro.com/attach/348269e90cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /attach/:fileId`


## List all connected persons of logged in user

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/?name=Ash&orgs=Doc" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person`


## Return a filtered list of record entries for a given person

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/264809e90cf0d618312737f24/summary/cct" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/summary/:type`


## List labResults of specified person

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/7231410cf0d618312737f24/labresult/?test=bloodTest" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/labresult`



## List prescriptions of specified person

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/947260cf0d618312737f24/rx-timeline/?test=urineTest" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/rx-timeline`

## List orgs of logged-in user

```shell
curl -v GET "http://api.rangehealthpro.com/api/org" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org`

## List orgs of specified user

```shell
curl -v GET "http://api.rangehealthpro.com/api/org/232155cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:id`



## Create specified org for logged in user

```shell
curl -v POST "http://api.rangehealthpro.com/api/org" \
  -H "Content-Type:application/json" \
  -d '{
  		"profile": 
  			{
  				"prefs": 
  					{
  					"fullname": "John Doe",
                	email: doe@john.com,
                	description: "I am updated prefs",
                	comments: "hey, nice article",
                	address: "4660, West 10th Avenue",
                	phone: 777757169
                }
  			}
  	}'
 ```


### HTTP Request

`POST /api/org`

## Update specified org for logged in user

```shell
curl -v PUT "http://api.rangehealthpro.com/api/org/483958cf0d618312737f24" \
  -H "Content-Type:application/json" \
  -d '{
  		"profile": 
  			{
  				"prefs": 
  					{
  					"fullname": "John Doe",
                	email: doe@john.com,
                	description: "I am updated prefs",
                	comments: "hey, nice article",
                	address: "4660, West 10th Avenue",
                	phone: 777757169
                }
  			}
  	}'
 ```


### HTTP Request

`PUT /api/org/:id`




## Delete specified org for logged in user

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/org/912378cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:id`

## List membership requests for current user

```shell
curl -v GET "http://api.rangehealthpro.com/api/membership-request/?status=pending" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/membership-request`


## List membership requests for specified orgId

```shell
curl -v GET "http://api.rangehealthpro.com/api/org/45234868cf0d618312737f24/membership-request/?status=pending" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:orgId/membership-request`




## Read specified membership request for specified orgId

```shell
curl -v GET "http://api.rangehealthpro.com/api/org/4523e64o62618312737f24/membership-request/567868cf0d618312737f24/?status=connected" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:orgId/membership-request/:id`



## Create membership request for specified orgId

```shell
curl -v POST "http://api.rangehealthpro.com/api/org/4523464362/membership-request/?subject="exampleMembRequest"" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`POST /api/org/:orgId/membership-request`



## Approve membership request for specified org with specified id

```shell
curl -v PUT "http://api.rangehealthpro.com/api/org/4523868cf0d618312737f24/membership-request/98758v1cf0d618312737f24/" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/org/:orgId/membership-request/:id`



## Delete membership request for specified org with specified id

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/org/45234868cf0d618312737f24/membership-request/9875869acf0d618312737f24/" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:orgId/membership-request/:id`



## Delete membership of logged-in user with specified org

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/org/45234868cf0d618312737f24/membership" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:orgId/membership`


## List entries of logged-in user

```shell
curl -v GET "http://api.rangehealthpro.com/api/entry/?limit=5" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/entry`

## Read profile of logged-in user

```shell
curl -v GET "http://api.rangehealthpro.com/api/profile" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/profile`



## Update profile of logged-in user

```shell
curl -v PUT "http://api.rangehealthpro.com/api/profile" \
  -H "Content-Type:application/json" \
  -d '{
  		"profile": 
  			{
  				"prefs": 
  				{
  					"fullname": "John Doe",
                	email: doe@john.com,
                	description: "I am updated prefs",
                	comments: "hey, nice article",
                	address: "4660, West 10th Avenue",
                	phone: 777757169
                }
  			}
  	}'
 ```


### HTTP Request

`PUT /api/profile`



## Read permissions of logged-in user

```shell
curl -v GET "http://api.rangehealthpro.com/api/permission" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/permission`


