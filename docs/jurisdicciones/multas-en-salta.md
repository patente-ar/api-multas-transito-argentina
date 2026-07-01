---
title: "API multas en Salta por patente"
description: "Documentacion para integrar consulta de multas de transito en Salta por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-salta/
---

# API multas en Salta por patente

Consultá gratis tus multas de tránsito en Salta en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-salta`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-salta`.

## Resumen local

Consultá gratis multas de tránsito en Salta por patente. Tribunal Administrativo de Faltas, pago online ARMSa, descuento 50%.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Salta |
| Pagina publica | [patente.ar/multas-en-salta](https://patente.ar/multas-en-salta) |
| Slug publico | multas-en-salta |
| Referencia de integracion | infracciones-salta |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Tribunal Administrativo de Faltas de la Municipalidad de Salta |
| Host oficial | municipalidadsalta.gob.ar |

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
Idempotency-Key: multas-en-salta-demo-001
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

- Organismo o fuente informativa: Tribunal Administrativo de Faltas de la Municipalidad de Salta
- Direccion publicada: Av. Paraguay N°1240, Salta
- Horario publicado: Lunes a viernes de 8:00 a 20:00 hs
- Telefono o canal publicado: (0387) 416-0900 int. 1122
- Sitio oficial: [municipalidadsalta.gob.ar](https://www.municipalidadsalta.gob.ar)


## Contexto del organismo

El Tribunal Administrativo de Faltas de la Municipalidad de Salta es el organismo que juzga las infracciones al Código de Faltas municipal y las contravenciones viales en la ciudad capital. Funciona con 5 Juzgados de Faltas y la Cámara de Apelaciones. En el resto de la Provincia, cada Juzgado de Faltas Municipal gestiona las multas de su ejido urbano. Si preferís evitar la fila, consultá gratis tus multas en Salta online desde Patente.ar antes de acercarte.


## Pago online

La Municipalidad de Salta ofrece consulta y pago online a través de armsa.dgrmsalta.gov.ar. Permite consultar por dominio, generar boleta y abonar con tarjeta. Disponible las 24 hs.


## Pago presencial

Podés acercarte al Tribunal Administrativo de Faltas (Av. Paraguay 1240) en horario de atención. El pago se acepta en cajas municipales, Banco Macro, Rapipago, Pago Fácil y Mercado Pago, en efectivo, débito o crédito.


## Pago voluntario o descuento

La Ciudad de Salta ofrece un descuento del 50% sobre el monto mínimo de la multa por Pago Voluntario para faltas leves, dentro del plazo establecido tras la notificación.


## Descargo

Si considerás que una multa fue mal labrada, podés presentar un descargo ante el Tribunal Administrativo de Faltas. Antes de iniciar, consultá gratis tus multas en Salta desde Patente.ar.


## Pasos de descargo

- **Presentarte dentro del plazo:** Dentro de los 5 días hábiles desde la realización de la multa para presentar el descargo.
- **Reunir la documentación:** Nota de descargo, DNI del titular, cédula verde, título automotor, licencia (si corresponde), seguro y prueba que respalde tu defensa.
- **Presentar el descargo:** Vía mail al Juzgado actuante (tribunaldefaltas01..05@municipalidadsalta.gob.ar) o presencialmente en Av. Paraguay 1240 con turno previo (Whyline).
- **Resolución:** El Juzgado emite resolución que se notifica por el medio fijado. En caso de rechazo, podés apelar ante la Cámara de Apelaciones del Tribunal.


## Plazos

Las multas de tránsito en la Provincia de Salta siguen los plazos establecidos por la Ordenanza 14.136/11 (Código de Faltas Municipal) y la Ley Nacional 24.449.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la realización de la multa.
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves.


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan la Provincia de Salta (como la Ruta Nacional 9, la Ruta Nacional 51, la Ruta Nacional 34 o la Ruta Nacional 40), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en el Tribunal Administrativo de Faltas. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Salta, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Tribunal Administrativo de Faltas de la Provincia de Salta.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Salta y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Departamentos y ciudades de la Provincia de Salta

Esta guía aplica para infracciones de tránsito en toda la Provincia de Salta

- Salta (Capital)
- San Ramón de la Nueva Orán
- Tartagal
- Metán
- Cafayate
- Rosario de la Frontera
- General Güemes
- Embarcación
- Cerrillos
- Vaqueros


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Salta?

Podés consultar si tu vehículo tiene multas de tránsito en Salta ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Tribunal Administrativo de Faltas y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Salta?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Salta por DNI?

Actualmente, la consulta de multas en Salta se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Tribunal Administrativo de Faltas con tu DNI.

## Probar Salta en Playground

Para validar una consulta de multas en Salta, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Salta](https://patente.ar/multas-en-salta)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
