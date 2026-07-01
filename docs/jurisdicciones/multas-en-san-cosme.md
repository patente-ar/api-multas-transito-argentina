---
title: "API multas en San Cosme por patente"
description: "Documentacion para integrar consulta de multas de transito en San Cosme por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-san-cosme/
---

# API multas en San Cosme por patente

Consultá tus multas de tránsito en San Cosme por patente y revisá qué organismo interviene, cómo seguir el pago y dónde presentar un descargo.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-san-cosme`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-san-cosme`.

## Resumen local

Consultá multas de tránsito en San Cosme por patente. Información oficial, pago, descargos y controles de rutas/SINAI.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | San Cosme |
| Pagina publica | [patente.ar/multas-en-san-cosme](https://patente.ar/multas-en-san-cosme) |
| Slug publico | multas-en-san-cosme |
| Referencia de integracion | infracciones-san-cosme |
| Ultima actualizacion | 2026-06-30 |
| Organismo o fuente | Juzgado Administrativo de Faltas de San Cosme |
| Host oficial | munired.mcypcorrientes.gob.ar |

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
Idempotency-Key: multas-en-san-cosme-demo-001
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
- Jurisdicción declarada para San Cosme y provincia asociada
- Organismo o autoridad que interviene en la infracción cuando el proveedor lo devuelve
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales publicados por la jurisdicción consultada

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.


## Fuente local y canales oficiales

- Organismo o fuente informativa: Juzgado Administrativo de Faltas de San Cosme
- Direccion publicada: No publicada en la fuente oficial consultada; verificar el dato vigente en Munired Corrientes - San Cosme antes de gestionar un acta.
- Horario publicado: No publicada en la fuente oficial consultada; verificar el dato vigente en Munired Corrientes - San Cosme antes de gestionar un acta.
- Telefono o canal publicado: No publicada en la fuente oficial consultada; verificar el dato vigente en Munired Corrientes - San Cosme antes de gestionar un acta.
- Sitio oficial: [munired.mcypcorrientes.gob.ar](https://munired.mcypcorrientes.gob.ar/municipios-de-corrientes/san-cosme)


## Contexto del organismo

Munired Corrientes - San Cosme es la fuente oficial usada para esta landing. Si una multa fue emitida por el Municipio de San Cosme, el trámite de pago, liquidación o descargo debe seguir el canal oficial indicado por el organismo emisor. Cuando la fuente no publica un juzgado específico, Patente.ar lo deja explicitado para no inventar datos administrativos.


## Pago online

No se confirmó un portal oficial único de pago online para todas las multas de San Cosme. Si existe liquidación digital, usá únicamente el enlace publicado por Munired Corrientes - San Cosme, SINAI o el organismo emisor del acta.


## Pago presencial

La fuente oficial consultada no publica en forma suficiente un punto presencial único para todas las actas de San Cosme. Presentate solo ante el canal indicado por Munired Corrientes - San Cosme o por la notificación recibida, con dominio, DNI y número de acta.


## Pago voluntario o descuento

El pago voluntario o descuento por pronto pago depende de la liquidación oficial, la fecha de notificación y la normativa aplicable al acta concreta.


## Descargo

Si considerás que una multa en San Cosme fue mal labrada o tenés documentación para impugnarla, presentá el descargo por el canal oficial de Juzgado Administrativo de Faltas de San Cosme o por el medio indicado en la notificación. Antes de iniciar el trámite, consultá la patente en Patente.ar para ubicar las actas disponibles.


## Pasos de descargo

- **Identificá el acta:** Reuní número de acta, dominio, fecha de infracción y organismo emisor.
- **Prepará la documentación:** Tené a mano DNI, licencia, cédula o título del vehículo y la prueba que respalde tu presentación.
- **Presentá el descargo:** Usá el canal oficial publicado por Munired Corrientes - San Cosme o el que indique la notificación recibida.
- **Seguimiento:** Guardá constancia de la presentación y consultá el estado por número de expediente, acta o dominio.


## Plazos

Los plazos para pagar, adherir a pago voluntario o presentar descargo en San Cosme dependen de la notificación y de la normativa aplicable a la autoridad que emitió el acta. Usá siempre el plazo que figure en la liquidación oficial.


## Plazos operativos

- **Pago voluntario:** Si la autoridad lo habilita, el vencimiento y descuento aparecen en la liquidación oficial.
- **Descargo:** El plazo corre desde la notificación del acta o desde la fecha indicada por el organismo emisor.
- **Prescripción:** La prescripción depende del tipo de falta y de la normativa nacional, provincial o municipal aplicable.


## Rutas, controles y SINAI

Si la infracción fue labrada en rutas nacionales, provinciales o por una autoridad distinta a Juzgado Administrativo de Faltas de San Cosme, puede no tramitarse por el canal local de San Cosme. En esos casos conviene consultar SINAI o el organismo emisor que figure en el acta. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


## Controles frecuentes

- Foto-radares
- Exceso de velocidad en rutas
- Controles provinciales o nacionales



## Compra venta y riesgo operativo

Si estás por comprar o vender un vehículo vinculado a San Cosme, consultá multas pendientes antes de cerrar la operación. Las infracciones impagas pueden complicar transferencias, renovar documentación o generar costos no previstos.


## Puntos a revisar antes de operar

- Las multas pendientes pueden aparecer al transferir el vehículo
- El comprador puede recibir una deuda que no estaba contemplada en el precio
- Consultar la patente antes de firmar evita costos y demoras administrativas


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar, con formato viejo o Mercosur.
- **Consulta por jurisdicción:** Patente.ar deja preparada la consulta para el Municipio de San Cosme y cruza el dominio con otras jurisdicciones integradas.
- **Revisá el detalle:** Cuando hay actas disponibles, vas a ver fecha, motivo, estado, monto informado y organismo emisor.
- **Usá el canal oficial:** Para pagar, pedir una liquidación o presentar descargo, verificá siempre el canal oficial publicado por Munired Corrientes - San Cosme.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Zonas de San Cosme

Esta guía aplica para infracciones de tránsito vinculadas con la jurisdicción local

- Zona urbana de San Cosme
- Accesos a San Cosme
- Calles y avenidas principales de San Cosme
- Rutas cercanas en Corrientes
- Barrios y parajes vinculados a San Cosme


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Curuzú Cuatiá por patente](https://patente.ar/multas-en-curuzu-cuatia)
- [Consultar multas en Manuel Derqui por patente](https://patente.ar/multas-en-manuel-derqui)
- [Consultar multas en Saladas por patente](https://patente.ar/multas-en-saladas)
- [Consultar multas en San Lorenzo por patente](https://patente.ar/multas-en-san-lorenzo)
- [Consultar multas en Tabay por patente](https://patente.ar/multas-en-tabay)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas en San Cosme por patente?

Ingresá el dominio en Patente.ar. Si la jurisdicción devuelve datos para San Cosme, vas a ver las infracciones disponibles y el organismo que interviene.

### ¿Qué organismo gestiona las multas en San Cosme?

Las actas se gestionan por el organismo emisor. Para San Cosme, esta landing usa como fuente oficial Munired Corrientes - San Cosme; las infracciones de rutas o controles nacionales pueden corresponder a SINAI u otra autoridad.

### ¿Puedo pagar multas de San Cosme online?

Usá solo canales oficiales publicados por Munired Corrientes - San Cosme, SINAI o el organismo que figure en el acta. Si Patente.ar no recibe un portal de pago confirmado, no inventa enlaces de pago.

## Probar San Cosme en Playground

Para validar una consulta de multas en San Cosme, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en San Cosme](https://patente.ar/multas-en-san-cosme)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
