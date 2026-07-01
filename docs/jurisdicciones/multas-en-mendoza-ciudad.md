---
title: "API multas en Mendoza Ciudad por patente"
description: "Documentacion para integrar consulta de multas de transito en Mendoza Ciudad por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-mendoza-ciudad/
---

# API multas en Mendoza Ciudad por patente

Consultá tus multas de tránsito en Mendoza Ciudad por patente y revisá qué organismo interviene, cómo pagar y dónde presentar un descargo.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-mendoza-ciudad`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-mendoza-ciudad`.

## Resumen local

Consultá multas de tránsito en Mendoza Ciudad por patente. Datos de organismo local, pago, descargos y rutas/SINAI con fuentes oficiales.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Mendoza Ciudad |
| Pagina publica | [patente.ar/multas-en-mendoza-ciudad](https://patente.ar/multas-en-mendoza-ciudad) |
| Slug publico | multas-en-mendoza-ciudad |
| Referencia de integracion | infracciones-mendoza-ciudad |
| Ultima actualizacion | 2026-05-20 |
| Organismo o fuente | Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza |
| Host oficial | ciudaddemendoza.gob.ar |

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
Idempotency-Key: multas-en-mendoza-ciudad-demo-001
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

- Organismo o fuente informativa: Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza
- Direccion publicada: 9 de Julio 500, Ciudad de Mendoza
- Horario publicado: Atención municipal en días hábiles; consultar turnos y canales vigentes en ciudaddemendoza.gob.ar
- Telefono o canal publicado: 147 / 0800-222-248323
- Sitio oficial: [ciudaddemendoza.gob.ar](https://ciudaddemendoza.gob.ar/)


## Contexto del organismo

La Ciudad de Mendoza publica canales oficiales para consultar y pagar multas de tránsito municipales, además de información sobre estacionamiento medido y juzgados administrativos de tránsito.


## Pago online

La Ciudad de Mendoza publica canales digitales para consultas y pagos municipales. Para actas provinciales, usá el portal de la autoridad provincial indicado en la notificación.


## Pago presencial

Las actas municipales se gestionan ante los Juzgados Administrativos de Tránsito o por los canales oficiales de la Ciudad de Mendoza.


## Pago voluntario o descuento

El beneficio de pago voluntario depende del estado del acta y debe figurar en la liquidación oficial de la Ciudad de Mendoza.


## Descargo

Si considerás que una multa en Mendoza Ciudad fue mal labrada o tenés documentación para impugnarla, presentá el descargo por el canal oficial de Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza. Antes de iniciar el trámite, consultá la patente en Patente.ar para ubicar las actas disponibles.


## Pasos de descargo

- **Identificá el acta:** Reuní número de acta, dominio, fecha de infracción y organismo emisor.
- **Prepará la documentación:** Tené a mano DNI, licencia, cédula o título del vehículo y la prueba que respalde tu presentación.
- **Presentá el descargo:** Usá el canal oficial de Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza o el que indique la notificación recibida.
- **Seguimiento:** Guardá constancia de la presentación y consultá el estado por el número de expediente o acta.


## Plazos

Los plazos para pagar, adherir a pago voluntario o presentar descargo dependen de la notificación y de la normativa aplicable a la autoridad que emitió el acta. Para Mendoza Ciudad, usá siempre el plazo que figure en el acta o liquidación oficial.


## Plazos operativos

- **Pago voluntario:** Si la autoridad lo habilita, el vencimiento y descuento aparecen en la liquidación oficial.
- **Descargo:** El plazo corre desde la notificación del acta o desde la fecha indicada por el organismo emisor.
- **Prescripción:** La prescripción depende del tipo de falta y de la normativa nacional, provincial o municipal aplicable.


## Rutas, controles y SINAI

Si la infracción fue labrada en rutas nacionales, provinciales o por una autoridad distinta a Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza, puede no tramitarse por el canal municipal. En esos casos conviene consultar el sistema SINAI o el organismo emisor que figura en el acta. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo vinculado a Mendoza Ciudad, consultá multas pendientes antes de cerrar la operación. Las infracciones impagas pueden complicar transferencias, renovar documentación o generar costos no previstos.


## Puntos a revisar antes de operar

- Las multas pendientes pueden aparecer al transferir el vehículo
- El comprador puede recibir una deuda que no estaba contemplada en el precio
- Consultar la patente antes de firmar evita costos y demoras administrativas


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar, con formato viejo o Mercosur.
- **Consulta por jurisdicción:** Patente.ar consulta las infracciones disponibles para Mendoza Ciudad y las cruza con otras jurisdicciones integradas.
- **Revisá el detalle:** Cuando hay actas disponibles, vas a ver fecha, motivo, estado, monto informado y organismo emisor.
- **Usá el canal oficial:** Para pagar, pedir una liquidación o presentar descargo, seguí el canal oficial de Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Barrios y secciones de la Ciudad de Mendoza

Esta guía aplica para infracciones de tránsito en toda la Ciudad de Mendoza

- Ciudad (Sección 1ª - Centro)
- Sección 2ª - Norte
- Sección 3ª - Oeste
- Sección 4ª - Sur
- Sección 5ª - Este
- Sección 6ª - Bombal
- Sección 7ª - Parque
- Sección 8ª - Suroeste


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas en Mendoza Ciudad por patente?

Ingresá el dominio en Patente.ar. Si la jurisdicción devuelve datos para Mendoza Ciudad, vas a ver las infracciones disponibles y el organismo que interviene.

### ¿Qué organismo gestiona las multas en Mendoza Ciudad?

Las actas municipales se canalizan por Unidad de Juzgados Administrativos de Tránsito de la Ciudad de Mendoza. Las infracciones de rutas o controles provinciales y nacionales pueden corresponder a otra autoridad.

### ¿Puedo pagar multas de Mendoza Ciudad online?

La Ciudad de Mendoza publica canales digitales para consultas y pagos municipales. Para actas provinciales, usá el portal de la autoridad provincial indicado en la notificación.

## Probar Mendoza Ciudad en Playground

Para validar una consulta de multas en Mendoza Ciudad, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Mendoza Ciudad](https://patente.ar/multas-en-mendoza-ciudad)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
