# Coverages

Methods about policies

## Response Object

> Example JSON API response

```json
{
    "" : True
}
```

Methods return a JSON encoded object

Attribute | Get Policy response | Insert Policy response
--------- | ------------------- | ----------------------

## Get Coverages

> Request data example

```json
{
    "cod_ramo": 25,
    "cod_suc": 1000,
    "nro_pol": 123456789
}
```

Request token method.

### HTTP Request
`GET /api/asegurado/?cod_tipo_doc=<cod_tipo_doc>&nro_doc=<nro_doc>`

### Content-type
`application/json`

### body data

Attribute | Type | Required | Description
--------- | ---- | -------- | -----------
cod_ramo | int | True | Branch code
cod_suc | int | True | Branch Office code
nro_pol | long | True | Policy number
