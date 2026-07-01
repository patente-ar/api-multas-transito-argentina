# API de multas de transito en Argentina

[![Docs](https://img.shields.io/badge/docs-patente.ar-0A66C2)](https://patente.ar/api-multas)
[![Playground](https://img.shields.io/badge/playground-probar%20API-7C3AED)](https://patente.ar/desarrolladores/api?tab=playground)
[![Jurisdicciones](https://img.shields.io/badge/jurisdicciones-109-0F766E)](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-3.1-16A34A)](../openapi/openapi.yaml)
[![Webhooks](https://img.shields.io/badge/webhooks-HMAC%20SHA--256-7C3AED)](#webhooks)
[![Examples](https://img.shields.io/badge/examples-curl%20%7C%20Node.js%20%7C%20Python-F97316)](#inicio-rapido)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](../LICENSE)

Conecta consultas de infracciones por patente a CRMs, ERPs, sistemas de scoring, portales de flota y validaciones preoperativas sin construir scrapers propios.

Esta documentacion publica esta pensada para que un equipo tecnico entienda el contrato de integracion, pruebe el flujo en Playground y sepa cuando pedir la habilitacion comercial de API multas Argentina. En multas, las paginas por jurisdiccion agregan contexto local real para no depender de una unica pagina generica.

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

## Webhooks

Los resultados asincronicos pueden recibirse por webhook firmado con HMAC SHA-256. Guardar `requestId`, validar `x-patente-signature` y usar `Idempotency-Key` para reintentos seguros.

## Confianza operativa

- 109 jurisdicciones publicadas en patente.ar para busquedas de multas por patente.
- Endpoint unico con API key por producto, idempotencia y trazabilidad.
- Webhook firmado para flujos asincronicos y auditoria por request.


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


## Links

- Producto comercial: [https://patente.ar/api-multas](https://patente.ar/api-multas)
- Crear cuenta: [https://patente.ar/registro](https://patente.ar/registro)
- Habilitar API: [https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- Playground: [https://patente.ar/desarrolladores/api?tab=playground](https://patente.ar/desarrolladores/api?tab=playground)
- Sitio principal: [https://patente.ar](https://patente.ar)
- Paginas por jurisdiccion: [jurisdicciones](./jurisdicciones/)
- Repositorio: [https://github.com/patente-ar/api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina)
