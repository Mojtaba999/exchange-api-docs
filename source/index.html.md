---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to [Exchange](https://www.exchange.com/index) API document for developers.

This file provides the related API application introduction. Open-API includes the port to acquire balance, all orders ,and all transaction record. Ws-API response for the port of K line functions.

# Getting Started

REST, a.k.a Respresntational State Transfer, is an architectural style that defines a set of constraints and properties based on HTTP. REST is known for its clear structure, readability, standardization and scalability. Its advantages are as follows:

* Each URL represents one web resource in RESTful architecture.
* Acting as a representation of resources between client and server.
* Client is enabled to operate server-side resources with 4 HTTP requests - representational state transfer.

Developers are recommended to use REST API to proceed spot trading and withdrawals.

# Encrypted Verification of API

## Generate an API Key

Before signing any request, you must generate an API key via [Exchange’s official website](https://www.exchange.com/index) 【User Center】-【API】. After generating the key, there are three things you must bear in mind:

* API Key
* Secret Key

API Key and Secret are randomly generated and provided, Passphrase is set by user.

## Initiate a Request

All REST requests must include the following headings:

* ACCESS-KEY API Key as a string.
* ACCESS-SIGN uses base64-encoded signatures (see Signed Messages).
* ACCESS-TIMESTAMP is the timestamp of your request.header MUST be number of seconds since Unix Epoch in UTC. Decimal values are allowed.
* All requests should contain content like application/x-www-form-urlencoded and be valid JSON.

## Signature

Generate a string to be signed - [open-api Demo](https://github.com/exchange-doc/api/blob/master/demo/demo.java)

1. Sort the parameters in ascending order of their parameter names in lexicographic order
2. Traversing the sorted dictionary, splicing all parameters together in "keyvalue" format (non-null parameters)
3. Use MD5 to treat signature strings

**For example:**

api_key = 1234567
time = 12312312312137
secret_key = 789654
sign = md5(api_key1234567time12312312312137789654)

## <span id="a6">Request Process</span>

The root URL for REST access：``` https://api.Exchange.com ```

###  <span id="a7">Request</span>
All requests are based on Https protocol, contentType in the request header must be uniformly set as: ‘application/x-www-form-urlencoded’.

**Request Process Descriptions**

1、Request parameter: parameter encapsulation based on the port request.

2、Submitting request parameter: submit the encapsulated parameter request to the server via POST/GET/PUT/DELETE or other methods.

3、Server response: the server will first perform a security validation, then send back the requested data to the client in JSON format.

4、Data processing: processing server response data.

**Success**





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
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
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
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
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
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
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
curl "http://example.com/api/kittens/2"
  -X DELETE
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

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

