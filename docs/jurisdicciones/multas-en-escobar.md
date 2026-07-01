---
title: "API multas en Escobar por patente"
description: "Documentacion para integrar consulta de multas de transito en Escobar por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-escobar/
---

# API multas en Escobar por patente

Consultá gratis tus multas de tránsito en Escobar en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-escobar`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-escobar`.

## Resumen local

Consultá gratis multas de tránsito en Escobar por patente. Secretaría Contravencional, pago online, descargo en 5 días hábiles, SINAI, valor UF $160 (abril 2026).

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Escobar |
| Pagina publica | [patente.ar/multas-en-escobar](https://patente.ar/multas-en-escobar) |
| Slug publico | multas-en-escobar |
| Referencia de integracion | infracciones-escobar |
| Ultima actualizacion | 2026-04-14 |
| Organismo o fuente | Secretaría Contravencional |
| Host oficial | escobar.gob.ar |

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
Idempotency-Key: multas-en-escobar-demo-001
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

- Organismo o fuente informativa: Secretaría Contravencional
- Direccion publicada: Alberdi 526, Belén de Escobar, Buenos Aires
- Horario publicado: Lunes a viernes de 8:00 a 14:00 hs
- Telefono o canal publicado: (0348) 443-4040
- Sitio oficial: [escobar.gob.ar](https://escobar.gob.ar)


## Contexto del organismo

La Secretaría Contravencional del Municipio de Escobar es el organismo encargado de gestionar las infracciones de tránsito cometidas dentro del partido de Escobar. Allí se pueden realizar descargos, consultar el estado de actas y gestionar el pago de multas de forma presencial. Si preferís evitar la fila, consultá gratis tus multas en Escobar online desde Patente.ar antes de acercarte.


## Pago online

El Municipio de Escobar no ofrece pago online de multas de tránsito al momento de esta verificación. El pago se realiza de forma presencial en la Secretaría Contravencional (Alberdi 526, Belén de Escobar). Consultá el sitio oficial escobar.gob.ar por si se habilita esta opción.


## Pago presencial

Podés acercarte a la Secretaría Contravencional (Alberdi 526, Belén de Escobar) en el horario de atención de lunes a viernes de 8:00 a 14:00 hs. Se aceptan pagos en efectivo y con tarjeta según disponibilidad.


## Pago voluntario o descuento

El Municipio de Escobar no cuenta con un programa de descuento por pronto pago al momento de esta verificación. Se recomienda consultar en la Secretaría Contravencional (Alberdi 526) si existen condiciones especiales de pago vigentes.


## Descargo

Si considerás que una multa fue mal labrada o tenés argumentos para impugnarla, podés presentar un descargo ante la Secretaría Contravencional del Municipio de Escobar. Antes de ir, consultá gratis tus multas en Escobar desde Patente.ar para tener el detalle de cada acta. El procedimiento general es:


## Pasos de descargo

- **Presentarte dentro del plazo:** Tenés un plazo de 5 días hábiles desde la notificación del acta para presentar el descargo (verificar plazo vigente).
- **Reunir la documentación:** Llevá copia del acta de infracción, DNI, licencia de conducir y toda la documentación que respalde tu descargo.
- **Presentar el escrito:** Podés redactar el descargo por escrito explicando los motivos de la impugnación y presentarlo en mesa de entradas de la Secretaría Contravencional.
- **Resolución:** La Secretaría Contravencional evaluará tu descargo y emitirá una resolución. En caso de rechazo, podés apelar ante la instancia correspondiente.


## Plazos

Las multas de tránsito en Escobar siguen los plazos establecidos por la normativa provincial y la ordenanza municipal vigente. En la Provincia de Buenos Aires, el plazo de prescripción de las infracciones de tránsito es de 2 años desde la fecha del acta, aunque puede interrumpirse por acciones administrativas o judiciales.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta.
- **Prescripción de la infracción:** 2 años desde la fecha del acta (Ley Provincial de Tránsito).
- **Prescripción de la multa firme:** 2 años desde que queda firme la resolución.


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan el Partido de Escobar (como la Ruta Nacional 9 / Panamericana o la Ruta Provincial 25), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en la Secretaría Contravencional municipal. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Escobar, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador. Antes de cerrar la operación, consultá el estado del vehículo.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en la Secretaría Contravencional del Municipio de Escobar.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Escobar y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Localidades relacionadas

- Belén de Escobar
- Garín
- Ingeniero Maschwitz
- Loma Verde
- Matheu
- Maquinista Savio


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en Buenos Aires (Provincia) por patente](https://patente.ar/multas-en-buenos-aires)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Hurlingham por patente](https://patente.ar/multas-en-hurlingham)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Escobar?

Podés consultar si tu vehículo tiene multas de tránsito en Escobar ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en la Secretaría Contravencional del Municipio de Escobar y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Escobar?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Escobar por DNI?

Actualmente, la consulta de multas en el Municipio de Escobar se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a la Secretaría Contravencional con tu DNI.

## Probar Escobar en Playground

Para validar una consulta de multas en Escobar, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Escobar](https://patente.ar/multas-en-escobar)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
