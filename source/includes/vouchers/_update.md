## Update voucher

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/guest_wifi/vouchers/92187a40-5bc7-485d-ba61-65a59585c6f7")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"id\": \"example2@example.com\", \"active\": \"2019-06-16\"}"

response = http.request(request)
puts response.read_body
```

```shell
curl --request PUT \
  --url https://api.flameanalytics.com/v2/guest_wifi/vouchers/92187a40-5bc7-485d-ba61-65a59585c6f7 \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "id": "example2@example.com", "active": "2019-06-16"}'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/guest_wifi/vouchers/92187a40-5bc7-485d-ba61-65a59585c6f7",
  "method": "PUT",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{ \"id\": \"example2@example.com\", \"active\": \"2019-06-16\"}"
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
          "id": "92181a40-5bc7-485d-ba61-65a59585c6f7",
          "type": "voucher",
          "attributes": {
            "id": "example2@example.com",
            "active": "2019-06-16"
        },
        "relationships": {
            "wifi_experience": {
                "data": {
                    "id": "7d613ab05-6400-4ade-8484-3911cb3709ca",
                    "type": "wifi_experience"
                }
            }
        }
      },
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

Allows to update a voucher that can be used to login at the wifi experiences

### HTTP Request

`GET https://api.flameanalytics.com/v2/guest_wifi/vouchers/:id`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | String | Identification id of an organization
id | String | Identification id for wifi experience object
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a voucher
type | String | Type of the retrieve object
attributes | Object | Attributes for voucher
id | String | Value for identification of the voucher
active | Date | **ISO 8601**, date of last visit
