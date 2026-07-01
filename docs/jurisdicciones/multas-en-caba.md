---
title: "API multas en CABA por patente"
description: "Documentacion para integrar consulta de multas de transito en CABA por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-caba/
---

# API multas en CABA por patente

Consultá gratis tus multas de tránsito en CABA en segundos — Ingresá la patente y verificá infracciones pendientes al instante

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-caba`. La API usa el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado. Referencia interna de cobertura: `infracciones-caba`.

## Resumen local

Consultá gratis multas de tránsito en CABA por patente. DGAI, pago voluntario 50% descuento, descargo con controlador, Ley 451.

| Dato | Valor |
| --- | --- |
| Jurisdiccion | CABA |
| Pagina publica | [patente.ar/multas-en-caba](https://patente.ar/multas-en-caba) |
| Slug publico | multas-en-caba |
| Referencia de integracion | infracciones-caba |
| Ultima actualizacion | 2026-04-29 |
| Organismo o fuente | Dirección General de Administración de Infracciones (DGAI) |
| Host oficial | buenosaires.gob.ar |

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
Idempotency-Key: multas-en-caba-demo-001
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

- Organismo o fuente informativa: Dirección General de Administración de Infracciones (DGAI)
- Direccion publicada: Av. Regimiento de Patricios 65, CABA
- Horario publicado: Lunes a viernes de 8:00 a 19:00 hs
- Telefono o canal publicado: (011) 5030-9860 / 147 (línea de la Ciudad) / WhatsApp Boti +54 9 11 5050-0147
- Sitio oficial: [buenosaires.gob.ar](https://buenosaires.gob.ar)


## Contexto del organismo

La Dirección General de Administración de Infracciones (DGAI) es el organismo del Gobierno de la Ciudad de Buenos Aires con competencia en el tratamiento de las faltas de tránsito según la Ley 451 (Régimen de Faltas). Sus controladores administrativos resuelven los descargos y la prescripción de las actas. Allí se pueden realizar descargos, audiencias virtuales con un controlador y gestionar el pago de multas. Si preferís evitar la fila, consultá gratis tus multas en CABA online desde Patente.ar antes de acercarte.


## Pago online

El Gobierno de la Ciudad ofrece pago online de multas a través de buenosaires.gob.ar, Boti (WhatsApp +54 9 11 5050-0147), Mercado Pago, Pago mis Cuentas, Bapro Pagos y Provincia Net. La acreditación es inmediata con tarjeta de crédito y puede tardar hasta 24-48 hs en otros medios.


## Pago presencial

Podés acercarte a la DGAI (Av. Regimiento de Patricios 65) o a cualquier sede comunal con turno previo. Se acepta pago en efectivo en Pago Fácil, Rapipago, Banco Ciudad y Banco Provincia, y con tarjeta de crédito o débito en terminales automáticas (ATM) y sedes comunales.


## Pago voluntario o descuento

La Ciudad de Buenos Aires aplica un descuento del 50% sobre el monto mínimo de la multa por Pago Voluntario, vigente durante 40 días desde la notificación. Si hacés un descargo con un controlador o iniciás audiencia, perdés automáticamente este beneficio.


## Descargo

Si considerás que una multa fue mal labrada o tenés argumentos para impugnarla, podés presentar un descargo ante la DGAI. Se realiza ante una Unidad Administrativa de Control de Faltas (controlador) en audiencia presencial o por videollamada vía Boti. Antes de iniciar el trámite, consultá gratis tus multas en CABA desde Patente.ar para tener el detalle de cada acta. Tené en cuenta que al presentar descargo perdés el beneficio del 50% de Pago Voluntario.


## Pasos de descargo

- **Solicitar turno con un controlador:** Podés sacar turno por buenosaires.gob.ar/turnos, llamando al 147 o por Boti (WhatsApp +54 9 11 5050-0147). Solo el controlador asignado a tu acta puede resolverla.
- **Reunir la documentación:** DNI vigente (frente y dorso), cédula verde o azul del vehículo, y toda la documentación que respalde tu descargo (fotos, comprobantes, etc.).
- **Presentar el descargo:** Asistí al turno presencial en Av. Regimiento de Patricios 65 o a la audiencia por videollamada. Si vivís a más de 60 km de CABA, podés escribir a infracciones.ciudad@gmail.com.
- **Resolución:** El controlador emite resolución que concluye la vía administrativa. Podés apelar ante la Justicia Contravencional y de Faltas de la Ciudad (Ley 1217).


## Plazos

Las multas de tránsito en la Ciudad de Buenos Aires siguen los plazos establecidos por la Ley 451 (Régimen de Faltas) y la Ley Nacional de Tránsito 24.449.


## Plazos operativos

- **Plazo de Pago Voluntario con descuento:** 40 días desde la notificación, con 50% de descuento sobre el monto mínimo.
- **Prescripción de la acción por faltas:** 2 años desde la fecha de la infracción, salvo notificación fehaciente al imputado, en cuyo caso el plazo se computa desde esa fecha (Ley 451).
- **Prescripción de la multa firme:** Debe solicitarse ante un Controlador Administrativo de Faltas; no opera de pleno derecho. Verificar el plazo aplicable según gravedad de la falta.


## Rutas, controles y SINAI

Para infracciones cometidas en autopistas urbanas (AU1 25 de Mayo, AU6 Perito Moreno, AU7 Dellepiane, AU9 Illia), las multas son competencia de la DGAI ya que están dentro del ejido de la Ciudad. Para infracciones en rutas nacionales o en jurisdicciones limítrofes, las multas se gestionan a través del sistema SINAI (Sistema Nacional de Administración de Infracciones) de la Agencia Nacional de Seguridad Vial. Referencia nacional: [SINAI](https://consultainfracciones.seguridadvial.gob.ar).


## Controles frecuentes

- Foto-radares en autopistas
- Exceso de velocidad
- Controles nacionales


## Valores orientativos publicados

| Infraccion | Rango UF |
| --- | --- |
| Estacionamiento en lugar prohibido | 50 a 200 UF |
| Exceso de velocidad | 100 a 500 UF |
| No respetar semáforo en rojo | 200 a 1000 UF |
| Alcoholemia positiva | 500 a 2000 UF |
| Conducir sin licencia | 300 a 1500 UF |


## Compra venta y riesgo operativo

Si estás por comprar o vender un vehículo en CABA, es fundamental verificar que no tenga multas de tránsito pendientes. Las infracciones impagas pueden bloquear la transferencia del dominio y generar costos inesperados para el comprador.


## Puntos a revisar antes de operar

- Las multas pendientes pueden impedir la transferencia del vehículo
- El comprador puede heredar multas no declaradas por el vendedor
- Verificar multas antes de la compra evita sorpresas y gastos no previstos


## Consulta web usada como referencia

- **Ingresá el dominio:** Escribí la patente del vehículo en el buscador de Patente.ar (formato viejo o nuevo: ABC123 o AB123CD).
- **Verificación automática:** Nuestro sistema consulta en tiempo real las infracciones registradas en Dirección General de Administración de Infracciones (DGAI) de la Ciudad Autónoma de Buenos Aires.
- **Revisá el resultado:** Vas a ver el detalle de cada acta o boleta: fecha, tipo de infracción, monto y estado de pago.
- **Descargá tu informe:** Podés descargar un informe completo con todas las multas del vehículo en CABA y otros municipios.


## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Barrios y zonas de la Ciudad de Buenos Aires

Esta guía aplica para infracciones de tránsito en toda la Ciudad Autónoma de Buenos Aires

- Microcentro
- Palermo
- Recoleta
- Belgrano
- Caballito
- Almagro
- Villa Crespo
- Flores
- Boedo
- San Telmo


## Jurisdicciones cercanas o relacionadas

- [Consultar multas en Almirante Brown por patente](https://patente.ar/multas-en-almirante-brown)
- [Consultar multas en Avellaneda por patente](https://patente.ar/multas-en-avellaneda)
- [Consultar multas en CABA por patente](https://patente.ar/multas-en-caba)
- [Consultar multas en Lanús por patente](https://patente.ar/multas-en-lanus)
- [Consultar multas en Lomas de Zamora por patente](https://patente.ar/multas-en-lomas-de-zamora)


## Preguntas frecuentes para integradores

### ¿Cómo puedo saber si tengo multas en CABA?

Podés consultar si tu vehículo tiene multas de tránsito en CABA ingresando la patente en Patente.ar. Nuestro sistema verifica automáticamente las infracciones registradas en Dirección General de Administración de Infracciones (DGAI) y te muestra el detalle de cada acta pendiente.

### ¿Qué necesito para consultar multas en CABA?

Solo necesitás el número de patente (dominio) del vehículo. Aceptamos tanto el formato de patente vieja (ABC123) como el formato nuevo Mercosur (AB123CD).

### ¿Cómo consultar multas en CABA por DNI?

Actualmente, la consulta de multas en CABA se realiza por dominio del vehículo (patente), no por DNI. Ingresá la patente en Patente.ar para verificar si tiene infracciones pendientes. Si necesitás consultar multas asociadas a tu persona, podés acercarte a Dirección General de Administración de Infracciones (DGAI) con tu DNI.

## Probar CABA en Playground

Para validar una consulta de multas en CABA, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en CABA](https://patente.ar/multas-en-caba)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
