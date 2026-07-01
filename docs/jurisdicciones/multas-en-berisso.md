---
title: "API multas en Berisso por patente"
description: "Documentacion para integrar consulta de multas de transito en Berisso por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-berisso/
---

# API multas en Berisso por patente

Consultá gratis tus multas de tránsito en Berisso en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-berisso`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-berisso`.

## Resumen local

Consultá gratis multas de tránsito en Berisso por patente. Juzgado de Faltas Municipal, descargo en 5 días hábiles, SINAI.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Berisso |
| Pagina publica | [patente.ar/multas-en-berisso](https://patente.ar/multas-en-berisso) |
| Slug publico | multas-en-berisso |
| Referencia de integracion | infracciones-berisso |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Juzgado de Faltas Municipal de Berisso |
| Host oficial | berisso.gob.ar |

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
Idempotency-Key: multas-en-berisso-demo-001
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

- Organismo o fuente informativa: Juzgado de Faltas Municipal de Berisso
- Direccion publicada: Montevideo y Calle 17, Berisso (verificar dirección actualizada)
- Horario publicado: verificar
- Telefono o canal publicado: (0221) 461-7362
- Sitio oficial: [berisso.gob.ar](https://www.berisso.gob.ar)


## Contexto del organismo

El Juzgado de Faltas Municipal de Berisso es el organismo encargado de gestionar las infracciones de tránsito cometidas dentro del partido. Allí se pueden realizar descargos, consultar el estado de actas y gestionar el pago de multas. Si preferís evitar la fila, consultá gratis tus multas en Berisso online desde Patente.ar antes de acercarte.


## Pago online

La existencia de pago online de multas en Berisso debe verificarse en el sitio oficial berisso.gob.ar. El trámite suele realizarse de forma presencial.


## Pago presencial

Podés acercarte al Juzgado de Faltas Municipal de Berisso en el horario de atención. Se aceptan pagos según las modalidades habilitadas por la Tesorería Municipal.


## Pago voluntario o descuento

Las condiciones de pago voluntario y descuentos por pronto pago en Berisso deben verificarse directamente en el Juzgado de Faltas.


## Descargo

Si considerás que una multa fue mal labrada o tenés argumentos para impugnarla, podés presentar un descargo ante Juzgado de Faltas Municipal. Antes de ir, consultá gratis tus multas en Berisso desde Patente.ar para tener el detalle de cada acta. El procedimiento general es:


## Pasos de descargo

- **Presentarte dentro del plazo:** Tenés un plazo de 5 días hábiles desde la notificación del acta para presentar el descargo.
- **Reunir la documentación:** Llevá copia del acta de infracción, DNI, licencia de conducir y toda la documentación que respalde tu descargo.
- **Presentar el escrito:** Podés redactar el descargo por escrito explicando los motivos y presentarlo en mesa de entradas de Juzgado de Faltas Municipal.
- **Resolución:** Juzgado de Faltas Municipal evaluará tu descargo y emitirá una resolución. En caso de rechazo, podés apelar ante la instancia correspondiente.


## Plazos

Las multas de tránsito en Berisso siguen los plazos establecidos por la normativa provincial (Ley 13.927 de la Provincia de Buenos Aires) y la ordenanza municipal vigente.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta (Ley 13.927).
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves desde la fecha del acta (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves (Ley Nacional 24.449, art. 89).


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan el Partido de Berisso (como la Autopista Buenos Aires - La Plata o la Ruta Provincial 11), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en Juzgado de Faltas Municipal. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Berisso, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Juzgado de Faltas Municipal de Berisso, Buenos Aires.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Berisso y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Localidades relacionadas

- Berisso
- Los Talas
- Villa Argüello
- Villa Progreso
- Villa Nueva


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Berisso?

Podés consultar si tu vehículo tiene multas de tránsito en Berisso ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Juzgado de Faltas Municipal y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Berisso?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Berisso por DNI?

Actualmente, la consulta de multas en Berisso se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Juzgado de Faltas Municipal con tu DNI.

## Probar Berisso en Playground

Para validar una consulta de multas en Berisso, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Berisso](https://patente.ar/multas-en-berisso)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
