# Authentication

All API requests must be authenticated by including your secret key in the header request:

<span style="text-align: center;display: block;">`Authorization: Token token=nugyUyuzq6nqvm_uiesD`</span>

You can obtain your token at the response from the creation of your account session at API. Your API token carry many privileges, so be sure to keep them secret, do not share your token key in publicly accessible areas such client-side code, and so forth.

**_API requests without header authentication token will fail_**

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
 "id": ,
 "email": "support@flameanalytics.com",
 "full_name": "Support",
 "photo_url": "/defaults/user_small.png"
}
```

Create a new session for a register user on the web application.

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
  --url http://pull.flameanalytics.com/api/v1/sessions \
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
