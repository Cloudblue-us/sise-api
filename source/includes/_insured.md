# Insured

Methods related the insured party

## Insured Party Object

> Example Insured JSON

```json
{
    "cod_usuario" : "123456789",
    "cod_aseg": 123456789,
    "nombre": "Name",
    "apellido1": "LastName 1",
    "apellido2": "LastName 2",
    "tipo_doc": 1,
    "nro_doc": "123456789",
    "digito_verificacion": 8,
    "fec_nacimiento": "AAAA-MM-DD",
    "cod_pais_nacionalidad": 0,
    "cuidad_nacimiento": "",
    "sexo": "M",
    "cod_est_civil": 1,
    "cod_tipo_agente": 1,
    "deportes": "",
    "empresa": "",
    "ocupacionActual": "",
    "cod_tipo_iva": 1,
    "direcciones": [
        {
            "cod_tipo_dir": 1,
            "cod_pais": 1,
            "cod_dpto": 1,
            "cod_municipio": 1,
            "txt_direccion": "Cll 1 1 1",
            "sn_direccion_correo": true
        }
    ],
    "telefonos": [
        {
            "cod_tipo_telef": 1,
            "txt_telefono": "1234567890"
        }
    ]
}
```

Methods return a JSON encoded object

Attribute | Type | Required | Description | Vlocity mapping
--------- | ---- | -------- | ----------- | -------------
cod_usuario | string | false | User ID assigned by Mundial | 
cod_aseg | long | false | Insured ID in SISE | `Default: 0`
nombre | string | false | First and middle name of the insured | 
apellido1 | string | false | Last name 1 | 
apellido2 | string | false | Last name 2 | 
tipo_doc | int | false | Document type ID | [Document Types](#document-types)
nro_doc | string | false | Document number |
digito_verificacion | int | false | Verification number if tipo_doc is NIT |
fec_nacimiento | date | false | Birthdate | 
cod_pais_nacionalidad | date | false | Birthdate | 
cuidad_nacimiento | date | false | Birthdate | 
sexo | date | false | Gender | [Gender Types](#gender-types)
cod_est_civil | int | false | Marital status code | [Marital Status Codes](#marital-status-code)
cod_tipo_agente | int | false | Broker type code | 
deportes | string | false | Insured party sports | `Default: ""` 
empresa | string | false | Insured party company | `Default: ""` 
ocupacionActual | string | false | current occupation | `Default: ""` 
cod_tipo_iva | int | false | VAT type ID | 
direcciones | Array of [Insured Addresses](#insured-addresses) | false | List of Insured addresses |  
telefonos | Array of [Insured Telephone](#insured-telephone) | false | List of Insured telephones |  

## Insured Addresses 

Attribute | Type | Required | Description | Vlocity mapping
--------- | ---- | -------- | ----------- | -------------
cod_tipo_dir | int | true | Address type ID | [Address Types](#address-types) `Default: 1`
cod_pais | int | true | Country code ID | `Default: 1`
cod_dpto | int | true | State code ID | `Default: 1`
cod_municipio | int | true | City code ID | `Default: 1`
txt_direccion | int | true | Address | 
sn_direccion_correo | bool | true | Is correspondence address | `Default: false`

## Insured Telephone

Emails can be stored on this field using cod_tipo_telef = 10 or 20

Attribute | Type | Required | Description | Vlocity mapping
--------- | ---- | -------- | ----------- | -------------
cod_tipo_telef | int | true | Telephone type ID | [Telephone Types](#telephone-types) `Default: 1`
txt_telefono | string | true | Telephone or email text | `Default: ""`


## Get Insured

> Request data example

```json
```

Request token method.

### HTTP Request
`GET /api/asegurado/?cod_tipo_doc=<cod_tipo_doc>&nro_doc=<nro_doc>`

### Content-type
`application/json`

### Response

[Insured Party Object](#insured-party-object)

## Insert Insured

### HTTP Request
`POST, PUT /api/asegurado`

### Content-type
`application/json`

### Body data

[Insured Party Object](#insured-party-object)

### Response

If it's a new object cod_aseg is returned with the code asigned by SISE

[Insured Party Object](#insured-party-object)