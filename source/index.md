---
title: Airslip API v2022.5
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

<h1 id="airslip-api">Airslip API v2022.5</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Airslip API enables financial institutions to get access to real-time financial risk data on small and medium sized businesses.Financial institutions all assess risk differently and that is why we have built the platform so you get notified when only the risk you care about happens.- Get access to financials such as balance sheets, cashflow statements, P&L and cash position.- Get notified when new invoices are uploaded to accounting systems within seconds.

Base URLs:

* <a href="http://localhost:7101">http://localhost:7101</a>

# Authentication

* API Key (Bearer)
    - Parameter Name: **Authorization**, in: header. e.g Bearer Api_Key.

Requests to the Airslip API are authenticated using the applications `Api_Key`. You can view and manage your credentials in the Airslip Dashboard.

An Api_Key provides connectivity to all authenticated Airslip API endpoints, so it is important to keep these credentials secure. Do not share your Api_Key in publicly accessible areas such as GitHub, client-side code, or easily accessible configuration settings.

Authentication is performed using Bearer Authentication. Your Api_Key should be sent as the token.

All requests should be made via HTTPS.

<h1 id="airslip-api-banking">Banking</h1>

A collection of banking APIs for a connected business after linking at least one of their bank accounts

## Get Bank Transactions

<a id="opIdGet Bank Transactions"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/banking/{businessId}/transactions/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/banking/{businessId}/transactions/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/banking/{businessId}/transactions/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/banking/{businessId}/transactions/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/banking/{businessId}/transactions/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/banking/{businessId}/transactions/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/banking/{businessId}/transactions/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/banking/{businessId}/transactions/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/banking/{businessId}/transactions/search`

*Search for bank transactions for a connected business*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-bank-transactions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[QueryModel](#schemaquerymodel)|false|The bank transaction model within the search query. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "id": "4873a037963341e0b5f9de6b8260b8b2",
      "bankTransactionId": "3bd0a590ec6345b4916de2fb99315083",
      "transactionHash": "adad72d7b3069ab9e4a6cb2844e2e3e9.1",
      "integration": {
        "id": "9a64fc137f2f4b28864e2d64728469bf",
        "name": "American Express Business Current Account",
        "accountDetail": {
          "lastCardDigits": "1234",
          "currencyCode": "GBP",
          "usageType": "BUSINESS",
          "accountType": "CURRENT",
          "sortCode": "01-23-45",
          "accountNumber": "12345678"
        },
        "provider": {
          "id": "",
          "name": "American Express Business Current Account",
          "provider": "amex",
          "friendlyName": "American Express",
          "integrationType": "Commerce"
        }
      },
      "authorisedDate": 1651600087633,
      "capturedDate": 1651686487633,
      "amount": 359900,
      "currencyCode": "GBP",
      "description": "SLACK T01GDPJA77D       DUBLIN",
      "lastCardDigits": "6578",
      "isoFamilyCode": "ICDT",
      "proprietaryCode": "Debit",
      "reference": "T01GDPJA77D",
      "merchant": {
        "id": "2faf811eb18b46cd899e6db2dd83af12",
        "legalName": "Slack Technologies Limited",
        "tradingName": "Slack",
        "companyNumber": "IE558379",
        "taxNumber": "GB369212978",
        "category": {
          "name": "ComputerSoftware",
          "iso18245MerchantCategoryCode": "7372"
        },
        "merchantIdentifierNumber": null,
        "subsidiaries": [
          "Lattice",
          "Awesome and Howdy",
          "Small Wins",
          "Rimeto",
          "Spaces, Inc",
          "Screenhero, Inc",
          "Woven Software, Inc"
        ],
        "parentCompany": "Salesforce",
        "headquartersAddress": {
          "firstLine": "One Park Place, 4th Floor",
          "secondLine": "Hatch Street Dublin 2",
          "locality": "Saint Kevin's",
          "administrativeArea": "Dublin",
          "subAdministrativeArea": null,
          "postalCode": "D02 E651",
          "countryCode": "IL"
        },
        "contactDetail": {
          "email": "example@slack.com",
          "contactNumber": "01234567890",
          "websiteUrl": "https://slack.com"
        },
        "directors": [
          {
            "firstName": "Stewart",
            "surname": "Butterfield",
            "nationality": "CA",
            "countryOfResidence": "US",
            "hasNegativeInfo": false,
            "signingAuthority": true,
            "address": null,
            "position": {
              "name": "Chief Executive Officer",
              "authority": "",
              "dateAppointedTimestamp": 1645967251000,
              "companyName": "Slack Technologies Limited",
              "companyNumber": "IE558379",
              "latestTurnoverFigure": 63000000000,
              "latestTurnoverCurrency": "USD",
              "status": "Current",
              "commonCode": null,
              "providerCode": "LLC",
              "creditScore": "999",
              "latestRatingChangeTimestamp": 1651686487633,
              "additionalData": null
            }
          }
        ],
        "logoUrl": null
      },
      "merchantTransactionType": "Supplier",
      "entityStatus": 0
    }
  ],
  "paging": {
    "totalRecords": 1,
    "recordsPerPage": 10,
    "page": 1,
    "next": null
  }
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-bank-transactions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[BankTransactionReportModelEntitySearchResponse](#schemabanktransactionreportmodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Bank Transaction

<a id="opIdGet Bank Transaction"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/banking/{businessId}/transactions/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/banking/{businessId}/transactions/{id} HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/banking/{businessId}/transactions/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/banking/{businessId}/transactions/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/banking/{businessId}/transactions/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/banking/{businessId}/transactions/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/banking/{businessId}/transactions/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/banking/{businessId}/transactions/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/banking/{businessId}/transactions/{id}`

*Get a singular bank transaction by id*

<h3 id="get-bank-transaction-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|id|path|string|true|The identifier for the bank transaction|

> Example responses

> 200 Response

```json
{
  "id": "4873a037963341e0b5f9de6b8260b8b2",
  "bankTransactionId": "1d4ce1ae52db4cf082a7f4a2de2c7607",
  "transactionHash": "adad72d7b3069ab9e4a6cb2844e2e3e9.1",
  "integration": {
    "id": "a1d01ae564e7403686226b788d27a78e",
    "name": "American Express Business Current Account",
    "accountDetail": {
      "lastCardDigits": "1234",
      "currencyCode": "GBP",
      "usageType": "BUSINESS",
      "accountType": "CURRENT",
      "sortCode": "01-23-45",
      "accountNumber": "12345678"
    },
    "provider": {
      "id": "",
      "name": "American Express Business Current Account",
      "provider": "amex",
      "friendlyName": "American Express",
      "integrationType": "Commerce"
    }
  },
  "authorisedDate": 1651600087635,
  "capturedDate": 1651686487635,
  "amount": 359900,
  "currencyCode": "GBP",
  "description": "SLACK T01GDPJA77D       DUBLIN",
  "lastCardDigits": "6578",
  "isoFamilyCode": "ICDT",
  "proprietaryCode": "Debit",
  "reference": "T01GDPJA77D",
  "merchant": {
    "id": "5dfaecd77f8f4046a2f77c277644051b",
    "legalName": "Slack Technologies Limited",
    "tradingName": "Slack",
    "companyNumber": "IE558379",
    "taxNumber": "GB369212978",
    "category": {
      "name": "ComputerSoftware",
      "iso18245MerchantCategoryCode": "7372"
    },
    "merchantIdentifierNumber": null,
    "subsidiaries": [
      "Lattice",
      "Awesome and Howdy",
      "Small Wins",
      "Rimeto",
      "Spaces, Inc",
      "Screenhero, Inc",
      "Woven Software, Inc"
    ],
    "parentCompany": "Salesforce",
    "headquartersAddress": {
      "firstLine": "One Park Place, 4th Floor",
      "secondLine": "Hatch Street Dublin 2",
      "locality": "Saint Kevin's",
      "administrativeArea": "Dublin",
      "subAdministrativeArea": null,
      "postalCode": "D02 E651",
      "countryCode": "IL"
    },
    "contactDetail": {
      "email": "example@slack.com",
      "contactNumber": "01234567890",
      "websiteUrl": "https://slack.com"
    },
    "directors": [
      {
        "firstName": "Stewart",
        "surname": "Butterfield",
        "nationality": "CA",
        "countryOfResidence": "US",
        "hasNegativeInfo": false,
        "signingAuthority": true,
        "address": null,
        "position": {
          "name": "Chief Executive Officer",
          "authority": "",
          "dateAppointedTimestamp": 1645967251000,
          "companyName": "Slack Technologies Limited",
          "companyNumber": "IE558379",
          "latestTurnoverFigure": 63000000000,
          "latestTurnoverCurrency": "USD",
          "status": "Current",
          "commonCode": null,
          "providerCode": "LLC",
          "creditScore": "999",
          "latestRatingChangeTimestamp": 1651686487635,
          "additionalData": null
        }
      }
    ],
    "logoUrl": null
  },
  "merchantTransactionType": "Supplier",
  "entityStatus": 0
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-bank-transaction-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[BankTransactionReportModel](#schemabanktransactionreportmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Account Balances

<a id="opIdGet Account Balances"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/banking/{businessId}/balances/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/banking/{businessId}/balances/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/banking/{businessId}/balances/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/banking/{businessId}/balances/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/banking/{businessId}/balances/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/banking/{businessId}/balances/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/banking/{businessId}/balances/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/banking/{businessId}/balances/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/banking/{businessId}/balances/search`

*Search for balances for a connected business*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-account-balances-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[QueryModel](#schemaquerymodel)|false|The account balance model within the search query. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "id": "string",
      "integrationProviderId": "string",
      "accountStatus": "Active",
      "sortCode": "string",
      "accountNumber": "string",
      "currencyCode": "string",
      "balance": 0,
      "updatedOn": "2019-08-24T14:15:22Z",
      "provider": {
        "id": "string",
        "name": "string",
        "provider": "string",
        "friendlyName": "string",
        "integrationType": "Banking"
      },
      "accountDetail": {
        "lastCardDigits": "string",
        "currencyCode": "string",
        "usageType": "PERSONAL",
        "accountType": "CASH_TRADING",
        "sortCode": "string",
        "accountNumber": "string"
      }
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}
```

<h3 id="get-account-balances-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AccountBalanceReportModelEntitySearchResponse](#schemaaccountbalancereportmodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-commerce">Commerce</h1>

A collection of APIs for commerce transactions after a connected business links at least one of its commerce, e-commerce, POS or marketplace accounts

## Get Commerce Transactions

<a id="opIdGet Commerce Transactions"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/commerce/{businessId}/transactions/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/commerce/{businessId}/transactions/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/commerce/{businessId}/transactions/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/commerce/{businessId}/transactions/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/commerce/{businessId}/transactions/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/commerce/{businessId}/transactions/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/commerce/{businessId}/transactions/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/commerce/{businessId}/transactions/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/commerce/{businessId}/transactions/search`

*Get all commerce transactions for a connected business*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-commerce-transactions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[QueryModel](#schemaquerymodel)|false|The commerce transaction model within the search query. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "id": "string",
      "dataSource": "Yapily",
      "timeStamp": 0,
      "trackingId": "string",
      "internalId": "string",
      "source": "string",
      "transactionNumber": "string",
      "refundCode": "string",
      "datetime": "2019-08-24T14:15:22Z",
      "storeLocationId": "string",
      "storeAddress": "string",
      "onlinePurchase": true,
      "subtotal": 0,
      "serviceCharge": 0,
      "total": 0,
      "currencyCode": "string",
      "customerEmail": "string",
      "operatorName": "string",
      "date": "2019-08-24T14:15:22Z",
      "time": "string",
      "till": "string",
      "number": "string",
      "store": "string",
      "description": "string",
      "year": 0,
      "month": 0,
      "day": 0,
      "totalRefund": 0,
      "orderStatus": "string",
      "paymentStatus": "string"
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}
```

<h3 id="get-commerce-transactions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CommerceTransactionReportModelEntitySearchResponse](#schemacommercetransactionreportmodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-webhooks">Webhooks</h1>

You can configure webhook endpoints via the API to be notified about events that happen in your for connected businesses.
Most users configure webhooks from the dashboard, which provides a user interface for registering and testing your webhook endpoints.

## Create Webhook

<a id="opIdCreate Webhook"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/web-hooks/{businessId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/web-hooks/{businessId} HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "object": "string",
  "apiVersion": null,
  "application": null,
  "created": 0,
  "description": "string",
  "enabledEvents": [
    "None"
  ],
  "status": "Enabled",
  "url": "string",
  "secret": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/web-hooks/{businessId}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/web-hooks/{businessId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/web-hooks/{businessId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/web-hooks/{businessId}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/web-hooks/{businessId}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/web-hooks/{businessId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/web-hooks/{businessId}`

*Create a webhook so you can get notified when a new event has occured*

> Body parameter

```json
{
  "id": "string",
  "object": "string",
  "apiVersion": null,
  "application": null,
  "created": 0,
  "description": "string",
  "enabledEvents": [
    "None"
  ],
  "status": "Enabled",
  "url": "string",
  "secret": "string"
}
```

<h3 id="create-webhook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[WebhookModel](#schemawebhookmodel)|false|The body of the webhook to create. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "id": null,
  "entityStatus": 0,
  "object": null,
  "apiVersion": null,
  "application": null,
  "created": 0,
  "description": null,
  "enabledEvents": null,
  "status": "Enabled",
  "url": null,
  "secret": null
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="create-webhook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[WebhookModel](#schemawebhookmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-employees">Employees</h1>

A collection of APIs that allows you to retrieve payroll for employees.

## Get Employees

<a id="opIdGet Employees"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/payroll/{businessId}/employees/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/payroll/{businessId}/employees/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/payroll/{businessId}/employees/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/payroll/{businessId}/employees/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/payroll/{businessId}/employees/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/payroll/{businessId}/employees/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/payroll/{businessId}/employees/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/payroll/{businessId}/employees/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/payroll/{businessId}/employees/search`

*Allows you to search for employees*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-employees-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|none|
|body|body|[QueryModel](#schemaquerymodel)|false|The search model for employees. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "id": "4d0ac9324afe444dad97008f020bc7f7",
      "title": "Mr",
      "firstName": "Derek",
      "lastName": "Longer",
      "dateOfBirthUtc": "1968-10-20T00:00:00",
      "gender": "Male",
      "email": "dlonger@airslip.com",
      "phoneNumber": "07123456789",
      "startDate": 1649026800000,
      "nationalInsuranceNumber": "JL329791A",
      "isOffPayrollWorker": false,
      "address": {
        "firstLine": "One Park Place, 4th Floor",
        "secondLine": "Hatch Street Dublin 2",
        "locality": "Saint Kevin's",
        "administrativeArea": "Dublin",
        "subAdministrativeArea": null,
        "postalCode": "D02 E651",
        "countryCode": "IL"
      },
      "payrollCalendarId": "ff61093f13bf402d991e6e1e00785189",
      "updatedDate": 1651618800000,
      "createdDate": 1649026800000,
      "niCategories": [
        {
          "startDate": 1649026800000,
          "category": "A"
        }
      ],
      "employeeNumber": "A12345678",
      "endDate": null,
      "entityStatus": 0
    }
  ],
  "paging": {
    "totalRecords": 1,
    "recordsPerPage": 10,
    "page": 1,
    "next": null
  }
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-employees-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[EmployeeModelEntitySearchResponse](#schemaemployeemodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Employee

<a id="opIdGet Employee"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/payroll/{businessId}/employees/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/payroll/{businessId}/employees/{id} HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/payroll/{businessId}/employees/{id}`

*Use this method to get an employee*

<h3 id="get-employee-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|The id of the employee|
|businessId|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "title": "string",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirthUtc": "2019-08-24T14:15:22Z",
  "gender": "Female",
  "email": "string",
  "phoneNumber": "string",
  "startDate": 0,
  "nationalInsuranceNumber": "string",
  "isOffPayrollWorker": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "payrollCalendarId": "string",
  "updatedDate": 0,
  "createdDate": 0,
  "niCategories": [
    {
      "startDate": 0,
      "category": "string"
    }
  ],
  "employeeNumber": "string",
  "endDate": 0
}
```

<h3 id="get-employee-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[EmployeeModel](#schemaemployeemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundResponse](#schemanotfoundresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Update Employee

<a id="opIdUpdate Employee"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://localhost:7101/2022.5/payroll/{businessId}/employees/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
PUT http://localhost:7101/2022.5/payroll/{businessId}/employees/{id} HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "title": "string",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirthUtc": "2019-08-24T14:15:22Z",
  "gender": "Female",
  "email": "string",
  "phoneNumber": "string",
  "startDate": 0,
  "nationalInsuranceNumber": "string",
  "isOffPayrollWorker": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "payrollCalendarId": "string",
  "updatedDate": 0,
  "createdDate": 0,
  "niCategories": [
    {
      "startDate": 0,
      "category": "string"
    }
  ],
  "employeeNumber": "string",
  "endDate": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.put 'http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.put('http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://localhost:7101/2022.5/payroll/{businessId}/employees/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /2022.5/payroll/{businessId}/employees/{id}`

*Use this method to update an employee*

> Body parameter

```json
{
  "id": "string",
  "title": "string",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirthUtc": "2019-08-24T14:15:22Z",
  "gender": "Female",
  "email": "string",
  "phoneNumber": "string",
  "startDate": 0,
  "nationalInsuranceNumber": "string",
  "isOffPayrollWorker": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "payrollCalendarId": "string",
  "updatedDate": 0,
  "createdDate": 0,
  "niCategories": [
    {
      "startDate": 0,
      "category": "string"
    }
  ],
  "employeeNumber": "string",
  "endDate": 0
}
```

<h3 id="update-employee-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|The id of the employee to update|
|businessId|path|string|true|none|
|body|body|[EmployeeModel](#schemaemployeemodel)|false|The body of the employee to update|

> Example responses

> 200 Response

```json
{}
```

<h3 id="update-employee-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[Success](#schemasuccess)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundResponse](#schemanotfoundresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create Employee

<a id="opIdCreate Employee"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/payroll/{businessId}/employees \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/payroll/{businessId}/employees HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "title": "string",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirthUtc": "2019-08-24T14:15:22Z",
  "gender": "Female",
  "email": "string",
  "phoneNumber": "string",
  "startDate": 0,
  "nationalInsuranceNumber": "string",
  "isOffPayrollWorker": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "payrollCalendarId": "string",
  "updatedDate": 0,
  "createdDate": 0,
  "niCategories": [
    {
      "startDate": 0,
      "category": "string"
    }
  ],
  "employeeNumber": "string",
  "endDate": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/payroll/{businessId}/employees',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/payroll/{businessId}/employees',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/payroll/{businessId}/employees', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/payroll/{businessId}/employees', array(
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
URL obj = new URL("http://localhost:7101/2022.5/payroll/{businessId}/employees");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/payroll/{businessId}/employees", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/payroll/{businessId}/employees`

*Use this method to create an employee*

> Body parameter

```json
{
  "id": "string",
  "title": "string",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirthUtc": "2019-08-24T14:15:22Z",
  "gender": "Female",
  "email": "string",
  "phoneNumber": "string",
  "startDate": 0,
  "nationalInsuranceNumber": "string",
  "isOffPayrollWorker": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "payrollCalendarId": "string",
  "updatedDate": 0,
  "createdDate": 0,
  "niCategories": [
    {
      "startDate": 0,
      "category": "string"
    }
  ],
  "employeeNumber": "string",
  "endDate": 0
}
```

<h3 id="create-employee-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|none|
|body|body|[EmployeeModel](#schemaemployeemodel)|false|The body of the employee to create|

> Example responses

> 200 Response

```json
{
  "id": "12b14d2970984e359e8bf4dc9af7812b"
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="create-employee-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CreatedModel](#schemacreatedmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-assets">Assets</h1>

The Assets API exposes fixed asset related functions and can be used for a variety of purposes such as creating assets, retrieving asset valuations and visualising asset depreciation.

## Get Assets

<a id="opIdGet Assets"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/assets/{businessId}/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/assets/{businessId}/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/assets/{businessId}/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/assets/{businessId}/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/assets/{businessId}/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/assets/{businessId}/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/assets/{businessId}/search`

*Allows you to retrieve assets*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-assets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[QueryModel](#schemaquerymodel)|false|The search model for assets. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "id": "fce0a735c937486cb6173d83b19dc8cb",
      "assetName": "Computer",
      "assetNumber": "FA-0021",
      "purchaseDate": 1620169200000,
      "purchasePrice": 199999,
      "disposalPrice": 20000,
      "assetStatus": "Draft",
      "accountingBookValue": 199999,
      "bookDepreciationSetting": {
        "depreciationMethod": "DiminishingValue100",
        "averagingMethod": "ActualDays",
        "depreciationRate": 40,
        "depreciationCalculationMethod": "Rate"
      },
      "bookDepreciationDetail": {
        "currentCapitalGain": 0,
        "currentGainLoss": null,
        "depreciationStartDate": 1620169200000,
        "costLimit": 199999,
        "residualValue": 199999,
        "priorAccumulativeDepreciationAmount": 0,
        "currentAccumulativeDepreciationAmount": 0
      },
      "entityStatus": 0
    }
  ],
  "paging": {
    "totalRecords": 1,
    "recordsPerPage": 10,
    "page": 1,
    "next": null
  }
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-assets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AssetModelEntitySearchResponse](#schemaassetmodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Asset

<a id="opIdGet Asset"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/assets/{businessId}/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/assets/{businessId}/{id} HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/assets/{businessId}/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/assets/{businessId}/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/assets/{businessId}/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/assets/{businessId}/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/assets/{businessId}/{id}`

*Use this method to get an asset*

<h3 id="get-asset-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|id|path|string|true|The id of the asset|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}
```

<h3 id="get-asset-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AssetModel](#schemaassetmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundResponse](#schemanotfoundresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Update Asset

<a id="opIdUpdate Asset"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://localhost:7101/2022.5/assets/{businessId}/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
PUT http://localhost:7101/2022.5/assets/{businessId}/{id} HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.put 'http://localhost:7101/2022.5/assets/{businessId}/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.put('http://localhost:7101/2022.5/assets/{businessId}/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','http://localhost:7101/2022.5/assets/{businessId}/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://localhost:7101/2022.5/assets/{businessId}/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /2022.5/assets/{businessId}/{id}`

*Use this method to update assets.*

> Body parameter

```json
{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}
```

<h3 id="update-asset-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|id|path|string|true|The id of the asset to update|
|body|body|[AssetModel](#schemaassetmodel)|false|The body of the asset to update|

> Example responses

> 200 Response

```json
{}
```

<h3 id="update-asset-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[Success](#schemasuccess)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundResponse](#schemanotfoundresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create Asset

<a id="opIdCreate Asset"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/assets/{businessId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/assets/{businessId} HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/assets/{businessId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/assets/{businessId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/assets/{businessId}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/assets/{businessId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/assets/{businessId}`

*Use this method to create draft fixed assets.*

> Body parameter

```json
{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}
```

<h3 id="create-asset-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[AssetModel](#schemaassetmodel)|false|The body of the asset to create|

> Example responses

> 200 Response

```json
{
  "id": "12b14d2970984e359e8bf4dc9af7812b"
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="create-asset-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CreatedModel](#schemacreatedmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-assettypes">AssetTypes</h1>

The Assets API exposes fixed asset related functions and can be used for a variety of purposes such as creating assets, retrieving asset valuations and visualising asset depreciation.

## Get Asset Types

<a id="opIdGet Asset Types"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/assets/{businessId}/types/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/assets/{businessId}/types/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/types/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/assets/{businessId}/types/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/assets/{businessId}/types/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/assets/{businessId}/types/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/types/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/assets/{businessId}/types/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/assets/{businessId}/types/search`

*Allows you to retrieve asset types*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-asset-types-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[QueryModel](#schemaquerymodel)|false|The search model for asset types. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "name": "Laptop ProV1 2022",
      "fixedAssetAccountId": "cb2974f8abce43a89a155c38ac8329cc",
      "depreciationExpenseAccountId": "4b3e3fae74bd4008b6fd50659652af80",
      "accumulatedDepreciationAccountId": "6150fbd3c62c4926934fb548d9c97fb0",
      "bookDepreciationSetting": {
        "depreciationMethod": "DiminishingValue100",
        "averagingMethod": "ActualDays",
        "depreciationRate": 40,
        "depreciationCalculationMethod": "Rate"
      },
      "entityStatus": 0,
      "id": "f65782e4eb3c40ebaf6874056deaafe0"
    }
  ],
  "paging": {
    "totalRecords": 1,
    "recordsPerPage": 10,
    "page": 1,
    "next": null
  }
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-asset-types-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AssetTypeModelEntitySearchResponse](#schemaassettypemodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Asset Type

<a id="opIdGet Asset Type"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/assets/{businessId}/types/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/assets/{businessId}/types/{id} HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/types/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/assets/{businessId}/types/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/assets/{businessId}/types/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/assets/{businessId}/types/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/types/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/assets/{businessId}/types/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/assets/{businessId}/types/{id}`

*Use this method to get an asset type*

<h3 id="get-asset-type-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|id|path|string|true|The id of the employee|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "fixedAssetAccountId": "string",
  "depreciationExpenseAccountId": "string",
  "accumulatedDepreciationAccountId": "string",
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "id": "string"
}
```

<h3 id="get-asset-type-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AssetTypeModel](#schemaassettypemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundResponse](#schemanotfoundresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Update Asset Type

<a id="opIdUpdate Asset Type"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://localhost:7101/2022.5/assets/{businessId}/types/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
PUT http://localhost:7101/2022.5/assets/{businessId}/types/{id} HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/types/{id}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.put 'http://localhost:7101/2022.5/assets/{businessId}/types/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.put('http://localhost:7101/2022.5/assets/{businessId}/types/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','http://localhost:7101/2022.5/assets/{businessId}/types/{id}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/types/{id}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://localhost:7101/2022.5/assets/{businessId}/types/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /2022.5/assets/{businessId}/types/{id}`

*Use this method to update assets*

> Body parameter

```json
{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}
```

<h3 id="update-asset-type-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|id|path|string|true|The id of the asset type to update|
|body|body|[AssetModel](#schemaassetmodel)|false|The body of the asset type to update|

> Example responses

> 200 Response

```json
{
  "id": "12b14d2970984e359e8bf4dc9af7812b"
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="update-asset-type-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CreatedModel](#schemacreatedmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundResponse](#schemanotfoundresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create Asset Type

<a id="opIdCreate Asset Type"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/assets/{businessId}/types \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/assets/{businessId}/types HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/assets/{businessId}/types',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/assets/{businessId}/types',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/assets/{businessId}/types', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/assets/{businessId}/types', array(
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
URL obj = new URL("http://localhost:7101/2022.5/assets/{businessId}/types");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/assets/{businessId}/types", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/assets/{businessId}/types`

*Use this method to create asset types*

> Body parameter

```json
{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}
```

<h3 id="create-asset-type-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[AssetModel](#schemaassetmodel)|false|The body of the asset type to create|

> Example responses

> 200 Response

```json
{
  "id": "12b14d2970984e359e8bf4dc9af7812b"
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="create-asset-type-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CreatedModel](#schemacreatedmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-invoices">Invoices</h1>

Get, search, create and update invoices for a particular business

## Get Invoices

<a id="opIdGet Invoices"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/invoices/{businessId}/search \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/invoices/{businessId}/search HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/invoices/{businessId}/search',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/invoices/{businessId}/search',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/invoices/{businessId}/search', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/invoices/{businessId}/search', array(
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
URL obj = new URL("http://localhost:7101/2022.5/invoices/{businessId}/search");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/invoices/{businessId}/search", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/invoices/{businessId}/search`

*Use this method to retrieve one or many invoices.
When you retrieve multiple invoices, only a summary of the contact is returned and no line details are returned - this is to keep the response more compact.
The line item details will be returned when you retrieve an individual invoice, either by specifying Invoice ID, Invoice Number, querying by Statuses or by using the optional paging parameter (below).
When you retrieve invoices by querying by Statuses, pagination is enforced by default.
Individual invoices (e.g. Invoices/97c2dc5-cc47-4afd-8ec8-74990b8761e9) can also be returned as PDF's see our HTTP GET documentation*

> Body parameter

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}
```

<h3 id="get-invoices-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[QueryModel](#schemaquerymodel)|false|The invoice model within the search query. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "results": [
    {
      "id": "66b84d2970984e359e8bf4dc9af7812e",
      "type": "AccountReceivable",
      "contact": {
        "id": "b37096cde4344931b82c240bd286fc02",
        "type": "Supplier",
        "contactStatus": "Active",
        "companyName": "Microsoft",
        "firstName": "Derek",
        "surname": "Longer",
        "email": "dlonger@company.com",
        "phoneNumber": "07987123456",
        "addresses": null,
        "updatedDate": 1651686487690
      },
      "issuedDate": 1649026800000,
      "dueDate": 1651618800000,
      "status": "Paid",
      "invoiceTaxType": "Exclusive",
      "lineItems": [
        {
          "id": "1cb3955f7c2f4aa8b858b2dcf333754b",
          "itemCode": "A123",
          "accountCode": "AIRSLIP_A123",
          "description": "Microsoft Azure Services",
          "quantity": 1,
          "unitAmount": 140730,
          "taxDetails": [
            {
              "taxRateReference": "20",
              "amount": 28145
            }
          ],
          "lineAmount": 168875,
          "discountDetails": null,
          "trackingCategories": [
            {
              "id": "1f224639bb7047b3a0ca933eae295769",
              "name": "IT Infrastructure",
              "countryCode": "GB"
            }
          ]
        }
      ],
      "subTotal": 140730,
      "totalTax": 28145,
      "total": 168875,
      "createdDate": 1651618800000,
      "updatedDate": 1651618800000,
      "currencyCode": "GBP",
      "invoiceNumber": "E0700GKMNI",
      "bankTransactionId": "5120a037963341e0b5f9de6b8260b7b9",
      "businessId": "ca56467b498c48f3adf3c160ae3e0e56",
      "reference": null,
      "expectedPaymentDate": 1651618800000,
      "plannedPaymentDate": 1651618800000,
      "repeatingInvoiceID": null,
      "cisDeduction": null,
      "payments": [
        {
          "id": "2a23b4b0f1b6485598d323eb65a09f74",
          "paymentType": "StandardPayment",
          "date": 1651618800000,
          "amount": 168875
        }
      ],
      "creditNotes": null,
      "amountDue": 0,
      "amountPaid": 168875,
      "fullyPaidOnDate": 1651618800000,
      "amountCredited": 0
    }
  ],
  "paging": {
    "totalRecords": 1,
    "recordsPerPage": 10,
    "page": 1,
    "next": null
  }
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-invoices-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[InvoiceModelEntitySearchResponse](#schemainvoicemodelentitysearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Create Invoice

<a id="opIdCreate Invoice"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:7101/2022.5/invoices/{businessId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
POST http://localhost:7101/2022.5/invoices/{businessId} HTTP/1.1
Host: localhost:7101
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "id": "string",
  "type": "AccountReceivable",
  "contact": {
    "id": "string",
    "type": "Anonymous",
    "contactStatus": "Active",
    "companyName": "string",
    "firstName": "string",
    "surname": "string",
    "email": "string",
    "phoneNumber": "string",
    "addresses": [
      {
        "firstLine": "string",
        "secondLine": "string",
        "locality": "string",
        "administrativeArea": "string",
        "subAdministrativeArea": "string",
        "postalCode": "string",
        "countryCode": "AF"
      }
    ],
    "updatedDate": 0
  },
  "issuedDate": 0,
  "dueDate": 0,
  "status": "Draft",
  "invoiceTaxType": "Exclusive",
  "lineItems": [
    {
      "id": "string",
      "itemCode": "string",
      "accountCode": "string",
      "description": "string",
      "quantity": 0,
      "unitAmount": 0,
      "taxDetails": [
        {
          "taxRateReference": "string",
          "amount": 0
        }
      ],
      "lineAmount": 0,
      "discountDetails": [
        {
          "rate": "string",
          "amount": 0
        }
      ],
      "trackingCategories": [
        {
          "id": "string",
          "name": "string",
          "countryCode": "AF"
        }
      ]
    }
  ],
  "subTotal": 0,
  "totalTax": 0,
  "total": 0,
  "createdDate": 0,
  "updatedDate": 0,
  "currencyCode": "AED",
  "invoiceNumber": "string",
  "bankTransactionId": "string",
  "businessId": "string",
  "reference": "string",
  "expectedPaymentDate": 0,
  "plannedPaymentDate": 0,
  "repeatingInvoiceID": "string",
  "cisDeduction": "string",
  "payments": [
    {
      "id": "string",
      "paymentType": "StandardPayment",
      "date": 0,
      "amount": 0
    }
  ],
  "creditNotes": [
    {}
  ],
  "amountDue": 0,
  "amountPaid": 0,
  "fullyPaidOnDate": 0,
  "amountCredited": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/invoices/{businessId}',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.post 'http://localhost:7101/2022.5/invoices/{businessId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.post('http://localhost:7101/2022.5/invoices/{businessId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','http://localhost:7101/2022.5/invoices/{businessId}', array(
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
URL obj = new URL("http://localhost:7101/2022.5/invoices/{businessId}");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://localhost:7101/2022.5/invoices/{businessId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /2022.5/invoices/{businessId}`

*Use this method to create or update an invoice*

> Body parameter

```json
{
  "id": "string",
  "type": "AccountReceivable",
  "contact": {
    "id": "string",
    "type": "Anonymous",
    "contactStatus": "Active",
    "companyName": "string",
    "firstName": "string",
    "surname": "string",
    "email": "string",
    "phoneNumber": "string",
    "addresses": [
      {
        "firstLine": "string",
        "secondLine": "string",
        "locality": "string",
        "administrativeArea": "string",
        "subAdministrativeArea": "string",
        "postalCode": "string",
        "countryCode": "AF"
      }
    ],
    "updatedDate": 0
  },
  "issuedDate": 0,
  "dueDate": 0,
  "status": "Draft",
  "invoiceTaxType": "Exclusive",
  "lineItems": [
    {
      "id": "string",
      "itemCode": "string",
      "accountCode": "string",
      "description": "string",
      "quantity": 0,
      "unitAmount": 0,
      "taxDetails": [
        {
          "taxRateReference": "string",
          "amount": 0
        }
      ],
      "lineAmount": 0,
      "discountDetails": [
        {
          "rate": "string",
          "amount": 0
        }
      ],
      "trackingCategories": [
        {
          "id": "string",
          "name": "string",
          "countryCode": "AF"
        }
      ]
    }
  ],
  "subTotal": 0,
  "totalTax": 0,
  "total": 0,
  "createdDate": 0,
  "updatedDate": 0,
  "currencyCode": "AED",
  "invoiceNumber": "string",
  "bankTransactionId": "string",
  "businessId": "string",
  "reference": "string",
  "expectedPaymentDate": 0,
  "plannedPaymentDate": 0,
  "repeatingInvoiceID": "string",
  "cisDeduction": "string",
  "payments": [
    {
      "id": "string",
      "paymentType": "StandardPayment",
      "date": 0,
      "amount": 0
    }
  ],
  "creditNotes": [
    {}
  ],
  "amountDue": 0,
  "amountPaid": 0,
  "fullyPaidOnDate": 0,
  "amountCredited": 0
}
```

<h3 id="create-invoice-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|body|body|[InvoiceModel](#schemainvoicemodel)|false|The body of the invoice to update or create. You can use this to sort or search for any column within the model|

> Example responses

> 200 Response

```json
{
  "id": "12b14d2970984e359e8bf4dc9af7812b"
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="create-invoice-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CreatedModel](#schemacreatedmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

<h1 id="airslip-api-financials">Financials</h1>

## Get Balance Sheet

<a id="opIdGet Balance Sheet"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/financials/{businessId}/balance-sheet \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/financials/{businessId}/balance-sheet HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/financials/{businessId}/balance-sheet',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/financials/{businessId}/balance-sheet',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/financials/{businessId}/balance-sheet', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/financials/{businessId}/balance-sheet', array(
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
URL obj = new URL("http://localhost:7101/2022.5/financials/{businessId}/balance-sheet");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/financials/{businessId}/balance-sheet", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/financials/{businessId}/balance-sheet`

*The balance sheet report is a standard financial report which describes the financial position of an organisation at a point in time.*

<h3 id="get-balance-sheet-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|balanceDate|query|string(date-time)|false|Specifies the date for balance sheet report|
|months|query|integer(int32)|false|The number of months to run the balance sheet for|

> Example responses

> 200 Response

```json
{
  "balanceDate": 0,
  "reports": [
    {
      "balanceSheetType": "Asset",
      "accountTypes": [
        {
          "type": "Inventory",
          "accounts": [
            {
              "code": "630",
              "id": "2cc2ab45be224ef18433cb68ade6fa5b",
              "name": "Inventory",
              "reportingCode": "ASS.CUR.INY",
              "total": 12289
            }
          ],
          "total": 12289
        }
      ],
      "total": 12289
    },
    {
      "balanceSheetType": "Liability",
      "accountTypes": [
        {
          "type": "CurrentLiability",
          "accounts": [
            {
              "code": "610",
              "id": "3be8c266cec44958b0efa16d173d9aae",
              "name": "GST",
              "reportingCode": "LIA.CUR.TAX.GST",
              "total": 1239
            }
          ],
          "total": 1239
        }
      ],
      "total": 1239
    },
    {
      "balanceSheetType": "Equity",
      "accountTypes": [
        {
          "type": "Equity",
          "accounts": [
            {
              "code": "122",
              "id": "45102e99eec34417b2b6b7e4b74dbeb4",
              "name": "Current Year Earnings",
              "reportingCode": "EQU.CUR.YR",
              "total": 1418
            }
          ],
          "total": 1418
        }
      ],
      "total": 1418
    }
  ],
  "entityStatus": 0,
  "id": "12b84d2970984e309e8bf4dc9af7812f"
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-balance-sheet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[BalanceSheetModel](#schemabalancesheetmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Cashflow

<a id="opIdGet Cashflow"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/financials/{businessId}/cashflow \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/financials/{businessId}/cashflow HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/financials/{businessId}/cashflow',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/financials/{businessId}/cashflow',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/financials/{businessId}/cashflow', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/financials/{businessId}/cashflow', array(
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
URL obj = new URL("http://localhost:7101/2022.5/financials/{businessId}/cashflow");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/financials/{businessId}/cashflow", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/financials/{businessId}/cashflow`

*The statement of cash flows - direct method, provides the year to date changes in operating, financing and investing cash
flow activities for an organisation. Cashflow statement is not available in US region at this stage.*

<h3 id="get-cashflow-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|startDate|query|string(date-time)|false|Specifies the start date for cash flow report. If no parameter is provided, the date of 12 months before the end date will be used.|
|endDate|query|string(date-time)|false|Specifies the end date for cash flow report. If no parameter is provided, the current date will be used.|

> Example responses

> 200 Response

```json
{
  "startDate": 0,
  "endDate": 0,
  "cashBalance": {
    "openingCashBalance": 0,
    "closingCashBalance": 0,
    "netCashMovement": 0
  },
  "cashflowActivities": [
    {
      "name": "",
      "total": 0,
      "cashflowTypes": [
        {
          "name": "",
          "total": 0,
          "accounts": [
            {
              "id": "",
              "type": "Cash",
              "classType": "Asset",
              "code": "",
              "name": "",
              "reportingCode": "",
              "total": 0
            }
          ]
        }
      ]
    }
  ],
  "id": null,
  "entityStatus": 0
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-cashflow-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CashflowModel](#schemacashflowmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Profit And Loss

<a id="opIdGet Profit And Loss"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss', array(
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
URL obj = new URL("http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/financials/{businessId}/profit-and-loss", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/financials/{businessId}/profit-and-loss`

*The profit and loss statement is a standard financial report providing detailed year to date income and expense detail for an organisation.*

<h3 id="get-profit-and-loss-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|startDate|query|string(date-time)|false|Specifies the start date for profit and loss report|
|endDate|query|string(date-time)|false|Specifies the end date for profit and loss report|

#### Detailed descriptions

**startDate**: Specifies the start date for profit and loss report
            If no parameter is provided, the date of 12 months before the end date will be used.

**endDate**: Specifies the end date for profit and loss report
            If no parameter is provided, the current date will be used.

> Example responses

> 200 Response

```json
{
  "startDate": 1620169200000,
  "endDate": 1651618800000,
  "netProfitLoss": 0,
  "reports": [
    {
      "profitLossType": "Revenue",
      "accountTypes": [
        {
          "type": "OtherIncome",
          "accounts": [
            {
              "code": "",
              "id": "",
              "name": "null",
              "reportingCode": "",
              "total": 0
            }
          ],
          "total": 0
        }
      ],
      "total": 0
    },
    {
      "profitLossType": "Expense",
      "accountTypes": [
        {
          "type": "DirectCosts",
          "accounts": [
            {
              "code": "",
              "id": "",
              "name": "null",
              "reportingCode": "",
              "total": 0
            }
          ],
          "total": 0
        }
      ],
      "total": 0
    }
  ],
  "entityStatus": 0,
  "id": null
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-profit-and-loss-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ProfitLossModel](#schemaprofitlossmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

## Get Cash Position

<a id="opIdGet Cash Position"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:7101/2022.5/financials/{businessId}/cash-position \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET http://localhost:7101/2022.5/financials/{businessId}/cash-position HTTP/1.1
Host: localhost:7101
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('http://localhost:7101/2022.5/financials/{businessId}/cash-position',
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
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'http://localhost:7101/2022.5/financials/{businessId}/cash-position',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('http://localhost:7101/2022.5/financials/{businessId}/cash-position', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','http://localhost:7101/2022.5/financials/{businessId}/cash-position', array(
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
URL obj = new URL("http://localhost:7101/2022.5/financials/{businessId}/cash-position");
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
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://localhost:7101/2022.5/financials/{businessId}/cash-position", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /2022.5/financials/{businessId}/cash-position`

*Summarizes the total cash position for each account for an org*

<h3 id="get-cash-position-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|businessId|path|string|true|The connected business identifier|
|balanceDate|query|string(date-time)|false|The `balance date` will return transactions based on the accounting date entered by the user. Transactions before the balanceDate will be included.|

> Example responses

> 200 Response

```json
{
  "accountId": "",
  "statementBalance": {
    "value": 0,
    "type": "Debit"
  },
  "statementBalanceDate": 0,
  "bankStatement": {
    "statementLines": {
      "unreconciledAmountPos": 0,
      "unreconciledAmountNeg": 0,
      "unreconciledLines": 0,
      "averagePositiveDaysUnreconciled": 0,
      "averageNegativeDaysUnreconciled": 0,
      "earliestUnreconciledTransaction": 0,
      "latestUnreconciledTransaction": 0,
      "deletedAmount": 0,
      "totalAmount": 0,
      "dataSources": [],
      "earliestReconciledTransaction": 0,
      "latestReconciledTransaction": 0,
      "reconciledPositiveAmount": 0,
      "reconciledNegativeAmount": 0,
      "reconciledLines": 0,
      "totalPositiveAmount": 0,
      "totalNegativeAmount": 0
    },
    "currentStatement": {
      "startDate": 0,
      "endDate": 0,
      "startBalance": 0,
      "endBalance": 0,
      "importedDateTime": 0,
      "importSourceType": "DirectBankFeed"
    }
  },
  "cashAccount": {
    "unreconciledPositionAmount": 0,
    "unreconciledNegativeAmount": 0,
    "startingBalance": 0,
    "accountBalance": 0,
    "balanceCurrency": "AED"
  },
  "entityStatus": 0,
  "id": null
}
```

> 400 Response

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}
```

<h3 id="get-cash-position-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[CashPositionModel](#schemacashpositionmodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
Bearer
</aside>

# Schemas

<h2 id="tocS_AccountBalanceReportModel">AccountBalanceReportModel</h2>
<!-- backwards compatibility -->
<a id="schemaaccountbalancereportmodel"></a>
<a id="schema_AccountBalanceReportModel"></a>
<a id="tocSaccountbalancereportmodel"></a>
<a id="tocsaccountbalancereportmodel"></a>

```json
{
  "id": "string",
  "integrationProviderId": "string",
  "accountStatus": "Active",
  "sortCode": "string",
  "accountNumber": "string",
  "currencyCode": "string",
  "balance": 0,
  "updatedOn": "2019-08-24T14:15:22Z",
  "provider": {
    "id": "string",
    "name": "string",
    "provider": "string",
    "friendlyName": "string",
    "integrationType": "Banking"
  },
  "accountDetail": {
    "lastCardDigits": "string",
    "currencyCode": "string",
    "usageType": "PERSONAL",
    "accountType": "CASH_TRADING",
    "sortCode": "string",
    "accountNumber": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|integrationProviderId|string|true|none|none|
|accountStatus|[BankingAccountStatus](#schemabankingaccountstatus)|true|none|none|
|sortCode|string¦null|false|none|none|
|accountNumber|string¦null|false|none|none|
|currencyCode|string|true|none|none|
|balance|number(double)|true|none|none|
|updatedOn|string(date-time)|true|none|none|
|provider|[IntegrationProviderReportModel](#schemaintegrationproviderreportmodel)|true|none|none|
|accountDetail|[IntegrationAccountDetailReportModel](#schemaintegrationaccountdetailreportmodel)|true|none|none|

<h2 id="tocS_AccountBalanceReportModelEntitySearchResponse">AccountBalanceReportModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemaaccountbalancereportmodelentitysearchresponse"></a>
<a id="schema_AccountBalanceReportModelEntitySearchResponse"></a>
<a id="tocSaccountbalancereportmodelentitysearchresponse"></a>
<a id="tocsaccountbalancereportmodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "id": "string",
      "integrationProviderId": "string",
      "accountStatus": "Active",
      "sortCode": "string",
      "accountNumber": "string",
      "currencyCode": "string",
      "balance": 0,
      "updatedOn": "2019-08-24T14:15:22Z",
      "provider": {
        "id": "string",
        "name": "string",
        "provider": "string",
        "friendlyName": "string",
        "integrationType": "Banking"
      },
      "accountDetail": {
        "lastCardDigits": "string",
        "currencyCode": "string",
        "usageType": "PERSONAL",
        "accountType": "CASH_TRADING",
        "sortCode": "string",
        "accountNumber": "string"
      }
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[AccountBalanceReportModel](#schemaaccountbalancereportmodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_AccountingAccountClassTypes">AccountingAccountClassTypes</h2>
<!-- backwards compatibility -->
<a id="schemaaccountingaccountclasstypes"></a>
<a id="schema_AccountingAccountClassTypes"></a>
<a id="tocSaccountingaccountclasstypes"></a>
<a id="tocsaccountingaccountclasstypes"></a>

```json
"Asset"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Asset|
|*anonymous*|Equity|
|*anonymous*|Expense|
|*anonymous*|Liability|
|*anonymous*|Revenue|

<h2 id="tocS_AccountingAccountTypes">AccountingAccountTypes</h2>
<!-- backwards compatibility -->
<a id="schemaaccountingaccounttypes"></a>
<a id="schema_AccountingAccountTypes"></a>
<a id="tocSaccountingaccounttypes"></a>
<a id="tocsaccountingaccounttypes"></a>

```json
"Cash"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Cash|
|*anonymous*|Current|
|*anonymous*|CurrentLiability|
|*anonymous*|Depreciation|
|*anonymous*|DirectCosts|
|*anonymous*|Equity|
|*anonymous*|Expense|
|*anonymous*|Fixed|
|*anonymous*|Inventory|
|*anonymous*|Liability|
|*anonymous*|NonCurrent|
|*anonymous*|OtherIncome|
|*anonymous*|Overheads|
|*anonymous*|PrePayment|
|*anonymous*|Revenue|
|*anonymous*|Sales|
|*anonymous*|TermLiability|
|*anonymous*|PayAsYouGoLiability|
|*anonymous*|SuperannuationExpense|
|*anonymous*|SuperannuationLiability|
|*anonymous*|WagesExpense|

<h2 id="tocS_Address">Address</h2>
<!-- backwards compatibility -->
<a id="schemaaddress"></a>
<a id="schema_Address"></a>
<a id="tocSaddress"></a>
<a id="tocsaddress"></a>

```json
{
  "firstLine": "string",
  "secondLine": "string",
  "locality": "string",
  "administrativeArea": "string",
  "subAdministrativeArea": "string",
  "postalCode": "string",
  "countryCode": "AF"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|firstLine|string¦null|false|none|none|
|secondLine|string¦null|false|none|none|
|locality|string¦null|false|none|none|
|administrativeArea|string¦null|false|none|none|
|subAdministrativeArea|string¦null|false|none|none|
|postalCode|string¦null|false|none|none|
|countryCode|[Alpha2CountryCodes](#schemaalpha2countrycodes)|true|none|none|

<h2 id="tocS_Alpha2CountryCodes">Alpha2CountryCodes</h2>
<!-- backwards compatibility -->
<a id="schemaalpha2countrycodes"></a>
<a id="schema_Alpha2CountryCodes"></a>
<a id="tocSalpha2countrycodes"></a>
<a id="tocsalpha2countrycodes"></a>

```json
"AF"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|AF|
|*anonymous*|AX|
|*anonymous*|AL|
|*anonymous*|DZ|
|*anonymous*|AS|
|*anonymous*|AD|
|*anonymous*|AO|
|*anonymous*|AI|
|*anonymous*|AQ|
|*anonymous*|AG|
|*anonymous*|AR|
|*anonymous*|AM|
|*anonymous*|AW|
|*anonymous*|AU|
|*anonymous*|AT|
|*anonymous*|AZ|
|*anonymous*|BS|
|*anonymous*|BH|
|*anonymous*|BD|
|*anonymous*|BB|
|*anonymous*|BY|
|*anonymous*|BE|
|*anonymous*|BZ|
|*anonymous*|BJ|
|*anonymous*|BM|
|*anonymous*|BT|
|*anonymous*|BO|
|*anonymous*|BQ|
|*anonymous*|BA|
|*anonymous*|BW|
|*anonymous*|BV|
|*anonymous*|BR|
|*anonymous*|IO|
|*anonymous*|BN|
|*anonymous*|BG|
|*anonymous*|BF|
|*anonymous*|BI|
|*anonymous*|KH|
|*anonymous*|CM|
|*anonymous*|CA|
|*anonymous*|CV|
|*anonymous*|KY|
|*anonymous*|CF|
|*anonymous*|TD|
|*anonymous*|CL|
|*anonymous*|CN|
|*anonymous*|CX|
|*anonymous*|CC|
|*anonymous*|CO|
|*anonymous*|KM|
|*anonymous*|CG|
|*anonymous*|CD|
|*anonymous*|CK|
|*anonymous*|CR|
|*anonymous*|CI|
|*anonymous*|HR|
|*anonymous*|CU|
|*anonymous*|CW|
|*anonymous*|CY|
|*anonymous*|CZ|
|*anonymous*|DK|
|*anonymous*|DJ|
|*anonymous*|DM|
|*anonymous*|DO|
|*anonymous*|EC|
|*anonymous*|EG|
|*anonymous*|SV|
|*anonymous*|GQ|
|*anonymous*|ER|
|*anonymous*|EE|
|*anonymous*|ET|
|*anonymous*|FK|
|*anonymous*|FO|
|*anonymous*|FJ|
|*anonymous*|FI|
|*anonymous*|FR|
|*anonymous*|GF|
|*anonymous*|PF|
|*anonymous*|TF|
|*anonymous*|GA|
|*anonymous*|GM|
|*anonymous*|GE|
|*anonymous*|DE|
|*anonymous*|GH|
|*anonymous*|GI|
|*anonymous*|GR|
|*anonymous*|GL|
|*anonymous*|GD|
|*anonymous*|GP|
|*anonymous*|GU|
|*anonymous*|GT|
|*anonymous*|GG|
|*anonymous*|GN|
|*anonymous*|GW|
|*anonymous*|GY|
|*anonymous*|HT|
|*anonymous*|HM|
|*anonymous*|VA|
|*anonymous*|HN|
|*anonymous*|HK|
|*anonymous*|HU|
|*anonymous*|IS|
|*anonymous*|IN|
|*anonymous*|ID|
|*anonymous*|IR|
|*anonymous*|IQ|
|*anonymous*|IE|
|*anonymous*|IM|
|*anonymous*|IL|
|*anonymous*|IT|
|*anonymous*|JM|
|*anonymous*|JP|
|*anonymous*|JE|
|*anonymous*|JO|
|*anonymous*|KZ|
|*anonymous*|KE|
|*anonymous*|KI|
|*anonymous*|KP|
|*anonymous*|KR|
|*anonymous*|KW|
|*anonymous*|KG|
|*anonymous*|LA|
|*anonymous*|LV|
|*anonymous*|LB|
|*anonymous*|LS|
|*anonymous*|LR|
|*anonymous*|LY|
|*anonymous*|LI|
|*anonymous*|LT|
|*anonymous*|LU|
|*anonymous*|MO|
|*anonymous*|MK|
|*anonymous*|MG|
|*anonymous*|MW|
|*anonymous*|MY|
|*anonymous*|MV|
|*anonymous*|ML|
|*anonymous*|MT|
|*anonymous*|MH|
|*anonymous*|MQ|
|*anonymous*|MR|
|*anonymous*|MU|
|*anonymous*|YT|
|*anonymous*|MX|
|*anonymous*|FM|
|*anonymous*|MD|
|*anonymous*|MC|
|*anonymous*|MN|
|*anonymous*|ME|
|*anonymous*|MS|
|*anonymous*|MA|
|*anonymous*|MZ|
|*anonymous*|MM|
|*anonymous*|NA|
|*anonymous*|NR|
|*anonymous*|NP|
|*anonymous*|NL|
|*anonymous*|NC|
|*anonymous*|NZ|
|*anonymous*|NI|
|*anonymous*|NE|
|*anonymous*|NG|
|*anonymous*|NU|
|*anonymous*|NF|
|*anonymous*|MP|
|*anonymous*|NO|
|*anonymous*|OM|
|*anonymous*|PK|
|*anonymous*|PW|
|*anonymous*|PS|
|*anonymous*|PA|
|*anonymous*|PG|
|*anonymous*|PY|
|*anonymous*|PE|
|*anonymous*|PH|
|*anonymous*|PN|
|*anonymous*|PL|
|*anonymous*|PT|
|*anonymous*|PR|
|*anonymous*|QA|
|*anonymous*|RE|
|*anonymous*|RO|
|*anonymous*|RU|
|*anonymous*|RW|
|*anonymous*|BL|
|*anonymous*|SH|
|*anonymous*|KN|
|*anonymous*|LC|
|*anonymous*|MF|
|*anonymous*|PM|
|*anonymous*|VC|
|*anonymous*|WS|
|*anonymous*|SM|
|*anonymous*|ST|
|*anonymous*|SA|
|*anonymous*|SN|
|*anonymous*|RS|
|*anonymous*|SC|
|*anonymous*|SL|
|*anonymous*|SG|
|*anonymous*|SX|
|*anonymous*|SK|
|*anonymous*|SI|
|*anonymous*|SB|
|*anonymous*|SO|
|*anonymous*|ZA|
|*anonymous*|GS|
|*anonymous*|SS|
|*anonymous*|ES|
|*anonymous*|LK|
|*anonymous*|SD|
|*anonymous*|SR|
|*anonymous*|SJ|
|*anonymous*|SZ|
|*anonymous*|SE|
|*anonymous*|CH|
|*anonymous*|SY|
|*anonymous*|TW|
|*anonymous*|TJ|
|*anonymous*|TZ|
|*anonymous*|TH|
|*anonymous*|TL|
|*anonymous*|TG|
|*anonymous*|TK|
|*anonymous*|TO|
|*anonymous*|TT|
|*anonymous*|TN|
|*anonymous*|TR|
|*anonymous*|TM|
|*anonymous*|TC|
|*anonymous*|TV|
|*anonymous*|UG|
|*anonymous*|UA|
|*anonymous*|AE|
|*anonymous*|GB|
|*anonymous*|US|
|*anonymous*|UM|
|*anonymous*|UY|
|*anonymous*|UZ|
|*anonymous*|VU|
|*anonymous*|VE|
|*anonymous*|VN|
|*anonymous*|VG|
|*anonymous*|VI|
|*anonymous*|WF|
|*anonymous*|EH|
|*anonymous*|YE|
|*anonymous*|ZM|
|*anonymous*|ZW|

<h2 id="tocS_AssetModel">AssetModel</h2>
<!-- backwards compatibility -->
<a id="schemaassetmodel"></a>
<a id="schema_AssetModel"></a>
<a id="tocSassetmodel"></a>
<a id="tocsassetmodel"></a>

```json
{
  "id": "string",
  "assetName": "string",
  "assetNumber": "string",
  "purchaseDate": 0,
  "purchasePrice": 0,
  "disposalPrice": 0,
  "assetStatus": "Draft",
  "accountingBookValue": 0,
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "bookDepreciationDetail": {
    "currentCapitalGain": 0,
    "currentGainLoss": 0,
    "depreciationStartDate": 0,
    "costLimit": 0,
    "residualValue": 0,
    "priorAccumulativeDepreciationAmount": 0,
    "currentAccumulativeDepreciationAmount": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|assetName|string|true|none|none|
|assetNumber|string|true|none|none|
|purchaseDate|integer(int64)|true|none|none|
|purchasePrice|integer(int64)|true|none|none|
|disposalPrice|integer(int64)¦null|false|none|none|
|assetStatus|[AssetStatus](#schemaassetstatus)|true|none|none|
|accountingBookValue|integer(int64)|true|none|none|
|bookDepreciationSetting|[BookDepreciationSetting](#schemabookdepreciationsetting)|true|none|none|
|bookDepreciationDetail|[BookDepreciationDetail](#schemabookdepreciationdetail)|true|none|none|

<h2 id="tocS_AssetModelEntitySearchResponse">AssetModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemaassetmodelentitysearchresponse"></a>
<a id="schema_AssetModelEntitySearchResponse"></a>
<a id="tocSassetmodelentitysearchresponse"></a>
<a id="tocsassetmodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "id": "string",
      "assetName": "string",
      "assetNumber": "string",
      "purchaseDate": 0,
      "purchasePrice": 0,
      "disposalPrice": 0,
      "assetStatus": "Draft",
      "accountingBookValue": 0,
      "bookDepreciationSetting": {
        "depreciationMethod": "NoDepreciation",
        "averagingMethod": "ActualDays",
        "depreciationRate": 0,
        "depreciationCalculationMethod": "Rate"
      },
      "bookDepreciationDetail": {
        "currentCapitalGain": 0,
        "currentGainLoss": 0,
        "depreciationStartDate": 0,
        "costLimit": 0,
        "residualValue": 0,
        "priorAccumulativeDepreciationAmount": 0,
        "currentAccumulativeDepreciationAmount": 0
      }
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[AssetModel](#schemaassetmodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_AssetStatus">AssetStatus</h2>
<!-- backwards compatibility -->
<a id="schemaassetstatus"></a>
<a id="schema_AssetStatus"></a>
<a id="tocSassetstatus"></a>
<a id="tocsassetstatus"></a>

```json
"Draft"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Draft|
|*anonymous*|Registered|
|*anonymous*|Disposed|

<h2 id="tocS_AssetTypeModel">AssetTypeModel</h2>
<!-- backwards compatibility -->
<a id="schemaassettypemodel"></a>
<a id="schema_AssetTypeModel"></a>
<a id="tocSassettypemodel"></a>
<a id="tocsassettypemodel"></a>

```json
{
  "name": "string",
  "fixedAssetAccountId": "string",
  "depreciationExpenseAccountId": "string",
  "accumulatedDepreciationAccountId": "string",
  "bookDepreciationSetting": {
    "depreciationMethod": "NoDepreciation",
    "averagingMethod": "ActualDays",
    "depreciationRate": 0,
    "depreciationCalculationMethod": "Rate"
  },
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|fixedAssetAccountId|string|true|none|none|
|depreciationExpenseAccountId|string|true|none|none|
|accumulatedDepreciationAccountId|string|true|none|none|
|bookDepreciationSetting|[BookDepreciationSetting](#schemabookdepreciationsetting)|true|none|none|
|id|string¦null|false|none|none|

<h2 id="tocS_AssetTypeModelEntitySearchResponse">AssetTypeModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemaassettypemodelentitysearchresponse"></a>
<a id="schema_AssetTypeModelEntitySearchResponse"></a>
<a id="tocSassettypemodelentitysearchresponse"></a>
<a id="tocsassettypemodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "name": "string",
      "fixedAssetAccountId": "string",
      "depreciationExpenseAccountId": "string",
      "accumulatedDepreciationAccountId": "string",
      "bookDepreciationSetting": {
        "depreciationMethod": "NoDepreciation",
        "averagingMethod": "ActualDays",
        "depreciationRate": 0,
        "depreciationCalculationMethod": "Rate"
      },
      "id": "string"
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[AssetTypeModel](#schemaassettypemodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_AveragingMethods">AveragingMethods</h2>
<!-- backwards compatibility -->
<a id="schemaaveragingmethods"></a>
<a id="schema_AveragingMethods"></a>
<a id="tocSaveragingmethods"></a>
<a id="tocsaveragingmethods"></a>

```json
"ActualDays"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|ActualDays|
|*anonymous*|FullMonth|

<h2 id="tocS_BalanceSheetAccount">BalanceSheetAccount</h2>
<!-- backwards compatibility -->
<a id="schemabalancesheetaccount"></a>
<a id="schema_BalanceSheetAccount"></a>
<a id="tocSbalancesheetaccount"></a>
<a id="tocsbalancesheetaccount"></a>

```json
{
  "code": "string",
  "id": "string",
  "name": "string",
  "reportingCode": "string",
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|string|true|none|none|
|id|string|true|none|none|
|name|string|true|none|none|
|reportingCode|string|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_BalanceSheetAccountAccountType">BalanceSheetAccountAccountType</h2>
<!-- backwards compatibility -->
<a id="schemabalancesheetaccountaccounttype"></a>
<a id="schema_BalanceSheetAccountAccountType"></a>
<a id="tocSbalancesheetaccountaccounttype"></a>
<a id="tocsbalancesheetaccountaccounttype"></a>

```json
{
  "type": "Cash",
  "accounts": [
    {
      "code": "string",
      "id": "string",
      "name": "string",
      "reportingCode": "string",
      "total": 0
    }
  ],
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|[AccountingAccountTypes](#schemaaccountingaccounttypes)|true|none|none|
|accounts|[[BalanceSheetAccount](#schemabalancesheetaccount)]|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_BalanceSheetModel">BalanceSheetModel</h2>
<!-- backwards compatibility -->
<a id="schemabalancesheetmodel"></a>
<a id="schema_BalanceSheetModel"></a>
<a id="tocSbalancesheetmodel"></a>
<a id="tocsbalancesheetmodel"></a>

```json
{
  "balanceDate": 0,
  "reports": [
    {
      "balanceSheetType": "Asset",
      "accountTypes": [
        {
          "type": "Cash",
          "accounts": [
            {
              "code": "string",
              "id": "string",
              "name": "string",
              "reportingCode": "string",
              "total": 0
            }
          ],
          "total": 0
        }
      ],
      "total": 0
    }
  ],
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|balanceDate|integer(int64)|true|none|none|
|reports|[[BalanceSheetReport](#schemabalancesheetreport)]|true|none|none|
|id|string¦null|false|none|none|

<h2 id="tocS_BalanceSheetReport">BalanceSheetReport</h2>
<!-- backwards compatibility -->
<a id="schemabalancesheetreport"></a>
<a id="schema_BalanceSheetReport"></a>
<a id="tocSbalancesheetreport"></a>
<a id="tocsbalancesheetreport"></a>

```json
{
  "balanceSheetType": "Asset",
  "accountTypes": [
    {
      "type": "Cash",
      "accounts": [
        {
          "code": "string",
          "id": "string",
          "name": "string",
          "reportingCode": "string",
          "total": 0
        }
      ],
      "total": 0
    }
  ],
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|balanceSheetType|[BalanceSheetTypes](#schemabalancesheettypes)|true|none|none|
|accountTypes|[[BalanceSheetAccountAccountType](#schemabalancesheetaccountaccounttype)]|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_BalanceSheetTypes">BalanceSheetTypes</h2>
<!-- backwards compatibility -->
<a id="schemabalancesheettypes"></a>
<a id="schema_BalanceSheetTypes"></a>
<a id="tocSbalancesheettypes"></a>
<a id="tocsbalancesheettypes"></a>

```json
"Asset"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Asset|
|*anonymous*|Liability|
|*anonymous*|Equity|

<h2 id="tocS_BankStatement">BankStatement</h2>
<!-- backwards compatibility -->
<a id="schemabankstatement"></a>
<a id="schema_BankStatement"></a>
<a id="tocSbankstatement"></a>
<a id="tocsbankstatement"></a>

```json
{
  "statementLines": {
    "unreconciledAmountPos": 0,
    "unreconciledAmountNeg": 0,
    "unreconciledLines": 0,
    "averagePositiveDaysUnreconciled": 0,
    "averageNegativeDaysUnreconciled": 0,
    "earliestUnreconciledTransaction": 0,
    "latestUnreconciledTransaction": 0,
    "deletedAmount": 0,
    "totalAmount": 0,
    "dataSources": [
      {
        "type": "DirectBankFeed",
        "positiveTransactionCount": 0,
        "negativeTransactionCount": 0
      }
    ],
    "earliestReconciledTransaction": 0,
    "latestReconciledTransaction": 0,
    "reconciledPositiveAmount": 0,
    "reconciledNegativeAmount": 0,
    "reconciledLines": 0,
    "totalPositiveAmount": 0,
    "totalNegativeAmount": 0
  },
  "currentStatement": {
    "startDate": 0,
    "endDate": 0,
    "startBalance": 0,
    "endBalance": 0,
    "importedDateTime": 0,
    "importSourceType": "DirectBankFeed"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statementLines|[StatementLines](#schemastatementlines)|true|none|none|
|currentStatement|[CurrentStatement](#schemacurrentstatement)|true|none|none|

<h2 id="tocS_BankTransactionReportModel">BankTransactionReportModel</h2>
<!-- backwards compatibility -->
<a id="schemabanktransactionreportmodel"></a>
<a id="schema_BankTransactionReportModel"></a>
<a id="tocSbanktransactionreportmodel"></a>
<a id="tocsbanktransactionreportmodel"></a>

```json
{
  "id": "string",
  "bankTransactionId": "string",
  "transactionHash": "string",
  "integration": {
    "id": "string",
    "name": "string",
    "accountDetail": {
      "lastCardDigits": "string",
      "currencyCode": "string",
      "usageType": "PERSONAL",
      "accountType": "CASH_TRADING",
      "sortCode": "string",
      "accountNumber": "string"
    },
    "provider": {
      "id": "string",
      "name": "string",
      "provider": "string",
      "friendlyName": "string",
      "integrationType": "Banking"
    }
  },
  "authorisedDate": 0,
  "capturedDate": 0,
  "amount": 0,
  "currencyCode": "string",
  "description": "string",
  "lastCardDigits": "string",
  "isoFamilyCode": "string",
  "proprietaryCode": "string",
  "reference": "string",
  "merchant": {
    "id": "string",
    "legalName": "string",
    "tradingName": "string",
    "companyNumber": "string",
    "taxNumber": "string",
    "category": {
      "name": "Advertising",
      "iso18245MerchantCategoryCode": "string"
    },
    "merchantIdentifierNumber": "string",
    "subsidiaries": [
      "string"
    ],
    "parentCompany": "string",
    "headquartersAddress": {
      "firstLine": "string",
      "secondLine": "string",
      "locality": "string",
      "administrativeArea": "string",
      "subAdministrativeArea": "string",
      "postalCode": "string",
      "countryCode": "AF"
    },
    "contactDetail": {
      "email": "string",
      "contactNumber": "string",
      "websiteUrl": "string"
    },
    "directors": [
      {
        "firstName": "string",
        "surname": "string",
        "nationality": "string",
        "countryOfResidence": "string",
        "hasNegativeInfo": true,
        "signingAuthority": true,
        "address": {
          "firstLine": "string",
          "secondLine": "string",
          "locality": "string",
          "administrativeArea": "string",
          "subAdministrativeArea": "string",
          "postalCode": "string",
          "countryCode": "AF"
        },
        "position": {
          "name": "string",
          "authority": "string",
          "dateAppointedTimestamp": 0,
          "companyName": "string",
          "companyNumber": "string",
          "latestTurnoverFigure": 0,
          "latestTurnoverCurrency": "AED",
          "status": "Current",
          "commonCode": "string",
          "providerCode": "string",
          "creditScore": "string",
          "latestRatingChangeTimestamp": 0,
          "additionalData": null
        }
      }
    ],
    "logoUrl": "string"
  },
  "merchantTransactionType": "Anonymous"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|bankTransactionId|string|true|none|none|
|transactionHash|string¦null|false|none|none|
|integration|[IntegrationReportModel](#schemaintegrationreportmodel)|true|none|none|
|authorisedDate|integer(int64)¦null|false|none|none|
|capturedDate|integer(int64)|true|none|none|
|amount|integer(int64)|true|none|none|
|currencyCode|string¦null|false|none|none|
|description|string|true|none|none|
|lastCardDigits|string¦null|false|none|none|
|isoFamilyCode|string¦null|false|none|none|
|proprietaryCode|string¦null|false|none|none|
|reference|string¦null|false|none|none|
|merchant|[MerchantResponse](#schemamerchantresponse)|true|none|none|
|merchantTransactionType|[BusinessTypes](#schemabusinesstypes)|true|none|none|

<h2 id="tocS_BankTransactionReportModelEntitySearchResponse">BankTransactionReportModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemabanktransactionreportmodelentitysearchresponse"></a>
<a id="schema_BankTransactionReportModelEntitySearchResponse"></a>
<a id="tocSbanktransactionreportmodelentitysearchresponse"></a>
<a id="tocsbanktransactionreportmodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "id": "string",
      "bankTransactionId": "string",
      "transactionHash": "string",
      "integration": {
        "id": "string",
        "name": "string",
        "accountDetail": {
          "lastCardDigits": "string",
          "currencyCode": "string",
          "usageType": "PERSONAL",
          "accountType": "CASH_TRADING",
          "sortCode": "string",
          "accountNumber": "string"
        },
        "provider": {
          "id": "string",
          "name": "string",
          "provider": "string",
          "friendlyName": "string",
          "integrationType": "Banking"
        }
      },
      "authorisedDate": 0,
      "capturedDate": 0,
      "amount": 0,
      "currencyCode": "string",
      "description": "string",
      "lastCardDigits": "string",
      "isoFamilyCode": "string",
      "proprietaryCode": "string",
      "reference": "string",
      "merchant": {
        "id": "string",
        "legalName": "string",
        "tradingName": "string",
        "companyNumber": "string",
        "taxNumber": "string",
        "category": {
          "name": "Advertising",
          "iso18245MerchantCategoryCode": "string"
        },
        "merchantIdentifierNumber": "string",
        "subsidiaries": [
          "string"
        ],
        "parentCompany": "string",
        "headquartersAddress": {
          "firstLine": "string",
          "secondLine": "string",
          "locality": "string",
          "administrativeArea": "string",
          "subAdministrativeArea": "string",
          "postalCode": "string",
          "countryCode": "AF"
        },
        "contactDetail": {
          "email": "string",
          "contactNumber": "string",
          "websiteUrl": "string"
        },
        "directors": [
          {
            "firstName": "string",
            "surname": "string",
            "nationality": "string",
            "countryOfResidence": "string",
            "hasNegativeInfo": true,
            "signingAuthority": true,
            "address": {
              "firstLine": "string",
              "secondLine": "string",
              "locality": "string",
              "administrativeArea": "string",
              "subAdministrativeArea": "string",
              "postalCode": "string",
              "countryCode": "AF"
            },
            "position": {
              "name": "string",
              "authority": "string",
              "dateAppointedTimestamp": 0,
              "companyName": "string",
              "companyNumber": "string",
              "latestTurnoverFigure": 0,
              "latestTurnoverCurrency": "AED",
              "status": "Current",
              "commonCode": "string",
              "providerCode": "string",
              "creditScore": "string",
              "latestRatingChangeTimestamp": 0,
              "additionalData": null
            }
          }
        ],
        "logoUrl": "string"
      },
      "merchantTransactionType": "Anonymous"
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[BankTransactionReportModel](#schemabanktransactionreportmodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_BankingAccountStatus">BankingAccountStatus</h2>
<!-- backwards compatibility -->
<a id="schemabankingaccountstatus"></a>
<a id="schema_BankingAccountStatus"></a>
<a id="tocSbankingaccountstatus"></a>
<a id="tocsbankingaccountstatus"></a>

```json
"Active"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Active|
|*anonymous*|Expired|

<h2 id="tocS_BankingAccountTypes">BankingAccountTypes</h2>
<!-- backwards compatibility -->
<a id="schemabankingaccounttypes"></a>
<a id="schema_BankingAccountTypes"></a>
<a id="tocSbankingaccounttypes"></a>
<a id="tocsbankingaccounttypes"></a>

```json
"CASH_TRADING"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|CASH_TRADING|
|*anonymous*|CASH_INCOME|
|*anonymous*|CASH_PAYMENT|
|*anonymous*|CHARGE_CARD|
|*anonymous*|CHARGES|
|*anonymous*|COMMISSION|
|*anonymous*|CREDIT_CARD|
|*anonymous*|CURRENT|
|*anonymous*|E_MONEY|
|*anonymous*|LIMITED_LIQUIDITY_SAVINGS_ACCOUNT|
|*anonymous*|LOAN|
|*anonymous*|MARGINAL_LENDING|
|*anonymous*|MONEY_MARKET|
|*anonymous*|MORTGAGE|
|*anonymous*|NON_RESIDENT_EXTERNAL|
|*anonymous*|OTHER|
|*anonymous*|OVERDRAFT|
|*anonymous*|OVERNIGHT_DEPOSIT|
|*anonymous*|PREPAID_CARD|
|*anonymous*|SALARY|
|*anonymous*|SAVINGS|
|*anonymous*|SETTLEMENT|
|*anonymous*|TAX|
|*anonymous*|UNKNOWN|

<h2 id="tocS_BankingUsageTypes">BankingUsageTypes</h2>
<!-- backwards compatibility -->
<a id="schemabankingusagetypes"></a>
<a id="schema_BankingUsageTypes"></a>
<a id="tocSbankingusagetypes"></a>
<a id="tocsbankingusagetypes"></a>

```json
"PERSONAL"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|PERSONAL|
|*anonymous*|BUSINESS|
|*anonymous*|OTHER|
|*anonymous*|UNKNOWN|
|*anonymous*|SANDBOX|
|*anonymous*|CORPORATE|

<h2 id="tocS_BookDepreciationDetail">BookDepreciationDetail</h2>
<!-- backwards compatibility -->
<a id="schemabookdepreciationdetail"></a>
<a id="schema_BookDepreciationDetail"></a>
<a id="tocSbookdepreciationdetail"></a>
<a id="tocsbookdepreciationdetail"></a>

```json
{
  "currentCapitalGain": 0,
  "currentGainLoss": 0,
  "depreciationStartDate": 0,
  "costLimit": 0,
  "residualValue": 0,
  "priorAccumulativeDepreciationAmount": 0,
  "currentAccumulativeDepreciationAmount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|currentCapitalGain|integer(int64)¦null|false|none|none|
|currentGainLoss|integer(int64)¦null|false|none|none|
|depreciationStartDate|integer(int64)|true|none|none|
|costLimit|integer(int64)|true|none|none|
|residualValue|integer(int64)|true|none|none|
|priorAccumulativeDepreciationAmount|integer(int64)|true|none|none|
|currentAccumulativeDepreciationAmount|integer(int64)|true|none|none|

<h2 id="tocS_BookDepreciationSetting">BookDepreciationSetting</h2>
<!-- backwards compatibility -->
<a id="schemabookdepreciationsetting"></a>
<a id="schema_BookDepreciationSetting"></a>
<a id="tocSbookdepreciationsetting"></a>
<a id="tocsbookdepreciationsetting"></a>

```json
{
  "depreciationMethod": "NoDepreciation",
  "averagingMethod": "ActualDays",
  "depreciationRate": 0,
  "depreciationCalculationMethod": "Rate"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|depreciationMethod|[DepreciationMethods](#schemadepreciationmethods)|true|none|none|
|averagingMethod|[AveragingMethods](#schemaaveragingmethods)|true|none|none|
|depreciationRate|integer(int64)|true|none|none|
|depreciationCalculationMethod|[DepreciationCalculationMethods](#schemadepreciationcalculationmethods)|true|none|none|

<h2 id="tocS_BusinessTypes">BusinessTypes</h2>
<!-- backwards compatibility -->
<a id="schemabusinesstypes"></a>
<a id="schema_BusinessTypes"></a>
<a id="tocSbusinesstypes"></a>
<a id="tocsbusinesstypes"></a>

```json
"Anonymous"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Anonymous|
|*anonymous*|Customer|
|*anonymous*|Supplier|

<h2 id="tocS_CashAccount">CashAccount</h2>
<!-- backwards compatibility -->
<a id="schemacashaccount"></a>
<a id="schema_CashAccount"></a>
<a id="tocScashaccount"></a>
<a id="tocscashaccount"></a>

```json
{
  "unreconciledPositionAmount": 0,
  "unreconciledNegativeAmount": 0,
  "startingBalance": 0,
  "accountBalance": 0,
  "balanceCurrency": "AED"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unreconciledPositionAmount|integer(int32)|true|none|none|
|unreconciledNegativeAmount|integer(int32)|true|none|none|
|startingBalance|integer(int64)|true|none|none|
|accountBalance|integer(int64)|true|none|none|
|balanceCurrency|[Iso4217CurrencyCodes](#schemaiso4217currencycodes)|true|none|none|

<h2 id="tocS_CashBalance">CashBalance</h2>
<!-- backwards compatibility -->
<a id="schemacashbalance"></a>
<a id="schema_CashBalance"></a>
<a id="tocScashbalance"></a>
<a id="tocscashbalance"></a>

```json
{
  "openingCashBalance": 0,
  "closingCashBalance": 0,
  "netCashMovement": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|openingCashBalance|integer(int64)|true|none|none|
|closingCashBalance|integer(int64)|true|none|none|
|netCashMovement|integer(int64)|true|none|none|

<h2 id="tocS_CashPositionModel">CashPositionModel</h2>
<!-- backwards compatibility -->
<a id="schemacashpositionmodel"></a>
<a id="schema_CashPositionModel"></a>
<a id="tocScashpositionmodel"></a>
<a id="tocscashpositionmodel"></a>

```json
{
  "accountId": "string",
  "statementBalance": {
    "value": 0,
    "type": "Debit"
  },
  "statementBalanceDate": 0,
  "bankStatement": {
    "statementLines": {
      "unreconciledAmountPos": 0,
      "unreconciledAmountNeg": 0,
      "unreconciledLines": 0,
      "averagePositiveDaysUnreconciled": 0,
      "averageNegativeDaysUnreconciled": 0,
      "earliestUnreconciledTransaction": 0,
      "latestUnreconciledTransaction": 0,
      "deletedAmount": 0,
      "totalAmount": 0,
      "dataSources": [
        {
          "type": "DirectBankFeed",
          "positiveTransactionCount": 0,
          "negativeTransactionCount": 0
        }
      ],
      "earliestReconciledTransaction": 0,
      "latestReconciledTransaction": 0,
      "reconciledPositiveAmount": 0,
      "reconciledNegativeAmount": 0,
      "reconciledLines": 0,
      "totalPositiveAmount": 0,
      "totalNegativeAmount": 0
    },
    "currentStatement": {
      "startDate": 0,
      "endDate": 0,
      "startBalance": 0,
      "endBalance": 0,
      "importedDateTime": 0,
      "importSourceType": "DirectBankFeed"
    }
  },
  "cashAccount": {
    "unreconciledPositionAmount": 0,
    "unreconciledNegativeAmount": 0,
    "startingBalance": 0,
    "accountBalance": 0,
    "balanceCurrency": "AED"
  },
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|accountId|string|true|none|none|
|statementBalance|[StatementBalance](#schemastatementbalance)|true|none|none|
|statementBalanceDate|integer(int64)|true|none|none|
|bankStatement|[BankStatement](#schemabankstatement)|true|none|none|
|cashAccount|[CashAccount](#schemacashaccount)|true|none|none|
|id|string¦null|false|none|none|

<h2 id="tocS_CashflowAccount">CashflowAccount</h2>
<!-- backwards compatibility -->
<a id="schemacashflowaccount"></a>
<a id="schema_CashflowAccount"></a>
<a id="tocScashflowaccount"></a>
<a id="tocscashflowaccount"></a>

```json
{
  "id": "string",
  "type": "Cash",
  "classType": "Asset",
  "code": "string",
  "name": "string",
  "reportingCode": "string",
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|[AccountingAccountTypes](#schemaaccountingaccounttypes)|true|none|none|
|classType|[AccountingAccountClassTypes](#schemaaccountingaccountclasstypes)|true|none|none|
|code|string|true|none|none|
|name|string|true|none|none|
|reportingCode|string|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_CashflowActivity">CashflowActivity</h2>
<!-- backwards compatibility -->
<a id="schemacashflowactivity"></a>
<a id="schema_CashflowActivity"></a>
<a id="tocScashflowactivity"></a>
<a id="tocscashflowactivity"></a>

```json
{
  "name": "string",
  "total": 0,
  "cashflowTypes": [
    {
      "name": "string",
      "total": 0,
      "accounts": [
        {
          "id": "string",
          "type": "Cash",
          "classType": "Asset",
          "code": "string",
          "name": "string",
          "reportingCode": "string",
          "total": 0
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|total|integer(int64)|true|none|none|
|cashflowTypes|[[CashflowType](#schemacashflowtype)]|true|none|none|

<h2 id="tocS_CashflowModel">CashflowModel</h2>
<!-- backwards compatibility -->
<a id="schemacashflowmodel"></a>
<a id="schema_CashflowModel"></a>
<a id="tocScashflowmodel"></a>
<a id="tocscashflowmodel"></a>

```json
{
  "startDate": 0,
  "endDate": 0,
  "cashBalance": {
    "openingCashBalance": 0,
    "closingCashBalance": 0,
    "netCashMovement": 0
  },
  "cashflowActivities": [
    {
      "name": "string",
      "total": 0,
      "cashflowTypes": [
        {
          "name": "string",
          "total": 0,
          "accounts": [
            {
              "id": "string",
              "type": "Cash",
              "classType": "Asset",
              "code": "string",
              "name": "string",
              "reportingCode": "string",
              "total": 0
            }
          ]
        }
      ]
    }
  ],
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|startDate|integer(int64)|true|none|none|
|endDate|integer(int64)|true|none|none|
|cashBalance|[CashBalance](#schemacashbalance)|true|none|none|
|cashflowActivities|[[CashflowActivity](#schemacashflowactivity)]|true|none|none|
|id|string¦null|false|none|none|

<h2 id="tocS_CashflowType">CashflowType</h2>
<!-- backwards compatibility -->
<a id="schemacashflowtype"></a>
<a id="schema_CashflowType"></a>
<a id="tocScashflowtype"></a>
<a id="tocscashflowtype"></a>

```json
{
  "name": "string",
  "total": 0,
  "accounts": [
    {
      "id": "string",
      "type": "Cash",
      "classType": "Asset",
      "code": "string",
      "name": "string",
      "reportingCode": "string",
      "total": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|total|integer(int64)|true|none|none|
|accounts|[[CashflowAccount](#schemacashflowaccount)]|true|none|none|

<h2 id="tocS_Categories">Categories</h2>
<!-- backwards compatibility -->
<a id="schemacategories"></a>
<a id="schema_Categories"></a>
<a id="tocScategories"></a>
<a id="tocscategories"></a>

```json
"Advertising"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Advertising|
|*anonymous*|BankFees|
|*anonymous*|ComputerHardware|
|*anonymous*|ComputerSoftware|
|*anonymous*|ContractLabour|
|*anonymous*|Design|
|*anonymous*|EmployeePerks|
|*anonymous*|Entertainment|
|*anonymous*|Fuel|
|*anonymous*|Groceries|
|*anonymous*|Insurance|
|*anonymous*|LegalServices|
|*anonymous*|Mileage|
|*anonymous*|OfficeFurniture|
|*anonymous*|OfficeSupplies|
|*anonymous*|PaymentProcessingFees|
|*anonymous*|PostageAndShipping|
|*anonymous*|ProfessionalServices|
|*anonymous*|Rent|
|*anonymous*|Salaries|
|*anonymous*|ServerInfrastructure|
|*anonymous*|Tax|
|*anonymous*|Training|
|*anonymous*|Travel|
|*anonymous*|Utilities|
|*anonymous*|Vehicle|
|*anonymous*|VehicleMaintenance|

<h2 id="tocS_Categorisation">Categorisation</h2>
<!-- backwards compatibility -->
<a id="schemacategorisation"></a>
<a id="schema_Categorisation"></a>
<a id="tocScategorisation"></a>
<a id="tocscategorisation"></a>

```json
{
  "name": "Advertising",
  "iso18245MerchantCategoryCode": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|[Categories](#schemacategories)|true|none|none|
|iso18245MerchantCategoryCode|string¦null|false|none|none|

<h2 id="tocS_CommerceTransactionReportModel">CommerceTransactionReportModel</h2>
<!-- backwards compatibility -->
<a id="schemacommercetransactionreportmodel"></a>
<a id="schema_CommerceTransactionReportModel"></a>
<a id="tocScommercetransactionreportmodel"></a>
<a id="tocscommercetransactionreportmodel"></a>

```json
{
  "id": "string",
  "dataSource": "Yapily",
  "timeStamp": 0,
  "trackingId": "string",
  "internalId": "string",
  "source": "string",
  "transactionNumber": "string",
  "refundCode": "string",
  "datetime": "2019-08-24T14:15:22Z",
  "storeLocationId": "string",
  "storeAddress": "string",
  "onlinePurchase": true,
  "subtotal": 0,
  "serviceCharge": 0,
  "total": 0,
  "currencyCode": "string",
  "customerEmail": "string",
  "operatorName": "string",
  "date": "2019-08-24T14:15:22Z",
  "time": "string",
  "till": "string",
  "number": "string",
  "store": "string",
  "description": "string",
  "year": 0,
  "month": 0,
  "day": 0,
  "totalRefund": 0,
  "orderStatus": "string",
  "paymentStatus": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|dataSource|[DataSources](#schemadatasources)|true|none|none|
|timeStamp|integer(int64)|true|none|none|
|trackingId|string|true|none|none|
|internalId|string¦null|false|none|none|
|source|string¦null|false|none|none|
|transactionNumber|string¦null|false|none|none|
|refundCode|string¦null|false|none|none|
|datetime|string(date-time)¦null|false|none|none|
|storeLocationId|string¦null|false|none|none|
|storeAddress|string¦null|false|none|none|
|onlinePurchase|boolean¦null|false|none|none|
|subtotal|integer(int64)¦null|false|none|none|
|serviceCharge|integer(int64)¦null|false|none|none|
|total|integer(int64)¦null|false|none|none|
|currencyCode|string¦null|false|none|none|
|customerEmail|string¦null|false|none|none|
|operatorName|string¦null|false|none|none|
|date|string(date-time)¦null|false|none|none|
|time|string¦null|false|none|none|
|till|string¦null|false|none|none|
|number|string¦null|false|none|none|
|store|string¦null|false|none|none|
|description|string¦null|false|none|none|
|year|integer(int32)¦null|false|none|none|
|month|integer(int32)¦null|false|none|none|
|day|integer(int32)¦null|false|none|none|
|totalRefund|integer(int64)¦null|false|none|none|
|orderStatus|string|true|none|none|
|paymentStatus|string|true|none|none|

<h2 id="tocS_CommerceTransactionReportModelEntitySearchResponse">CommerceTransactionReportModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemacommercetransactionreportmodelentitysearchresponse"></a>
<a id="schema_CommerceTransactionReportModelEntitySearchResponse"></a>
<a id="tocScommercetransactionreportmodelentitysearchresponse"></a>
<a id="tocscommercetransactionreportmodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "id": "string",
      "dataSource": "Yapily",
      "timeStamp": 0,
      "trackingId": "string",
      "internalId": "string",
      "source": "string",
      "transactionNumber": "string",
      "refundCode": "string",
      "datetime": "2019-08-24T14:15:22Z",
      "storeLocationId": "string",
      "storeAddress": "string",
      "onlinePurchase": true,
      "subtotal": 0,
      "serviceCharge": 0,
      "total": 0,
      "currencyCode": "string",
      "customerEmail": "string",
      "operatorName": "string",
      "date": "2019-08-24T14:15:22Z",
      "time": "string",
      "till": "string",
      "number": "string",
      "store": "string",
      "description": "string",
      "year": 0,
      "month": 0,
      "day": 0,
      "totalRefund": 0,
      "orderStatus": "string",
      "paymentStatus": "string"
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[CommerceTransactionReportModel](#schemacommercetransactionreportmodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_Contact">Contact</h2>
<!-- backwards compatibility -->
<a id="schemacontact"></a>
<a id="schema_Contact"></a>
<a id="tocScontact"></a>
<a id="tocscontact"></a>

```json
{
  "id": "string",
  "type": "Anonymous",
  "contactStatus": "Active",
  "companyName": "string",
  "firstName": "string",
  "surname": "string",
  "email": "string",
  "phoneNumber": "string",
  "addresses": [
    {
      "firstLine": "string",
      "secondLine": "string",
      "locality": "string",
      "administrativeArea": "string",
      "subAdministrativeArea": "string",
      "postalCode": "string",
      "countryCode": "AF"
    }
  ],
  "updatedDate": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|[BusinessTypes](#schemabusinesstypes)|true|none|none|
|contactStatus|[ContactStatus](#schemacontactstatus)|true|none|none|
|companyName|string¦null|false|none|none|
|firstName|string¦null|false|none|none|
|surname|string¦null|false|none|none|
|email|string¦null|false|none|none|
|phoneNumber|string¦null|false|none|none|
|addresses|[[Address](#schemaaddress)]¦null|false|none|none|
|updatedDate|integer(int64)|true|none|none|

<h2 id="tocS_ContactDetail">ContactDetail</h2>
<!-- backwards compatibility -->
<a id="schemacontactdetail"></a>
<a id="schema_ContactDetail"></a>
<a id="tocScontactdetail"></a>
<a id="tocscontactdetail"></a>

```json
{
  "email": "string",
  "contactNumber": "string",
  "websiteUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string¦null|false|none|none|
|contactNumber|string¦null|false|none|none|
|websiteUrl|string¦null|false|none|none|

<h2 id="tocS_ContactStatus">ContactStatus</h2>
<!-- backwards compatibility -->
<a id="schemacontactstatus"></a>
<a id="schema_ContactStatus"></a>
<a id="tocScontactstatus"></a>
<a id="tocscontactstatus"></a>

```json
"Active"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Active|
|*anonymous*|Archived|
|*anonymous*|GdprRequest|

<h2 id="tocS_CreatedModel">CreatedModel</h2>
<!-- backwards compatibility -->
<a id="schemacreatedmodel"></a>
<a id="schema_CreatedModel"></a>
<a id="tocScreatedmodel"></a>
<a id="tocscreatedmodel"></a>

```json
{
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|

<h2 id="tocS_CreditNote">CreditNote</h2>
<!-- backwards compatibility -->
<a id="schemacreditnote"></a>
<a id="schema_CreditNote"></a>
<a id="tocScreditnote"></a>
<a id="tocscreditnote"></a>

```json
{}

```

### Properties

*None*

<h2 id="tocS_CurrentStatement">CurrentStatement</h2>
<!-- backwards compatibility -->
<a id="schemacurrentstatement"></a>
<a id="schema_CurrentStatement"></a>
<a id="tocScurrentstatement"></a>
<a id="tocscurrentstatement"></a>

```json
{
  "startDate": 0,
  "endDate": 0,
  "startBalance": 0,
  "endBalance": 0,
  "importedDateTime": 0,
  "importSourceType": "DirectBankFeed"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|startDate|integer(int64)|true|none|none|
|endDate|integer(int64)|true|none|none|
|startBalance|integer(int64)|true|none|none|
|endBalance|integer(int64)|true|none|none|
|importedDateTime|integer(int64)|true|none|none|
|importSourceType|[ImportSourceTypes](#schemaimportsourcetypes)|true|none|none|

<h2 id="tocS_DataSource">DataSource</h2>
<!-- backwards compatibility -->
<a id="schemadatasource"></a>
<a id="schema_DataSource"></a>
<a id="tocSdatasource"></a>
<a id="tocsdatasource"></a>

```json
{
  "type": "DirectBankFeed",
  "positiveTransactionCount": 0,
  "negativeTransactionCount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|[ImportSourceTypes](#schemaimportsourcetypes)|true|none|none|
|positiveTransactionCount|integer(int32)|true|none|none|
|negativeTransactionCount|integer(int32)|true|none|none|

<h2 id="tocS_DataSources">DataSources</h2>
<!-- backwards compatibility -->
<a id="schemadatasources"></a>
<a id="schema_DataSources"></a>
<a id="tocSdatasources"></a>
<a id="tocsdatasources"></a>

```json
"Yapily"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Yapily|
|*anonymous*|Api2Cart|
|*anonymous*|SwanRetail|
|*anonymous*|CustomerPortal|
|*anonymous*|Analytics|
|*anonymous*|QrMatching|
|*anonymous*|SmartReceipts|
|*anonymous*|MockData|
|*anonymous*|Unknown|

<h2 id="tocS_DepreciationCalculationMethods">DepreciationCalculationMethods</h2>
<!-- backwards compatibility -->
<a id="schemadepreciationcalculationmethods"></a>
<a id="schema_DepreciationCalculationMethods"></a>
<a id="tocSdepreciationcalculationmethods"></a>
<a id="tocsdepreciationcalculationmethods"></a>

```json
"Rate"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Rate|
|*anonymous*|Life|
|*anonymous*|None|

<h2 id="tocS_DepreciationMethods">DepreciationMethods</h2>
<!-- backwards compatibility -->
<a id="schemadepreciationmethods"></a>
<a id="schema_DepreciationMethods"></a>
<a id="tocSdepreciationmethods"></a>
<a id="tocsdepreciationmethods"></a>

```json
"NoDepreciation"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|NoDepreciation|
|*anonymous*|StraightLine|
|*anonymous*|DiminishingValue100|
|*anonymous*|DiminishingValue150|
|*anonymous*|DiminishingValue200|
|*anonymous*|FullDepreciation|

<h2 id="tocS_DirectorDetail">DirectorDetail</h2>
<!-- backwards compatibility -->
<a id="schemadirectordetail"></a>
<a id="schema_DirectorDetail"></a>
<a id="tocSdirectordetail"></a>
<a id="tocsdirectordetail"></a>

```json
{
  "firstName": "string",
  "surname": "string",
  "nationality": "string",
  "countryOfResidence": "string",
  "hasNegativeInfo": true,
  "signingAuthority": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "position": {
    "name": "string",
    "authority": "string",
    "dateAppointedTimestamp": 0,
    "companyName": "string",
    "companyNumber": "string",
    "latestTurnoverFigure": 0,
    "latestTurnoverCurrency": "AED",
    "status": "Current",
    "commonCode": "string",
    "providerCode": "string",
    "creditScore": "string",
    "latestRatingChangeTimestamp": 0,
    "additionalData": null
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|firstName|string¦null|false|none|none|
|surname|string¦null|false|none|none|
|nationality|string¦null|false|none|none|
|countryOfResidence|string¦null|false|none|none|
|hasNegativeInfo|boolean¦null|false|none|none|
|signingAuthority|boolean¦null|false|none|none|
|address|[Address](#schemaaddress)|true|none|none|
|position|[DirectorPosition](#schemadirectorposition)|true|none|none|

<h2 id="tocS_DirectorPosition">DirectorPosition</h2>
<!-- backwards compatibility -->
<a id="schemadirectorposition"></a>
<a id="schema_DirectorPosition"></a>
<a id="tocSdirectorposition"></a>
<a id="tocsdirectorposition"></a>

```json
{
  "name": "string",
  "authority": "string",
  "dateAppointedTimestamp": 0,
  "companyName": "string",
  "companyNumber": "string",
  "latestTurnoverFigure": 0,
  "latestTurnoverCurrency": "AED",
  "status": "Current",
  "commonCode": "string",
  "providerCode": "string",
  "creditScore": "string",
  "latestRatingChangeTimestamp": 0,
  "additionalData": null
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string¦null|false|none|Name of Job Title|
|authority|string¦null|false|none|none|
|dateAppointedTimestamp|integer(int64)¦null|false|none|none|
|companyName|string¦null|false|none|none|
|companyNumber|string¦null|false|none|none|
|latestTurnoverFigure|integer(int64)¦null|false|none|none|
|latestTurnoverCurrency|[Iso4217CurrencyCodes](#schemaiso4217currencycodes)|true|none|none|
|status|[JobStatus](#schemajobstatus)|true|none|none|
|commonCode|string¦null|false|none|none|
|providerCode|string¦null|false|none|none|
|creditScore|string¦null|false|none|none|
|latestRatingChangeTimestamp|integer(int64)¦null|false|none|none|
|additionalData|any|false|none|none|

<h2 id="tocS_DiscountDetail">DiscountDetail</h2>
<!-- backwards compatibility -->
<a id="schemadiscountdetail"></a>
<a id="schema_DiscountDetail"></a>
<a id="tocSdiscountdetail"></a>
<a id="tocsdiscountdetail"></a>

```json
{
  "rate": "string",
  "amount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|rate|string|true|none|none|
|amount|integer(int64)|true|none|none|

<h2 id="tocS_EmployeeModel">EmployeeModel</h2>
<!-- backwards compatibility -->
<a id="schemaemployeemodel"></a>
<a id="schema_EmployeeModel"></a>
<a id="tocSemployeemodel"></a>
<a id="tocsemployeemodel"></a>

```json
{
  "id": "string",
  "title": "string",
  "firstName": "string",
  "lastName": "string",
  "dateOfBirthUtc": "2019-08-24T14:15:22Z",
  "gender": "Female",
  "email": "string",
  "phoneNumber": "string",
  "startDate": 0,
  "nationalInsuranceNumber": "string",
  "isOffPayrollWorker": true,
  "address": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "payrollCalendarId": "string",
  "updatedDate": 0,
  "createdDate": 0,
  "niCategories": [
    {
      "startDate": 0,
      "category": "string"
    }
  ],
  "employeeNumber": "string",
  "endDate": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|title|string|true|none|none|
|firstName|string|true|none|none|
|lastName|string|true|none|none|
|dateOfBirthUtc|string(date-time)|true|none|none|
|gender|[Genders](#schemagenders)|true|none|none|
|email|string|true|none|none|
|phoneNumber|string|true|none|none|
|startDate|integer(int64)|true|none|none|
|nationalInsuranceNumber|string|true|none|none|
|isOffPayrollWorker|boolean|true|none|none|
|address|[Address](#schemaaddress)|true|none|none|
|payrollCalendarId|string|true|none|none|
|updatedDate|integer(int64)|true|none|none|
|createdDate|integer(int64)|true|none|none|
|niCategories|[[NiCategory](#schemanicategory)]|true|none|none|
|employeeNumber|string|true|none|none|
|endDate|integer(int64)¦null|false|none|none|

<h2 id="tocS_EmployeeModelEntitySearchResponse">EmployeeModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemaemployeemodelentitysearchresponse"></a>
<a id="schema_EmployeeModelEntitySearchResponse"></a>
<a id="tocSemployeemodelentitysearchresponse"></a>
<a id="tocsemployeemodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "id": "string",
      "title": "string",
      "firstName": "string",
      "lastName": "string",
      "dateOfBirthUtc": "2019-08-24T14:15:22Z",
      "gender": "Female",
      "email": "string",
      "phoneNumber": "string",
      "startDate": 0,
      "nationalInsuranceNumber": "string",
      "isOffPayrollWorker": true,
      "address": {
        "firstLine": "string",
        "secondLine": "string",
        "locality": "string",
        "administrativeArea": "string",
        "subAdministrativeArea": "string",
        "postalCode": "string",
        "countryCode": "AF"
      },
      "payrollCalendarId": "string",
      "updatedDate": 0,
      "createdDate": 0,
      "niCategories": [
        {
          "startDate": 0,
          "category": "string"
        }
      ],
      "employeeNumber": "string",
      "endDate": 0
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[EmployeeModel](#schemaemployeemodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_EntitySearchModel">EntitySearchModel</h2>
<!-- backwards compatibility -->
<a id="schemaentitysearchmodel"></a>
<a id="schema_EntitySearchModel"></a>
<a id="tocSentitysearchmodel"></a>
<a id="tocsentitysearchmodel"></a>

```json
{
  "items": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ],
  "linkOperator": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[[SearchFilterModel](#schemasearchfiltermodel)]|true|none|none|
|linkOperator|string|true|none|none|

<h2 id="tocS_EntitySearchPagingModel">EntitySearchPagingModel</h2>
<!-- backwards compatibility -->
<a id="schemaentitysearchpagingmodel"></a>
<a id="schema_EntitySearchPagingModel"></a>
<a id="tocSentitysearchpagingmodel"></a>
<a id="tocsentitysearchpagingmodel"></a>

```json
{
  "totalRecords": 0,
  "recordsPerPage": 0,
  "page": 0,
  "next": {
    "page": 0,
    "recordsPerPage": 0,
    "sort": [
      {
        "field": "string",
        "sort": "Asc"
      }
    ],
    "search": {
      "items": [
        {
          "columnField": "string",
          "value": null,
          "operatorValue": "string"
        }
      ],
      "linkOperator": "string"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|totalRecords|integer(int32)¦null|false|none|none|
|recordsPerPage|integer(int32)¦null|false|none|none|
|page|integer(int32)|true|none|none|
|next|[EntitySearchQueryModel](#schemaentitysearchquerymodel)|true|none|none|

<h2 id="tocS_EntitySearchQueryModel">EntitySearchQueryModel</h2>
<!-- backwards compatibility -->
<a id="schemaentitysearchquerymodel"></a>
<a id="schema_EntitySearchQueryModel"></a>
<a id="tocSentitysearchquerymodel"></a>
<a id="tocsentitysearchquerymodel"></a>

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": [
    {
      "field": "string",
      "sort": "Asc"
    }
  ],
  "search": {
    "items": [
      {
        "columnField": "string",
        "value": null,
        "operatorValue": "string"
      }
    ],
    "linkOperator": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page|integer(int32)|true|none|none|
|recordsPerPage|integer(int32)|true|none|none|
|sort|[[EntitySearchSortModel](#schemaentitysearchsortmodel)]|true|none|none|
|search|[EntitySearchModel](#schemaentitysearchmodel)|true|none|none|

<h2 id="tocS_EntitySearchSortModel">EntitySearchSortModel</h2>
<!-- backwards compatibility -->
<a id="schemaentitysearchsortmodel"></a>
<a id="schema_EntitySearchSortModel"></a>
<a id="tocSentitysearchsortmodel"></a>
<a id="tocsentitysearchsortmodel"></a>

```json
{
  "field": "string",
  "sort": "Asc"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|field|string|true|none|none|
|sort|[SortOrder](#schemasortorder)|true|none|none|

<h2 id="tocS_EntityStatus">EntityStatus</h2>
<!-- backwards compatibility -->
<a id="schemaentitystatus"></a>
<a id="schema_EntityStatus"></a>
<a id="tocSentitystatus"></a>
<a id="tocsentitystatus"></a>

```json
"Active"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Active|
|*anonymous*|Deleted|

<h2 id="tocS_ErrorResponse">ErrorResponse</h2>
<!-- backwards compatibility -->
<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errorCode|string|true|none|none|
|message|string¦null|false|none|none|
|metadata|object|true|none|none|
|» **additionalProperties**|any|false|none|none|
|links|[[Link](#schemalink)]|true|none|none|

<h2 id="tocS_Genders">Genders</h2>
<!-- backwards compatibility -->
<a id="schemagenders"></a>
<a id="schema_Genders"></a>
<a id="tocSgenders"></a>
<a id="tocsgenders"></a>

```json
"Female"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Female|
|*anonymous*|Male|
|*anonymous*|Other|

<h2 id="tocS_ImportSourceTypes">ImportSourceTypes</h2>
<!-- backwards compatibility -->
<a id="schemaimportsourcetypes"></a>
<a id="schema_ImportSourceTypes"></a>
<a id="tocSimportsourcetypes"></a>
<a id="tocsimportsourcetypes"></a>

```json
"DirectBankFeed"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|DirectBankFeed|
|*anonymous*|IndirectBankFeed|
|*anonymous*|FileUpload|
|*anonymous*|Manual|
|*anonymous*|Other|

<h2 id="tocS_IntegrationAccountDetailReportModel">IntegrationAccountDetailReportModel</h2>
<!-- backwards compatibility -->
<a id="schemaintegrationaccountdetailreportmodel"></a>
<a id="schema_IntegrationAccountDetailReportModel"></a>
<a id="tocSintegrationaccountdetailreportmodel"></a>
<a id="tocsintegrationaccountdetailreportmodel"></a>

```json
{
  "lastCardDigits": "string",
  "currencyCode": "string",
  "usageType": "PERSONAL",
  "accountType": "CASH_TRADING",
  "sortCode": "string",
  "accountNumber": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|lastCardDigits|string¦null|false|none|none|
|currencyCode|string|true|none|none|
|usageType|[BankingUsageTypes](#schemabankingusagetypes)|true|none|none|
|accountType|[BankingAccountTypes](#schemabankingaccounttypes)|true|none|none|
|sortCode|string¦null|false|none|none|
|accountNumber|string¦null|false|none|none|

<h2 id="tocS_IntegrationProviderReportModel">IntegrationProviderReportModel</h2>
<!-- backwards compatibility -->
<a id="schemaintegrationproviderreportmodel"></a>
<a id="schema_IntegrationProviderReportModel"></a>
<a id="tocSintegrationproviderreportmodel"></a>
<a id="tocsintegrationproviderreportmodel"></a>

```json
{
  "id": "string",
  "name": "string",
  "provider": "string",
  "friendlyName": "string",
  "integrationType": "Banking"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|
|provider|string|true|none|none|
|friendlyName|string|true|none|none|
|integrationType|[IntegrationType](#schemaintegrationtype)|true|none|none|

<h2 id="tocS_IntegrationReportModel">IntegrationReportModel</h2>
<!-- backwards compatibility -->
<a id="schemaintegrationreportmodel"></a>
<a id="schema_IntegrationReportModel"></a>
<a id="tocSintegrationreportmodel"></a>
<a id="tocsintegrationreportmodel"></a>

```json
{
  "id": "string",
  "name": "string",
  "accountDetail": {
    "lastCardDigits": "string",
    "currencyCode": "string",
    "usageType": "PERSONAL",
    "accountType": "CASH_TRADING",
    "sortCode": "string",
    "accountNumber": "string"
  },
  "provider": {
    "id": "string",
    "name": "string",
    "provider": "string",
    "friendlyName": "string",
    "integrationType": "Banking"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|name|string|true|none|none|
|accountDetail|[IntegrationAccountDetailReportModel](#schemaintegrationaccountdetailreportmodel)|true|none|none|
|provider|[IntegrationProviderReportModel](#schemaintegrationproviderreportmodel)|true|none|none|

<h2 id="tocS_IntegrationType">IntegrationType</h2>
<!-- backwards compatibility -->
<a id="schemaintegrationtype"></a>
<a id="schema_IntegrationType"></a>
<a id="tocSintegrationtype"></a>
<a id="tocsintegrationtype"></a>

```json
"Banking"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Banking|
|*anonymous*|Commerce|
|*anonymous*|Accounting|

<h2 id="tocS_InvoiceModel">InvoiceModel</h2>
<!-- backwards compatibility -->
<a id="schemainvoicemodel"></a>
<a id="schema_InvoiceModel"></a>
<a id="tocSinvoicemodel"></a>
<a id="tocsinvoicemodel"></a>

```json
{
  "id": "string",
  "type": "AccountReceivable",
  "contact": {
    "id": "string",
    "type": "Anonymous",
    "contactStatus": "Active",
    "companyName": "string",
    "firstName": "string",
    "surname": "string",
    "email": "string",
    "phoneNumber": "string",
    "addresses": [
      {
        "firstLine": "string",
        "secondLine": "string",
        "locality": "string",
        "administrativeArea": "string",
        "subAdministrativeArea": "string",
        "postalCode": "string",
        "countryCode": "AF"
      }
    ],
    "updatedDate": 0
  },
  "issuedDate": 0,
  "dueDate": 0,
  "status": "Draft",
  "invoiceTaxType": "Exclusive",
  "lineItems": [
    {
      "id": "string",
      "itemCode": "string",
      "accountCode": "string",
      "description": "string",
      "quantity": 0,
      "unitAmount": 0,
      "taxDetails": [
        {
          "taxRateReference": "string",
          "amount": 0
        }
      ],
      "lineAmount": 0,
      "discountDetails": [
        {
          "rate": "string",
          "amount": 0
        }
      ],
      "trackingCategories": [
        {
          "id": "string",
          "name": "string",
          "countryCode": "AF"
        }
      ]
    }
  ],
  "subTotal": 0,
  "totalTax": 0,
  "total": 0,
  "createdDate": 0,
  "updatedDate": 0,
  "currencyCode": "AED",
  "invoiceNumber": "string",
  "bankTransactionId": "string",
  "businessId": "string",
  "reference": "string",
  "expectedPaymentDate": 0,
  "plannedPaymentDate": 0,
  "repeatingInvoiceID": "string",
  "cisDeduction": "string",
  "payments": [
    {
      "id": "string",
      "paymentType": "StandardPayment",
      "date": 0,
      "amount": 0
    }
  ],
  "creditNotes": [
    {}
  ],
  "amountDue": 0,
  "amountPaid": 0,
  "fullyPaidOnDate": 0,
  "amountCredited": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|type|[InvoiceTypes](#schemainvoicetypes)|true|none|none|
|contact|[Contact](#schemacontact)|true|none|none|
|issuedDate|integer(int64)|true|none|none|
|dueDate|integer(int64)|true|none|none|
|status|[InvoiceStatus](#schemainvoicestatus)|true|none|none|
|invoiceTaxType|[InvoiceTaxTypes](#schemainvoicetaxtypes)|true|none|none|
|lineItems|[[LineItem](#schemalineitem)]|true|none|none|
|subTotal|integer(int64)|true|none|none|
|totalTax|integer(int64)|true|none|none|
|total|integer(int64)|true|none|none|
|createdDate|integer(int64)|true|none|none|
|updatedDate|integer(int64)|true|none|none|
|currencyCode|[Iso4217CurrencyCodes](#schemaiso4217currencycodes)|true|none|none|
|invoiceNumber|string|true|none|none|
|bankTransactionId|string¦null|false|none|none|
|businessId|string¦null|false|none|none|
|reference|string¦null|false|none|none|
|expectedPaymentDate|integer(int64)|true|none|none|
|plannedPaymentDate|integer(int64)|true|none|none|
|repeatingInvoiceID|string¦null|false|none|none|
|cisDeduction|string¦null|false|none|none|
|payments|[[Payment](#schemapayment)]|true|none|none|
|creditNotes|[[CreditNote](#schemacreditnote)]¦null|false|none|none|
|amountDue|integer(int64)|true|none|none|
|amountPaid|integer(int64)|true|none|none|
|fullyPaidOnDate|integer(int64)|true|none|none|
|amountCredited|integer(int64)|true|none|none|

<h2 id="tocS_InvoiceModelEntitySearchResponse">InvoiceModelEntitySearchResponse</h2>
<!-- backwards compatibility -->
<a id="schemainvoicemodelentitysearchresponse"></a>
<a id="schema_InvoiceModelEntitySearchResponse"></a>
<a id="tocSinvoicemodelentitysearchresponse"></a>
<a id="tocsinvoicemodelentitysearchresponse"></a>

```json
{
  "results": [
    {
      "id": "string",
      "type": "AccountReceivable",
      "contact": {
        "id": "string",
        "type": "Anonymous",
        "contactStatus": "Active",
        "companyName": "string",
        "firstName": "string",
        "surname": "string",
        "email": "string",
        "phoneNumber": "string",
        "addresses": [
          {
            "firstLine": "string",
            "secondLine": "string",
            "locality": "string",
            "administrativeArea": "string",
            "subAdministrativeArea": "string",
            "postalCode": "string",
            "countryCode": "AF"
          }
        ],
        "updatedDate": 0
      },
      "issuedDate": 0,
      "dueDate": 0,
      "status": "Draft",
      "invoiceTaxType": "Exclusive",
      "lineItems": [
        {
          "id": "string",
          "itemCode": "string",
          "accountCode": "string",
          "description": "string",
          "quantity": 0,
          "unitAmount": 0,
          "taxDetails": [
            {
              "taxRateReference": "string",
              "amount": 0
            }
          ],
          "lineAmount": 0,
          "discountDetails": [
            {
              "rate": "string",
              "amount": 0
            }
          ],
          "trackingCategories": [
            {
              "id": "string",
              "name": "string",
              "countryCode": "AF"
            }
          ]
        }
      ],
      "subTotal": 0,
      "totalTax": 0,
      "total": 0,
      "createdDate": 0,
      "updatedDate": 0,
      "currencyCode": "AED",
      "invoiceNumber": "string",
      "bankTransactionId": "string",
      "businessId": "string",
      "reference": "string",
      "expectedPaymentDate": 0,
      "plannedPaymentDate": 0,
      "repeatingInvoiceID": "string",
      "cisDeduction": "string",
      "payments": [
        {
          "id": "string",
          "paymentType": "StandardPayment",
          "date": 0,
          "amount": 0
        }
      ],
      "creditNotes": [
        {}
      ],
      "amountDue": 0,
      "amountPaid": 0,
      "fullyPaidOnDate": 0,
      "amountCredited": 0
    }
  ],
  "paging": {
    "totalRecords": 0,
    "recordsPerPage": 0,
    "page": 0,
    "next": {
      "page": 0,
      "recordsPerPage": 0,
      "sort": [
        {
          "field": "string",
          "sort": "Asc"
        }
      ],
      "search": {
        "items": [
          {
            "columnField": "string",
            "value": null,
            "operatorValue": "string"
          }
        ],
        "linkOperator": "string"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|results|[[InvoiceModel](#schemainvoicemodel)]|true|none|none|
|paging|[EntitySearchPagingModel](#schemaentitysearchpagingmodel)|true|none|none|

<h2 id="tocS_InvoiceStatus">InvoiceStatus</h2>
<!-- backwards compatibility -->
<a id="schemainvoicestatus"></a>
<a id="schema_InvoiceStatus"></a>
<a id="tocSinvoicestatus"></a>
<a id="tocsinvoicestatus"></a>

```json
"Draft"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Draft|
|*anonymous*|Submitted|
|*anonymous*|Deleted|
|*anonymous*|Authorised|
|*anonymous*|PartiallyPaid|
|*anonymous*|Paid|
|*anonymous*|Voided|

<h2 id="tocS_InvoiceTaxTypes">InvoiceTaxTypes</h2>
<!-- backwards compatibility -->
<a id="schemainvoicetaxtypes"></a>
<a id="schema_InvoiceTaxTypes"></a>
<a id="tocSinvoicetaxtypes"></a>
<a id="tocsinvoicetaxtypes"></a>

```json
"Exclusive"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Exclusive|
|*anonymous*|Inclusive|
|*anonymous*|NoTax|

<h2 id="tocS_InvoiceTypes">InvoiceTypes</h2>
<!-- backwards compatibility -->
<a id="schemainvoicetypes"></a>
<a id="schema_InvoiceTypes"></a>
<a id="tocSinvoicetypes"></a>
<a id="tocsinvoicetypes"></a>

```json
"AccountReceivable"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|AccountReceivable|
|*anonymous*|AccountPayable|

<h2 id="tocS_Iso4217CurrencyCodes">Iso4217CurrencyCodes</h2>
<!-- backwards compatibility -->
<a id="schemaiso4217currencycodes"></a>
<a id="schema_Iso4217CurrencyCodes"></a>
<a id="tocSiso4217currencycodes"></a>
<a id="tocsiso4217currencycodes"></a>

```json
"AED"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|AED|
|*anonymous*|AFN|
|*anonymous*|ALL|
|*anonymous*|AMD|
|*anonymous*|ANG|
|*anonymous*|AOA|
|*anonymous*|ARS|
|*anonymous*|AUD|
|*anonymous*|AWG|
|*anonymous*|AZN|
|*anonymous*|BAM|
|*anonymous*|BBD|
|*anonymous*|BDT|
|*anonymous*|BGN|
|*anonymous*|BHD|
|*anonymous*|BIF|
|*anonymous*|BMD|
|*anonymous*|BND|
|*anonymous*|BOB|
|*anonymous*|BOV|
|*anonymous*|BRL|
|*anonymous*|BSD|
|*anonymous*|BTN|
|*anonymous*|BWP|
|*anonymous*|BYN|
|*anonymous*|BZD|
|*anonymous*|CAD|
|*anonymous*|CDF|
|*anonymous*|CHE|
|*anonymous*|CHF|
|*anonymous*|CHW|
|*anonymous*|CLF|
|*anonymous*|CLP|
|*anonymous*|CNY|
|*anonymous*|COP|
|*anonymous*|COU|
|*anonymous*|CRC|
|*anonymous*|CUC|
|*anonymous*|CUP|
|*anonymous*|CVE|
|*anonymous*|CZK|
|*anonymous*|DJF|
|*anonymous*|DKK|
|*anonymous*|DOP|
|*anonymous*|DZD|
|*anonymous*|EGP|
|*anonymous*|ERN|
|*anonymous*|ETB|
|*anonymous*|EUR|
|*anonymous*|FJD|
|*anonymous*|FKP|
|*anonymous*|GBP|
|*anonymous*|GEL|
|*anonymous*|GHS|
|*anonymous*|GIP|
|*anonymous*|GMD|
|*anonymous*|GNF|
|*anonymous*|GTQ|
|*anonymous*|GYD|
|*anonymous*|HKD|
|*anonymous*|HNL|
|*anonymous*|HRK|
|*anonymous*|HTG|
|*anonymous*|HUF|
|*anonymous*|IDR|
|*anonymous*|ILS|
|*anonymous*|INR|
|*anonymous*|IQD|
|*anonymous*|IRR|
|*anonymous*|ISK|
|*anonymous*|JMD|
|*anonymous*|JOD|
|*anonymous*|JPY|
|*anonymous*|KES|
|*anonymous*|KGS|
|*anonymous*|KHR|
|*anonymous*|KMF|
|*anonymous*|KPW|
|*anonymous*|KRW|
|*anonymous*|KWD|
|*anonymous*|KYD|
|*anonymous*|KZT|
|*anonymous*|LAK|
|*anonymous*|LBP|
|*anonymous*|LKR|
|*anonymous*|LRD|
|*anonymous*|LSL|
|*anonymous*|LYD|
|*anonymous*|MAD|
|*anonymous*|MDL|
|*anonymous*|MGA|
|*anonymous*|MKD|
|*anonymous*|MMK|
|*anonymous*|MNT|
|*anonymous*|MOP|
|*anonymous*|MRU|
|*anonymous*|MUR|
|*anonymous*|MVR|
|*anonymous*|MWK|
|*anonymous*|MXN|
|*anonymous*|MXV|
|*anonymous*|MYR|
|*anonymous*|MZN|
|*anonymous*|NAD|
|*anonymous*|NGN|
|*anonymous*|NIO|
|*anonymous*|NOK|
|*anonymous*|NPR|
|*anonymous*|NZD|
|*anonymous*|OMR|
|*anonymous*|PAB|
|*anonymous*|PEN|
|*anonymous*|PGK|
|*anonymous*|PHP|
|*anonymous*|PKR|
|*anonymous*|PLN|
|*anonymous*|PYG|
|*anonymous*|QAR|
|*anonymous*|RON|
|*anonymous*|RSD|
|*anonymous*|RUB|
|*anonymous*|RWF|
|*anonymous*|SAR|
|*anonymous*|SBD|
|*anonymous*|SCR|
|*anonymous*|SDG|
|*anonymous*|SEK|
|*anonymous*|SGD|
|*anonymous*|SHP|
|*anonymous*|SLL|
|*anonymous*|SOS|
|*anonymous*|SRD|
|*anonymous*|SSP|
|*anonymous*|STN|
|*anonymous*|SVC|
|*anonymous*|SYP|
|*anonymous*|SZL|
|*anonymous*|THB|
|*anonymous*|TJS|
|*anonymous*|TMT|
|*anonymous*|TND|
|*anonymous*|TOP|
|*anonymous*|TRY|
|*anonymous*|TTD|
|*anonymous*|TWD|
|*anonymous*|TZS|
|*anonymous*|UAH|
|*anonymous*|UGX|
|*anonymous*|USD|
|*anonymous*|USN|
|*anonymous*|UYI|
|*anonymous*|UYU|
|*anonymous*|UYW|
|*anonymous*|UZS|
|*anonymous*|VES|
|*anonymous*|VND|
|*anonymous*|VUV|
|*anonymous*|WST|
|*anonymous*|XAF|
|*anonymous*|XAG|
|*anonymous*|XAU|
|*anonymous*|XBA|
|*anonymous*|XBB|
|*anonymous*|XBC|
|*anonymous*|XBD|
|*anonymous*|XCD|
|*anonymous*|XDR|
|*anonymous*|XOF|
|*anonymous*|XPD|
|*anonymous*|XPF|
|*anonymous*|XPT|
|*anonymous*|XSU|
|*anonymous*|XTS|
|*anonymous*|XUA|
|*anonymous*|XXX|
|*anonymous*|YER|
|*anonymous*|ZAR|
|*anonymous*|ZMW|
|*anonymous*|ZWL|

<h2 id="tocS_JobStatus">JobStatus</h2>
<!-- backwards compatibility -->
<a id="schemajobstatus"></a>
<a id="schema_JobStatus"></a>
<a id="tocSjobstatus"></a>
<a id="tocsjobstatus"></a>

```json
"Current"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Current|
|*anonymous*|Previous|
|*anonymous*|Inactive|

<h2 id="tocS_LineItem">LineItem</h2>
<!-- backwards compatibility -->
<a id="schemalineitem"></a>
<a id="schema_LineItem"></a>
<a id="tocSlineitem"></a>
<a id="tocslineitem"></a>

```json
{
  "id": "string",
  "itemCode": "string",
  "accountCode": "string",
  "description": "string",
  "quantity": 0,
  "unitAmount": 0,
  "taxDetails": [
    {
      "taxRateReference": "string",
      "amount": 0
    }
  ],
  "lineAmount": 0,
  "discountDetails": [
    {
      "rate": "string",
      "amount": 0
    }
  ],
  "trackingCategories": [
    {
      "id": "string",
      "name": "string",
      "countryCode": "AF"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|itemCode|string|true|none|none|
|accountCode|string|true|none|none|
|description|string|true|none|none|
|quantity|integer(int64)|true|none|none|
|unitAmount|integer(int64)|true|none|none|
|taxDetails|[[TaxDetail](#schemataxdetail)]|true|none|none|
|lineAmount|integer(int64)|true|none|none|
|discountDetails|[[DiscountDetail](#schemadiscountdetail)]¦null|false|none|none|
|trackingCategories|[[TrackingCategory](#schematrackingcategory)]|true|none|none|

<h2 id="tocS_Link">Link</h2>
<!-- backwards compatibility -->
<a id="schemalink"></a>
<a id="schema_Link"></a>
<a id="tocSlink"></a>
<a id="tocslink"></a>

```json
{
  "href": "string",
  "rel": "string",
  "method": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|href|string|true|none|none|
|rel|string|true|none|none|
|method|string|true|none|none|

<h2 id="tocS_MerchantResponse">MerchantResponse</h2>
<!-- backwards compatibility -->
<a id="schemamerchantresponse"></a>
<a id="schema_MerchantResponse"></a>
<a id="tocSmerchantresponse"></a>
<a id="tocsmerchantresponse"></a>

```json
{
  "id": "string",
  "legalName": "string",
  "tradingName": "string",
  "companyNumber": "string",
  "taxNumber": "string",
  "category": {
    "name": "Advertising",
    "iso18245MerchantCategoryCode": "string"
  },
  "merchantIdentifierNumber": "string",
  "subsidiaries": [
    "string"
  ],
  "parentCompany": "string",
  "headquartersAddress": {
    "firstLine": "string",
    "secondLine": "string",
    "locality": "string",
    "administrativeArea": "string",
    "subAdministrativeArea": "string",
    "postalCode": "string",
    "countryCode": "AF"
  },
  "contactDetail": {
    "email": "string",
    "contactNumber": "string",
    "websiteUrl": "string"
  },
  "directors": [
    {
      "firstName": "string",
      "surname": "string",
      "nationality": "string",
      "countryOfResidence": "string",
      "hasNegativeInfo": true,
      "signingAuthority": true,
      "address": {
        "firstLine": "string",
        "secondLine": "string",
        "locality": "string",
        "administrativeArea": "string",
        "subAdministrativeArea": "string",
        "postalCode": "string",
        "countryCode": "AF"
      },
      "position": {
        "name": "string",
        "authority": "string",
        "dateAppointedTimestamp": 0,
        "companyName": "string",
        "companyNumber": "string",
        "latestTurnoverFigure": 0,
        "latestTurnoverCurrency": "AED",
        "status": "Current",
        "commonCode": "string",
        "providerCode": "string",
        "creditScore": "string",
        "latestRatingChangeTimestamp": 0,
        "additionalData": null
      }
    }
  ],
  "logoUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|legalName|string¦null|false|none|none|
|tradingName|string¦null|false|none|none|
|companyNumber|string¦null|false|none|none|
|taxNumber|string¦null|false|none|none|
|category|[Categorisation](#schemacategorisation)|true|none|none|
|merchantIdentifierNumber|string¦null|false|none|none|
|subsidiaries|[string]¦null|false|none|none|
|parentCompany|string¦null|false|none|none|
|headquartersAddress|[Address](#schemaaddress)|true|none|none|
|contactDetail|[ContactDetail](#schemacontactdetail)|true|none|none|
|directors|[[DirectorDetail](#schemadirectordetail)]¦null|false|none|none|
|logoUrl|string¦null|false|none|none|

<h2 id="tocS_NiCategory">NiCategory</h2>
<!-- backwards compatibility -->
<a id="schemanicategory"></a>
<a id="schema_NiCategory"></a>
<a id="tocSnicategory"></a>
<a id="tocsnicategory"></a>

```json
{
  "startDate": 0,
  "category": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|startDate|integer(int64)|true|none|none|
|category|string|true|none|none|

<h2 id="tocS_NotFoundResponse">NotFoundResponse</h2>
<!-- backwards compatibility -->
<a id="schemanotfoundresponse"></a>
<a id="schema_NotFoundResponse"></a>
<a id="tocSnotfoundresponse"></a>
<a id="tocsnotfoundresponse"></a>

```json
{
  "errorCode": "string",
  "message": "string",
  "metadata": {
    "property1": null,
    "property2": null
  },
  "links": [
    {
      "href": "string",
      "rel": "string",
      "method": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errorCode|string|true|none|none|
|message|string¦null|false|none|none|
|metadata|object|true|none|none|
|» **additionalProperties**|any|false|none|none|
|links|[[Link](#schemalink)]|true|none|none|

<h2 id="tocS_Payment">Payment</h2>
<!-- backwards compatibility -->
<a id="schemapayment"></a>
<a id="schema_Payment"></a>
<a id="tocSpayment"></a>
<a id="tocspayment"></a>

```json
{
  "id": "string",
  "paymentType": "StandardPayment",
  "date": 0,
  "amount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|paymentType|[PaymentTypes](#schemapaymenttypes)|true|none|none|
|date|integer(int64)|true|none|none|
|amount|integer(int64)|true|none|none|

<h2 id="tocS_PaymentTypes">PaymentTypes</h2>
<!-- backwards compatibility -->
<a id="schemapaymenttypes"></a>
<a id="schema_PaymentTypes"></a>
<a id="tocSpaymenttypes"></a>
<a id="tocspaymenttypes"></a>

```json
"StandardPayment"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|StandardPayment|
|*anonymous*|PrePayment|
|*anonymous*|OverPayment|

<h2 id="tocS_ProfitLossAccount">ProfitLossAccount</h2>
<!-- backwards compatibility -->
<a id="schemaprofitlossaccount"></a>
<a id="schema_ProfitLossAccount"></a>
<a id="tocSprofitlossaccount"></a>
<a id="tocsprofitlossaccount"></a>

```json
{
  "code": "string",
  "id": "string",
  "name": "string",
  "reportingCode": "string",
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|string|true|none|none|
|id|string|true|none|none|
|name|string|true|none|none|
|reportingCode|string|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_ProfitLossAccountAccountType">ProfitLossAccountAccountType</h2>
<!-- backwards compatibility -->
<a id="schemaprofitlossaccountaccounttype"></a>
<a id="schema_ProfitLossAccountAccountType"></a>
<a id="tocSprofitlossaccountaccounttype"></a>
<a id="tocsprofitlossaccountaccounttype"></a>

```json
{
  "type": "Cash",
  "accounts": [
    {
      "code": "string",
      "id": "string",
      "name": "string",
      "reportingCode": "string",
      "total": 0
    }
  ],
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|[AccountingAccountTypes](#schemaaccountingaccounttypes)|true|none|none|
|accounts|[[ProfitLossAccount](#schemaprofitlossaccount)]|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_ProfitLossModel">ProfitLossModel</h2>
<!-- backwards compatibility -->
<a id="schemaprofitlossmodel"></a>
<a id="schema_ProfitLossModel"></a>
<a id="tocSprofitlossmodel"></a>
<a id="tocsprofitlossmodel"></a>

```json
{
  "startDate": 0,
  "endDate": 0,
  "netProfitLoss": 0,
  "reports": [
    {
      "profitLossType": "Revenue",
      "accountTypes": [
        {
          "type": "Cash",
          "accounts": [
            {
              "code": "string",
              "id": "string",
              "name": "string",
              "reportingCode": "string",
              "total": 0
            }
          ],
          "total": 0
        }
      ],
      "total": 0
    }
  ],
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|startDate|integer(int64)|true|none|none|
|endDate|integer(int64)|true|none|none|
|netProfitLoss|integer(int64)|true|none|none|
|reports|[[ProfitLossReport](#schemaprofitlossreport)]|true|none|none|
|id|string¦null|false|none|none|

<h2 id="tocS_ProfitLossReport">ProfitLossReport</h2>
<!-- backwards compatibility -->
<a id="schemaprofitlossreport"></a>
<a id="schema_ProfitLossReport"></a>
<a id="tocSprofitlossreport"></a>
<a id="tocsprofitlossreport"></a>

```json
{
  "profitLossType": "Revenue",
  "accountTypes": [
    {
      "type": "Cash",
      "accounts": [
        {
          "code": "string",
          "id": "string",
          "name": "string",
          "reportingCode": "string",
          "total": 0
        }
      ],
      "total": 0
    }
  ],
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|profitLossType|[ProfitLossTypes](#schemaprofitlosstypes)|true|none|none|
|accountTypes|[[ProfitLossAccountAccountType](#schemaprofitlossaccountaccounttype)]|true|none|none|
|total|integer(int64)|true|none|none|

<h2 id="tocS_ProfitLossTypes">ProfitLossTypes</h2>
<!-- backwards compatibility -->
<a id="schemaprofitlosstypes"></a>
<a id="schema_ProfitLossTypes"></a>
<a id="tocSprofitlosstypes"></a>
<a id="tocsprofitlosstypes"></a>

```json
"Revenue"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Revenue|
|*anonymous*|Expense|

<h2 id="tocS_QueryModel">QueryModel</h2>
<!-- backwards compatibility -->
<a id="schemaquerymodel"></a>
<a id="schema_QueryModel"></a>
<a id="tocSquerymodel"></a>
<a id="tocsquerymodel"></a>

```json
{
  "page": 0,
  "recordsPerPage": 0,
  "sort": {
    "field": "string",
    "sort": "Asc"
  },
  "search": [
    {
      "columnField": "string",
      "value": null,
      "operatorValue": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page|integer(int32)|true|none|none|
|recordsPerPage|integer(int32)|true|none|none|
|sort|[EntitySearchSortModel](#schemaentitysearchsortmodel)|true|none|none|
|search|[[SearchFilterModel](#schemasearchfiltermodel)]|true|none|none|

<h2 id="tocS_SearchFilterModel">SearchFilterModel</h2>
<!-- backwards compatibility -->
<a id="schemasearchfiltermodel"></a>
<a id="schema_SearchFilterModel"></a>
<a id="tocSsearchfiltermodel"></a>
<a id="tocssearchfiltermodel"></a>

```json
{
  "columnField": "string",
  "value": null,
  "operatorValue": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|columnField|string|true|none|none|
|value|any|false|none|none|
|operatorValue|string|true|none|none|

<h2 id="tocS_SortOrder">SortOrder</h2>
<!-- backwards compatibility -->
<a id="schemasortorder"></a>
<a id="schema_SortOrder"></a>
<a id="tocSsortorder"></a>
<a id="tocssortorder"></a>

```json
"Asc"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Asc|
|*anonymous*|Desc|

<h2 id="tocS_StatementBalance">StatementBalance</h2>
<!-- backwards compatibility -->
<a id="schemastatementbalance"></a>
<a id="schema_StatementBalance"></a>
<a id="tocSstatementbalance"></a>
<a id="tocsstatementbalance"></a>

```json
{
  "value": 0,
  "type": "Debit"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|integer(int64)|true|none|none|
|type|[TransactionFlows](#schematransactionflows)|true|none|none|

<h2 id="tocS_StatementLines">StatementLines</h2>
<!-- backwards compatibility -->
<a id="schemastatementlines"></a>
<a id="schema_StatementLines"></a>
<a id="tocSstatementlines"></a>
<a id="tocsstatementlines"></a>

```json
{
  "unreconciledAmountPos": 0,
  "unreconciledAmountNeg": 0,
  "unreconciledLines": 0,
  "averagePositiveDaysUnreconciled": 0,
  "averageNegativeDaysUnreconciled": 0,
  "earliestUnreconciledTransaction": 0,
  "latestUnreconciledTransaction": 0,
  "deletedAmount": 0,
  "totalAmount": 0,
  "dataSources": [
    {
      "type": "DirectBankFeed",
      "positiveTransactionCount": 0,
      "negativeTransactionCount": 0
    }
  ],
  "earliestReconciledTransaction": 0,
  "latestReconciledTransaction": 0,
  "reconciledPositiveAmount": 0,
  "reconciledNegativeAmount": 0,
  "reconciledLines": 0,
  "totalPositiveAmount": 0,
  "totalNegativeAmount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unreconciledAmountPos|integer(int64)|true|none|none|
|unreconciledAmountNeg|integer(int64)|true|none|none|
|unreconciledLines|integer(int32)|true|none|none|
|averagePositiveDaysUnreconciled|number(double)|true|none|none|
|averageNegativeDaysUnreconciled|number(double)|true|none|none|
|earliestUnreconciledTransaction|integer(int64)|true|none|none|
|latestUnreconciledTransaction|integer(int64)|true|none|none|
|deletedAmount|integer(int32)|true|none|none|
|totalAmount|integer(int32)|true|none|none|
|dataSources|[[DataSource](#schemadatasource)]|true|none|none|
|earliestReconciledTransaction|integer(int64)|true|none|none|
|latestReconciledTransaction|integer(int64)|true|none|none|
|reconciledPositiveAmount|integer(int32)|true|none|none|
|reconciledNegativeAmount|integer(int32)|true|none|none|
|reconciledLines|integer(int32)|true|none|none|
|totalPositiveAmount|integer(int32)|true|none|none|
|totalNegativeAmount|integer(int32)|true|none|none|

<h2 id="tocS_Success">Success</h2>
<!-- backwards compatibility -->
<a id="schemasuccess"></a>
<a id="schema_Success"></a>
<a id="tocSsuccess"></a>
<a id="tocssuccess"></a>

```json
{}

```

### Properties

*None*

<h2 id="tocS_TaxDetail">TaxDetail</h2>
<!-- backwards compatibility -->
<a id="schemataxdetail"></a>
<a id="schema_TaxDetail"></a>
<a id="tocStaxdetail"></a>
<a id="tocstaxdetail"></a>

```json
{
  "taxRateReference": "string",
  "amount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|taxRateReference|string|true|none|none|
|amount|integer(int64)|true|none|none|

<h2 id="tocS_TrackingCategory">TrackingCategory</h2>
<!-- backwards compatibility -->
<a id="schematrackingcategory"></a>
<a id="schema_TrackingCategory"></a>
<a id="tocStrackingcategory"></a>
<a id="tocstrackingcategory"></a>

```json
{
  "id": "string",
  "name": "string",
  "countryCode": "AF"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|
|countryCode|[Alpha2CountryCodes](#schemaalpha2countrycodes)|true|none|none|

<h2 id="tocS_TransactionFlows">TransactionFlows</h2>
<!-- backwards compatibility -->
<a id="schematransactionflows"></a>
<a id="schema_TransactionFlows"></a>
<a id="tocStransactionflows"></a>
<a id="tocstransactionflows"></a>

```json
"Debit"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Debit|
|*anonymous*|Credit|

<h2 id="tocS_WebhookEvents">WebhookEvents</h2>
<!-- backwards compatibility -->
<a id="schemawebhookevents"></a>
<a id="schema_WebhookEvents"></a>
<a id="tocSwebhookevents"></a>
<a id="tocswebhookevents"></a>

```json
"None"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|None|
|*anonymous*|InvoiceCreate|
|*anonymous*|InvoiceUpdate|

<h2 id="tocS_WebhookModel">WebhookModel</h2>
<!-- backwards compatibility -->
<a id="schemawebhookmodel"></a>
<a id="schema_WebhookModel"></a>
<a id="tocSwebhookmodel"></a>
<a id="tocswebhookmodel"></a>

```json
{
  "id": "string",
  "object": "string",
  "apiVersion": null,
  "application": null,
  "created": 0,
  "description": "string",
  "enabledEvents": [
    "None"
  ],
  "status": "Enabled",
  "url": "string",
  "secret": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string¦null|false|none|none|
|object|string|true|none|none|
|apiVersion|any|true|none|none|
|application|any|true|none|none|
|created|integer(int64)|true|none|none|
|description|string|true|none|none|
|enabledEvents|[[WebhookEvents](#schemawebhookevents)]|true|none|none|
|status|[WebhookStatus](#schemawebhookstatus)|true|none|none|
|url|string|true|none|The URL of the webhook endpoint.|
|secret|string|true|none|The endpoint’s secret, used to generate webhook signatures. Only returned at creation.|

<h2 id="tocS_WebhookStatus">WebhookStatus</h2>
<!-- backwards compatibility -->
<a id="schemawebhookstatus"></a>
<a id="schema_WebhookStatus"></a>
<a id="tocSwebhookstatus"></a>
<a id="tocswebhookstatus"></a>

```json
"Enabled"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Enabled|
|*anonymous*|Disabled|

