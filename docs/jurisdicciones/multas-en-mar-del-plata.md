---
title: "API multas en Mar del Plata por patente"
description: "Documentacion para integrar consulta de multas de transito en Mar del Plata por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-mar-del-plata/
---

# API multas en Mar del Plata por patente

Consultá gratis multas municipales e infracciones de tránsito en Mar del Plata — Ingresá la patente y verificá actas pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-mar-del-plata`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-mar-del-plata`.

## Resumen local

Consultá multas municipales en Mar del Plata por patente. Tribunal Municipal de Faltas, infracciones provinciales, pago y SINAI.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Mar del Plata |
| Pagina publica | [patente.ar/multas-en-mar-del-plata](https://patente.ar/multas-en-mar-del-plata) |
| Slug publico | multas-en-mar-del-plata |
| Referencia de integracion | infracciones-mar-del-plata |
| Ultima actualizacion | 2026-06-09 |
| Organismo o fuente | Tribunal Municipal de Faltas y Juzgado Administrativo Provincial |
| Host oficial | mardelplata.gob.ar |

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
Idempotency-Key: multas-en-mar-del-plata-demo-001
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

- Verificación de infracciones de tránsito pendientes
- Detalle de cada acta o boleta
- Fecha y tipo de infracción
- Monto de la multa en Unidades Fijas (UF)
- Estado de pago y vencimientos

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.


## Fuente local y canales oficiales

- Organismo o fuente informativa: Tribunal Municipal de Faltas y Juzgado Administrativo Provincial
- Direccion publicada: Mitre 1435, Mar del Plata (Tribunal Municipal de Faltas) — 25 de Mayo 3735 (Juzgado Provincial)
- Horario publicado: Lunes a viernes de 8:30 a 13:30 hs (Municipal) / 9:00 a 14:00 hs (Provincial)
- Telefono o canal publicado: (0223) 499-6282 / 499-6283 (Municipal) — (0223) 475-1451 (Provincial)
- Sitio oficial: [mardelplata.gob.ar](https://www.mardelplata.gob.ar)


## Contexto del organismo

En Mar del Plata (Partido de General Pueyrredon), el Tribunal Municipal de Faltas (Mitre 1435) gestiona las infracciones cometidas dentro del ejido urbano. Las cometidas en rutas y autopistas son competencia del Juzgado Administrativo de Infracciones de Tránsito Provincial (25 de Mayo 3735, entre 14 de Julio y Dorrego). Si preferís evitar la fila, consultá gratis tus multas en Mar del Plata desde Patente.ar antes de acercarte.


## Pago online

Las multas provinciales se pueden consultar y pagar en infraccionesba.gba.gob.ar. Para multas municipales, verificá el portal mardelplata.gob.ar y modalidades online disponibles.


## Pago presencial

El pago presencial municipal se realiza en el Tribunal Municipal de Faltas (Mitre 1435) y el provincial en el Juzgado Administrativo (25 de Mayo 3735). Se aceptan los medios habilitados por cada Tesorería.


## Pago voluntario o descuento

Las condiciones de pago voluntario y descuentos en Mar del Plata varían según se trate de multa municipal o provincial; verificá en cada organismo al momento del pago.


## Descargo

Si considerás que una multa fue mal labrada o tenés argumentos para impugnarla, podés presentar un descargo ante Tribunal Municipal de Faltas. Antes de ir, consultá gratis tus multas en Mar del Plata desde Patente.ar para tener el detalle de cada acta. El procedimiento general es:


## Pasos de descargo

- **Presentarte dentro del plazo:** Tenés un plazo de 5 días hábiles desde la notificación del acta para presentar el descargo.
- **Reunir la documentación:** Llevá copia del acta de infracción, DNI, licencia de conducir y toda la documentación que respalde tu descargo.
- **Presentar el escrito:** Podés redactar el descargo por escrito explicando los motivos y presentarlo en mesa de entradas de Tribunal Municipal de Faltas.
- **Resolución:** Tribunal Municipal de Faltas evaluará tu descargo y emitirá una resolución. En caso de rechazo, podés apelar ante la instancia correspondiente.


## Plazos

Las multas de tránsito en Mar del Plata siguen los plazos establecidos por la normativa provincial (Ley 13.927 de la Provincia de Buenos Aires) y la ordenanza municipal vigente.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta (Ley 13.927).
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves desde la fecha del acta (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves (Ley Nacional 24.449, art. 89).


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan Mar del Plata (como la Ruta Nacional 226, la Ruta Provincial 11 o la Ruta Provincial 88), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en Tribunal Municipal de Faltas. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Mar del Plata, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Tribunal Municipal de Faltas de Mar del Plata, Buenos Aires.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Mar del Plata y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Barrios y zonas de Mar del Plata

Esta guía aplica para infracciones de tránsito en toda la ciudad

- Centro
- Punta Mogotes
- La Perla
- Playa Grande
- Los Troncos
- Constitución
- Sierra de los Padres
- Batán


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo consultar multas municipales en Mar del Plata por patente?

Podés consultar multas municipales e infracciones en Mar del Plata ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las actas registradas en Tribunal Municipal de Faltas y te muestra el detalle de cada infracción pendiente.

### ¿Qué necesito para consultar multas en Mar del Plata?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Mar del Plata por DNI?

Actualmente, la consulta de multas en Mar del Plata se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Tribunal Municipal de Faltas con tu DNI.

## Probar Mar del Plata en Playground

Para validar una consulta de multas en Mar del Plata, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Mar del Plata](https://patente.ar/multas-en-mar-del-plata)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
