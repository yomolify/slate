---
title: API Reference

language_tabs:
  - shell


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
curl -v POST "http://api.rangehealthpro.com/emr/api/update"
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /emr/api/update`


## Recieves notification that a patient has been changed in the EMR


```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/patient_change_event"
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /emr/api/patient_change_event`

# Messages API

## Create a Direct Message from an EMR Message



```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/message"
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /emr/api/message`

## Read a message



```shell
curl -v GET "http://api.rangehealthpro.com/emr/api/message/:id"
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /emr/api/message/:id`


## Update a message



```shell
curl -v PUT "http://api.rangehealthpro.com/emr/api/message/:id"
  -H "Content-Type:application/json"
```


### HTTP Request

`PUT /emr/api/message/:id`

# emrEvent API

## Create emrEvent



```shell
curl -v POST "http://api.rangehealthpro.com/emr/api/event"
  -H "Content-Type:application/json"
```


### HTTP Request

`POST /emr/api/event`


## Read emrEvent



```shell
curl -v GET "http://api.rangehealthpro.com/emr/api/event/:id"
  -H "Content-Type:application/json"
```


### HTTP Request

`GET /emr/api/event/:id`



