# Policies

Policies Methods

## Response Object

> Example JSON API response

```json
{
    "procesadoExitoso" : true,
    "mensaje" : "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "codigoSise" : 123456789
}
```

Methods return a JSON encoded object

Attribute | Get Policy response | Insert Policy response
--------- | ------------------- | ----------------------
procesadoExitoso | True if policy exists | True if operation was successful
mensaje | Not used | Issued message or error message
codigoSise | Not used | ID issued by SISE

## Get Policy Number

> Request data example

```json
{
    "cod_ramo": 25,
    "cod_suc": 1000,
    "nro_pol": 123456789
}
```

Get policy number and availability.

### HTTP Request
`POST /api/poliza/ConsultarNroPoliza`

### Content-type
`application/json`

### body data

Attribute | Type | Required | Description
--------- | ---- | -------- | -----------
cod_ramo | int | True | Branch code
cod_suc | int | True | Branch Office code
nro_pol | long | True | Policy number

## Insert Policy

> Insert JSON body

```json
{
    "cod_usuario": "12341234A",
    "cod_ramo": 25,
    "cod_suc": 1000,
    "nro_pol": 123456789,
    "nro_endoso": 0,
    "certificado_sise": 123456789,
    "fec_vig_desde" : "AAAA-MM-DD 00:00:00",
    "fec_vig_hasta" : "AAAA-MM-DD 00:00:00",
    "fec_emision" : "AAAA-MM-DD 00:00:00",
    "cod_agente" : 123456789,
    "cod_tipo_agente" : 12,
    "cod_aseg" : 123456789,
    "cod_moneda" : 0,
    "cod_imp_cambio" : 1,
    "cod_grupo_endo" : 1,
    "imp_prima" : 1000000,
    "pje_iva" : 19,
    "imp_iva" : 19000,
    "imp_decreto": 0,
    "imp_descuento": 0,
    "imp_gasto_emision": 0,
    "imp_recargo": 0,
    "imp_base_disponible": 0,
    "cod_pto_vta": 123456789,
    "cod_tipo_poliza": 25,
    "cod_giro_negocio": 25,
    "sn_pagador": true,
    "referencia_pago": "abcd",
    "convenio_id": "",
    "plan_id": "",
    "fechaDesembolso": "AAAA-MM-DD 00:00:00",
    "fechaSolicitud": "AAAA-MM-DD 00:00:00",
    "detalleCoberturas": [
        {
            "cod_ramo": 25,
            "cod_sub_ramo": 25,
            "cod_tarifa": 0,
            "imp_prima": 500000,
            "imp_iva": 80000,
            "imp_suma_asegurada": 100000,
            "imp_resp_max": 10000,
            "sn_suma_total_suma_aseg": true,
            "cod_estado": 1
        }
    ],
    "detalleIntermediario": [
        {
            "cod_agente": 123456789,
            "cod_tipo_agente": 1,
            "pje_partic": 10,
            "pje_comis_normal": 10,
            "pje_comis_extra": 0,
            "imp_comis_normal_me": 0,
            "imp_comis_extra_me": 0
        }
    ],
    "InfomacionTomador": {},
    "detallePagador": [
        {
            "cod_aseg": 123456789,
            "sn_pagador": true,
            "sn_asegurado": true,
            "referencia_pago": "",
            "imp_prima": 1000000,
            "pje_iva": 19,
            "imp_iva": 19000,
            "imp_decreto": 0,
            "imp_descuento": 0,
            "imp_gasto_emision": 0,
            "imp_recargo": 0,
            "infomacionAsegurado": {},
            "detalleBeneficiarios": [
                {
                    "nombre": "Carlos",
                    "apellido1": "Perez",
                    "apellido2": "Rodriguez",
                    "parentesco": "",
                    "porcentajeValorAsegurado": 100.0
                }
            ],
            "fec_vig_desde" : "AAAA-MM-DD 00:00:00",
            "fec_vig_hasta" : "AAAA-MM-DD 00:00:00",
        }
    ],
    "tipo_coaseguro": "",
    "detalleCoaseguro": [
        {
            "nro_doc_cia": "",
            "pje_part": 100.0,
            "pje_gastos_admon": 10.0,
            "imp_coaseguro": 10.0,
        }
    ],
    "detalleInformacionPago": {
        "for_pago": "",
        "franquicia": "",
        "num_tarjeta": "",
        "num_autoriza": "",
        "valor_pago": "",
        "fec_pago": "AAAA-MM-DD 00:00:00",
        "cod_banco": "",
        "nro_consignacion": "",
        "txt_nom_banco": "",
        "id_proc_sync": ""
    },
    "agrupar_recaudo": false
}
```

Insert new policy.

### HTTP Request
`PUT /api/poliza`

### Content-type
`application/json`

### body data
Attribute | Type | Required | Description | Vlocity field
--------- | ---- | -------- | ----------- | -------------
cod_ramo | int | True | Branch code
cod_suc | int | True | Branch Office code
nro_pol | long | True | Policy number