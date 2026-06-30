# API de multas de transito en Argentina

[![Docs](https://img.shields.io/badge/docs-patente.ar-0A66C2)](https://patente.ar/api-multas)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-public%20docs-181717)](https://patente-ar.github.io/api-multas-transito-argentina/)
[![Coverage](https://img.shields.io/badge/jurisdicciones-109-0F766E)](#cobertura-de-jurisdicciones)
[![Pages](https://img.shields.io/badge/pages-109%20jurisdicciones-7C3AED)](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
[![Argentina](https://img.shields.io/badge/market-Argentina-38BDF8)](https://patente.ar)
[![Endpoint](https://img.shields.io/badge/endpoint-POST%20%2Fv1%2Fconsultas-111827)](https://patente.ar/api-multas)
[![Payload](https://img.shields.io/badge/payload-JSON-334155)](./openapi/openapi.yaml)
[![Auth](https://img.shields.io/badge/auth-Bearer%20API%20key-2563EB)](#request)
[![Cuenta](https://img.shields.io/badge/cuenta-crear%20gratis-0A66C2)](https://patente.ar/registro)
[![Playground](https://img.shields.io/badge/playground-probar%20API-7C3AED)](https://patente.ar/desarrolladores/api?tab=playground)
[![Webhooks](https://img.shields.io/badge/webhooks-HMAC%20SHA--256-7C3AED)](#webhooks)
[![Idempotency](https://img.shields.io/badge/idempotency-Idempotency--Key-059669)](#request)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-3.1-16A34A)](./openapi/openapi.yaml)
[![Examples](https://img.shields.io/badge/examples-curl%20%7C%20Node.js%20%7C%20Python-F97316)](#inicio-rapido)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](./LICENSE)

> Conecta consultas de infracciones por patente a CRMs, ERPs, sistemas de scoring, portales de flota y validaciones preoperativas sin construir scrapers propios.

**patente.ar** centraliza APIs vehiculares para Argentina: consultas por patente o VIN, procesamiento asincronico, trazabilidad por request y documentacion pensada para equipos de producto, datos y operaciones.

Este kit publico esta escrito para busquedas tecnicas y comerciales como "API multas Argentina", "API de multas de transito en Argentina", "API patente Argentina", "consulta por patente API" e "integracion vehicular Argentina". Para multas, tambien cubre "API infracciones de transito", "consultar multas por patente" y paginas por jurisdiccion.

## Por que este repo

- 109 jurisdicciones publicadas en patente.ar para busquedas de multas por patente.
- Endpoint unico con API key por producto, idempotencia y trazabilidad.
- Webhook firmado para flujos asincronicos y auditoria por request.

## Lo que trae

| Pieza | Para que sirve |
| --- | --- |
| `README.md` | Guia comercial y tecnica para integrar API multas Argentina. |
| `openapi/openapi.yaml` | Contrato OpenAPI 3.1 para documentacion, SDKs o pruebas. |
| `examples/curl/consulta.sh` | Prueba rapida desde terminal. |
| `examples/node/consulta.mjs` | Ejemplo Node.js con `fetch`. |
| `examples/python/consulta.py` | Ejemplo Python sin dependencias externas. |
| `webhooks/*` | Verificacion HMAC SHA-256 de webhooks de patente.ar. |
| `.github/workflows/validate.yml` | Validacion de sintaxis para ejemplos. |

## Endpoint

```text
POST https://api.patente.ar/v1/consultas
```

El producto queda definido por la API key emitida para `infracciones`. No hace falta inventar rutas como `/v1/multas` o `/v1/vtv`: el contrato publico se mantiene estable en `POST /v1/consultas`.

## Para que sirve

- Scoring vehicular.
- Flotas.
- Seguros.
- Marketplaces.
- Gestorias.

## Inicio rapido

1. Pedir una API key desde [patente.ar](https://patente.ar/api-multas).
2. Copiar `.env.example` como `.env`.
3. Ejecutar un ejemplo:

```bash
export PATENTE_API_KEY="pa_live_xxx"
./examples/curl/consulta.sh
node examples/node/consulta.mjs
python3 examples/python/consulta.py
```

La respuesta puede ser inmediata o asincronica. Cuando queda en proceso, patente.ar responde con `202 accepted` y un `requestId`; el resultado final puede llegar por webhook.

## Activar API y probar en Playground

Para probar API multas Argentina sin armar un backend desde cero, crea una cuenta en patente.ar, pedi habilitar la API `infracciones` y usa el Playground para ejecutar requests con API keys, payloads de ejemplo, idempotencia, webhooks y logs.

| Paso | Link | Que hacer |
| --- | --- | --- |
| 1 | [Crear cuenta en patente.ar](https://patente.ar/registro) | Registrar la cuenta de empresa o equipo que va a consumir la API. |
| 2 | [Pedir habilitacion de la API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones) | Solicitar que activen el producto `infracciones` y el esquema de creditos. |
| 3 | [Abrir el Playground](https://patente.ar/desarrolladores/api?tab=playground) | Probar payloads reales de integracion, revisar respuestas y validar webhooks sin publicar credenciales. |
| 4 | [Pasar a produccion](https://patente.ar/api-multas) | Configurar API keys, webhook firmado, idempotencia y trazabilidad por `requestId`. |

El Playground requiere iniciar sesion y tener el modulo API habilitado para la cuenta. Si todavia no aparece, pedi la habilitacion desde el link anterior.


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

## Response aceptada

```json
{
  "code": 202,
  "status": "accepted",
  "message": "La solicitud fue aceptada y se procesara en breve.",
  "requestId": "req_01HZX...",
  "timestamp": "2026-06-30T12:00:00.000Z"
}
```


## Cobertura de jurisdicciones

El repositorio tiene una pagina dedicada por jurisdiccion para las 109 jurisdicciones de multas publicadas en patente.ar. La disponibilidad efectiva por API puede depender del contrato, la fuente activa y el estado operativo de cada organismo.

<details markdown="1">
<summary>Ver las 109 jurisdicciones</summary>

- [Alcira Gigena](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-alcira-gigena/) - [consulta en patente.ar](https://patente.ar/multas-en-alcira-gigena)
- [Almirante Brown](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-almirante-brown/) - [consulta en patente.ar](https://patente.ar/multas-en-almirante-brown)
- [Alpa Corral](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-alpa-corral/) - [consulta en patente.ar](https://patente.ar/multas-en-alpa-corral)
- [Alta Gracia](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-alta-gracia/) - [consulta en patente.ar](https://patente.ar/multas-en-alta-gracia)
- [Arias](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-arias/) - [consulta en patente.ar](https://patente.ar/multas-en-arias)
- [Avellaneda](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-avellaneda/) - [consulta en patente.ar](https://patente.ar/multas-en-avellaneda)
- [Bahía Blanca](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-bahia-blanca/) - [consulta en patente.ar](https://patente.ar/multas-en-bahia-blanca)
- [Berisso](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-berisso/) - [consulta en patente.ar](https://patente.ar/multas-en-berisso)
- [Bonpland](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-bonpland/) - [consulta en patente.ar](https://patente.ar/multas-en-bonpland)
- [Buenos Aires](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-buenos-aires/) - [consulta en patente.ar](https://patente.ar/multas-en-buenos-aires)
- [CABA](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-caba/) - [consulta en patente.ar](https://patente.ar/multas-en-caba)
- [Caminos de las Sierras](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-caminos-de-las-sierras/) - [consulta en patente.ar](https://patente.ar/multas-en-caminos-de-las-sierras)
- [Canals](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-canals/) - [consulta en patente.ar](https://patente.ar/multas-en-canals)
- [Cañuelas](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-canuelas/) - [consulta en patente.ar](https://patente.ar/multas-en-canuelas)
- [Catamarca](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-catamarca/) - [consulta en patente.ar](https://patente.ar/multas-en-catamarca)
- [Chacabuco](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-chacabuco/) - [consulta en patente.ar](https://patente.ar/multas-en-chacabuco)
- [Chaco](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-chaco/) - [consulta en patente.ar](https://patente.ar/multas-en-chaco)
- [Chubut](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-chubut/) - [consulta en patente.ar](https://patente.ar/multas-en-chubut)
- [Cinco Saltos](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-cinco-saltos/) - [consulta en patente.ar](https://patente.ar/multas-en-cinco-saltos)
- [Colonia Tirolesa](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-colonia-tirolesa/) - [consulta en patente.ar](https://patente.ar/multas-en-colonia-tirolesa)
- [Colonia Victoria](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-colonia-victoria/) - [consulta en patente.ar](https://patente.ar/multas-en-colonia-victoria)
- [Córdoba](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-cordoba/) - [consulta en patente.ar](https://patente.ar/multas-en-cordoba)
- [Córdoba Capital](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-cordoba-municipalidad/) - [consulta en patente.ar](https://patente.ar/multas-en-cordoba-municipalidad)
- [Corrientes](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-corrientes/) - [consulta en patente.ar](https://patente.ar/multas-en-corrientes)
- [Cosquín](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-cosquin/) - [consulta en patente.ar](https://patente.ar/multas-en-cosquin)
- [Curuzú Cuatiá](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-curuzu-cuatia/) - [consulta en patente.ar](https://patente.ar/multas-en-curuzu-cuatia)
- [El Alcázar](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-el-alcazar/) - [consulta en patente.ar](https://patente.ar/multas-en-el-alcazar)
- [Ente Ansenuza](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-ente-ansenuza/) - [consulta en patente.ar](https://patente.ar/multas-en-ente-ansenuza)
- [Entre Ríos](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-entre-rios/) - [consulta en patente.ar](https://patente.ar/multas-en-entre-rios)
- [Escobar](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-escobar/) - [consulta en patente.ar](https://patente.ar/multas-en-escobar)
- [Ezeiza](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-ezeiza/) - [consulta en patente.ar](https://patente.ar/multas-en-ezeiza)
- [Florencio Varela](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-florencio-varela/) - [consulta en patente.ar](https://patente.ar/multas-en-florencio-varela)
- [Formosa](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-formosa/) - [consulta en patente.ar](https://patente.ar/multas-en-formosa)
- [General Levalle](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-general-levalle/) - [consulta en patente.ar](https://patente.ar/multas-en-general-levalle)
- [Hurlingham](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-hurlingham/) - [consulta en patente.ar](https://patente.ar/multas-en-hurlingham)
- [James Craik](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-james-craik/) - [consulta en patente.ar](https://patente.ar/multas-en-james-craik)
- [Juárez Celman](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-juarez-celman/) - [consulta en patente.ar](https://patente.ar/multas-en-juarez-celman)
- [La Calera](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-calera/) - [consulta en patente.ar](https://patente.ar/multas-en-la-calera)
- [La Cruz](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-cruz/) - [consulta en patente.ar](https://patente.ar/multas-en-la-cruz)
- [La Cumbre](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-cumbre/) - [consulta en patente.ar](https://patente.ar/multas-en-la-cumbre)
- [La Matanza](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-matanza/) - [consulta en patente.ar](https://patente.ar/multas-en-la-matanza)
- [La Pampa](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-pampa/) - [consulta en patente.ar](https://patente.ar/multas-en-la-pampa)
- [La Plata](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-plata/) - [consulta en patente.ar](https://patente.ar/multas-en-la-plata)
- [La Rioja](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-la-rioja/) - [consulta en patente.ar](https://patente.ar/multas-en-la-rioja)
- [Lanús](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-lanus/) - [consulta en patente.ar](https://patente.ar/multas-en-lanus)
- [Las Heras](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-las-heras/) - [consulta en patente.ar](https://patente.ar/multas-en-las-heras)
- [Lomas de Zamora](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-lomas-de-zamora/) - [consulta en patente.ar](https://patente.ar/multas-en-lomas-de-zamora)
- [Luján](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-lujan/) - [consulta en patente.ar](https://patente.ar/multas-en-lujan)
- [Luque](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-luque/) - [consulta en patente.ar](https://patente.ar/multas-en-luque)
- [Manuel Derqui](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-manuel-derqui/) - [consulta en patente.ar](https://patente.ar/multas-en-manuel-derqui)
- [Mar del Plata](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-mar-del-plata/) - [consulta en patente.ar](https://patente.ar/multas-en-mar-del-plata)
- [Marcos Juárez](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-marcos-juarez/) - [consulta en patente.ar](https://patente.ar/multas-en-marcos-juarez)
- [Mendiolaza](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-mendiolaza/) - [consulta en patente.ar](https://patente.ar/multas-en-mendiolaza)
- [Mendoza](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-mendoza/) - [consulta en patente.ar](https://patente.ar/multas-en-mendoza)
- [Mendoza Ciudad](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-mendoza-ciudad/) - [consulta en patente.ar](https://patente.ar/multas-en-mendoza-ciudad)
- [Merlo](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-merlo/) - [consulta en patente.ar](https://patente.ar/multas-en-merlo)
- [Misiones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-misiones/) - [consulta en patente.ar](https://patente.ar/multas-en-misiones)
- [Monte Maíz](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-monte-maiz/) - [consulta en patente.ar](https://patente.ar/multas-en-monte-maiz)
- [Morón](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-moron/) - [consulta en patente.ar](https://patente.ar/multas-en-moron)
- [Necochea](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-necochea/) - [consulta en patente.ar](https://patente.ar/multas-en-necochea)
- [Neuquén](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-neuquen/) - [consulta en patente.ar](https://patente.ar/multas-en-neuquen)
- [Neuquén Capital](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-neuquen-capital/) - [consulta en patente.ar](https://patente.ar/multas-en-neuquen-capital)
- [Noetinger](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-noetinger/) - [consulta en patente.ar](https://patente.ar/multas-en-noetinger)
- [Parada Pucheta](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-parada-pucheta/) - [consulta en patente.ar](https://patente.ar/multas-en-parada-pucheta)
- [Picún Leufú](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-picun-leufu/) - [consulta en patente.ar](https://patente.ar/multas-en-picun-leufu)
- [Pilar](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-pilar/) - [consulta en patente.ar](https://patente.ar/multas-en-pilar)
- [Plottier](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-plottier/) - [consulta en patente.ar](https://patente.ar/multas-en-plottier)
- [Posadas](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-posadas/) - [consulta en patente.ar](https://patente.ar/multas-en-posadas)
- [Quilmes](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-quilmes/) - [consulta en patente.ar](https://patente.ar/multas-en-quilmes)
- [Ramada Paso](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-ramada-paso/) - [consulta en patente.ar](https://patente.ar/multas-en-ramada-paso)
- [Riachuelo](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-riachuelo/) - [consulta en patente.ar](https://patente.ar/multas-en-riachuelo)
- [Río Ceballos](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-rio-ceballos/) - [consulta en patente.ar](https://patente.ar/multas-en-rio-ceballos)
- [Río Gallegos](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-rio-gallegos/) - [consulta en patente.ar](https://patente.ar/multas-en-rio-gallegos)
- [Río Negro](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-rio-negro/) - [consulta en patente.ar](https://patente.ar/multas-en-rio-negro)
- [Río Segundo](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-rio-segundo/) - [consulta en patente.ar](https://patente.ar/multas-en-rio-segundo)
- [Río Tercero](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-rio-tercero/) - [consulta en patente.ar](https://patente.ar/multas-en-rio-tercero)
- [Rosario](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-rosario/) - [consulta en patente.ar](https://patente.ar/multas-en-rosario)
- [Sáenz Peña](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-saenz-pena/) - [consulta en patente.ar](https://patente.ar/multas-en-saenz-pena)
- [Saladas](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-saladas/) - [consulta en patente.ar](https://patente.ar/multas-en-saladas)
- [Salta](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-salta/) - [consulta en patente.ar](https://patente.ar/multas-en-salta)
- [San Basilio](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-basilio/) - [consulta en patente.ar](https://patente.ar/multas-en-san-basilio)
- [San Cosme](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-cosme/) - [consulta en patente.ar](https://patente.ar/multas-en-san-cosme)
- [San Isidro](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-isidro/) - [consulta en patente.ar](https://patente.ar/multas-en-san-isidro)
- [San Juan](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-juan/) - [consulta en patente.ar](https://patente.ar/multas-en-san-juan)
- [San Juan Capital](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-juan-capital/) - [consulta en patente.ar](https://patente.ar/multas-en-san-juan-capital)
- [San Lorenzo](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-lorenzo/) - [consulta en patente.ar](https://patente.ar/multas-en-san-lorenzo)
- [San Luis](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-luis/) - [consulta en patente.ar](https://patente.ar/multas-en-san-luis)
- [San Miguel](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-miguel/) - [consulta en patente.ar](https://patente.ar/multas-en-san-miguel)
- [San Patricio del Chañar](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-patricio-del-chanar/) - [consulta en patente.ar](https://patente.ar/multas-en-san-patricio-del-chanar)
- [San Pedro de Jujuy](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-pedro-de-jujuy/) - [consulta en patente.ar](https://patente.ar/multas-en-san-pedro-de-jujuy)
- [San Vicente](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-san-vicente/) - [consulta en patente.ar](https://patente.ar/multas-en-san-vicente)
- [Santa Cruz](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-santa-cruz/) - [consulta en patente.ar](https://patente.ar/multas-en-santa-cruz)
- [Santa Fe](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-santa-fe/) - [consulta en patente.ar](https://patente.ar/multas-en-santa-fe)
- [Santa Isabel](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-santa-isabel/) - [consulta en patente.ar](https://patente.ar/multas-en-santa-isabel)
- [Santa Rosa](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-santa-rosa/) - [consulta en patente.ar](https://patente.ar/multas-en-santa-rosa)
- [Santiago del Estero](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-santiago-del-estero/) - [consulta en patente.ar](https://patente.ar/multas-en-santiago-del-estero)
- [Tabay](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-tabay/) - [consulta en patente.ar](https://patente.ar/multas-en-tabay)
- [Tierra del Fuego](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-tierra-del-fuego/) - [consulta en patente.ar](https://patente.ar/multas-en-tierra-del-fuego)
- [Tigre](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-tigre/) - [consulta en patente.ar](https://patente.ar/multas-en-tigre)
- [Tres de Febrero](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-tres-de-febrero/) - [consulta en patente.ar](https://patente.ar/multas-en-tres-de-febrero)
- [Tucumán](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-tucuman/) - [consulta en patente.ar](https://patente.ar/multas-en-tucuman)
- [Vaqueros](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-vaqueros/) - [consulta en patente.ar](https://patente.ar/multas-en-vaqueros)
- [Venado Tuerto](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-venado-tuerto/) - [consulta en patente.ar](https://patente.ar/multas-en-venado-tuerto)
- [Vicente López](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-vicente-lopez/) - [consulta en patente.ar](https://patente.ar/multas-en-vicente-lopez)
- [Villa Carlos Paz](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-villa-carlos-paz/) - [consulta en patente.ar](https://patente.ar/multas-en-villa-carlos-paz)
- [Villa de Soto](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-villa-de-soto/) - [consulta en patente.ar](https://patente.ar/multas-en-villa-de-soto)
- [Villa La Angostura](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-villa-la-angostura/) - [consulta en patente.ar](https://patente.ar/multas-en-villa-la-angostura)
- [Villa María](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-villa-maria/) - [consulta en patente.ar](https://patente.ar/multas-en-villa-maria)
- [Villa Olivari](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-villa-olivari/) - [consulta en patente.ar](https://patente.ar/multas-en-villa-olivari)

</details>


## Webhooks

Cuando el resultado esta disponible, patente.ar puede enviar un `POST` al webhook configurado para la API key.

Headers relevantes:

- `x-patente-timestamp`
- `x-patente-signature`
- `x-patente-request-id`
- `x-patente-api-key`
- `x-token` si fue enviado en el request original

La firma usa HMAC SHA-256 sobre:

```text
timestamp.raw_body
```

Ver ejemplos en:

- [Node.js](./webhooks/node/verify-signature.mjs)
- [Python](./webhooks/python/verify_signature.py)

## Checklist de produccion

- Usar `Idempotency-Key` en todos los reintentos.
- Guardar `requestId` y `x-token` para conciliacion.
- Validar `x-patente-signature` antes de procesar webhooks.
- Reintentar `429` y errores temporales con backoff.
- No registrar API keys, webhook secrets ni payloads sensibles en logs.

## Errores frecuentes

| Codigo | Causa | Accion |
| --- | --- | --- |
| 401 | API key ausente, revocada o invalida | Rotar o revisar la key en patente.ar |
| 402 | Creditos insuficientes | Cargar saldo o cambiar el producto contratado |
| 409 | Idempotencia ya en curso | Reusar el `requestId` previo o cambiar `Idempotency-Key` |
| 422 | Payload fuera de contrato | Revisar el ejemplo y normalizar la entrada |
| 429 | Rate limit | Reintentar con backoff |

## Links

- Producto: [https://patente.ar/api-multas](https://patente.ar/api-multas)
- Crear cuenta: [https://patente.ar/registro](https://patente.ar/registro)
- Habilitar API: [https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- Playground: [https://patente.ar/desarrolladores/api?tab=playground](https://patente.ar/desarrolladores/api?tab=playground)
- Patente.ar: [https://patente.ar](https://patente.ar)
- Documentacion OpenAPI: [openapi/openapi.yaml](./openapi/openapi.yaml)

## Licencia

MIT. Este repositorio contiene ejemplos de integracion; no incluye credenciales ni codigo backend de patente.ar.
