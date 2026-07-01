---
title: "API multas en Mendoza por patente"
description: "Documentacion para integrar consulta de multas de transito en Mendoza por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-mendoza/
---

# API multas en Mendoza por patente

Consultá gratis tus multas de tránsito en Mendoza en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-mendoza`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-mendoza`.

## Resumen local

Consultá gratis multas de tránsito en Mendoza por patente. Ley 9024, ATM, descargo en 5 días, pago online con descuento.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | Mendoza |
| Pagina publica | [patente.ar/multas-en-mendoza](https://patente.ar/multas-en-mendoza) |
| Slug publico | multas-en-mendoza |
| Referencia de integracion | infracciones-mendoza |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Juzgados Administrativos Municipales de Tránsito y Dirección de Seguridad Vial |
| Host oficial | atm.mendoza.gov.ar |

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
Idempotency-Key: multas-en-mendoza-demo-001
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

- Organismo o fuente informativa: Juzgados Administrativos Municipales de Tránsito y Dirección de Seguridad Vial
- Direccion publicada: ATM Casa Central: Peltier 351, Mendoza Capital
- Horario publicado: Lunes a viernes según sede (verificar)
- Telefono o canal publicado: verificar
- Sitio oficial: [atm.mendoza.gov.ar](https://www.atm.mendoza.gov.ar)


## Contexto del organismo

En la Provincia de Mendoza, la Ley 9024 estableció Juzgados Administrativos Municipales de Tránsito en cada departamento. La Dirección de Seguridad Vial, dependiente del Ministerio de Seguridad, controla rutas y caminos provinciales. El cobro y consulta se centraliza en la Administración Tributaria Mendoza (ATM). Si preferís evitar la fila, consultá gratis tus multas en Mendoza online desde Patente.ar antes de acercarte.


## Pago online

Mendoza ofrece pago online de multas a través de atm.mendoza.gov.ar y sistemas.seguridad.mendoza.gov.ar. Permite consultar por dominio, generar planes de pago y abonar con tarjeta o débito.


## Pago presencial

El pago presencial se realiza en cualquier banco habilitado (Banco Nación, Banco Supervielle, HSBC, Patagonia, Credicoop, Macro, San Juan), Provincia Net, Rapipago, Pago Fácil o Cobro Express, con la boleta generada en ATM.


## Pago voluntario o descuento

La Provincia de Mendoza ofrece un descuento del 10% por Pago Voluntario si abonás dentro de los 3 días hábiles desde la emisión del acta de infracción.


## Descargo

Si considerás que una multa fue mal labrada, podés presentar un descargo ante el Juez Administrativo de Tránsito correspondiente al lugar de la infracción. La Ley 9024 establece el procedimiento. Antes de iniciar, consultá gratis tus multas en Mendoza desde Patente.ar.


## Pasos de descargo

- **Presentarte dentro del plazo:** 5 días hábiles desde la notificación del acta (3 días hábiles para algunos casos en la Ciudad de Mendoza). Verificar plazo según sede.
- **Reunir la documentación:** DNI, cédula del vehículo, licencia de conducir, copia del acta y pruebas que respalden tu descargo.
- **Presentar el descargo:** Vía mail al juzgado correspondiente (uresvialnor@mendoza.gov.ar y otros según URV) o presencialmente en el Juzgado Administrativo Municipal.
- **Resolución:** El Juez admite o rechaza la prueba en 3 días y resuelve en hasta 5 días desde la presentación (Ley 9024, art. 116).


## Plazos

Las multas de tránsito en la Provincia de Mendoza siguen los plazos establecidos por la Ley Provincial de Tránsito 9024 y la Ley Nacional 24.449.


## Plazos operativos

- **Plazo para presentar descargo:** 5 días hábiles desde la notificación del acta (3 días en Ciudad de Mendoza, según el caso).
- **Prescripción de la infracción:** 2 años para faltas leves y 5 años para faltas graves (Ley Nacional 24.449, art. 89).
- **Prescripción de la multa firme:** 5 años desde que queda firme la resolución para faltas graves.


## Rutas, controles y SINAI

Para infracciones cometidas en rutas provinciales o nacionales que atraviesan la Provincia de Mendoza (como la Ruta Nacional 7, la Ruta Nacional 40, la Ruta Nacional 143 o la Ruta Provincial 82), las multas son competencia provincial y se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Estas infracciones no aparecen en los Juzgados Administrativos Municipales. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


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

Si estás por comprar o vender un vehículo en Mendoza, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Juzgados Administrativos Municipales de Tránsito de la Provincia de Mendoza.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en Mendoza y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Departamentos de la Provincia de Mendoza

Esta guía aplica para infracciones de tránsito en toda la Provincia de Mendoza

- Capital (Ciudad de Mendoza)
- Godoy Cruz
- Guaymallén
- Las Heras
- Maipú
- Luján de Cuyo
- San Rafael
- General Alvear
- Malargüe
- San Martín


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en Mendoza?

Podés consultar si tu vehículo tiene multas de tránsito en Mendoza ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Juzgados Administrativos Municipales de Tránsito y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en Mendoza?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en Mendoza por DNI?

Actualmente, la consulta de multas en Mendoza se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Juzgados Administrativos Municipales de Tránsito con tu DNI.

## Probar Mendoza en Playground

Para validar una consulta de multas en Mendoza, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Mendoza](https://patente.ar/multas-en-mendoza)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
