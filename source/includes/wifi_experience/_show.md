## Show wifi experience

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/guest_wifi/wifi_experience/5ahnm3ab05-6400-4ade-8484-3911cb3709ca")

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
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/guest_wifi/wifi_experience/5ahnm3ab05-6400-4ade-8484-3911cb3709ca \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/guest_wifi/wifi_experience/5ahnm3ab05-6400-4ade-8484-3911cb3709ca",
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
    "data": {
          "id": "5ahnm3ab05-6400-4ade-8484-3911cb3709ca",
          "type": "wifi_experience",
          "attributes": {
              "name": "WiFi - Cosmetic one",
              "actual_language": "es",
              "primary_language": "spanish",
              "locales": [
                  "es"
              ],
              "connection_modes": [],
              "autologin": false,
              "external_portal_access": true,
              "provider": "meraki",
              "provider_redirect_url": "cwp.flameanalytics.com/5ahnm3ab05-6400-4ade-8484-3911cb3709ca/ok",
              "access_url": "https://cwp.flameanalytics.com/5ahnm3ab05-6400-4ade-8484-3911cb3709ca",
              "access_url_landing": "https://cwp.flameanalytics.com/5ahnm3ab05-6400-4ade-8484-3911cb3709ca/ok",
              "updated_at": "2019-11-20T09:19:33.304Z"
          }
        },
    },
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

Allows obtaining a guest wifi experience which the user can access.

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations/:organization_id/guest_wifi/wifi_experience/:id`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | String | Identification of an organization
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a wifi experience
type | String | Type of the retrieve object
attributes | Object | Attributes for that experience
name | String | Name of the retrieve object
actual_lenguage | String | Actual language of experience
primary_language | String | Primary language that load for default
autologin | Boolean |  If it's true, the user reload at login experience if it's logged
external_portal_access | Boolean | If it's true the user recieve a email to login at portal (RGPD)
locales | Array | List of lenguages avaliable for that experience
connection_modes | Array | List of social connections avaliable for that experience
provider | String | Provider of the retieve experience
provide_redirect_url | String | Url that the device goes at login success
access_url | String | Login url for experince
access_url_landing | String | Landing url for experience
update_at | Date | **ISO 8601**, date of last visit