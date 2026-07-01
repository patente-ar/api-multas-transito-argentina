---
title: "API multas en Córdoba Capital por patente"
description: "Documentacion para integrar consulta de multas de transito en Córdoba Capital por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-cordoba-municipalidad/
---

# API multas en Córdoba Capital por patente

Consultá gratis tus multas de tránsito en Córdoba Capital en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-cordoba-municipalidad`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-cordoba-municipalidad`.

## Resumen local

Consultá gratis multas de tránsito en Córdoba Capital por patente. Tribunal Administrativo de Faltas, descargo online, pago voluntario 40%.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Córdoba Capital |
| Pagina publica | [patente.ar/multas-en-cordoba-municipalidad](https://patente.ar/multas-en-cordoba-municipalidad) |
| Slug publico | multas-en-cordoba-municipalidad |
| Referencia de integracion | infracciones-cordoba-municipalidad |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Tribunal Administrativo Municipal de Faltas de la Ciudad de Córdoba |
| Host oficial | tribunaldefaltas.cordoba.gov.ar |

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
Idempotency-Key: multas-en-cordoba-municipalidad-demo-001
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

- Organismo o fuente informativa: Tribunal Administrativo Municipal de Faltas de la Ciudad de Córdoba
- Direccion publicada: Avellaneda 439, B° Centro, Córdoba
- Horario publicado: Lunes a viernes de 7:30 a 19:30 hs
- Telefono o canal publicado: (0351) 428-5600 int. 3119 / WhatsApp (0351) 6100527 / 6100528
- Sitio oficial: [tribunaldefaltas.cordoba.gov.ar](https://tribunaldefaltas.cordoba.gov.ar)


## Contexto del organismo

El Tribunal Administrativo Municipal de Faltas de la Ciudad de Córdoba es el organismo encargado de juzgar las infracciones al Código de Convivencia Ciudadana, incluidas las faltas de tránsito en el ejido urbano. Cuenta con Portal Ciudadano de Descargos online, Centro de Monitoreo Urbano y Cámara de Apelaciones de Faltas. Si preferís evitar la fila, consultá gratis tus multas en Córdoba Capital online desde Patente.ar antes de acercarte.


## Pago online

La Municipalidad de Córdoba ofrece consulta y pago online de multas a través de tribunaldefaltas.cordoba.gov.ar y la app MiDocta, con tarjeta de crédito, débito o boleta para pago bancario. Disponible las 24 hs.


## Pago presencial

Podés acercarte al Tribunal Administrativo de Faltas (Avellaneda 439) en horario de atención. También se acepta pago en Banco de Córdoba y entidades habilitadas con la boleta generada online.


## Pago voluntario o descuento

La Ciudad de Córdoba aplica un descuento del 40% sobre el monto de la multa por Pago Voluntario si abonás dentro del plazo establecido tras la notificación. Si presentás descargo, perdés el beneficio.


## Descargo

Si considerás que una multa fue mal labrada, podés presentar un descargo a través del Portal Ciudadano de Descargos en tribunaldefaltas.cordoba.gov.ar o presencialmente en Avellaneda 439. Antes de iniciar, consultá gratis tus multas en Córdoba Capital desde Patente.ar.


## Pasos de descargo

- **Presentarte dentro del plazo:** 5 días hábiles desde la notificación del acta para presentar el descargo.
- **Reunir la documentación:** DNI, cédula del vehículo, licencia de conducir y toda documentación que respalde tu defensa.
- **Presentar el descargo:** Online en el Portal Ciudadano de Descargos (firma digital) o presencial en Avellaneda 439, mesa de entradas del Tribunal.
- **Resolución y apelación:** El Juez de Faltas evaluará el descargo. En caso de rechazo, podés apelar ante la Cámara de Apelaciones de Faltas y, en última instancia, ante el Poder Judicial provincial.


## Plazos

Las multas de tránsito en la Ciudad de Córdoba siguen los plazos establecidos por la normativa municipal vigente y la Ley Nacional 24.449.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta.
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves (Ley Nacional 24.449).


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan la ciudad de Córdoba (como la Autopista Córdoba - Carlos Paz, la Avenida de Circunvalación o las rutas que ingresan a la ciudad), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en el Tribunal Administrativo de Faltas. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Córdoba Capital, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Tribunal Administrativo Municipal de Faltas de la ciudad de Córdoba.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Córdoba Capital y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Barrios y zonas de la Ciudad de Córdoba

Esta guía aplica para infracciones de tránsito en toda la Ciudad de Córdoba

- Centro
- Nueva Córdoba
- Cerro de las Rosas
- Alberdi
- Alta Córdoba
- Güemes
- General Paz
- Centro Norte
- Argüello
- Villa Allende Parque


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Córdoba Capital?

Podés consultar si tu vehículo tiene multas de tránsito en Córdoba Capital ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Tribunal Administrativo Municipal de Faltas y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Córdoba Capital?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Córdoba Capital por DNI?

Actualmente, la consulta de multas en Córdoba Capital se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Tribunal Administrativo Municipal de Faltas con tu DNI.

## Probar Córdoba Capital en Playground

Para validar una consulta de multas en Córdoba Capital, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Córdoba Capital](https://patente.ar/multas-en-cordoba-municipalidad)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
