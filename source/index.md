---
title: API Reference


includes:
  - errors

search: true
---

# Introduction

Welcome to the RangeHealth API! You can use our API to access RangeHealth's API endpoints.

You can view code examples in the dark area to the right.



# EMR Communication

The following end points are for use by the EMR server to communicate with the RangeHealth web application.

## EMR changes and reminder notifications

When a reminder activates, or a change is made in the EMR system, a notification is sent to the RangeHealth web application.

```shell
curl -v POST "https://rangehealthpro.com/emr/api/update/?emr=Doe" \
  -H "Content-Type:application/json" \
  -d '{
  	   "messages": 
  			{
  		  "messages":[
  				{
  					"updates":[
  						{
  							"timestamp": 12569537329,
							"id": 55798976,
							"userInitials": "AS",
							"patientId": 748320123,
							"displayText": "EMR Text version",
							"tags": ["Patient", "Rx", "High priority"]
						}
					]
				}
			]
		}
	}'
```


### HTTP Request

`POST /emr/api/update`


## EMR patient change

When a change is made to a patient record, a notification is sent to the RangeHealth web application.

```shell
curl -v POST "https://rangehealthpro.com/emr/api/patient_change_event/?emr=John" \
  -H "Content-Type:application/json" \
  -d '{
		"patientChangeEvent": [101, 107, 754]
	}'
```


### HTTP Request

`POST /emr/api/patient_change_event`

# EMR Messages

## EMR message sent

When a new message is sent between EMR users, a notification is sent to the RangeHealth web application.

```shell
curl -v POST "https://rangehealthpro.com/emr/api/message" \
  -H "Content-Type:application/json" \
  -d '{
		"messages": [
			{
    			emrId: 789051f9cf0d616452737p12,
   				text: "Hi, I am an EMR message with target @pat",
    			subject: "EMR Test Message",
    			emrMessageId: 558051f9cf0d618312737e38,
    			timestamp: 12569537939,
    			chainId: 558051f9cf0d618312737f67,
    			emrConvoId: 798121f9cf0d618312737f68,
    			to: [{
        			initials: "@pat"
    			}],
    			from: "@con",	
    			patientId: 456751f9cf0d618312737e86,
    			_directMsg: 25073f9cf0d618920737e81,
    			_directConvo: 176485f9cf0d618312737w80
			}
		]
	}'
```


### HTTP Request

`POST /emr/api/message`

## Message retrieval

When a message is sent in the RangeHealth web application, and the EMR system is notified, it will then retrieve the message contents.

```shell
curl -v GET "https://rangehealthpro.com/emr/api/message/557989f28f2a7a91d36b26e6" \
  -H "Content-Type:application/json"  
```


### HTTP Request

`GET /emr/api/message/:id`


## Conversation update

When a new message is sent in an existing conversation thread, the conversation is updated and a notification is sent to the RangeHealth web application.

```shell
curl -v PUT "https://rangehealthpro.com/emr/api/message/557989f28f2a7a91d36b26e6/?convoId=558051f9cf0d618312737e38&messageId=558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`PUT /emr/api/message/:id`

# EMR Appointments

## Create an EMR appointment

When an appointment is entered into the EMR appointment book, a notification is sent to the RangeHealth web application.

```shell
curl -v POST "https://rangehealthpro.com/emr/api/event" \
  -H "Content-Type:application/json" \
  -d '{
  		"data": ["emrEvent1", "emrEvent2"]
  	}'
```


### HTTP Request

`POST /emr/api/event`



# Direct Messages


## List direct messages (example shows archived messages)



```shell
curl -v GET "https://rangehealthpro.com/api/direct-msg/?tags=archive" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/direct-msg`

## Read direct message



```shell
curl -v GET "https://rangehealthpro.com/api/direct-msg/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/direct-msg/:id`

## Create direct message



```shell
curl -v POST "https://rangehealthpro.com/api/direct-msg" \
  -H "Content-Type:application/json" \
  -d '{
  		"from": 558051f9cf0d618312737f68,
  		"to": [target1, target2],
  		"re": [558051f9cf0d618312737f67],
  		"text": "Sample message text"
  	}'
```


### HTTP Request

`POST /api/direct-msg`


## Archive direct message



```shell
curl -v POST "https://rangehealthpro.com/api/direct-msg/archive" \
  -H "Content-Type:application/json" \
  -d '{
  		"ids": [558051f9cf0d618312737f67, 456751f9cf0d618312737e86, 789051f9cf0d616452737p12]
  	}'
```


### HTTP Request

`POST /api/direct-msg/archive`

## Mark direct message as read



```shell
curl -v POST "https://rangehealthpro.com/api/direct-msg/markAsRead" \
  -H "Content-Type:application/json" \
  -d '{
  		"ids": [558051f9cf0d618312737f67, 456751f9cf0d618312737e86, 789051f9cf0d616452737p12]  
  	}'
```


### HTTP Request

`POST /api/direct-msg/markAsRead`

# Events

## List events



```shell
curl -v GET "https://rangehealthpro.com/api/event/?owner=558051f9cf0d618312737f67&forUser=558051f9cf0d618312737f67&start=567480238&end=612349062" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/event`


## Get event details



```shell
curl -v GET "https://rangehealthpro.com/api/event/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/event/:id`


# Person

## Retrieve basic person details



```shell
curl -v GET "https://rangehealthpro.com/api/person/558051f9cf0d618312737f67" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/person/:id`

## Retrieve record entries (and person details)



```shell
curl -v GET "https://rangehealthpro.com/api/record/558051f9cf0d618312737f67/?filterBy=form" \
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /api/record/:id`

## Create a record entry



```shell
curl -v POST "https://rangehealthpro.com/api/record" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": 558051f9cf0d618312737f67,
  		"message": "Sample record entry (note)",
  		"attachments": [attach1, attach2]
  	}'
```

### HTTP Request

`POST /api/record/`

## List fellow organization members OR people matching the specified name

```shell
curl -v GET "https://rangehealthpro.com/api/person/?orgs=true" \
  -H "Content-Type:application/json"

curl -v GET "https://rangehealthpro.com/api/person/?name=Ash" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person`


## Return a filtered list of record entries for a given person

```shell
curl -v GET "https://rangehealthpro.com/api/person/264809e90cf0d618312737f24/summary/cct" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/summary/:type`


## List lab results of specified person

```shell
curl -v GET "https://rangehealthpro.com/api/person/7231410cf0d618312737f24/labresult/?test=RBC" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/labresult`



## List prescriptions for specified person

```shell
curl -v GET "https://rangehealthpro.com/api/person/947260cf0d618312737f24/rx-timeline/?test=urineTest" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/person/:id/rx-timeline`

## Limited list of entries for patient connections of logged-in user

```shell
curl -v GET "https://rangehealthpro.com/api/entry/?limit=5" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/entry`

## Read profile of logged-in user

```shell
curl -v GET "https://rangehealthpro.com/api/profile" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/profile`



## Update profile of logged-in user

```shell
curl -v PUT "https://rangehealthpro.com/api/profile" \
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
                	phone: 777.757.7169
                }
  			}
  	}'
 ```


### HTTP Request

`PUT /api/profile`



## Read permissions of logged-in user

```shell
curl -v GET "https://rangehealthpro.com/api/permission" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/permission`




# Connections

## List connections of logged-in user



```shell
curl -v GET "https://rangehealthpro.com/api/connection/?status=connected&type=pro" \
  -H "Content-Type:application/json"
 ```


### HTTP Request

`GET /api/connection/`

## List connections of specified user



```shell
curl -v GET "https://rangehealthpro.com/api/connection/558051f9cf0d618312737f67/?status=connected&type=pro" \
  -H "Content-Type:application/json"
 ```


### HTTP Request

`GET /api/connection/:userId`

## Create a new pro connection request to the target user



```shell
curl -v POST "https://rangehealthpro.com/api/connection" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": 55805e90cf0d618312737e39
  	}'
 ```


### HTTP Request

`POST /api/connection/`

## Accept specified professional connection request



```shell
curl -v PUT "https://rangehealthpro.com/api/connection/55805e90cf0d618312737e39" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/connection/:userId`


## Reject the specified connection request



```shell
curl -v DELETE "https://rangehealthpro.com/api/connection/55805e90cf0d618312737e39" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/connection/:userId`

# Connection Requests

## List the patient referral requests for the logged-in user



```shell
curl -v GET "https://rangehealthpro.com/api/connection-request/?status=pending&type=pro" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/connection-request`



## Retrieve the specified patient referral request


```shell
curl -v GET "https://rangehealthpro.com/api/connection-request/55805e90cf0d618312737e39/?status=pending" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/connection-request/:id`


## Create a patient referral request for logged-in user to specified target



```shell
curl -v POST "https://rangehealthpro.com/api/connection-request" \
  -H "Content-Type:application/json" \
  -d '{
  		"target": 67543e90cf0d618312737q31,
  		"subject": "Sample connRequest",
  		"text": "Hey, I am a sample!"
  	}'
 ```


### HTTP Request

`POST /api/connection-request`


## Accept patient referral request



```shell
curl -v PUT "https://rangehealthpro.com/api/connection-request/72839e90cf0d618312737q31" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/connection-request/:id`



## Reject patient referral request



```shell
curl -v DELETE "https://rangehealthpro.com/api/connection-request/75039e90cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/connection-request/:id`

# Attachments

## Get specified attachment

```shell
curl -v GET "https://rangehealthpro.com/attach/774059e90cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /attach/:fileId`


## Read specified attachment

```shell
curl -v GET "https://rangehealthpro.com/attach/991759e90cf0d618312737f24/testFile.txt" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /attach/:fileId/:fileName`


## Create an attachment

```shell
curl -v POST "https://rangehealthpro.com/attach" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`POST /api/attach`


## Delete an attachment

```shell
curl -v DELETE "https://rangehealthpro.com/attach/348269e90cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /attach/:fileId`




# Organizations

## List all organizations

```shell
curl -v GET "https://rangehealthpro.com/api/org" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org`

## Get specified organization details

```shell
curl -v GET "https://rangehealthpro.com/api/org/232155cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:id`



## Create new organization

```shell
curl -v POST "https://rangehealthpro.com/api/org" \
  -H "Content-Type:application/json" \
  -d '{
  		"profile": 
  			{
  				"prefs": 
  					{
  					"fullname": "Organization Name",
                	email: org@email.com,
                	description: "Organization description",
                	comments: "Internal field",
                	address: "4660, West 10th Avenue",
                	phone: 777.757.1690
                }
  			}
  	}'
 ```


### HTTP Request

`POST /api/org`

## Update organization details

```shell
curl -v PUT "https://rangehealthpro.com/api/org/483958cf0d618312737f24" \
  -H "Content-Type:application/json" \
  -d '{
  		"profile": 
  			{
  				"prefs": 
  					{
  					"fullname": "Organization Name",
                	email: org@email.com,
                	description: "New organization description",
                	comments: "Internal field",
                	address: "4660, West 10th Avenue",
                	phone: 777.757.1699
                }
  			}
  	}'
 ```


### HTTP Request

`PUT /api/org/:id`


## Delete specified organization

```shell
curl -v DELETE "https://rangehealthpro.com/api/org/912378cf0d618312737f24" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:id`


## List membership requests for current user

```shell
curl -v GET "https://rangehealthpro.com/api/membership-request/?status=pending" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/membership-request`


## List membership requests for specified orgId

```shell
curl -v GET "https://rangehealthpro.com/api/org/45234868cf0d618312737f24/membership-request/?status=pending" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:orgId/membership-request`




## Retrieve membership request details

```shell
curl -v GET "https://rangehealthpro.com/api/org/4523e64o62618312737f24/membership-request/567868cf0d618312737f24/?status=connected" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`GET /api/org/:orgId/membership-request/:id`



## Create membership request for specified organization

```shell
curl -v POST "https://rangehealthpro.com/api/org/4523464362/membership-request/?subject=exampleMembRequest" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`POST /api/org/:orgId/membership-request`



## Approve membership request

```shell
curl -v PUT "https://rangehealthpro.com/api/org/4523868cf0d618312737f24/membership-request/98758v1cf0d618312737f24/" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`PUT /api/org/:orgId/membership-request/:id`



## Reject membership request

```shell
curl -v DELETE "https://rangehealthpro.com/api/org/45234868cf0d618312737f24/membership-request/9875869acf0d618312737f24/" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:orgId/membership-request/:id`


## Delete membership of logged-in user with specified org

```shell
curl -v DELETE "https://rangehealthpro.com/api/org/45234868cf0d618312737f24/membership" \
  -H "Content-Type:application/json" 
 ```


### HTTP Request

`DELETE /api/org/:orgId/membership`



