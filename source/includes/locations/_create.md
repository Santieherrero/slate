
## Create locations

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/places")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"name\": \"Madrid Test API\",\"address\": \"Calle Mayor, Madrid\",\"timezone\": \"Europe/Madrid\",\"async_weather\": false }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/places \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "name": "Madrid Test API","address": "Calle Mayor, Madrid","timezone": "Europe/Madrid","async_weather": false }'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/places",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  },
  "data": "{ \"name\": \"Madrid Test API\",\"address\": \"Calle Mayor, Madrid\",\"timezone\": \"Europe/Madrid\",\"async_weather\": false }"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "7f029d8b-fbf1-4b93-95f8-476e8b7de2a2",
        "type": "place",
        "attributes": {
            "name": "Madrid Test API",
            "address": "Calle Mayor, Madrid",
            "timezone": "Europe/Madrid",
            "rebound_time": 1,
            "admin_or_manager": false,
            "async_weather": false
        }
    }
}
```

Permit create a place for the organization that you are pointing and the user has access to it.

### HTTP Request

`POST https://api.flameanalytics.com/v2/organizations/:organization_id/places`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identifier of an organization you are targeting
name | true | Name for the place
address | false | Address for that place, **if you need the weather forecast, it's necesary**
timezone | false | Timezone for that place, you need insert with TZ DB format
async_weather | false | Boolean to indicate if you want the weather forecast


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a place
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
name | String | Name of the place
address | String | Address for that place
timezone | String | Timezone for that place
async_weather | Boolean | Boolean to indicate if have the weather forecast
