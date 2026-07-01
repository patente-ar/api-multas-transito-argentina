---
title: "API multas en Rosario por patente"
description: "Documentacion para integrar consulta de multas de transito en Rosario por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-rosario/
---

# API multas en Rosario por patente

Consultá gratis tus multas de tránsito en Rosario en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-rosario`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-rosario`.

## Resumen local

Consultá gratis multas de tránsito en Rosario por patente. Tribunal Municipal de Faltas, pago voluntario 50%, descargo virtual con Perfil Digital.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Rosario |
| Pagina publica | [patente.ar/multas-en-rosario](https://patente.ar/multas-en-rosario) |
| Slug publico | multas-en-rosario |
| Referencia de integracion | infracciones-rosario |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Tribunal Municipal de Faltas de Rosario |
| Host oficial | rosario.gob.ar |

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
Idempotency-Key: multas-en-rosario-demo-001
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

- Organismo o fuente informativa: Tribunal Municipal de Faltas de Rosario
- Direccion publicada: Oficinas en cada CMD: Centro (G. Wheelwright 1486), Norte (I. Warnes 1917), Noroeste (Provincias Unidas 150 Bis), Oeste (J. D. Perón 4602), Sudoeste (Francia 4435) y Sur (J. E. Uriburu 637)
- Horario publicado: Lunes a viernes de 8:00 a 13:30 hs (Servicios Públicos 8:00 a 14:00 hs)
- Telefono o canal publicado: (0341) 480-2999 (CMD Centro) / 480-7680 (CMD Noroeste) / 480-6822 (CMD Norte)
- Sitio oficial: [rosario.gob.ar](https://www.rosario.gob.ar)


## Contexto del organismo

El Tribunal Municipal de Faltas de Rosario opera en oficinas distribuidas en los Centros Municipales de Distrito (CMD) de la ciudad. Gestiona las infracciones al Código de Convivencia Ciudadana de Rosario. Cuenta con Perfil Digital para descargos online y pasarela de pagos integrada con el Banco Municipal. Si preferís evitar la fila, consultá gratis tus multas en Rosario online desde Patente.ar antes de acercarte.


## Pago online

Rosario habilita pago voluntario online con cualquier tarjeta a través de la pasarela de pagos de rosario.gob.ar (acreditación automática). También podés hacer un descargo virtual con un Juez de Faltas a través de Perfil Digital, sin asistir presencialmente.


## Pago presencial

Podés acercarte a la Oficina del Tribunal de Faltas del CMD que te corresponda en el horario de atención. Para retirar vehículos del corralón, oficinas específicas en Moreno 2480 y J.D. Perón 8070.


## Pago voluntario o descuento

Rosario aplica una quita de hasta 50% sobre el valor mínimo de la multa por Pago Voluntario (sólo para faltas leves), en un único pago. Si presentás descargo, perdés el beneficio.


## Descargo

Si considerás que una multa fue mal labrada, podés presentar un descargo virtual a través de tu Perfil Digital en rosario.gob.ar o presencial sacando turno y asistiendo al CMD correspondiente. Antes de iniciar, consultá gratis tus multas en Rosario desde Patente.ar.


## Pasos de descargo

- **Acceder a tu Perfil Digital:** Registrate en rosario.gob.ar/perfil-digital para gestionar tus multas online y poder presentar descargo virtual.
- **Reunir la documentación:** DNI, cédula del vehículo y todas las pruebas que respalden tu defensa (fotos, comprobantes, etc.).
- **Presentar el descargo:** Online a través de Perfil Digital o presencial con turno previo en el CMD correspondiente. Tené en cuenta que perdés el 50% de pago voluntario.
- **Resolución:** El Juez de Faltas evaluará el descargo y emitirá una resolución, que podrás consultar en tu Perfil Digital.


## Plazos

Las multas de tránsito en Rosario siguen los plazos establecidos por la normativa municipal vigente y la Ley Nacional 24.449.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta (verificar plazo municipal vigente).
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves (Ley Nacional 24.449).


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan Rosario (como la Autopista Rosario - Buenos Aires, la Ruta Nacional 33 o la Ruta Nacional 9), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en Tribunal Municipal de Faltas. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Rosario, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Tribunal Municipal de Faltas de Rosario, Santa Fe.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Rosario y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Barrios y zonas de Rosario

Esta guía aplica para infracciones de tránsito en toda la ciudad de Rosario

- Centro
- Pichincha
- Echesortu
- Fisherton
- Lourdes
- República de la Sexta
- Empalme Graneros
- Tablada
- Saladillo
- Tiro Suizo


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Rosario?

Podés consultar si tu vehículo tiene multas de tránsito en Rosario ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Tribunal Municipal de Faltas y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Rosario?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Rosario por DNI?

Actualmente, la consulta de multas en Rosario se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Tribunal Municipal de Faltas con tu DNI.

## Probar Rosario en Playground

Para validar una consulta de multas en Rosario, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Rosario](https://patente.ar/multas-en-rosario)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
