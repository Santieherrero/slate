## Create organizations

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"name\": \"API TEST\"}"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/organizations \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "name": "API TEST"}'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{ \"name\": \"API TEST\"}"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response example:

```json
{
  "data":
    {
      "id": "b61a560e-0df7-4y7c-b0dc-757108181f1872",
      "type": "organization",
      "attributes": {
          "name": "API TEST",
          "active_modules": [
              "affluence",
              "presence",
              "dashboard",
              "places"
          ]
      }
    }
}
```
Permits create an organization if the user have permissions.

### HTTP Request

`POST https://api.flameanalytics.com/v2/organizations`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | Indicates the organization name


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an organization
type | String | Type of the retrieve object
attributes | Object | Attributes of that organization
name | String | Name of the organization
active_modules | Array | Array with the names of active modules that have the organization
