# Authentication

The connection with SISE y done via authentication token (Oauth2). It has to be renewed before the expiration time is reached.

The API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <access_token>`

<aside class="notice">
You must replace <code>access_token</code> with your personal API key.
</aside>

## Response Object

> Example JSON API response

```json
{
    "access_token" : "nVPU0rtD5fFjzJz9Nezzal9RhqhVauGX5j2bYRS6dkAErBkQJnpHR5JzIG_BjI1QY-lphu7OS0Z3auwMJg9LcA3uNF_wYMkn5KdAuWcVHg9eJV45Ul9mV9T4tcaLDd3DlRmFsTy70ps4NmHVeNoR1PvOQLY-imFiX600eJPQCQ8bDFsxwyt5K9iW-T8_c6_GiJnuH1hxdxesK3u_-QbPPdnJZl7qJ4ko7JUD6g6EnWpLDnHQr1-LGIJiZEJEBms0vfN1ygm6P-IIeHYMSpkQGpQvSuwwhImO8-WqgV-TGoJGaOYU8zO8zSd1Y4Vp_y7XXAWk0zeXy9ZeJRWrzM1sL6xM0c83YNJldL6yFb__Bju86JOkBGM7l6XxW0jPueRR",
    "token_type" : "bearer",
    "expires_in" : 599,
    "refresh_token" : "bb240d997e3f47ab9cb89b6e726af0f6",
    "as:client_id" : "ngAuthApp",
    "userName" : "SISTRANDO",
    ".refresh" : true,
    ".issued" : "Thu, 19 Mar 2015 04:57:42 GMT",
    ".expires" :"Thu, 19 Mar 2015 05:07:42 GMT"
}
```

Methods return a JSON encoded object

Attribute | Description
--------- | -----------
access_token | Authentication Token. Must be used on all API requests
token_type | Bearer
expires_in | Time of token expiration in seconds
refresh_token | Token used on the renew method
as:client_id | Token client id
userName | Token user name
.refresh | If true the Token is renewable using oAuth2
.issued | `datetime` of token 
.expires | `datetime` of token expiration. The token expires after 10 minutes

## Request token

> Body data example

```json
UserName=AppUsrInterno&Password=Usr@App|1t3rn0&client_id=AppInterna&client_secret=%2FUlg9u9VVF0H4C5eEPMxaby17ykwUGvkn%2BfxGGhSIFY%3D&grant_type=password
```

Request token method.

### HTTP Request
`POST /api/Account/Token`

### Content-type
`application/x-www-form-urlencoded charset=utf-8`

### body data

Attribute | Type | Description
--------- | ---- | -----------
UserName | String | Username issued by Mundial
password | String | Password issued by Mundial
grant_type | String | `password`
client_id | String | Client Id issued by SISE
client_secret | String | Hash issued by SISE


## Renew token

> Body data example

```json
grant_type=refresh_token&refresh_token=0eedcc126f9e412ab59a19353a5146b7&client_id=ngAuthApp&client_secret=5YV7M1r981yoGhELyB84aC%2BKiYksxZf1OY3
```

Once the Token has been issued, it can be renewed just sending the <code>refresh_token</code>. Username and password is not needed.

### HTTP Request
`POST /api/Account/Token`

### Content-type
`application/x-www-form-urlencoded charset=utf-8`

### body data

Attribute | Type | Description
--------- | ---- | -----------
grant_type | String | `password`
refresh_token | String | Token issued 
client_id | String | Client Id issued by SISE
client_secret | String | Hash issued by SISE