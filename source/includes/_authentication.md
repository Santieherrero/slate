# Authentication

All API requests must be authenticated by including your secret key in the header request:

<span style="text-align: center;display: block;">`Authorization: Token token=ULzr7GuYA6iyo9EyiFrf`</span>

You can obtain your token at the response from the creation of your account session at API. Your API token carry many privileges, so be sure to keep them secret, do not share your token key in publicly accessible areas such client-side code, and so forth.

**_API requests without header authentication token will fail_**

## Create a session

```ruby
require 'uri'
require 'net/http'

url = URI("https://pull.flameanalytics.com/api/v1/sessions")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request.body = "{\"user\": \"support@flameanalytics.com\",\"password\": \"apipassword\"}"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://pull.flameanalytics.com/api/v1/sessions \
  --header 'Accept-Encoding: application/json' \
  --header 'Content-Type: application/json' \
  --data '{"user": "support@flameanalytics.com","password": "apipassword"}'
```

```javascript
var settings = {
  "url": "https://pull.flameanalytics.com/api/v1/sessions",
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
 "auth_token": "ULzr7GuYA6iyo9EyiFrf",
 "id": ,
 "email": "support@flameanalytics.com"
}
```

Create a new session for a register user on the web application.

### HTTP Request

`POST https://pull.flameanalytics.com/api/v1/sessions`

### Parameters

Parameter | Required | Description
--------- | ------- | -----------
user | true | Login name of the registered user in the application.
password | true | Password of the registered user in the application.


### Response

Parameter | Type | Description
--------- | ------- | -----------
auth_token | string | Authenticate token for the user 
id | integer | Unique id of the user
email | string | Email of the registered user in the application.

  
## Delete a session

```ruby
require 'uri'
require 'net/http'

url = URI("http://pull.flameanalytics.dev:4003/api/v1/sessions")

http = Net::HTTP.new(url.host, url.port)
request = Net::HTTP::Delete.new(url)

request["Authorization"] = 'Token token=ULzr7GuYA6iyo9EyiFrf'

response = http.request(request)
puts response.read_body
```

```shell
> curl --request DELETE \
  --url http://pull.flameanalytics.dev:4003/api/v1/sessions \
  --header 'Authorization: Token token=ULzr7GuYA6iyo9EyiFrf' \
```

```javascript
var settings = {
  "url": "https://pull.flameanalytics.com/api/v1/sessions",
  "method": "DELETE",
  "headers": {
    "Authorization": "Token token=ULzr7GuYA6iyo9EyiFrf", 
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

Permanently deletes the authentication token of the user, i.e., the user wants to end the interaction with the API and the authentication token is invalidated.

### HTTP Request

`DELETE https://pull.flameanalytics.com/api/v1/sessions`

### Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Authenticate token of the user
