# Licenses

## List of licenses

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
    "data": [
        {
            "id": "3",
            "type": "subscription",
            "attributes": {
                "devices_number": 6,
                "organization_id": "a69a560e-0df7-4a6c-b0dc-7508181f1822",
                "started_at": "2018-01-01",
                "ended_at": "2018-12-31"
            }
        }
    ],
    "meta": {
        "pagination": {
            "per_page": 25,
            "current_page": 1,
            "total_pages": 1,
            "total_objects": 1
        }
    }
}
```

Allows obtaining all the licenses for the organization that you are pointing and if the user has access to it.

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations/:organization_id/licenses`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identifier of a organization
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the license
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
devices_number | String | Number of devices for that license
organization_id | String | Organization identifier for that license
started_at | String | Date of start of license (ISO8601)
ended_at | String | Date of end of license (ISO8601)

## Create license

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"started_at\": \"2019-01-09T0000\", \"ended_at\": \"2019-01-11T0000\", \"devices_number\": 5 }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "started_at": "2019-01-09T0000", "ended_at": "2019-01-11T0000", "devices_number": 5 }'
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
  "data": "{ \"started_at\": \"2019-01-09T0000\", \"ended_at\": \"2019-01-11T0000\", \"devices_number\": 5 }"
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

Permit create a license for the organization that you are pointing and if the user has access to it.

### HTTP Request

`POST https://api.flameanalytics.com/v2/organizations/:organization_id/licenses`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identifier of an organization you are targeting
devices_number | String | Number of devices for active at license
started_at | String | Date of start of license, need format **ISO8601**
ended_at | String | Date of end of license **ISO8601**


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the license
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
devices_number | String | Number of devices for that license
organization_id | String | Organization identifier for that license
started_at | String | Date of start of license (ISO8601)
ended_at | String | Date of end of license (ISO8601)
