---
title: "API multas en General Levalle por patente"
description: "Documentacion para integrar consulta de multas de transito en General Levalle por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-general-levalle/
---

# API multas en General Levalle por patente

Consultá tus multas de tránsito en General Levalle por patente y revisá qué organismo interviene, cómo seguir el pago y dónde presentar un descargo.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-general-levalle`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-general-levalle`.

## Resumen local

Consultá multas de tránsito en General Levalle por patente. Información oficial, pago, descargos y controles de rutas/SINAI.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | General Levalle |
| Pagina publica | [patente.ar/multas-en-general-levalle](https://patente.ar/multas-en-general-levalle) |
| Slug publico | multas-en-general-levalle |
| Referencia de integracion | infracciones-general-levalle |
| Ultima actualizacion | 2026-06-30 |
| Organismo o fuente | Juzgado Administrativo de Faltas de General Levalle |
| Host oficial | generallevalle.gob.ar |

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
Idempotency-Key: multas-en-general-levalle-demo-001
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
- Jurisdicción declarada para General Levalle y provincia asociada
- Organismo o autoridad que interviene en la infracción cuando el proveedor lo devuelve
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales publicados por la jurisdicción consultada

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.


## Fuente local y canales oficiales

- Organismo o fuente informativa: Juzgado Administrativo de Faltas de General Levalle
- Direccion publicada: No publicada en la fuente oficial consultada; verificar el dato vigente en Municipalidad de General Levalle antes de gestionar un acta.
- Horario publicado: No publicada en la fuente oficial consultada; verificar el dato vigente en Municipalidad de General Levalle antes de gestionar un acta.
- Telefono o canal publicado: No publicada en la fuente oficial consultada; verificar el dato vigente en Municipalidad de General Levalle antes de gestionar un acta.
- Sitio oficial: [generallevalle.gob.ar](https://generallevalle.gob.ar/)


## Contexto del organismo

Municipalidad de General Levalle es la fuente oficial usada para esta landing. Si una multa fue emitida por el Municipio de General Levalle, el trámite de pago, liquidación o descargo debe seguir el canal oficial indicado por el organismo emisor. Cuando la fuente no publica un juzgado específico, Patente.ar lo deja explicitado para no inventar datos administrativos.


## Pago online

No se confirmó un portal oficial único de pago online para todas las multas de General Levalle. Si existe liquidación digital, usá únicamente el enlace publicado por Municipalidad de General Levalle, SINAI o el organismo emisor del acta.


## Pago presencial

La fuente oficial consultada no publica en forma suficiente un punto presencial único para todas las actas de General Levalle. Presentate solo ante el canal indicado por Municipalidad de General Levalle o por la notificación recibida, con dominio, DNI y número de acta.


## Pago voluntario o descuento

El pago voluntario o descuento por pronto pago depende de la liquidación oficial, la fecha de notificación y la normativa aplicable al acta concreta.


## Descargo

Si considerás que una multa en General Levalle fue mal labrada o tenés documentación para impugnarla, presentá el descargo por el canal oficial de Juzgado Administrativo de Faltas de General Levalle o por el medio indicado en la notificación. Antes de iniciar el trámite, consultá la patente en Patente.ar para ubicar las actas disponibles.


## Pasos de descargo

- **Identificá el acta:** Reuní número de acta, dominio, fecha de infracción y organismo emisor.
- **Prepará la documentación:** Tené a mano DNI, licencia, cédula o título del vehículo y la prueba que respalde tu presentación.
- **Presentá el descargo:** Usá el canal oficial publicado por Municipalidad de General Levalle o el que indique la notificación recibida.
- **Seguimiento:** Guardá constancia de la presentación y consultá el estado por número de expediente, acta o dominio.


## Plazos

Los plazos para pagar, adherir a pago voluntario o presentar descargo en General Levalle dependen de la notificación y de la normativa aplicable a la autoridad que emitió el acta. Usá siempre el plazo que figure en la liquidación oficial.


## Plazos operativos

- **Pago voluntario:** Si la autoridad lo habilita, el vencimiento y descuento aparecen en la liquidación oficial.
- **Descargo:** El plazo corre desde la notificación del acta o desde la fecha indicada por el organismo emisor.
- **Prescripción:** La prescripción depende del tipo de falta y de la normativa nacional, provincial o municipal aplicable.


## Rutas, controles y SINAI

Si la infracción fue labrada en rutas nacionales, provinciales o por una autoridad distinta a Juzgado Administrativo de Faltas de General Levalle, puede no tramitarse por el canal local de General Levalle. En esos casos conviene consultar SINAI o el organismo emisor que figure en el acta. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


## Controles frecuentes

- Foto-radares
- Exceso de velocidad en rutas
- Controles provinciales o nacionales



## Compra venta y riesgo operativo

Si estás por comprar o vender un vehículo vinculado a General Levalle, consultá multas pendientes antes de cerrar la operación. Las infracciones impagas pueden complicar transferencias, renovar documentación o generar costos no previstos.


## Puntos a revisar antes de operar

- Las multas pendientes pueden aparecer al transferir el vehículo
- El comprador puede recibir una deuda que no estaba contemplada en el precio
- Consultar la patente antes de firmar evita costos y demoras administrativas


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar, con formato viejo o Mercosur.
- **Consulta por jurisdicción:** Patente.ar deja preparada la consulta para el Municipio de General Levalle y cruza el dominio con otras jurisdicciones integradas.
- **Revisá el detalle:** Cuando hay actas disponibles, vas a ver fecha, motivo, estado, monto informado y organismo emisor.
- **Usá el canal oficial:** Para pagar, pedir una liquidación o presentar descargo, verificá siempre el canal oficial publicado por Municipalidad de General Levalle.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Zonas de General Levalle

Esta guía aplica para infracciones de tránsito vinculadas con la jurisdicción local

- Zona urbana de General Levalle
- Accesos a General Levalle
- Calles y avenidas principales de General Levalle
- Rutas cercanas en Córdoba
- Barrios y parajes vinculados a General Levalle


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Alcira Gigena por patente](https://patente.ar/multas-en-alcira-gigena)
- [Consultar multas en Alpa Corral por patente](https://patente.ar/multas-en-alpa-corral)
- [Consultar multas en Alta Gracia por patente](https://patente.ar/multas-en-alta-gracia)
- [Consultar multas en Arias por patente](https://patente.ar/multas-en-arias)
- [Consultar multas en Canals por patente](https://patente.ar/multas-en-canals)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas en General Levalle por patente?

Ingresá el dominio en Patente.ar. Si la jurisdicción devuelve datos para General Levalle, vas a ver las infracciones disponibles y el organismo que interviene.

### ¿Qué organismo gestiona las multas en General Levalle?

Las actas se gestionan por el organismo emisor. Para General Levalle, esta landing usa como fuente oficial Municipalidad de General Levalle; las infracciones de rutas o controles nacionales pueden corresponder a SINAI u otra autoridad.

### ¿Puedo pagar multas de General Levalle online?

Usá solo canales oficiales publicados por Municipalidad de General Levalle, SINAI o el organismo que figure en el acta. Si Patente.ar no recibe un portal de pago confirmado, no inventa enlaces de pago.

## Probar General Levalle en Playground

Para validar una consulta de multas en General Levalle, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en General Levalle](https://patente.ar/multas-en-general-levalle)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
