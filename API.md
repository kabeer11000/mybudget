---
title: myBudget API v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="mybudget-api">myBudget API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

API for managing authentication, transactions, budgets, categories, and financial analytics.

Base URLs:

* <a href="https://api.mybudget.com/v1">https://api.mybudget.com/v1</a>

# Authentication

- HTTP Authentication, scheme: bearer Access token obtained via /auth/login

<h1 id="mybudget-api-default">Default</h1>

## post__auth_signup

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/signup \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.mybudget.com/v1/auth/signup HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "name": "string",
  "email": "user@example.com",
  "password": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.mybudget.com/v1/auth/signup',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/signup',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.mybudget.com/v1/auth/signup', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/signup', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/signup");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/signup", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/signup`

*Register a new user*

> Body parameter

```json
{
  "name": "string",
  "email": "user@example.com",
  "password": "string"
}
```

<h3 id="post__auth_signup-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» name|body|string|true|none|
|» email|body|string(email)|true|none|
|» password|body|string|true|none|

> Example responses

> 201 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "user": {
      "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
      "name": "string",
      "email": "user@example.com",
      "phone": "string",
      "verified": true,
      "last_login": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__auth_signup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|User registered|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|Inline|

<h3 id="post__auth_signup-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» user|[User](#schemauser)|false|none|none|
|»»» id|string(uuid)|true|none|none|
|»»» name|string|true|none|none|
|»»» email|string(email)|true|none|none|
|»»» phone|string|false|none|none|
|»»» verified|boolean|true|none|none|
|»»» last_login|string(date-time)|false|none|none|
|»»» created_at|string(date-time)|true|none|none|
|»»» updated_at|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **409**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="success">
This operation does not require authentication
</aside>

## post__auth_login

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/login \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.mybudget.com/v1/auth/login HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "string",
  "password": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.mybudget.com/v1/auth/login',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/login',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.mybudget.com/v1/auth/login', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/login', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/login");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/login", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/login`

*Login with email and password*

> Body parameter

```json
{
  "email": "string",
  "password": "string"
}
```

<h3 id="post__auth_login-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» email|body|string|true|none|
|» password|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "access_token": "string",
    "refresh_token": "string",
    "user": {
      "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
      "name": "string",
      "email": "user@example.com",
      "phone": "string",
      "verified": true,
      "last_login": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__auth_login-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Login successful|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__auth_login-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» access_token|string|false|none|none|
|»» refresh_token|string|false|none|none|
|»» user|[User](#schemauser)|false|none|none|
|»»» id|string(uuid)|true|none|none|
|»»» name|string|true|none|none|
|»»» email|string(email)|true|none|none|
|»»» phone|string|false|none|none|
|»»» verified|boolean|true|none|none|
|»»» last_login|string(date-time)|false|none|none|
|»»» created_at|string(date-time)|true|none|none|
|»»» updated_at|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="success">
This operation does not require authentication
</aside>

## post__auth_login_webauthn

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/login/webauthn \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.mybudget.com/v1/auth/login/webauthn HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "user@example.com",
  "webauthn_response": {}
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.mybudget.com/v1/auth/login/webauthn',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/login/webauthn',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.mybudget.com/v1/auth/login/webauthn', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/login/webauthn', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/login/webauthn");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/login/webauthn", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/login/webauthn`

*Login using WebAuthn*

> Body parameter

```json
{
  "email": "user@example.com",
  "webauthn_response": {}
}
```

<h3 id="post__auth_login_webauthn-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» email|body|string(email)|true|none|
|» webauthn_response|body|object|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "access_token": "string",
    "refresh_token": "string",
    "user": {
      "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
      "name": "string",
      "email": "user@example.com",
      "phone": "string",
      "verified": true,
      "last_login": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__auth_login_webauthn-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|WebAuthn login successful|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__auth_login_webauthn-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» access_token|string|false|none|none|
|»» refresh_token|string|false|none|none|
|»» user|[User](#schemauser)|false|none|none|
|»»» id|string(uuid)|true|none|none|
|»»» name|string|true|none|none|
|»»» email|string(email)|true|none|none|
|»»» phone|string|false|none|none|
|»»» verified|boolean|true|none|none|
|»»» last_login|string(date-time)|false|none|none|
|»»» created_at|string(date-time)|true|none|none|
|»»» updated_at|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="success">
This operation does not require authentication
</aside>

## post__auth_refresh

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/refresh \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.mybudget.com/v1/auth/refresh HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "refresh_token": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.mybudget.com/v1/auth/refresh',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/refresh',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.mybudget.com/v1/auth/refresh', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/refresh', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/refresh");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/refresh", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/refresh`

*Refresh access token*

> Body parameter

```json
{
  "refresh_token": "string"
}
```

<h3 id="post__auth_refresh-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» refresh_token|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "access_token": "string",
    "refresh_token": "string"
  }
}
```

<h3 id="post__auth_refresh-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Tokens refreshed|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__auth_refresh-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|[Tokens](#schematokens)|false|none|none|
|»» access_token|string|true|none|none|
|»» refresh_token|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="success">
This operation does not require authentication
</aside>

## post__auth_forgot-password

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/forgot-password \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.mybudget.com/v1/auth/forgot-password HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "user@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.mybudget.com/v1/auth/forgot-password',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/forgot-password',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.mybudget.com/v1/auth/forgot-password', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/forgot-password', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/forgot-password");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/forgot-password", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/forgot-password`

*Request password reset email*

> Body parameter

```json
{
  "email": "user@example.com"
}
```

<h3 id="post__auth_forgot-password-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» email|body|string(email)|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string"
}
```

<h3 id="post__auth_forgot-password-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Reset email sent|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="post__auth_forgot-password-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="success">
This operation does not require authentication
</aside>

## post__auth_reset-password

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/reset-password \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.mybudget.com/v1/auth/reset-password HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "token": "string",
  "new_password": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.mybudget.com/v1/auth/reset-password',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/reset-password',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.mybudget.com/v1/auth/reset-password', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/reset-password', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/reset-password");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/reset-password", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/reset-password`

*Reset password using token*

> Body parameter

```json
{
  "token": "string",
  "new_password": "string"
}
```

<h3 id="post__auth_reset-password-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» token|body|string|true|none|
|» new_password|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string"
}
```

<h3 id="post__auth_reset-password-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Password reset|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__auth_reset-password-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="success">
This operation does not require authentication
</aside>

## put__auth_change-password

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.mybudget.com/v1/auth/change-password \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
PUT https://api.mybudget.com/v1/auth/change-password HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "old_password": "string",
  "new_password": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/auth/change-password',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://api.mybudget.com/v1/auth/change-password',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.mybudget.com/v1/auth/change-password', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','https://api.mybudget.com/v1/auth/change-password', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/change-password");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.mybudget.com/v1/auth/change-password", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /auth/change-password`

*Change password (authenticated)*

> Body parameter

```json
{
  "old_password": "string",
  "new_password": "string"
}
```

<h3 id="put__auth_change-password-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» old_password|body|string|true|none|
|» new_password|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string"
}
```

<h3 id="put__auth_change-password-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Password changed|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|Inline|

<h3 id="put__auth_change-password-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **403**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__auth_logout

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/auth/logout \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/auth/logout HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "refresh_token": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/auth/logout',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/auth/logout',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/auth/logout', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/auth/logout', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/logout");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/auth/logout", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/logout`

*Logout and invalidate tokens*

> Body parameter

```json
{
  "refresh_token": "string"
}
```

<h3 id="post__auth_logout-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» refresh_token|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string"
}
```

<h3 id="post__auth_logout-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Logged out|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__auth_logout-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__auth_profile

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/auth/profile \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/auth/profile HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/auth/profile',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/auth/profile',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/auth/profile', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/auth/profile', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/profile");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/auth/profile", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /auth/profile`

*Get authenticated user profile*

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "user": {
      "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
      "name": "string",
      "email": "user@example.com",
      "phone": "string",
      "verified": true,
      "last_login": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="get__auth_profile-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Profile retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__auth_profile-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» user|[User](#schemauser)|false|none|none|
|»»» id|string(uuid)|true|none|none|
|»»» name|string|true|none|none|
|»»» email|string(email)|true|none|none|
|»»» phone|string|false|none|none|
|»»» verified|boolean|true|none|none|
|»»» last_login|string(date-time)|false|none|none|
|»»» created_at|string(date-time)|true|none|none|
|»»» updated_at|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## put__auth_profile

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.mybudget.com/v1/auth/profile \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
PUT https://api.mybudget.com/v1/auth/profile HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "name": "string",
  "phone": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/auth/profile',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://api.mybudget.com/v1/auth/profile',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.mybudget.com/v1/auth/profile', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','https://api.mybudget.com/v1/auth/profile', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/auth/profile");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.mybudget.com/v1/auth/profile", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /auth/profile`

*Update user profile*

> Body parameter

```json
{
  "name": "string",
  "phone": "string"
}
```

<h3 id="put__auth_profile-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» name|body|string|false|none|
|» phone|body|string|false|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "user": {
      "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
      "name": "string",
      "email": "user@example.com",
      "phone": "string",
      "verified": true,
      "last_login": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="put__auth_profile-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Profile updated|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="put__auth_profile-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» user|[User](#schemauser)|false|none|none|
|»»» id|string(uuid)|true|none|none|
|»»» name|string|true|none|none|
|»»» email|string(email)|true|none|none|
|»»» phone|string|false|none|none|
|»»» verified|boolean|true|none|none|
|»»» last_login|string(date-time)|false|none|none|
|»»» created_at|string(date-time)|true|none|none|
|»»» updated_at|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__transactions_expense

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/transactions/expense \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/transactions/expense HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "amount": 0.01,
  "category": "string",
  "description": "string",
  "date": "2019-08-24"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/expense',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/transactions/expense',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/transactions/expense', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/transactions/expense', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/expense");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/transactions/expense", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /transactions/expense`

*Add manual expense*

> Body parameter

```json
{
  "amount": 0.01,
  "category": "string",
  "description": "string",
  "date": "2019-08-24"
}
```

<h3 id="post__transactions_expense-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» amount|body|number|true|none|
|» category|body|string|true|none|
|» description|body|string|false|none|
|» date|body|string(date)|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "transaction": {
      "id": "string",
      "type": "income",
      "amount": 0.01,
      "category": "string",
      "description": "string",
      "date": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__transactions_expense-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Expense added|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__transactions_expense-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» transaction|[Transaction](#schematransaction)|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__transactions_income

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/transactions/income \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/transactions/income HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "amount": 0.01,
  "category": "string",
  "description": "string",
  "date": "2019-08-24"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/income',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/transactions/income',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/transactions/income', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/transactions/income', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/income");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/transactions/income", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /transactions/income`

*Add manual income*

> Body parameter

```json
{
  "amount": 0.01,
  "category": "string",
  "description": "string",
  "date": "2019-08-24"
}
```

<h3 id="post__transactions_income-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» amount|body|number|true|none|
|» category|body|string|true|none|
|» description|body|string|false|none|
|» date|body|string(date)|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "transaction": {
      "id": "string",
      "type": "income",
      "amount": 0.01,
      "category": "string",
      "description": "string",
      "date": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__transactions_income-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Income added|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__transactions_income-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» transaction|[Transaction](#schematransaction)|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__transactions_expense_nlp

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/transactions/expense/nlp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/transactions/expense/nlp HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "text": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/expense/nlp',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/transactions/expense/nlp',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/transactions/expense/nlp', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/transactions/expense/nlp', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/expense/nlp");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/transactions/expense/nlp", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /transactions/expense/nlp`

*Add expense via NLP*

> Body parameter

```json
{
  "text": "string"
}
```

<h3 id="post__transactions_expense_nlp-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» text|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "transaction": {
      "id": "string",
      "type": "income",
      "amount": 0.01,
      "category": "string",
      "description": "string",
      "date": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__transactions_expense_nlp-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|NLP expense added|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__transactions_expense_nlp-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» transaction|[Transaction](#schematransaction)|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__transactions_income_nlp

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/transactions/income/nlp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/transactions/income/nlp HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "text": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/income/nlp',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/transactions/income/nlp',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/transactions/income/nlp', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/transactions/income/nlp', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/income/nlp");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/transactions/income/nlp", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /transactions/income/nlp`

*Add income via NLP*

> Body parameter

```json
{
  "text": "string"
}
```

<h3 id="post__transactions_income_nlp-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» text|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "transaction": {
      "id": "string",
      "type": "income",
      "amount": 0.01,
      "category": "string",
      "description": "string",
      "date": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__transactions_income_nlp-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|NLP income added|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__transactions_income_nlp-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» transaction|[Transaction](#schematransaction)|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__transactions

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/transactions \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/transactions HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/transactions',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/transactions', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/transactions', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/transactions", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /transactions`

*Get filtered transactions*

<h3 id="get__transactions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|query|integer|false|none|
|year|query|integer|false|none|
|type|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|type|income|
|type|expense|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "transactions": [
      {
        "id": "string",
        "type": "income",
        "amount": 0.01,
        "category": "string",
        "description": "string",
        "date": "2019-08-24T14:15:22Z"
      }
    ]
  }
}
```

<h3 id="get__transactions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Transactions retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__transactions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» transactions|[[Transaction](#schematransaction)]|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__transactions_{id}

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/transactions/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/transactions/{id} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/transactions/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/transactions/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/transactions/{id}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/transactions/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /transactions/{id}`

*Get transaction by ID*

<h3 id="get__transactions_{id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "transaction": {
      "id": "string",
      "type": "income",
      "amount": 0.01,
      "category": "string",
      "description": "string",
      "date": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="get__transactions_{id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Transaction retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="get__transactions_{id}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» transaction|[Transaction](#schematransaction)|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## put__transactions_{id}

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.mybudget.com/v1/transactions/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
PUT https://api.mybudget.com/v1/transactions/{id} HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "amount": 0.01,
  "category": "string",
  "description": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/{id}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://api.mybudget.com/v1/transactions/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.mybudget.com/v1/transactions/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','https://api.mybudget.com/v1/transactions/{id}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.mybudget.com/v1/transactions/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /transactions/{id}`

*Update transaction*

> Body parameter

```json
{
  "amount": 0.01,
  "category": "string",
  "description": "string"
}
```

<h3 id="put__transactions_{id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|
|body|body|object|false|none|
|» amount|body|number|false|none|
|» category|body|string|false|none|
|» description|body|string|false|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "transaction": {
      "id": "string",
      "type": "income",
      "amount": 0.01,
      "category": "string",
      "description": "string",
      "date": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="put__transactions_{id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Transaction updated|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="put__transactions_{id}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» transaction|[Transaction](#schematransaction)|false|none|none|
|»»» id|string|true|none|none|
|»»» type|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» category|string|true|none|none|
|»»» description|string|false|none|none|
|»»» date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## delete__transactions_{id}

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.mybudget.com/v1/transactions/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
DELETE https://api.mybudget.com/v1/transactions/{id} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/{id}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.mybudget.com/v1/transactions/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.mybudget.com/v1/transactions/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://api.mybudget.com/v1/transactions/{id}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.mybudget.com/v1/transactions/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /transactions/{id}`

*Delete transaction*

<h3 id="delete__transactions_{id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string"
}
```

<h3 id="delete__transactions_{id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Transaction deleted|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="delete__transactions_{id}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__transactions_history_current-month

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/transactions/history/current-month \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/transactions/history/current-month HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/history/current-month',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/transactions/history/current-month',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/transactions/history/current-month', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/transactions/history/current-month', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/history/current-month");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/transactions/history/current-month", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /transactions/history/current-month`

*Get current month's transaction history*

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "month": "string",
    "year": 0,
    "transactions": [
      {
        "id": "string",
        "type": "string",
        "amount": 0,
        "category": "string"
      }
    ]
  }
}
```

<h3 id="get__transactions_history_current-month-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|History retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__transactions_history_current-month-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» month|string|false|none|none|
|»» year|integer|false|none|none|
|»» transactions|[object]|false|none|none|
|»»» id|string|false|none|none|
|»»» type|string|false|none|none|
|»»» amount|number|false|none|none|
|»»» category|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__transactions_history_{month}_{year}

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/transactions/history/{month}/{year} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/transactions/history/{month}/{year} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/transactions/history/{month}/{year}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/transactions/history/{month}/{year}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/transactions/history/{month}/{year}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/transactions/history/{month}/{year}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/transactions/history/{month}/{year}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/transactions/history/{month}/{year}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /transactions/history/{month}/{year}`

*Get history for specific month/year*

<h3 id="get__transactions_history_{month}_{year}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|path|integer|true|none|
|year|path|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "month": 0,
    "year": 0,
    "transactions": [
      {
        "id": "string",
        "type": "string",
        "amount": 0,
        "category": "string"
      }
    ]
  }
}
```

<h3 id="get__transactions_history_{month}_{year}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|History retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__transactions_history_{month}_{year}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» month|integer|false|none|none|
|»» year|integer|false|none|none|
|»» transactions|[object]|false|none|none|
|»»» id|string|false|none|none|
|»»» type|string|false|none|none|
|»»» amount|number|false|none|none|
|»»» category|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__budget

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/budget \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/budget HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "amount": 0.01,
  "month": 1,
  "year": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/budget',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/budget',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/budget', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/budget', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/budget");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/budget", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /budget`

*Create or update monthly budget*

> Body parameter

```json
{
  "amount": 0.01,
  "month": 1,
  "year": 0
}
```

<h3 id="post__budget-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» amount|body|number|true|none|
|» month|body|integer|false|none|
|» year|body|integer|false|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "budget": {
      "id": "string",
      "user_id": "string",
      "amount": 0.01,
      "month": 1,
      "year": 2000,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="post__budget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Budget saved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__budget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» budget|[Budget](#schemabudget)|false|none|none|
|»»» id|string|true|none|none|
|»»» user_id|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» month|integer|true|none|none|
|»»» year|integer|true|none|none|
|»»» created_at|string(date-time)|false|none|none|
|»»» updated_at|string(date-time)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__budget

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/budget \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/budget HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/budget',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/budget',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/budget', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/budget', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/budget");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/budget", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /budget`

*Get current month's budget*

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "budget": {
      "id": "string",
      "user_id": "string",
      "amount": 0.01,
      "month": 1,
      "year": 2000,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="get__budget-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Budget retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="get__budget-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» budget|[Budget](#schemabudget)|false|none|none|
|»»» id|string|true|none|none|
|»»» user_id|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» month|integer|true|none|none|
|»»» year|integer|true|none|none|
|»»» created_at|string(date-time)|false|none|none|
|»»» updated_at|string(date-time)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__budget_{month}_{year}

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/budget/{month}/{year} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/budget/{month}/{year} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/budget/{month}/{year}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/budget/{month}/{year}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/budget/{month}/{year}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/budget/{month}/{year}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/budget/{month}/{year}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/budget/{month}/{year}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /budget/{month}/{year}`

*Get budget for specific month/year*

<h3 id="get__budget_{month}_{year}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|path|integer|true|none|
|year|path|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "budget": {
      "id": "string",
      "user_id": "string",
      "amount": 0.01,
      "month": 1,
      "year": 2000,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  }
}
```

<h3 id="get__budget_{month}_{year}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Budget retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="get__budget_{month}_{year}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» budget|[Budget](#schemabudget)|false|none|none|
|»»» id|string|true|none|none|
|»»» user_id|string|true|none|none|
|»»» amount|number|true|none|none|
|»»» month|integer|true|none|none|
|»»» year|integer|true|none|none|
|»»» created_at|string(date-time)|false|none|none|
|»»» updated_at|string(date-time)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## delete__budget_{month}_{year}

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.mybudget.com/v1/budget/{month}/{year} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
DELETE https://api.mybudget.com/v1/budget/{month}/{year} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/budget/{month}/{year}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.mybudget.com/v1/budget/{month}/{year}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.mybudget.com/v1/budget/{month}/{year}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://api.mybudget.com/v1/budget/{month}/{year}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/budget/{month}/{year}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.mybudget.com/v1/budget/{month}/{year}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /budget/{month}/{year}`

*Delete budget for specific month/year*

<h3 id="delete__budget_{month}_{year}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|path|integer|true|none|
|year|path|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "string",
  "data": {
    "deleted": true,
    "budget_id": "string"
  }
}
```

<h3 id="delete__budget_{month}_{year}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Budget deleted|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="delete__budget_{month}_{year}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» message|string|false|none|none|
|» data|object|false|none|none|
|»» deleted|boolean|false|none|none|
|»» budget_id|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|deleted|true|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__budget_status

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/budget/status \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/budget/status HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/budget/status',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/budget/status',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/budget/status', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/budget/status', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/budget/status");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/budget/status", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /budget/status`

*Get budget status*

<h3 id="get__budget_status-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|query|integer|false|none|
|year|query|integer|false|none|

> Example responses

> 200 Response

```json
{
  "budget": {
    "amount": 0,
    "month": 0,
    "year": 0
  },
  "spending": {
    "total_spent": 0,
    "remaining": 0,
    "percentage_used": 100,
    "is_overspent": true,
    "overspent_amount": 0
  }
}
```

<h3 id="get__budget_status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Status retrieved|[BudgetStatus](#schemabudgetstatus)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="get__budget_status-responseschema">Response Schema</h3>

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__budget_alerts

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/budget/alerts \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/budget/alerts HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/budget/alerts',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/budget/alerts',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/budget/alerts', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/budget/alerts', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/budget/alerts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/budget/alerts", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /budget/alerts`

*Check for budget alerts*

<h3 id="get__budget_alerts-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|query|integer|false|none|
|year|query|integer|false|none|

> Example responses

> 200 Response

```json
{
  "has_alert": true,
  "alert_type": "overspending",
  "budget": {
    "amount": 0,
    "month": 0,
    "year": 0
  },
  "spending": {
    "total_spent": 0,
    "overspent_amount": 0,
    "percentage_over": 0
  },
  "message": "string"
}
```

<h3 id="get__budget_alerts-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Alerts retrieved|[BudgetAlert](#schemabudgetalert)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|Inline|

<h3 id="get__budget_alerts-responseschema">Response Schema</h3>

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **404**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__analytics_summary_{month}_{year}

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/analytics/summary/{month}/{year} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/analytics/summary/{month}/{year} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/analytics/summary/{month}/{year}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/analytics/summary/{month}/{year}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/analytics/summary/{month}/{year}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/analytics/summary/{month}/{year}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/analytics/summary/{month}/{year}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/analytics/summary/{month}/{year}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /analytics/summary/{month}/{year}`

*Get monthly financial summary*

<h3 id="get__analytics_summary_{month}_{year}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|path|integer|true|none|
|year|path|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "month": 0,
    "year": 0,
    "total_income": 0,
    "total_expense": 0,
    "balance": 0
  }
}
```

<h3 id="get__analytics_summary_{month}_{year}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Summary retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__analytics_summary_{month}_{year}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|[MonthlySummary](#schemamonthlysummary)|false|none|none|
|»» month|integer|false|none|none|
|»» year|integer|false|none|none|
|»» total_income|number|false|none|none|
|»» total_expense|number|false|none|none|
|»» balance|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__analytics_charts_category

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/analytics/charts/category?month=1&year=0 \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/analytics/charts/category?month=1&year=0 HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/analytics/charts/category?month=1&year=0',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/analytics/charts/category',
  params: {
  'month' => 'integer',
'year' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/analytics/charts/category', params={
  'month': '1',  'year': '0'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/analytics/charts/category', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/analytics/charts/category?month=1&year=0");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/analytics/charts/category", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /analytics/charts/category`

*Get category-wise spending breakdown*

<h3 id="get__analytics_charts_category-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|query|integer|true|none|
|year|query|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "month": 0,
    "year": 0,
    "categories": [
      {
        "id": "string",
        "name": "string",
        "icon": "string",
        "color": "string",
        "total_spent": 0,
        "percentage": 0
      }
    ]
  }
}
```

<h3 id="get__analytics_charts_category-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Category breakdown retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__analytics_charts_category-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|[CategoryBreakdown](#schemacategorybreakdown)|false|none|none|
|»» month|integer|false|none|none|
|»» year|integer|false|none|none|
|»» categories|[object]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» icon|string|false|none|none|
|»»» color|string|false|none|none|
|»»» total_spent|number|false|none|none|
|»»» percentage|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__analytics_charts_monthly-trend_{year}

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/analytics/charts/monthly-trend/{year}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /analytics/charts/monthly-trend/{year}`

*Get spending trends over months*

<h3 id="get__analytics_charts_monthly-trend_{year}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|year|path|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "year": 0,
    "months": [
      {
        "month": 0,
        "total_income": 0,
        "total_expense": 0,
        "balance": 0
      }
    ]
  }
}
```

<h3 id="get__analytics_charts_monthly-trend_{year}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Monthly trend retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__analytics_charts_monthly-trend_{year}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|[MonthlyTrend](#schemamonthlytrend)|false|none|none|
|»» year|integer|false|none|none|
|»» months|[object]|false|none|none|
|»»» month|integer|false|none|none|
|»»» total_income|number|false|none|none|
|»»» total_expense|number|false|none|none|
|»»» balance|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__analytics_income-vs-expense_{month}_{year}

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year} HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/analytics/income-vs-expense/{month}/{year}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /analytics/income-vs-expense/{month}/{year}`

*Get income vs expense comparison*

<h3 id="get__analytics_income-vs-expense_{month}_{year}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|month|path|integer|true|none|
|year|path|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "month": 0,
    "year": 0,
    "total_income": 0,
    "total_expense": 0,
    "difference": 0,
    "income_percentage": 0,
    "expense_percentage": 0
  }
}
```

<h3 id="get__analytics_income-vs-expense_{month}_{year}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Comparison retrieved|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__analytics_income-vs-expense_{month}_{year}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|[IncomeVsExpense](#schemaincomevsexpense)|false|none|none|
|»» month|integer|false|none|none|
|»» year|integer|false|none|none|
|»» total_income|number|false|none|none|
|»» total_expense|number|false|none|none|
|»» difference|number|false|none|none|
|»» income_percentage|number|false|none|none|
|»» expense_percentage|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__categories_expense

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/categories/expense \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/categories/expense HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/categories/expense',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/categories/expense',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/categories/expense', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/categories/expense', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/categories/expense");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/categories/expense", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /categories/expense`

*Get expense categories*

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "categories": [
      {
        "id": "string",
        "name": "string",
        "type": "income",
        "icon": "string",
        "color": "string",
        "is_custom": true
      }
    ]
  }
}
```

<h3 id="get__categories_expense-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Categories retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__categories_expense-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» categories|[[Category](#schemacategory)]|false|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» type|string|true|none|none|
|»»» icon|string|false|none|none|
|»»» color|string|false|none|none|
|»»» is_custom|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## get__categories_income

> Code samples

```shell
# You can also use wget
curl -X GET https://api.mybudget.com/v1/categories/income \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.mybudget.com/v1/categories/income HTTP/1.1
Host: api.mybudget.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/categories/income',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.mybudget.com/v1/categories/income',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.mybudget.com/v1/categories/income', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.mybudget.com/v1/categories/income', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/categories/income");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.mybudget.com/v1/categories/income", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /categories/income`

*Get income categories*

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "categories": [
      {
        "id": "string",
        "name": "string",
        "type": "income",
        "icon": "string",
        "color": "string",
        "is_custom": true
      }
    ]
  }
}
```

<h3 id="get__categories_income-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Categories retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="get__categories_income-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» categories|[[Category](#schemacategory)]|false|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» type|string|true|none|none|
|»»» icon|string|false|none|none|
|»»» color|string|false|none|none|
|»»» is_custom|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## post__categories_custom

> Code samples

```shell
# You can also use wget
curl -X POST https://api.mybudget.com/v1/categories/custom \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://api.mybudget.com/v1/categories/custom HTTP/1.1
Host: api.mybudget.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "name": "string",
  "type": "income",
  "icon": "string",
  "color": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.mybudget.com/v1/categories/custom',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.mybudget.com/v1/categories/custom',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.mybudget.com/v1/categories/custom', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://api.mybudget.com/v1/categories/custom', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.mybudget.com/v1/categories/custom");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.mybudget.com/v1/categories/custom", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /categories/custom`

*Create custom category*

> Body parameter

```json
{
  "name": "string",
  "type": "income",
  "icon": "string",
  "color": "string"
}
```

<h3 id="post__categories_custom-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» name|body|string|true|none|
|» type|body|string|true|none|
|» icon|body|string|false|none|
|» color|body|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|income|
|» type|expense|

> Example responses

> 200 Response

```json
{
  "success": true,
  "data": {
    "category": {
      "id": "string",
      "name": "string",
      "type": "income",
      "icon": "string",
      "color": "string",
      "is_custom": true
    }
  }
}
```

<h3 id="post__categories_custom-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Category created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|Inline|

<h3 id="post__categories_custom-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|
|» data|object|false|none|none|
|»» category|[Category](#schemacategory)|false|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» type|string|true|none|none|
|»»» icon|string|false|none|none|
|»»» color|string|false|none|none|
|»»» is_custom|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|true|
|type|income|
|type|expense|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|true|none|none|
|» error|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|success|false|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

# Schemas

<h2 id="tocS_User">User</h2>
<!-- backwards compatibility -->
<a id="schemauser"></a>
<a id="schema_User"></a>
<a id="tocSuser"></a>
<a id="tocsuser"></a>

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "name": "string",
  "email": "user@example.com",
  "phone": "string",
  "verified": true,
  "last_login": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|none|
|name|string|true|none|none|
|email|string(email)|true|none|none|
|phone|string|false|none|none|
|verified|boolean|true|none|none|
|last_login|string(date-time)|false|none|none|
|created_at|string(date-time)|true|none|none|
|updated_at|string(date-time)|true|none|none|

<h2 id="tocS_Tokens">Tokens</h2>
<!-- backwards compatibility -->
<a id="schematokens"></a>
<a id="schema_Tokens"></a>
<a id="tocStokens"></a>
<a id="tocstokens"></a>

```json
{
  "access_token": "string",
  "refresh_token": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|access_token|string|true|none|none|
|refresh_token|string|true|none|none|

<h2 id="tocS_Transaction">Transaction</h2>
<!-- backwards compatibility -->
<a id="schematransaction"></a>
<a id="schema_Transaction"></a>
<a id="tocStransaction"></a>
<a id="tocstransaction"></a>

```json
{
  "id": "string",
  "type": "income",
  "amount": 0.01,
  "category": "string",
  "description": "string",
  "date": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|amount|number|true|none|none|
|category|string|true|none|none|
|description|string|false|none|none|
|date|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|income|
|type|expense|

<h2 id="tocS_Budget">Budget</h2>
<!-- backwards compatibility -->
<a id="schemabudget"></a>
<a id="schema_Budget"></a>
<a id="tocSbudget"></a>
<a id="tocsbudget"></a>

```json
{
  "id": "string",
  "user_id": "string",
  "amount": 0.01,
  "month": 1,
  "year": 2000,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|user_id|string|true|none|none|
|amount|number|true|none|none|
|month|integer|true|none|none|
|year|integer|true|none|none|
|created_at|string(date-time)|false|none|none|
|updated_at|string(date-time)|false|none|none|

<h2 id="tocS_Category">Category</h2>
<!-- backwards compatibility -->
<a id="schemacategory"></a>
<a id="schema_Category"></a>
<a id="tocScategory"></a>
<a id="tocscategory"></a>

```json
{
  "id": "string",
  "name": "string",
  "type": "income",
  "icon": "string",
  "color": "string",
  "is_custom": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|
|type|string|true|none|none|
|icon|string|false|none|none|
|color|string|false|none|none|
|is_custom|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|income|
|type|expense|

<h2 id="tocS_BudgetStatus">BudgetStatus</h2>
<!-- backwards compatibility -->
<a id="schemabudgetstatus"></a>
<a id="schema_BudgetStatus"></a>
<a id="tocSbudgetstatus"></a>
<a id="tocsbudgetstatus"></a>

```json
{
  "budget": {
    "amount": 0,
    "month": 0,
    "year": 0
  },
  "spending": {
    "total_spent": 0,
    "remaining": 0,
    "percentage_used": 100,
    "is_overspent": true,
    "overspent_amount": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|budget|object|false|none|none|
|» amount|number|false|none|none|
|» month|integer|false|none|none|
|» year|integer|false|none|none|
|spending|object|false|none|none|
|» total_spent|number|false|none|none|
|» remaining|number|false|none|none|
|» percentage_used|number|false|none|none|
|» is_overspent|boolean|false|none|none|
|» overspent_amount|number|false|none|none|

<h2 id="tocS_BudgetAlert">BudgetAlert</h2>
<!-- backwards compatibility -->
<a id="schemabudgetalert"></a>
<a id="schema_BudgetAlert"></a>
<a id="tocSbudgetalert"></a>
<a id="tocsbudgetalert"></a>

```json
{
  "has_alert": true,
  "alert_type": "overspending",
  "budget": {
    "amount": 0,
    "month": 0,
    "year": 0
  },
  "spending": {
    "total_spent": 0,
    "overspent_amount": 0,
    "percentage_over": 0
  },
  "message": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|has_alert|boolean|false|none|none|
|alert_type|string|false|none|none|
|budget|object|false|none|none|
|» amount|number|false|none|none|
|» month|integer|false|none|none|
|» year|integer|false|none|none|
|spending|object|false|none|none|
|» total_spent|number|false|none|none|
|» overspent_amount|number|false|none|none|
|» percentage_over|number|false|none|none|
|message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|alert_type|overspending|
|alert_type|approaching_limit|
|alert_type|none|

<h2 id="tocS_MonthlySummary">MonthlySummary</h2>
<!-- backwards compatibility -->
<a id="schemamonthlysummary"></a>
<a id="schema_MonthlySummary"></a>
<a id="tocSmonthlysummary"></a>
<a id="tocsmonthlysummary"></a>

```json
{
  "month": 0,
  "year": 0,
  "total_income": 0,
  "total_expense": 0,
  "balance": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|month|integer|false|none|none|
|year|integer|false|none|none|
|total_income|number|false|none|none|
|total_expense|number|false|none|none|
|balance|number|false|none|none|

<h2 id="tocS_CategoryBreakdown">CategoryBreakdown</h2>
<!-- backwards compatibility -->
<a id="schemacategorybreakdown"></a>
<a id="schema_CategoryBreakdown"></a>
<a id="tocScategorybreakdown"></a>
<a id="tocscategorybreakdown"></a>

```json
{
  "month": 0,
  "year": 0,
  "categories": [
    {
      "id": "string",
      "name": "string",
      "icon": "string",
      "color": "string",
      "total_spent": 0,
      "percentage": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|month|integer|false|none|none|
|year|integer|false|none|none|
|categories|[object]|false|none|none|
|» id|string|false|none|none|
|» name|string|false|none|none|
|» icon|string|false|none|none|
|» color|string|false|none|none|
|» total_spent|number|false|none|none|
|» percentage|number|false|none|none|

<h2 id="tocS_MonthlyTrend">MonthlyTrend</h2>
<!-- backwards compatibility -->
<a id="schemamonthlytrend"></a>
<a id="schema_MonthlyTrend"></a>
<a id="tocSmonthlytrend"></a>
<a id="tocsmonthlytrend"></a>

```json
{
  "year": 0,
  "months": [
    {
      "month": 0,
      "total_income": 0,
      "total_expense": 0,
      "balance": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|year|integer|false|none|none|
|months|[object]|false|none|none|
|» month|integer|false|none|none|
|» total_income|number|false|none|none|
|» total_expense|number|false|none|none|
|» balance|number|false|none|none|

<h2 id="tocS_IncomeVsExpense">IncomeVsExpense</h2>
<!-- backwards compatibility -->
<a id="schemaincomevsexpense"></a>
<a id="schema_IncomeVsExpense"></a>
<a id="tocSincomevsexpense"></a>
<a id="tocsincomevsexpense"></a>

```json
{
  "month": 0,
  "year": 0,
  "total_income": 0,
  "total_expense": 0,
  "difference": 0,
  "income_percentage": 0,
  "expense_percentage": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|month|integer|false|none|none|
|year|integer|false|none|none|
|total_income|number|false|none|none|
|total_expense|number|false|none|none|
|difference|number|false|none|none|
|income_percentage|number|false|none|none|
|expense_percentage|number|false|none|none|

