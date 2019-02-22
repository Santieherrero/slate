## Delete organizations

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Delete.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request DELETE \
  --url https://api.flameanalytics.com/v2/organizations \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872",
  "method": "DELETE",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  }
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

Permit delete a organization if the user have permissions.

### HTTP Request

`DELETE https://api.flameanalytics.com/v2/organizations/ab61a560e-0df7-4y7c-b0dc-757108181f1872`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | Indicate the id organization


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an organization
type | String | Type of the retrieve object
attributes | Object | Attributes of that organization
name | String | Name of the organization
active_modules | Array | Array with the names of active modules that have the organization