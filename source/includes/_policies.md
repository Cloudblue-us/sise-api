# Policies

Methods about policies

## Response Object


> Example JSON API response

```json
{
    "procesadoExitoso" : True,
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

## Get Policy


## Insert Policy