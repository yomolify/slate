---
title: API Reference




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
curl -v GET "http://api.rangehealthpro.com/emr/api/message/12345" \
  -H "Content-Type:application/json"  
```


### HTTP Request

`GET /emr/api/message/:id`


## Update a message



```shell
curl -v PUT "http://api.rangehealthpro.com/emr/api/message/12345/message?convoId=77655&messageId=67890" \
  -H "Content-Type:application/json"
```


### HTTP Request

`PUT /emr/api/message/:id`

# emrEvent API

## Create emrEvent



```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/event" \
  -H "Content-Type:application/json" \
  -d '["emrEvent1", "emrEvent2"	]'
```


### HTTP Request

`POST /emr/api/event`


## Read emrEvent



```shell
curl -v GET "http://api.rangehealthpro.com/emr/api/event/12345" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /emr/api/event/:id`


## Create or update subscription



```shell
curl -v POST "http://api.rangehealthpro.com/subscribe" \
  -H "Content-Type:application/json" \
  -d '{
		"token": "token1",
		"plan": "plan1"
	}'
```


### HTTP Request

`POST /subscribe`



## List referrals



```shell
curl -v GET "http://api.rangehealthpro.com/refer" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /refer`

# Login/Register/Recover API

## Check if user is logged in



```shell
curl -v GET "http://api.rangehealthpro.com/loggedin" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /loggedin`

## Route to log in



```shell
curl -v POST "http://api.rangehealthpro.com/login" \
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /login`


## Route to log out



```shell
curl -v POST "http://api.rangehealthpro.com/logout" \
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /logout`

## Create a user account



```shell
curl -v POST "http://api.rangehealthpro.com/signup" \
  -H "Content-Type:application/json" \
  -d '{
		"fullname": "Richard Davis",
		"email": "richard@davis.com",
		"password": "88jhkui24"
	}'
```


### HTTP Request

`POST /signup`

## Register a user account



```shell
curl -v POST "http://api.rangehealthpro.com/register" \
  -H "Content-Type:application/json" \
  -d '{
		"fullname": "Richard Davis",
		"email": "richard@davis.com",
		"password": "88jhkui24"
	}'
```


### HTTP Request

`POST /register`


## Get user file



```shell
curl -v GET "http://api.rangehealthpro.com/register" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /register`

## Render feedTitle: 'User Account Recovery'



```shell
curl -v GET "http://api.rangehealthpro.com/recover" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /recover`

## Recover user account



```shell
curl -v GET "http://api.rangehealthpro.com/recover" \
  -H "Content-Type:application/json" \
  -d '{
		"email": "richard@davis.com"
	}'
```


### HTTP Request

`GET /recover`

## getReset user account



```shell
curl -v GET "http://api.rangehealthpro.com/recover/uZVTLBCWcw33RIhvnbxTKxTxM2rKJ7YJrwyUXhXn" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /reset/:token`

## postReset user account



```shell
curl -v POST "http://api.rangehealthpro.com/recover/uZVTLB78995rwIhvnbxTKxTxM2rKJ7YJrwyUXhXn" \
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /reset/:token`


## Change password



```shell
curl -v POST "http://api.rangehealthpro.com/changepassword" \
  -H "Content-Type:application/json" \
  -d '{
		"user" : 
			{
				"prevpass": "ui87xhsgy",
				"newpass1": "pxjsdh127",
				"newpass2": "pxjsdh127"
			}
	}'
```


### HTTP Request

`POST /changepassword`

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
curl -v GET "http://api.rangehealthpro.com/api/direct-msg/?read="true"&tags="archive"/" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/direct-msg`

## Read direct message



```shell
curl -v GET "http://api.rangehealthpro.com/api/direct-msg/12345" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/direct-msg/:id`

## Create direct message



```shell
curl -v POST "http://api.rangehealthpro.com/api/direct-msg" \
  -H "Content-Type:application/json" \
  -d '{
  		"from": 89873129872,
  		"to": [target1, target2],
  		"re": [123130918230],
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
  		"ids": [1234, 4567, 7890]
  	}'
```


### HTTP Request

`POST /api/direct-msg/archive`

## Mark direct message as read



```shell
curl -v POST "http://api.rangehealthpro.com/api/direct-msg/markAsRead" \
  -H "Content-Type:application/json" \
  -d '{
  		"ids": [1234, 4567, 7890]
  	}'
```


### HTTP Request

`POST /api/direct-msg/markAsRead`



## List events



```shell
curl -v POST "http://api.rangehealthpro.com/api/event/?owner="Ash"" \
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /api/event`


## Read an event



```shell
curl -v GET "http://api.rangehealthpro.com/api/event/12345" \
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
  		"description": "Hey, I am a sample event"
  	}'
```


### HTTP Request

`POST /api/event`

## Read a person minimally



```shell
curl -v GET "http://api.rangehealthpro.com/api/person/12345" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/person/:id`

## Read a person with options



```shell
curl -v GET "http://api.rangehealthpro.com/api/record/12345/?useCached="true"" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/record/:id`

## Create a record



```shell
curl -v POST "http://api.rangehealthpro.com/api/record" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": "Shawn",
  		"message": "Hey, you are my target"
  	}'
```


### HTTP Request

`POST /api/record/`



## List all collabs of logged-in user



```shell
curl -v GET "http://api.rangehealthpro.com/api/collab" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/collab`


## List all collabs of specified user



```shell
curl -v GET "http://api.rangehealthpro.com/api/collab/1325752" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/collab/:id`

## Create collab of logged-in user



```shell
curl -v POST "http://api.rangehealthpro.com/api/collab" \
  -H "Content-Type:application/json" \
  -d '{
  		"re": "Shawn",
  		"to": "Joey"
  	}' 
```


### HTTP Request

`POST /api/collab`

## Update collab of specified user



```shell
curl -v PUT "http://api.rangehealthpro.com/api/collab/587967" \
  -H "Content-Type:application/json" \
  -d '{
  		"accept": "true"
  	}' 
```


### HTTP Request

`PUT /api/collab/:id`

## List connections of logged-in user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection/?status="connected"&type="pro"" \
  -H "Content-Type:application/json"
 ```


### HTTP Request

`GET /api/connection/`

## List connections of specified user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection/73573457/?status="connected"&type="pro"" \
  -H "Content-Type:application/json"
 ```


### HTTP Request

`GET /api/connection/:userId`

## Create a new pro connection for the logged in user



```shell
curl -v POST "http://api.rangehealthpro.com/api/connection" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": "Shawn"
  	}'
 ```


### HTTP Request

`POST /api/connection/`

## Confirm a new pro connection for the logged in user



```shell
curl -v PUT "http://api.rangehealthpro.com/api/connection/367357" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/connection/:userId`


## Deletes the specified connection of any type from the logged in user



```shell
curl -v DELETE "http://api.rangehealthpro.com/api/connection/34362" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/connection/:userId`


## List the connection requests of logged-in user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection-request/?status="pending"&type="pro"" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/connection-request`



## List the connection requests of specific user



```shell
curl -v GET "http://api.rangehealthpro.com/api/connection-request/1230987/?status="pending"" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/connection-request/:id`


## Create a connection request for logged-in user to specified target



```shell
curl -v POST "http://api.rangehealthpro.com/api/connection-request" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": "Ron",
  		"subject": "Sample connRequest",
  		"text": "Hey, I am a sample!"
  	}'
 ```


### HTTP Request

`POST /api/connection-request`


## Confirm a connection request and make logged-in user fully connected with specified user



```shell
curl -v PUT "http://api.rangehealthpro.com/api/connection-request/754786" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/connection-request/:id`



## Delete a connection request and make logged-in user fully disconnected with specified user



```shell
curl -v DELETE "http://api.rangehealthpro.com/api/connection-request/89767" \
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
curl -v GET "http://api.rangehealthpro.com/attach/1233245" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /attach/:fileId`


## Read specified attachment

```shell
curl -v GET "http://api.rangehealthpro.com/attach/1233245/testFile.txt" \
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
curl -v DELETE "http://api.rangehealthpro.com/attach/807986" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /attach/:fileId`


## List all connected persons of logged in user

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/?name="Ash"&orgs="Doc"" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /attach/:fileId`


## Return a filtered list of record entries for a given person

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/45637/summary/cct" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/summary/:type`


## List labResults of specified person

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/723141/labresult" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/labresult`



## List prescritptions of specified person

```shell
curl -v GET "http://api.rangehealthpro.com/api/person/723141/rx-timeline" \
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
curl -v GET "http://api.rangehealthpro.com/api/org/232155" \
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
  				"prefs": "allPrefsHere"
  			}
  	}'
 ```


### HTTP Request

`POST /api/org`

## Update specified org for logged in user

```shell
curl -v PUT "http://api.rangehealthpro.com/api/org/12325" \
  -H "Content-Type:application/json" \
  -d '{
  		"profile": 
  			{
  				"prefs": "newPrefsHere"
  			}
  	}'
 ```


### HTTP Request

`PUT /api/org/:id`




## Delete specified org for logged in user

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/org/12325" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:id`

## List membership requests for current user

```shell
curl -v GET "http://api.rangehealthpro.com/api/membership-request/?status="pending"" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/membership-request`


## List membership requests for specified orgId

```shell
curl -v GET "http://api.rangehealthpro.com/api/org/4523464362/membership-request/?status="pending"" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:orgId/membership-request`




## Read specified membership request for specified orgId

```shell
curl -v GET "http://api.rangehealthpro.com/api/org/4523464362/membership-request/56786/?status="connected"" \
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
curl -v PUT "http://api.rangehealthpro.com/api/org/4523464362/membership-request/9875869/" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/org/:orgId/membership-request/:id`



## Delete membership request for specified org with specified id

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/org/4523464362/membership-request/9875869/" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:orgId/membership-request/:id`



## Delete membership of logged-in user with specified org

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/org/4523464362/membership" \
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
  				"prefs": "updatedPrefsHere"
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


## Get lub 

```shell
curl -v GET "http://api.rangehealthpro.com/lub" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /lub`

## Request a booking 

```shell
curl -v POST "http://api.rangehealthpro.com/api/booking" \
  -H "Content-Type:application/json" \
  -d '{
  		"date": "14 June 2015",
  		"currentFeed": "prettyGood",
  		"currentFeedFullname": "longName"
  	}'
 ```


### HTTP Request

`POST /api/booking`



## Get type

```shell
curl -v GET "http://api.rangehealthpro.com/api/cct" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /api/:type`




## Get trends of specified target

```shell
curl -v GET "http://api.rangehealthpro.com/api/trends/Ash" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /api/trends/:target`


## Get counts of specified type

```shell
curl -v GET "http://api.rangehealthpro.com/api/counts/cct" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /api/counts/:type`


## Get partials for a specified view

```shell
curl -v GET "http://api.rangehealthpro.com/partials/68987698" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /partials/:view`


## Get views for a specified type and view

```shell
curl -v GET "http://api.rangehealthpro.com/views/cct/1213124" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /views/:type/:view`


## Get views for a specified view

```shell
curl -v GET "http://api.rangehealthpro.com/views/1213124" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`GET /views/:view`




## Delete a dub id

```shell
curl -v DELETE "http://api.rangehealthpro.com/api/dub/12325" \
  -H "Content-Type:application/json" 
```


### HTTP Request

`DELETE /api/dub/:id`


















