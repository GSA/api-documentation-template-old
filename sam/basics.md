---
layout: default
title: API Basics
nav: basics
---

### API basics
(New content added below for Modular Options)

The SAM API is a GET API which has one operation. The operation will retrieve an entity's public information. Its endpoint is ```https://api.data.gov/sam/v1/registrations/```. 

A couple basic notes: the rate limits for the API are currently 5,000 calls per 24 hours and 5 calls per 5 seconds. As we go forward and understand the impact of usage of the API on SAM, we will adjust the limits accordingly as well as allow for individual users with specific needs to have customized rate limits appropriate to their use.

##### Example URL

Currently, the below URL won't work without you adding in an API key from api.data.gov. Replace ```<YOUR_API_KEY>``` with your api.data.gov provided API key in the below URL to successfully execute the call.

[https://api.data.gov/sam/v1/registrations/1459697830000?api_key=YOUR_API_KEY](https://api.data.gov/sam/v1/registrations/1459697830000?api_key=YOUR_API_KEY)

##### Retrieving entity information
The endpoint for getting all data begins with ```/v1/registrations```. 

The endpoint takes a single URL parameter which is the DUNS and DUNS+4 information concatenated. If the entity does not have a DUNS+4, the user should include ```0000```. 

For example, if an entity of interest has a DUNS number of ```012345678``` with no DUNS+4, the access to the endpoint would be at ```/sam/v1/registrations/0123456780000```. An entity with the same DUNS but with a DUNS+4 of ```9999``` would be accessed at ```/sam/v1/registrations/0123456789999```.

The data in the API is updated daily by approximately 2 AM Eastern time for the prior day's data.

##### Finding DUNS numbers to use

In addition to the [search API](http://gsa.github.io/sam_api/sam/search.html), another way to get DUNS numbers is to go to [SAM](http://www.sam.gov), click on ```Search Records``` and enter in a company into the Quick Search box. Each entity has a DUNS number that you'll see in the result set. You'll see a 9-digit number which represents the DUNS. You can then pad it out with four ```0```s as mentioned above.

##### Search API

These are just the first of many steps in modernizing SAM and IAE. In fall 2014, the SAM API consumers added an API to search the SAM database and retrieve registration information specific to their needs. This means, most of the functionality you see on SAM right now to search for entities is available as an API. 

##### Modular Options

In fall 2015, the SAM API consumers enhanced the API to return only responded or all values. The returned API call will search the SAM database and retrieve registration information specific to their needs. 

For example, the API link with an endpoint "?return_values=full" will return all fields, regardless if the field was answered https://api.data.gov/samdata/v4/registrations/0123456780000?return_values=full)

The API link with an endpoint "?return_values=responded" will return all fields, regardless if the field was answered https://api.data.gov/samdata/v4/registrations/0123456780000?return_values=responded

In spring 2016, the SAM API will be further enhanced to include specific module returns. Core Data, Assertions, Reps and Certs, and Points of Contacts are the four main modules a consumer can select to return either all values or responded 


<body id="basics"></body>

