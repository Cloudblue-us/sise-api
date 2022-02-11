# Causes

Methods about causes

## Response Object

> Example JSON API response

```json
{
    "" : true
}
```

Methods return a JSON encoded object

Attribute | Get Policy response | Insert Policy response
--------- | ------------------- | ----------------------

## Get Causes

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
cod_ramo | int | true | Branch code
cod_suc | int | true | Branch Office code
nro_pol | long | true | Policy number
