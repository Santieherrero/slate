## Update license

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses/128f4c5a-57a8-40b6-ab8d-120f88b7d0b3")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"started_at\": \"2019-01-09T0000\", \"ended_at\": \"2019-01-25T0000\", \"devices_number\": 30 }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request PUT \
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses/128f4c5a-57a8-40b6-ab8d-120f88b7d0b3 \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "started_at": "2019-01-09T0000", "ended_at": "2019-01-25T0000", "devices_number": 30 }'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/licenses/128f4c5a-57a8-40b6-ab8d-120f88b7d0b3",
  "method": "PUT",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  },
  "data": "{ \"started_at\": \"2019-01-09T0000\", \"ended_at\": \"2019-01-25T0000\", \"devices_number\": 30 }"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
    "data": {
      "id": "128f4c5a-57a8-40b6-ab8d-120f88b7d0b3",
      "type": "subscription",
      "attributes": {
          "devices_number": 30,
          "started_at": "2019-01-09",
          "ended_at": "2019-01-25"
      }
    }
}
```

Permit update a license for the organization that you are pointing and if the user has access to it.

### HTTP Request

`PUT https://api.flameanalytics.com/v2/organizations/:organization_id/licenses/:license_id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identifier of an organization you are targeting
license_id | true | Identifier of an license that you are goin to update
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
