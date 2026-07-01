# API de multas de transito en Argentina

[![Docs](https://img.shields.io/badge/docs-patente.ar-0A66C2)](https://patente.ar/api-multas)
[![Playground](https://img.shields.io/badge/playground-probar%20API-7C3AED)](https://patente.ar/desarrolladores/api?tab=playground)
[![Jurisdicciones](https://img.shields.io/badge/jurisdicciones-109-0F766E)](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-3.1-16A34A)](./openapi/openapi.yaml)
[![Webhooks](https://img.shields.io/badge/webhooks-HMAC%20SHA--256-7C3AED)](#webhooks)
[![Examples](https://img.shields.io/badge/examples-curl%20%7C%20Node.js%20%7C%20Python-F97316)](#inicio-rapido)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](./LICENSE)

> Conecta consultas de infracciones por patente a CRMs, ERPs, sistemas de scoring, portales de flota y validaciones preoperativas sin construir scrapers propios.

Este repo no es un SDK ni un wrapper instalable. Es un kit publico de integracion para equipos que quieren evaluar la API de patente.ar antes de conectarla a un CRM, ERP, backoffice, marketplace, seguro o flujo de flota.

**patente.ar** centraliza APIs vehiculares para Argentina: consultas por patente o VIN, procesamiento asincronico, trazabilidad por request y documentacion pensada para equipos de producto, datos y operaciones.

## Que resuelve

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


## Cobertura en GitHub Pages

El repo mantiene 109 paginas por jurisdiccion con contexto local, fuente informativa, canales oficiales y notas de integracion. El README queda corto; la cobertura completa vive en GitHub Pages y en el sitemap publico.

- Indice completo: [jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- Sitemap: [sitemap.xml](https://patente-ar.github.io/api-multas-transito-argentina/sitemap.xml)
- Pagina comercial: [API multas en patente.ar](https://patente.ar/api-multas)

Ejemplos:

- [Alcira Gigena](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-alcira-gigena/) - [consulta web](https://patente.ar/multas-en-alcira-gigena)
- [Almirante Brown](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-almirante-brown/) - [consulta web](https://patente.ar/multas-en-almirante-brown)
- [Alpa Corral](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-alpa-corral/) - [consulta web](https://patente.ar/multas-en-alpa-corral)
- [Alta Gracia](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-alta-gracia/) - [consulta web](https://patente.ar/multas-en-alta-gracia)
- [Arias](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-arias/) - [consulta web](https://patente.ar/multas-en-arias)
- [Avellaneda](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-avellaneda/) - [consulta web](https://patente.ar/multas-en-avellaneda)
- [Bahía Blanca](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-bahia-blanca/) - [consulta web](https://patente.ar/multas-en-bahia-blanca)
- [Berisso](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-berisso/) - [consulta web](https://patente.ar/multas-en-berisso)
- [Bonpland](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-bonpland/) - [consulta web](https://patente.ar/multas-en-bonpland)
- [Buenos Aires](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-buenos-aires/) - [consulta web](https://patente.ar/multas-en-buenos-aires)
- [CABA](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-caba/) - [consulta web](https://patente.ar/multas-en-caba)
- [Caminos de las Sierras](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/multas-en-caminos-de-las-sierras/) - [consulta web](https://patente.ar/multas-en-caminos-de-las-sierras)


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
