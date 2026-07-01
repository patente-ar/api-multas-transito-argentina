---
title: "API multas en Tabay por patente"
description: "Documentacion para integrar consulta de multas de transito en Tabay por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-tabay/
---

# API multas en Tabay por patente

Consultá tus multas de tránsito en Tabay por patente y revisá qué organismo interviene, cómo seguir el pago y dónde presentar un descargo.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-tabay`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-tabay`.

## Resumen local

Consultá multas de tránsito en Tabay por patente. Información oficial, pago, descargos y controles de rutas/SINAI.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Tabay |
| Pagina publica | [patente.ar/multas-en-tabay](https://patente.ar/multas-en-tabay) |
| Slug publico | multas-en-tabay |
| Referencia de integracion | infracciones-tabay |
| Ultima actualizacion | 2026-06-30 |
| Organismo o fuente | Juzgado Administrativo de Faltas de Tabay |
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
Idempotency-Key: multas-en-tabay-demo-001
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
- Jurisdicción declarada para Tabay y provincia asociada
- Organismo o autoridad que interviene en la infracción cuando el proveedor lo devuelve
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales publicados por la jurisdicción consultada

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.


## Fuente local y canales oficiales

- Organismo o fuente informativa: Juzgado Administrativo de Faltas de Tabay
- Direccion publicada: No publicada en la fuente oficial consultada; verificar el dato vigente en Munired Corrientes - Tabay antes de gestionar un acta.
- Horario publicado: No publicada en la fuente oficial consultada; verificar el dato vigente en Munired Corrientes - Tabay antes de gestionar un acta.
- Telefono o canal publicado: No publicada en la fuente oficial consultada; verificar el dato vigente en Munired Corrientes - Tabay antes de gestionar un acta.
- Sitio oficial: [munired.mcypcorrientes.gob.ar](https://munired.mcypcorrientes.gob.ar/municipios-de-corrientes/tabay)


## Contexto del organismo

Munired Corrientes - Tabay es la fuente oficial usada para esta landing. Si una multa fue emitida por el Municipio de Tabay, el trámite de pago, liquidación o descargo debe seguir el canal oficial indicado por el organismo emisor. Cuando la fuente no publica un juzgado específico, Patente.ar lo deja explicitado para no inventar datos administrativos.


## Pago online

No se confirmó un portal oficial único de pago online para todas las multas de Tabay. Si existe liquidación digital, usá únicamente el enlace publicado por Munired Corrientes - Tabay, SINAI o el organismo emisor del acta.


## Pago presencial

La fuente oficial consultada no publica en forma suficiente un punto presencial único para todas las actas de Tabay. Presentate solo ante el canal indicado por Munired Corrientes - Tabay o por la notificación recibida, con dominio, DNI y número de acta.


## Pago voluntario o descuento

El pago voluntario o descuento por pronto pago depende de la liquidación oficial, la fecha de notificación y la normativa aplicable al acta concreta.


## Descargo

Si considerás que una multa en Tabay fue mal labrada o tenés documentación para impugnarla, presentá el descargo por el canal oficial de Juzgado Administrativo de Faltas de Tabay o por el medio indicado en la notificación. Antes de iniciar el trámite, consultá la patente en Patente.ar para ubicar las actas disponibles.


## Pasos de descargo

- **Identificá el acta:** Reuní número de acta, dominio, fecha de infracción y organismo emisor.
- **Prepará la documentación:** Tené a mano DNI, licencia, cédula o título del vehículo y la prueba que respalde tu presentación.
- **Presentá el descargo:** Usá el canal oficial publicado por Munired Corrientes - Tabay o el que indique la notificación recibida.
- **Seguimiento:** Guardá constancia de la presentación y consultá el estado por número de expediente, acta o dominio.


## Plazos

Los plazos para pagar, adherir a pago voluntario o presentar descargo en Tabay dependen de la notificación y de la normativa aplicable a la autoridad que emitió el acta. Usá siempre el plazo que figure en la liquidación oficial.


## Plazos operativos

- **Pago voluntario:** Si la autoridad lo habilita, el vencimiento y descuento aparecen en la liquidación oficial.
- **Descargo:** El plazo corre desde la notificación del acta o desde la fecha indicada por el organismo emisor.
- **Prescripción:** La prescripción depende del tipo de falta y de la normativa nacional, provincial o municipal aplicable.


## Rutas, controles y SINAI

Si la infracción fue labrada en rutas nacionales, provinciales o por una autoridad distinta a Juzgado Administrativo de Faltas de Tabay, puede no tramitarse por el canal local de Tabay. En esos casos conviene consultar SINAI o el organismo emisor que figure en el acta. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


## Controles frecuentes

- Foto-radares
- Exceso de velocidad en rutas
- Controles provinciales o nacionales



## Compra venta y riesgo operativo

Si estás por comprar o vender un vehículo vinculado a Tabay, consultá multas pendientes antes de cerrar la operación. Las infracciones impagas pueden complicar transferencias, renovar documentación o generar costos no previstos.


## Puntos a revisar antes de operar

- Las multas pendientes pueden aparecer al transferir el vehículo
- El comprador puede recibir una deuda que no estaba contemplada en el precio
- Consultar la patente antes de firmar evita costos y demoras administrativas


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar, con formato viejo o Mercosur.
- **Consulta por jurisdicción:** Patente.ar deja preparada la consulta para el Municipio de Tabay y cruza el dominio con otras jurisdicciones integradas.
- **Revisá el detalle:** Cuando hay actas disponibles, vas a ver fecha, motivo, estado, monto informado y organismo emisor.
- **Usá el canal oficial:** Para pagar, pedir una liquidación o presentar descargo, verificá siempre el canal oficial publicado por Munired Corrientes - Tabay.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Zonas de Tabay

Esta guía aplica para infracciones de tránsito vinculadas con la jurisdicción local

- Zona urbana de Tabay
- Accesos a Tabay
- Calles y avenidas principales de Tabay
- Rutas cercanas en Corrientes
- Barrios y parajes vinculados a Tabay


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Curuzú Cuatiá por patente](https://patente.ar/multas-en-curuzu-cuatia)
- [Consultar multas en Manuel Derqui por patente](https://patente.ar/multas-en-manuel-derqui)
- [Consultar multas en Saladas por patente](https://patente.ar/multas-en-saladas)
- [Consultar multas en San Cosme por patente](https://patente.ar/multas-en-san-cosme)
- [Consultar multas en San Lorenzo por patente](https://patente.ar/multas-en-san-lorenzo)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas en Tabay por patente?

Ingresá el dominio en Patente.ar. Si la jurisdicción devuelve datos para Tabay, vas a ver las infracciones disponibles y el organismo que interviene.

### ¿Qué organismo gestiona las multas en Tabay?

Las actas se gestionan por el organismo emisor. Para Tabay, esta landing usa como fuente oficial Munired Corrientes - Tabay; las infracciones de rutas o controles nacionales pueden corresponder a SINAI u otra autoridad.

### ¿Puedo pagar multas de Tabay online?

Usá solo canales oficiales publicados por Munired Corrientes - Tabay, SINAI o el organismo que figure en el acta. Si Patente.ar no recibe un portal de pago confirmado, no inventa enlaces de pago.

## Probar Tabay en Playground

Para validar una consulta de multas en Tabay, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Tabay](https://patente.ar/multas-en-tabay)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
