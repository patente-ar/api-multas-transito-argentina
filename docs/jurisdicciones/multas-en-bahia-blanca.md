---
title: "API multas en Bahía Blanca por patente"
description: "Documentacion para integrar consulta de multas de transito en Bahía Blanca por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-bahia-blanca/
---

# API multas en Bahía Blanca por patente

Integra consulta de multas de transito en Bahía Blanca dentro de sistemas propios usando la API de patente.ar, el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-bahia-blanca`.

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
Idempotency-Key: multas-en-bahia-blanca-demo-001
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
- Organismo o autoridad que interviene en la infracción
- Fecha, motivo, estado y monto informado cuando la jurisdicción lo devuelve
- Canales oficiales de pago o atención publicados por la jurisdicción
- Diferencia entre actas municipales y controles provinciales o nacionales

- Organismo o fuente informativa: Tribunal de Faltas de Bahía Blanca

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.

## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Localidades relacionadas

- Centro
- Bella Vista
- Universitario
- Patagonia
- Villa Mitre
- Ingeniero White
- General Daniel Cerri
- Cabildo
- Villa Bordeu

## Links

- [Consulta web de multas en Bahía Blanca](https://patente.ar/multas-en-bahia-blanca)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
