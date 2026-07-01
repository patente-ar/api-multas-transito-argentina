---
title: "API multas en Quilmes por patente"
description: "Documentacion para integrar consulta de multas de transito en Quilmes por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-quilmes/
---

# API multas en Quilmes por patente

Consultá tus multas de tránsito en Quilmes por patente y revisá qué organismo interviene, cómo pagar y dónde presentar un descargo.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-quilmes`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-quilmes`.

## Resumen local

Consultá multas de tránsito en Quilmes por patente. Datos de organismo local, pago, descargos y rutas/SINAI con fuentes oficiales.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Quilmes |
| Pagina publica | [patente.ar/multas-en-quilmes](https://patente.ar/multas-en-quilmes) |
| Slug publico | multas-en-quilmes |
| Referencia de integracion | infracciones-quilmes |
| Ultima actualizacion | 2026-05-20 |
| Organismo o fuente | Juzgado Municipal de Faltas de Quilmes |
| Host oficial | quilmes.gov.ar |

## Endpoint API

```text
POST https://api.patente.ar/v1/consultas
```

El producto queda definido por la API key emitida para `infracciones`. Para pruebas, usa el contrato OpenAPI del repo y evita guardar credenciales o respuestas reales en logs.

## Request de ejemplo

```http
POST /v1/consultas HTTP/1.1
Host: api.patente.ar
Authorization: Bearer pa_live_xxx
Content-Type: application/json
Idempotency-Key: multas-en-quilmes-demo-001
x-token: orden-externa-001
```

```json
{
  "patente": [
    "AB123CD"
  ]
}
```

## Que datos puede integrar

- Consulta de infracciones por dominio del vehículo
- Organismo o autoridad que interviene en la infracción
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales de pago o atención publicados por la jurisdicción
- Diferencia entre actas municipales y controles provinciales o nacionales

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.


## Fuente local y canales oficiales

- Organismo o fuente informativa: Juzgado Municipal de Faltas de Quilmes
- Direccion publicada: Alberdi 500, Quilmes, Buenos Aires
- Horario publicado: Atención municipal en días hábiles; consultar turnos y canales vigentes en quilmes.gov.ar
- Telefono o canal publicado: 0800-999-5656
- Sitio oficial: [quilmes.gov.ar](https://www.quilmes.gov.ar/)


## Contexto del organismo

Quilmes publica canales de atención municipal y trámites vinculados con faltas e infracciones. Las actas locales se gestionan ante el Juzgado Municipal de Faltas o los canales oficiales indicados por el municipio.


## Pago online

Quilmes publica trámites digitales y canales de atención municipal. Para infracciones provinciales o nacionales, usá el portal del organismo emisor o SINAI.


## Pago presencial

Las actas municipales se gestionan por el Juzgado Municipal de Faltas o los canales oficiales de Quilmes. Llevá dominio, DNI y número de acta.


## Pago voluntario o descuento

El pago voluntario, cuando corresponde, aparece en la liquidación oficial de la infracción.


## Descargo

Si considerás que una multa en Quilmes fue mal labrada o tenés documentación para impugnarla, presentá el descargo por el canal oficial de Juzgado Municipal de Faltas de Quilmes. Antes de iniciar el trámite, consultá la patente en Patente.ar para ubicar las actas disponibles.


## Pasos de descargo

- **Identificá el acta:** Reuní número de acta, dominio, fecha de infracción y organismo emisor.
- **Prepará la documentación:** Tené a mano DNI, licencia, cédula o título del vehículo y la prueba que respalde tu presentación.
- **Presentá el descargo:** Usá el canal oficial de Juzgado Municipal de Faltas de Quilmes o el que indique la notificación recibida.
- **Seguimiento:** Guardá constancia de la presentación y consultá el estado por el número de expediente o acta.


## Plazos

Los plazos para pagar, adherir a pago voluntario o presentar descargo dependen de la notificación y de la normativa aplicable a la autoridad que emitió el acta. Para Quilmes, usá siempre el plazo que figure en el acta o liquidación oficial.


## Plazos operativos

- **Pago voluntario:** Si la autoridad lo habilita, el vencimiento y descuento aparecen en la liquidación oficial.
- **Descargo:** El plazo corre desde la notificación del acta o desde la fecha indicada por el organismo emisor.
- **Prescripción:** La prescripción depende del tipo de falta y de la normativa nacional, provincial o municipal aplicable.


## Rutas, controles y SINAI

Si la infracción fue labrada en rutas nacionales, provinciales o por una autoridad distinta a Juzgado Municipal de Faltas de Quilmes, puede no tramitarse por el canal municipal. En esos casos conviene consultar el sistema SINAI o el organismo emisor que figura en el acta. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


## Controles frecuentes

- Foto-radares
- Exceso de velocidad en rutas
- Controles provinciales


## Valores orientativos publicados

| Infraccion | Rango UF |
| --- | --- |
| Estacionamiento en lugar prohibido | 50 a 200 UF |
| Exceso de velocidad | 100 a 500 UF |
| No respetar semáforo en rojo | 200 a 1000 UF |
| Alcoholemia positiva | 500 a 2000 UF |
| Conducir sin licencia | 300 a 1500 UF |


## Compra venta y riesgo operativo

Si estás por comprar o vender un vehículo vinculado a Quilmes, consultá multas pendientes antes de cerrar la operación. Las infracciones impagas pueden complicar transferencias, renovar documentación o generar costos no previstos.


## Puntos a revisar antes de operar

- Las multas pendientes pueden aparecer al transferir el vehículo
- El comprador puede recibir una deuda que no estaba contemplada en el precio
- Consultar la patente antes de firmar evita costos y demoras administrativas


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar, con formato viejo o Mercosur.
- **Consulta por jurisdicción:** Patente.ar consulta las infracciones disponibles para Quilmes y las cruza con otras jurisdicciones integradas.
- **Revisá el detalle:** Cuando hay actas disponibles, vas a ver fecha, motivo, estado, monto informado y organismo emisor.
- **Usá el canal oficial:** Para pagar, pedir una liquidación o presentar descargo, seguí el canal oficial de Juzgado Municipal de Faltas de Quilmes.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Localidades relacionadas

- Quilmes Centro
- Quilmes Oeste
- Bernal
- Don Bosco
- Ezpeleta
- San Francisco Solano
- Villa La Florida
- Villa Argentina


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas en Quilmes por patente?

Ingresá el dominio en Patente.ar. Si la jurisdicción devuelve datos para Quilmes, vas a ver las infracciones disponibles y el organismo que interviene.

### ¿Qué organismo gestiona las multas en Quilmes?

Las actas municipales se canalizan por Juzgado Municipal de Faltas de Quilmes. Las infracciones de rutas o controles provinciales y nacionales pueden corresponder a otra autoridad.

### ¿Puedo pagar multas de Quilmes online?

Quilmes publica trámites digitales y canales de atención municipal. Para infracciones provinciales o nacionales, usá el portal del organismo emisor o SINAI.

## Probar Quilmes en Playground

Para validar una consulta de multas en Quilmes, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Quilmes](https://patente.ar/multas-en-quilmes)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
