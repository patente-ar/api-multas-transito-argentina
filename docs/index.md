# API de multas de transito en Argentina

[![Docs](https://img.shields.io/badge/docs-patente.ar-0A66C2)](https://patente.ar/api-multas)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-public%20docs-181717)](https://patente-ar.github.io/api-multas-transito-argentina/)
[![Coverage](https://img.shields.io/badge/jurisdicciones-109-0F766E)](#cobertura-de-jurisdicciones)
[![Argentina](https://img.shields.io/badge/market-Argentina-38BDF8)](https://patente.ar)
[![Endpoint](https://img.shields.io/badge/endpoint-POST%20%2Fv1%2Fconsultas-111827)](https://patente.ar/api-multas)
[![Payload](https://img.shields.io/badge/payload-JSON-334155)](../openapi/openapi.yaml)
[![Auth](https://img.shields.io/badge/auth-Bearer%20API%20key-2563EB)](#request)
[![Webhooks](https://img.shields.io/badge/webhooks-HMAC%20SHA--256-7C3AED)](#webhooks)
[![Idempotency](https://img.shields.io/badge/idempotency-Idempotency--Key-059669)](#request)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-3.1-16A34A)](../openapi/openapi.yaml)
[![Examples](https://img.shields.io/badge/examples-curl%20%7C%20Node.js%20%7C%20Python-F97316)](#inicio-rapido)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](../LICENSE)

Conecta consultas de infracciones por patente a CRMs, ERPs, sistemas de scoring, portales de flota y validaciones preoperativas sin construir scrapers propios.

Este kit publico esta escrito para busquedas tecnicas y comerciales como "API multas Argentina", "API de multas de transito en Argentina", "API patente Argentina", "consulta por patente API" e "integracion vehicular Argentina". Para multas, tambien cubre "API infracciones de transito", "consultar multas por patente" y paginas por jurisdiccion.

## Inicio rapido

- Endpoint: `https://api.patente.ar/v1/consultas`
- Producto: `infracciones`
- Entrada: `plate`
- Ejemplo: `AB123CD`
- OpenAPI: [openapi.yaml](../openapi/openapi.yaml)
- Ejemplos: [curl](../examples/curl/consulta.sh), [Node.js](../examples/node/consulta.mjs), [Python](../examples/python/consulta.py)

## Casos de uso

- Scoring vehicular.
- Flotas.
- Seguros.
- Marketplaces.
- Gestorias.

## Request

```http
POST /v1/consultas HTTP/1.1
Host: api.patente.ar
Authorization: Bearer pa_live_xxx
Content-Type: application/json
Idempotency-Key: orden-externa-001
x-token: orden-externa-001
```

```json
{
  "patente": [
    "AB123CD"
  ]
}
```

## Webhooks

Los resultados asincronicos pueden recibirse por webhook firmado con HMAC SHA-256. Guardar `requestId`, validar `x-patente-signature` y usar `Idempotency-Key` para reintentos seguros.

## Confianza operativa

- 109 jurisdicciones publicadas en patente.ar para busquedas de multas por patente.
- Endpoint unico con API key por producto, idempotencia y trazabilidad.
- Webhook firmado para flujos asincronicos y auditoria por request.


## Cobertura de jurisdicciones

El repositorio lista las 109 jurisdicciones de multas publicadas en patente.ar para consulta por patente. La disponibilidad efectiva por API puede depender del contrato, la fuente activa y el estado operativo de cada organismo.

<details markdown="1">
<summary>Ver las 109 jurisdicciones</summary>

- [Alcira Gigena](https://patente.ar/multas-en-alcira-gigena)
- [Almirante Brown](https://patente.ar/multas-en-almirante-brown)
- [Alpa Corral](https://patente.ar/multas-en-alpa-corral)
- [Alta Gracia](https://patente.ar/multas-en-alta-gracia)
- [Arias](https://patente.ar/multas-en-arias)
- [Avellaneda](https://patente.ar/multas-en-avellaneda)
- [Bahia Blanca](https://patente.ar/multas-en-bahia-blanca)
- [Berisso](https://patente.ar/multas-en-berisso)
- [Bonpland](https://patente.ar/multas-en-bonpland)
- [Buenos Aires](https://patente.ar/multas-en-buenos-aires)
- [Caba](https://patente.ar/multas-en-caba)
- [Caminos De Las Sierras](https://patente.ar/multas-en-caminos-de-las-sierras)
- [Canals](https://patente.ar/multas-en-canals)
- [Canuelas](https://patente.ar/multas-en-canuelas)
- [Catamarca](https://patente.ar/multas-en-catamarca)
- [Chacabuco](https://patente.ar/multas-en-chacabuco)
- [Chaco](https://patente.ar/multas-en-chaco)
- [Chubut](https://patente.ar/multas-en-chubut)
- [Cinco Saltos](https://patente.ar/multas-en-cinco-saltos)
- [Colonia Tirolesa](https://patente.ar/multas-en-colonia-tirolesa)
- [Colonia Victoria](https://patente.ar/multas-en-colonia-victoria)
- [Cordoba](https://patente.ar/multas-en-cordoba)
- [Cordoba Municipalidad](https://patente.ar/multas-en-cordoba-municipalidad)
- [Corrientes](https://patente.ar/multas-en-corrientes)
- [Cosquin](https://patente.ar/multas-en-cosquin)
- [Curuzu Cuatia](https://patente.ar/multas-en-curuzu-cuatia)
- [El Alcazar](https://patente.ar/multas-en-el-alcazar)
- [Ente Ansenuza](https://patente.ar/multas-en-ente-ansenuza)
- [Entre Rios](https://patente.ar/multas-en-entre-rios)
- [Escobar](https://patente.ar/multas-en-escobar)
- [Ezeiza](https://patente.ar/multas-en-ezeiza)
- [Florencio Varela](https://patente.ar/multas-en-florencio-varela)
- [Formosa](https://patente.ar/multas-en-formosa)
- [General Levalle](https://patente.ar/multas-en-general-levalle)
- [Hurlingham](https://patente.ar/multas-en-hurlingham)
- [James Craik](https://patente.ar/multas-en-james-craik)
- [Juarez Celman](https://patente.ar/multas-en-juarez-celman)
- [La Calera](https://patente.ar/multas-en-la-calera)
- [La Cruz](https://patente.ar/multas-en-la-cruz)
- [La Cumbre](https://patente.ar/multas-en-la-cumbre)
- [La Matanza](https://patente.ar/multas-en-la-matanza)
- [La Pampa](https://patente.ar/multas-en-la-pampa)
- [La Plata](https://patente.ar/multas-en-la-plata)
- [La Rioja](https://patente.ar/multas-en-la-rioja)
- [Lanus](https://patente.ar/multas-en-lanus)
- [Las Heras](https://patente.ar/multas-en-las-heras)
- [Lomas De Zamora](https://patente.ar/multas-en-lomas-de-zamora)
- [Lujan](https://patente.ar/multas-en-lujan)
- [Luque](https://patente.ar/multas-en-luque)
- [Manuel Derqui](https://patente.ar/multas-en-manuel-derqui)
- [Mar Del Plata](https://patente.ar/multas-en-mar-del-plata)
- [Marcos Juarez](https://patente.ar/multas-en-marcos-juarez)
- [Mendiolaza](https://patente.ar/multas-en-mendiolaza)
- [Mendoza](https://patente.ar/multas-en-mendoza)
- [Mendoza Ciudad](https://patente.ar/multas-en-mendoza-ciudad)
- [Merlo](https://patente.ar/multas-en-merlo)
- [Misiones](https://patente.ar/multas-en-misiones)
- [Monte Maiz](https://patente.ar/multas-en-monte-maiz)
- [Moron](https://patente.ar/multas-en-moron)
- [Necochea](https://patente.ar/multas-en-necochea)
- [Neuquen](https://patente.ar/multas-en-neuquen)
- [Neuquen Capital](https://patente.ar/multas-en-neuquen-capital)
- [Noetinger](https://patente.ar/multas-en-noetinger)
- [Parada Pucheta](https://patente.ar/multas-en-parada-pucheta)
- [Picun Leufu](https://patente.ar/multas-en-picun-leufu)
- [Pilar](https://patente.ar/multas-en-pilar)
- [Plottier](https://patente.ar/multas-en-plottier)
- [Posadas](https://patente.ar/multas-en-posadas)
- [Quilmes](https://patente.ar/multas-en-quilmes)
- [Ramada Paso](https://patente.ar/multas-en-ramada-paso)
- [Riachuelo](https://patente.ar/multas-en-riachuelo)
- [Rio Ceballos](https://patente.ar/multas-en-rio-ceballos)
- [Rio Gallegos](https://patente.ar/multas-en-rio-gallegos)
- [Rio Negro](https://patente.ar/multas-en-rio-negro)
- [Rio Segundo](https://patente.ar/multas-en-rio-segundo)
- [Rio Tercero](https://patente.ar/multas-en-rio-tercero)
- [Rosario](https://patente.ar/multas-en-rosario)
- [Saenz Pena](https://patente.ar/multas-en-saenz-pena)
- [Saladas](https://patente.ar/multas-en-saladas)
- [Salta](https://patente.ar/multas-en-salta)
- [San Basilio](https://patente.ar/multas-en-san-basilio)
- [San Cosme](https://patente.ar/multas-en-san-cosme)
- [San Isidro](https://patente.ar/multas-en-san-isidro)
- [San Juan](https://patente.ar/multas-en-san-juan)
- [San Juan Capital](https://patente.ar/multas-en-san-juan-capital)
- [San Lorenzo](https://patente.ar/multas-en-san-lorenzo)
- [San Luis](https://patente.ar/multas-en-san-luis)
- [San Miguel](https://patente.ar/multas-en-san-miguel)
- [San Patricio Del Chanar](https://patente.ar/multas-en-san-patricio-del-chanar)
- [San Pedro De Jujuy](https://patente.ar/multas-en-san-pedro-de-jujuy)
- [San Vicente](https://patente.ar/multas-en-san-vicente)
- [Santa Cruz](https://patente.ar/multas-en-santa-cruz)
- [Santa Fe](https://patente.ar/multas-en-santa-fe)
- [Santa Isabel](https://patente.ar/multas-en-santa-isabel)
- [Santa Rosa](https://patente.ar/multas-en-santa-rosa)
- [Santiago Del Estero](https://patente.ar/multas-en-santiago-del-estero)
- [Tabay](https://patente.ar/multas-en-tabay)
- [Tierra Del Fuego](https://patente.ar/multas-en-tierra-del-fuego)
- [Tigre](https://patente.ar/multas-en-tigre)
- [Tres De Febrero](https://patente.ar/multas-en-tres-de-febrero)
- [Tucuman](https://patente.ar/multas-en-tucuman)
- [Vaqueros](https://patente.ar/multas-en-vaqueros)
- [Venado Tuerto](https://patente.ar/multas-en-venado-tuerto)
- [Vicente Lopez](https://patente.ar/multas-en-vicente-lopez)
- [Villa Carlos Paz](https://patente.ar/multas-en-villa-carlos-paz)
- [Villa De Soto](https://patente.ar/multas-en-villa-de-soto)
- [Villa La Angostura](https://patente.ar/multas-en-villa-la-angostura)
- [Villa Maria](https://patente.ar/multas-en-villa-maria)
- [Villa Olivari](https://patente.ar/multas-en-villa-olivari)

</details>


## Links

- Producto comercial: [https://patente.ar/api-multas](https://patente.ar/api-multas)
- Sitio principal: [https://patente.ar](https://patente.ar)
- Repositorio: [https://github.com/patente-ar/api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina)
