---
title: API v1 HTTP 
category: API
order: 2
---

HTTP API version 1
-----------
The L10n API allows developers to work with message bundles via HTTP protocol.

Base URL
--------
````html
https://l10n.ws/api/v1
````

Request and response formats
--------
The L10n API uses HTTP GET requests with URL parameters and JSON responses. Every string passed from the API is UTF-8 encoded.

Authorization
--------
Authorized requests to the API should use an Access-Token header with the value <TOKEN>, where <TOKEN> is an access token.

Error handling
--------
Errors are returned using standard HTTP error code syntax. Any additional info is included as JSON in the body of the response.

Standard API errors
--------

|Code |	Description|
|-----|:-----------|
|400  |	Bad input parameter. Error message should indicate which one and why.|
|401  |	Bad or expired token. This can happen if the access token is expired or if the access token has been revoked by L10n or the user.|
|405  |	Request method not expected.|
|429  | Your app is making too many requests for the given user or team and is being rate limited. Your app should wait for the number of seconds specified in the "Retry-After" response header before trying again.|
|5xx  |	An error occurred on the L10n servers.|

Path
====

## /m
#### Description
Returns all messages.

#### URL Structure

```html
https://l10n.ws/api/v1/m
```

#### Example
```html
https://l10n.ws/api/v1/m?b=12345&v=1.0.0&l[]=en_US&l[]=de_DE
```

#### Parameters

| Name | Required/Optional | Type | Description |
|-----|:----|:----|:------------|
|b   | required | String | Bundle key |
|v   | required | String | Version name |
|l[] | optional | Array | Locales array |

#### Returns
```json
{
  "defaultLocale": "en_US",
  "supportedLocales": "en_US",
  "content": [
    {
      "locale": "en_US",
      "messages": [
        {
          "key": "foo",
          "value": "bar"
        },
        {
          "key": "biz",
          "value": "baz"
        }
      ]
    }
  ]
}
```
#### Response

A JSON-encoded dictionary including ```defaultLocale``` field and ```content```. Content is a array of all locales with messages in selected bundle.
