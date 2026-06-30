---
title: "API multas en Marcos Juárez por patente"
description: "Documentacion para integrar consulta de multas de transito en Marcos Juárez por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-marcos-juarez/
---

# API multas en Marcos Juárez por patente

Integra consulta de multas de transito en Marcos Juárez dentro de sistemas propios usando la API de patente.ar, el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-marcos-juarez`.

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
Idempotency-Key: multas-en-marcos-juarez-demo-001
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
- Jurisdicción declarada para Marcos Juárez y provincia asociada
- Organismo o autoridad que interviene en la infracción cuando el proveedor lo devuelve
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales publicados por la jurisdicción consultada

- Organismo o fuente informativa: Juzgado Administrativo de Faltas de Marcos Juárez

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.

## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Localidades relacionadas

- Zona urbana de Marcos Juárez
- Accesos a Marcos Juárez
- Calles y avenidas principales de Marcos Juárez
- Rutas cercanas en Córdoba
- Barrios y parajes vinculados a Marcos Juárez

## Probar Marcos Juárez en Playground

Para validar una consulta de multas en Marcos Juárez, crea una cuenta, pedi habilitar la API `infracciones` y abri el Playground con una patente de prueba o un caso propio de integracion.

- [Crear cuenta en patente.ar](https://patente.ar/registro)
- [Pedir habilitacion de la API de multas](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Abrir Playground de APIs vehiculares](https://patente.ar/desarrolladores/api?tab=playground)

El Playground muestra API keys, payloads, idempotencia, estado de procesamiento, webhooks y logs para acelerar el pase a produccion.


## Links

- [Consulta web de multas en Marcos Juárez](https://patente.ar/multas-en-marcos-juarez)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Crear cuenta](https://patente.ar/registro)
- [Pedir habilitacion de API](https://patente.ar/contacto?asunto=Habilitar%20API%20infracciones)
- [Playground API](https://patente.ar/desarrolladores/api?tab=playground)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
