# Authentication

All API requests must be authenticated by including your secret key in the header request

<h4 style="margin-top: 20px;margin-bottom: 2px;font-size: 14px;">API key</h4>
<span style="text-align: center;display: block;">`Authorization: ApiKey c42aaacd-45b2-4f76-8574-ce36981cf488`</span>

<h4 style="margin-top: 20px;margin-bottom: 2px;font-size: 14px;">Token session</h4>
<span style="text-align: center;display: block;">`Authorization: Token token=nugyUyuzq6nqvm_uiesD`</span>

These tokens carry many privileges, so be sure to keep them secret, do not share your token key in publicly accessible areas such client-side code, and so forth.

**_API requests without header authentication token will fail_**

## API Key

Each organization can add a API Key, it is only necessary to enable and add this integration at the web application for your organization.

When it's enabled this integration, you can generate all tokens that you need for your team, with the ability to select the locations and permissions for that token

**_You don't need to create a session with this token, you can call all methods that the token has permission_**

```ruby
require 'uri'
require 'net/http'

url = URI('https://api.flameanalytics.com/v2/...')

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'ApiKey c42aaacd-45b2-4f76-8574-ce36981cf488'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://api.flameanalytics.com/v2/... \
  --header 'Accept-Encoding: application/json' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: ApiKey c42aaacd-45b2-4f76-8574-ce36981cf488' \
```

```javascript
var settings = {
  "url": "https://api.flameanalytics.com/v2/...",
  "method": "GET",
  "headers": {
    "Accept-Encoding": "application/json",
    "Content-Type": "application/json"
    "Authorization": "ApiKey c42aaacd-45b2-4f76-8574-ce36981cf488"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

## Create a session

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/sessions")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request.body = "{\"user\": \"support@flameanalytics.com\",\"password\": \"apipassword\"}"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/sessions \
  --header 'Accept-Encoding: application/json' \
  --header 'Content-Type: application/json' \
  --data '{"user": "support@flameanalytics.com","password": "apipassword"}'
```

```javascript
var settings = {
  "url": "https://api.flameanalytics.com/v2/sessions",
  "method": "POST",
  "headers": {
    "Accept-Encoding": "application/json",
    "Content-Type": "application/json"
  },
  "data": "{\"user\": \"support@flameanalytics.com\",\"password\": \"apipassword\"}"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response example

```json
{
 "auth_token": "nugyUyuzq6nqvm_uiesD",
 "id": "",
 "email": "support@flameanalytics.com",
 "full_name": "Support",
 "photo_url": "/defaults/user_small.png"
}
```

Creates a new session for a register user on the web application.<br/>
You can obtain your token at the response from the creation of your account session at API.

### HTTP Request

`POST https://api.flameanalytics.com/v2/sessions`

### Parameters

Parameter | Required | Description
--------- | ------- | -----------
user | true | Login name of the registered user in the application.
password | true | Password of the registered user in the application.


### Response

Parameter | Type | Description
--------- | ------- | -----------
auth_token | String | Authenticate token for the user
id | Integer | Unique id of the user
email | String | Email of the registered user in the application.
full_name | String | Full name of the registered user.


## Delete a session

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/sessions")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Delete.new(url)

request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
> curl --request DELETE \
  --url https://api.flameanalytics.com/v2/sessions \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
```

```javascript
var settings = {
  "url": "https://api.flameanalytics.com/v2/sessions",
  "method": "DELETE",
  "headers": {
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

Permanently deletes the authentication token of the user, i.e., the user wants to end the interaction with the API and the authentication token is invalidated.

### HTTP Request

`DELETE https://api.flameanalytics.com/v2/sessions`

### Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Authenticate token of the user
