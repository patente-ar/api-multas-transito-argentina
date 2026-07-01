---
title: "API multas en Buenos Aires por patente"
description: "Documentacion para integrar consulta de multas de transito en Buenos Aires por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-buenos-aires/
---

# API multas en Buenos Aires por patente

Consultá gratis tus multas de tránsito en Buenos Aires en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-buenos-aires`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-buenos-aires`.

## Resumen local

Consultá gratis multas de tránsito en Buenos Aires por patente. Justicia Administrativa Provincial, SINAI, Ley 13.927, descargo en 5 días.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Buenos Aires |
| Pagina publica | [patente.ar/multas-en-buenos-aires](https://patente.ar/multas-en-buenos-aires) |
| Slug publico | multas-en-buenos-aires |
| Referencia de integracion | infracciones-buenos-aires |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Justicia Administrativa de Infracciones de Tránsito Provincial |
| Host oficial | infraccionesba.gba.gob.ar |

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
Idempotency-Key: multas-en-buenos-aires-demo-001
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

- Organismo o fuente informativa: Justicia Administrativa de Infracciones de Tránsito Provincial
- Direccion publicada: Sede central: calle 6 N°928, La Plata (Dirección Provincial de Política y Seguridad Vial)
- Horario publicado: Lunes a viernes de 8:30 a 13:30 hs (verificar por sede)
- Telefono o canal publicado: (0221) 427-0034 (internos 2304/2307)
- Sitio oficial: [infraccionesba.gba.gob.ar](https://infraccionesba.gba.gob.ar)


## Contexto del organismo

La Justicia Administrativa de Infracciones de Tránsito Provincial es el organismo creado por la Ley 13.927 para juzgar las infracciones cometidas en rutas, caminos, autopistas y semiautopistas provinciales o nacionales en el territorio de la Provincia de Buenos Aires. Funciona con varios Juzgados Administrativos distribuidos por la provincia (La Plata, Mar del Plata, Bahía Blanca, Azul, Don Torcuato y otros). Las infracciones cometidas dentro del ejido urbano de cada partido se gestionan en su Juzgado de Faltas Municipal. Si preferís evitar la fila, consultá gratis tus multas desde Patente.ar antes de acercarte.


## Pago online

La Provincia de Buenos Aires habilita la consulta y pago online de multas a través del portal infraccionesba.gba.gob.ar, donde podés consultar por patente y abonar con tarjeta o generar boleta. También se acepta el pago en Registros Seccionales del Automotor por convenio con DNRPA.


## Pago presencial

El pago presencial se realiza en cualquier Juzgado Administrativo de Infracciones de Tránsito Provincial habilitado, en las cajas municipales habilitadas o en Registros Seccionales del Automotor de la provincia.


## Pago voluntario o descuento

La adhesión a un plan de pago voluntario en infraccionesba.gba.gob.ar implica el reconocimiento de la deuda. Las condiciones de descuento por pronto pago varían según el tipo de falta y deben verificarse al momento del trámite.


## Descargo

Si considerás que una multa fue mal labrada o tenés argumentos para impugnarla, podés presentar un descargo ante la Justicia Administrativa de Infracciones de Tránsito Provincial. Antes de ir, consultá gratis tus multas en la Provincia de Buenos Aires desde Patente.ar para tener el detalle de cada acta. El procedimiento general es:


## Pasos de descargo

- **Presentarte dentro del plazo:** Tenés un plazo de 5 días hábiles desde la notificación del acta para presentar el descargo.
- **Reunir la documentación:** Llevá copia del acta de infracción, DNI, licencia de conducir y toda la documentación que respalde tu descargo.
- **Presentar el escrito:** Podés redactar el descargo por escrito explicando los motivos y presentarlo en mesa de entradas de la Justicia Administrativa de Infracciones de Tránsito Provincial.
- **Resolución:** la Justicia Administrativa de Infracciones de Tránsito Provincial evaluará tu descargo y emitirá una resolución. En caso de rechazo, podés apelar ante la instancia correspondiente.


## Plazos

Las multas de tránsito en la Provincia de Buenos Aires siguen los plazos establecidos por la normativa provincial (Ley 13.927 de la Provincia de Buenos Aires) y la ordenanza municipal vigente.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta (Ley 13.927).
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves desde la fecha del acta (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves (Ley Nacional 24.449, art. 89).


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan el territorio de la Provincia de Buenos Aires (como la Ruta Nacional 9 (Panamericana), la Autopista Buenos Aires - La Plata, la Ruta Nacional 3, la Ruta Nacional 226 y otras), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en la Justicia Administrativa de Infracciones de Tránsito Provincial. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Buenos Aires, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Justicia Administrativa de Infracciones de Tránsito Provincial de la Provincia de Buenos Aires.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Buenos Aires y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Partidos y departamentos de la Provincia de Buenos Aires

Esta guía aplica para infracciones de tránsito en toda la Provincia de Buenos Aires

- La Plata
- Mar del Plata
- Bahía Blanca
- Tandil
- Quilmes
- La Matanza
- Lomas de Zamora
- Tigre
- Pilar
- Junín


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Buenos Aires?

Podés consultar si tu vehículo tiene multas de tránsito en Buenos Aires ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Justicia Administrativa de Infracciones de Tránsito Provincial y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Buenos Aires?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Buenos Aires por DNI?

Actualmente, la consulta de multas en Buenos Aires se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Justicia Administrativa de Infracciones de Tránsito Provincial con tu DNI.

## Probar Buenos Aires en Playground

Para validar una consulta de multas en Buenos Aires, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Buenos Aires](https://patente.ar/multas-en-buenos-aires)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
