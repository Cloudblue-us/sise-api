# Coverages

Consult Coverages of a requested branch

## Get Coverages



Request token method.

### HTTP Request
`GET GET /api/comunes/Ramo/<cod_ramo>/Coberturas`

### Content-type
`application/json`

### Response

> Example Coverages JSON

```json
[
    {
        "cod_ramo": 25,
        "cod_subramo": 25,
        "cod_tarifa": 25,
        "sn_acum_suma_aseg": 0,
        "sn_rc": "0",
        "sn_habilitado": "0",
        "txt_desc": "Lorem ipsum dolor sit amet, consectetur adipiscing elit"
    }
]
```

Attribute | Type | Description
--------- | ---- | -----------
cod_ramo | int | Branch code
cod_subramo | int | Sub branch code
cod_tarifa | int | Coverage number
sn_acum_suma_aseg | int | 0,-1, if added to the total insured amount
sn_rc | string | 0,-1, if it is a RC coverage
sn_habilitado | string | 0,-1, if coverage is enabled
txt_desc | string | Description
