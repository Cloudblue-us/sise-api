# Causes

Methods about causes

## Get Causes

### HTTP Request
`GET api/Siniestro/Causas/<cod_ramo>`

### Content-type
`application/json`

### Response

> Example Causes JSON

```json
[
    {
        "cod_ramo": 25,
        "cod_causa": 25,
        "txt_desc": "Lorem ipsum dolor sit amet, consectetur adipiscing elit"
    }
]
```

Attribute | Type | Description
--------- | ---- | -----------
cod_ramo | int | Branch code
cod_causa | int | Accident Cause code
txt_desc | string | Description
