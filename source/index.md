---
title: API Reference


includes:
  - errors

search: true
---

# Introduction

Welcome to the CareCru API! You can use our API to access CareCru's API-Server endpoints.

You can view code examples in the dark area to the right.



# Appointment Scheduling

The following end points are for use by the provider and customer end webservers to communicate with the API-Server.

## Add an Appointment

Booking an appointment

```shell
curl -v POST "https://api.carecru.com/appointment" \
  -H "Content-Type:application/json" \
  -d '{
  		"Provider": "Dr Amir",
		"Patient": "Carson",
		"StartTime": "2011-02-22T18:25:43.511Z",
		"EndTime": "2011-02-22T18:45:43.511Z",
		"Address": "7830 West 17th Ave",
		"City": "Tofino",
		"Province": "BC",
		"PostalCode": "V9Z 9A2",
		"Country": "Canada"
	}'
```


### HTTP Request

`POST /appointment`


