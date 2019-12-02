## List vouchers

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/guest_wifi/wifi_experience/5ahnm3ab05-6400-4ade-8484-3911cb3709ca/vouchers")

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
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/guest_wifi/wifi_experience/5ahnm3ab05-6400-4ade-8484-3911cb3709ca/vouchers \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/guest_wifi/wifi_experience/5ahnm3ab05-6400-4ade-8484-3911cb3709ca/vouchers",
  "method": "GET",
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
    "data":  [
      {
          "id": "92181a40-5bc7-485d-ba61-65a59585c6f7",
          "type": "voucher",
          "attributes": {
              "id": "example-1@example.es",
              "active": "2019-11-15"
          },
          "relationships": {}
      },
      {
          "id": "2a8e089b-9f62-475a-bd92-109760162fd0",
          "type": "voucher",
          "attributes": {
              "id": "example-2@example.es",
              "active": "2019-11-15"
          },
          "relationships": {}
      },
      {
          "id": "335b27a3-ab94-48b0-b361-b49012f6de75",
          "type": "voucher",
          "attributes": {
              "id": "example-3@example.es",
              "active": "2019-11-20"
          },
          "relationships": {}
      },
      {
          "id": "6760da65-dcc4-40f5-8969-29e1d660c59d",
          "type": "voucher",
          "attributes": {
              "id": "example-4@example.es",
              "active": "2019-11-20"
          },
          "relationships": {}
      }
    ],
    "meta": {
        "pagination": {
            "per_page": 25,
            "current_page": 1,
            "total_pages": 1,
            "total_objects": 2
        }
    }
}
```

Allows obtaining a list of vouchers that can be used to login at the wifi experiences

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations/:organization_id/guest_wifi/wifi_experience/:id/vouchers`

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
