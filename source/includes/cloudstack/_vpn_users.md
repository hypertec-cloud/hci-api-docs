### VPN users

VPN users are the accounts that are allowed to connect to [remote access VPNs](#cloudstack-remote-access-vpns).

#### List VPN users
```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://hypertec.cloud/api/v2/services/compute-on/test_area/vpnusers"
```
> The above command returns a JSON structured like this:

```json
{
    "data": [
        {
            "id": "5de76bf5-9f61-487a-a989-042b52882da4",
            "username": "wilson"
        }
    ],
    "metadata": {
        "recordCount": 1
    }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/vpnusers</code>

List VPN users.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the remote access VPN user
`username`<br/>*string* | The VPN user's username

#### Create a VPN user
```shell
curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://hypertec.cloud/api/v2/services/compute-on/test_area/vpnusers"
```
> Request body example:

```json
{
    {
    "username": "user123",
    "password": "user@1234"
    }
}
```
> The above command returns a JSON structured like this:

```json
{
  "taskId": "3e4d4466-ce4b-404b-ada5-ee5a3fb76f4e",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/vpnusers</code>

Create a VPN user.

Attributes | &nbsp;
---------- | -----
`username`<br/>*string* | The VPN user's username
`password`<br/>*string* | The VPN user's password

#### Retrieve a VPN user
```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://hypertec.cloud/api/v2/services/compute-on/test_area/vpnusers/5de76bf5-9f61-487a-a989-042b52882da4"
```
> The above command returns a JSON structured like this:

```json
{
    "data": {
        "id": "5de76bf5-9f61-487a-a989-042b52882da4",
        "username": "wilson"
    }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/vpnusers/:id</code>

Retrieve a VPN user.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the remote access VPN user
`username`<br/>*string* | The VPN user's username

#### Delete a VPN user
```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://hypertec.cloud/api/v2/services/compute-on/test_area/vpnusers/5de76bf5-9f61-487a-a989-042b52882da4"
```
<code>DELETE /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/vpnusers/:id</code>

Delete an existing remote access VPN user.