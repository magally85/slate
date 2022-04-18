---
title: API Reference MVVC

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript
  - csharp

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - examples

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Introduction to VIDSigner

The purpose of the services is to provide documents to sign to the
VIDsigner devices and retrieve the documents once they are signed.  
The services are suited under a SSL channel, which means that all data
sent and retrieved to/from the services is sent through a secure
ciphered channel.  
For all operation descriptions, we include a relative URL. There is both
a root URL for preproduction environment and for production environment.
The integration trials must be performed in the preproduction
environment.  
The root URLs are the following:  

<span>**PreProduction**</span>

  
https://pre-vidsignercloud.validatedid.com/api/v2.1

<span>**Production**</span>

  
https://vidsignercloud.validatedid.com/api/v2.1  

  
For instance, to get the list of available devices for a subscription in
preproduction, the full URL is:  
<span>
https://pre-vidsignercloud.validatedid.com/api/v2.1/devices</span>


# IP Address

The services are hold under a static IP address. Usually it is
sufficient using the URLs of the services and not necessary to deal with
IPs. The only exception is the case of creating a notification service
(see Annex I) to be informed when a document.  
Some networks require to add the VIDsigner Service IP Address to the
trusted IPs in order to not be blocked by the firewall and get access to
the notification service.

VIDsigner can send notifications when a document has been signed or
rejected (see Annex I for more information). Those notifications are
sent from the following IPs:  

<span>**Production:**</span>

23.101.65.212

<span>**Pre-Production:**</span>

52.166.168.111


# Conventions

General conventions for VIDsigner REST APIs:  
Requests require authentication (see “Authentication” in section
“[\[SEC:Authentication\]](#SEC:Authentication)”).  
HTTP requests behave uniformly with all resources by giving a uniform
meaning to HTTP verbs:  

<span>**GET:**</span>

read  

create  

erase data  

In all the samples of the present document the data of the HTTP request
and responses is codified in JSON. However XML language is supported as
well. Check the section “Data Format and Response Codes” to get more
information.

# SSL

All the information is sent to and received from the services through
SSL, keeping the data secured at all times. In order to establish the
SSL channel, it is necessary to install the ValidatedID Host Certificate
in your certificate store as a trusted root certificate.  
There are different certificate stores, such as Windows Certificate
Store, Java Certificate Store and SAP Certificate Store. Please refer to
your application framework documentation to check which store to use.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

```csharp
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

```csharp
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

```csharp
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

```csharp
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

