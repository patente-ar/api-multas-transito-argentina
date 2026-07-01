---
title: "API multas en La Plata por patente"
description: "Documentacion para integrar consulta de multas de transito en La Plata por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-la-plata/
---

# API multas en La Plata por patente

Consultá tus multas de tránsito en La Plata por patente y revisá qué organismo interviene, cómo seguir el pago y dónde presentar un descargo.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-la-plata`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-la-plata`.

## Resumen local

Consultá multas de tránsito en La Plata por patente. Información oficial, pago, descargos y controles de rutas/SINAI.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | La Plata |
| Pagina publica | [patente.ar/multas-en-la-plata](https://patente.ar/multas-en-la-plata) |
| Slug publico | multas-en-la-plata |
| Referencia de integracion | infracciones-la-plata |
| Ultima actualizacion | 2026-07-01 |
| Organismo o fuente | Juzgado Administrativo de Faltas de La Plata |
| Host oficial | laplata.gob.ar |

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
Idempotency-Key: multas-en-la-plata-demo-001
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
- Jurisdicción declarada para La Plata y provincia asociada
- Organismo o autoridad que interviene en la infracción cuando el proveedor lo devuelve
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales publicados por la jurisdicción consultada

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.


## Fuente local y canales oficiales

- Organismo o fuente informativa: Juzgado Administrativo de Faltas de La Plata
- Direccion publicada: Calle 48 786
- Horario publicado: Lunes a viernes de 8:00 a 15:00 hs
- Telefono o canal publicado: 0221 412-4200
- Sitio oficial: [laplata.gob.ar](https://www.laplata.gob.ar/)


## Contexto del organismo

InfraccionesBA publica juzgados municipales de faltas de La Plata para actas locales y un juzgado provincial para infracciones de PBA. Si una multa fue emitida por el Municipio de La Plata, el trámite de pago, liquidación o descargo debe seguir el canal oficial indicado por el organismo emisor.


## Pago online

No se confirmó un portal oficial único de pago online para todas las multas de La Plata. Si existe liquidación digital, usá únicamente el enlace publicado por Municipalidad de La Plata, SINAI o el organismo emisor del acta.


## Pago presencial

InfraccionesBA publica juzgados municipales de La Plata en Calle 48 786, con atención de lunes a viernes de 8:00 a 15:00 hs. Confirmá el juzgado que interviene y el medio de pago indicado en la notificación antes de concurrir.


## Pago voluntario o descuento

El pago voluntario o descuento por pronto pago depende de la liquidación oficial, la fecha de notificación y la normativa aplicable al acta concreta.


## Descargo

Si considerás que una multa en La Plata fue mal labrada o tenés documentación para impugnarla, presentá el descargo por el canal oficial de Juzgado Administrativo de Faltas de La Plata o por el medio indicado en la notificación. Antes de iniciar el trámite, consultá la patente en Patente.ar para ubicar las actas disponibles.


## Pasos de descargo

- **Identificá el acta:** Reuní número de acta, dominio, fecha de infracción y organismo emisor.
- **Prepará la documentación:** Tené a mano DNI, licencia, cédula o título del vehículo y la prueba que respalde tu presentación.
- **Presentá el descargo:** Usá el canal oficial publicado por Municipalidad de La Plata o el que indique la notificación recibida.
- **Seguimiento:** Guardá constancia de la presentación y consultá el estado por número de expediente, acta o dominio.


## Plazos

Los plazos para pagar, adherir a pago voluntario o presentar descargo en La Plata dependen de la notificación y de la normativa aplicable a la autoridad que emitió el acta. Usá siempre el plazo que figure en la liquidación oficial.


## Plazos operativos

- **Pago voluntario:** Si la autoridad lo habilita, el vencimiento y descuento aparecen en la liquidación oficial.
- **Descargo:** El plazo corre desde la notificación del acta o desde la fecha indicada por el organismo emisor.
- **Prescripción:** La prescripción depende del tipo de falta y de la normativa nacional, provincial o municipal aplicable.


## Rutas, controles y SINAI

Si la infracción fue labrada en rutas nacionales, provinciales o por una autoridad distinta a Juzgado Administrativo de Faltas de La Plata, puede no tramitarse por el canal local de La Plata. En esos casos conviene consultar SINAI o el organismo emisor que figure en el acta. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


## Controles frecuentes

- Foto-radares
- Exceso de velocidad en rutas
- Controles provinciales o nacionales



## Compra venta y riesgo operativo

Si estás por comprar o vender un vehículo vinculado a La Plata, consultá multas pendientes antes de cerrar la operación. Las infracciones impagas pueden complicar transferencias, renovar documentación o generar costos no previstos.


## Puntos a revisar antes de operar

- Las multas pendientes pueden aparecer al transferir el vehículo
- El comprador puede recibir una deuda que no estaba contemplada en el precio
- Consultar la patente antes de firmar evita costos y demoras administrativas


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar, con formato viejo o Mercosur.
- **Consulta por jurisdicción:** Patente.ar deja preparada la consulta para el Municipio de La Plata y cruza el dominio con otras jurisdicciones integradas.
- **Revisá el detalle:** Cuando hay actas disponibles, vas a ver fecha, motivo, estado, monto informado y organismo emisor.
- **Usá el canal oficial:** Para pagar, pedir una liquidación o presentar descargo, verificá siempre el canal oficial publicado por Municipalidad de La Plata.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Zonas de La Plata

Esta guía aplica para infracciones de tránsito vinculadas con la jurisdicción local

- Zona urbana de La Plata
- Accesos a La Plata
- Calles y avenidas principales de La Plata
- Rutas cercanas en Buenos Aires
- Barrios y parajes vinculados a La Plata


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Merlo por patente](https://patente.ar/multas-en-merlo)
- [Consultar multas en Necochea por patente](https://patente.ar/multas-en-necochea)
- [Consultar multas en Pilar por patente](https://patente.ar/multas-en-pilar)
- [Consultar multas en San Isidro por patente](https://patente.ar/multas-en-san-isidro)
- [Consultar multas en Alcira Gigena por patente](https://patente.ar/multas-en-alcira-gigena)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas en La Plata por patente?

Ingresá el dominio en Patente.ar. Si la jurisdicción devuelve datos para La Plata, vas a ver las infracciones disponibles y el organismo que interviene.

### ¿Qué organismo gestiona las multas en La Plata?

Las actas se gestionan por el organismo emisor. Para La Plata, esta landing usa como fuente oficial Municipalidad de La Plata; las infracciones de rutas o controles nacionales pueden corresponder a SINAI u otra autoridad.

### ¿Puedo pagar multas de La Plata online?

Usá solo canales oficiales publicados por Municipalidad de La Plata, SINAI o el organismo que figure en el acta. Si Patente.ar no recibe un portal de pago confirmado, no inventa enlaces de pago.

## Probar La Plata en Playground

Para validar una consulta de multas en La Plata, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en La Plata](https://patente.ar/multas-en-la-plata)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
