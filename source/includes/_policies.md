# Policies

Policies Methods

## Policies Response Object

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

stateDiagram-v2
    [*] --> Still
    Still --> [*]
    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
            

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

### Body data

Attribute | Type | Required | Description
--------- | ---- | -------- | -----------
cod_ramo | int | True | Branch code
cod_suc | int | True | Branch Office code
nro_pol | long | True | Policy number

### Response

[Policies Response Object](#policies-response-object)

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
Attribute | Type | Required | Description | Vlocity mapping
--------- | ---- | -------- | ----------- | -------------
cod_usuario | string | True | User assigned by mundial | 
cod_ramo | int | True | Branch code | `Default value: 25`
cod_suc | int | True | Branch Office code | `Account:Cod_Suc`
nro_pol | long | True | Policy number | ``
nro_endoso | int | True | Endorsement number | ``
certificado_sise | long | False | Autoincrementing number starting in 0. Must be saved in Vlocity | ``
fec_vig_desde | datetime | true | Policy starting date | `Asset:vlocity_ins__EffectiveDate__c` starting date hours begin on 00:00:00
fec_vig_hasta | datetime | true | Policy ending date | `Asset:vlocity_ins__EffectiveDate__c` endign date hours end on 23:59:59
fec_emision | datetime | true | Issuing date | `Asset:vlocity_ins__InceptionDate__c` 
cod_agente | long | true | Broker code | `Account:cod_agente__c` 
cod_tipo_agente | int | true | Broker type code | `Account:cod_agente__c` 
cod_aseg | long | false | Taker code |  
cod_moneda | int | true | issue currency code | `Default value: 0` 
cod_imp_cambio | double | true | foreign currency issuing code | `Default value: 1` 
cod_grupo_endo | int | true | Movement type | Matrix in the IP 
imp_prima | double | true | Premium amount | `Asset:vlocity_ins__TotalPremiumForTerm__c`
pje_iva | double | false | VAT percentage | `Tax and Fee:vlocity_ins__Percent__c`
imp_iva | double | false | VAT amount | `Asset:vlocity_ins__TotalFeeAmount__c`
imp_decreto | double | false | Decree amount | `Default value: 0`
imp_descuento | double | false | Discount amount | `Default value: 0`
imp_gasto_emision | double | false | emission expenses | `Default value: 0`
imp_recargo | double | false | surcharge amount | `Default value: 0`
imp_base_disponible | double | true | base premium, value used for VAT calculation |  `Asset:vlocity_ins__StandardPremium__c`
cod_pto_vta | long | false | Point of sale code | `Asset:vlocity_ins__StandardPremium__c`
cod_tipo_poliza | long | true | Policy type code | Matrix in the IP 
cod_giro_negocio | int | false | Identifies whether the policy is collective or individual | TBD 
sn_pagador | bool | true | Policy type code | If the policyholder is the same payer, send true.
referencia_pago | string | true | Payment reference. Must be filled if `sn_pagador` is true | TBD
convenio_id | int | false | SISE Agreement code | `default: ''`
plan_id | int | false | SISE plan code | `default: ''`
fechaDesembolso | datetime | false | Payout date | `default: ''`
fechaSolicitud | datetime | false | Application date | `default: ''`
detalleCoberturas | Array of []() | false | List of coverage associated with the policy movement | 
detalleIntermediario | Array of []() | true | List of brokers associated with the policy movement | 
InfomacionTomador | []() | false | Taker information | 

### Response

[Policies Response Object](#policies-response-object)