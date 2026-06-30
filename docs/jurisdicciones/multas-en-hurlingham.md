---
title: "API multas en Hurlingham por patente"
description: "Documentacion para integrar consulta de multas de transito en Hurlingham por patente con la API de patente.ar."
permalink: /jurisdicciones/multas-en-hurlingham/
---

# API multas en Hurlingham por patente

Integra consulta de multas de transito en Hurlingham dentro de sistemas propios usando la API de patente.ar, el endpoint unico `POST /v1/consultas`, API key del producto `infracciones`, idempotencia y webhook de resultado.

Esta pagina forma parte del repo publico [api-multas-transito-argentina](https://github.com/patente-ar/api-multas-transito-argentina) y funciona como documentacion tecnica para la jurisdiccion `multas-en-hurlingham`.

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
Idempotency-Key: multas-en-hurlingham-demo-001
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

- Organismo o fuente informativa: Juzgado de Faltas Municipal de Hurlingham

La disponibilidad efectiva por API puede depender del contrato, la fuente activa, el estado operativo del organismo y el flujo asincronico configurado para la cuenta.

## Flujo recomendado

1. Normalizar la patente antes de llamar a la API.
2. Enviar `Idempotency-Key` para reintentos seguros.
3. Guardar `requestId` para conciliacion.
4. Validar la firma HMAC SHA-256 del webhook.
5. Relacionar el resultado con la orden, cliente, vehiculo o legajo interno.

## Localidades relacionadas

- Hurlingham
- William C. Morris
- Villa Tesei

## Links

- [Consulta web de multas en Hurlingham](https://patente.ar/multas-en-hurlingham)
- [API multas en patente.ar](https://patente.ar/api-multas)
- [Indice de jurisdicciones](https://patente-ar.github.io/api-multas-transito-argentina/jurisdicciones/)
- [OpenAPI](../../openapi/openapi.yaml)
- [Repo GitHub](https://github.com/patente-ar/api-multas-transito-argentina)
