# Titan Global Connector — API Documentation

## Base URL
```
https://titan-banker.rcmdigitalmedia.net
```

---

## Endpoints

### GET /status
Returns system health and operational status.

**Response:**
```json
{
  "status": "operational",
  "rails": {
    "stripe": "active",
    "pix": "active",
    "oxxo": "active",
    "paystack": "active",
    "ideal": "active",
    "bancontact": "active",
    "alipay": "active"
  },
  "timestamp": "2026-02-20T00:00:00Z"
}
```

---

### POST /gateway/route
Submit a transaction for multi-rail routing. The engine selects the optimal rail based on cost, speed, geographic availability, and real-time reliability scoring.

**Request Body:**
```json
{
  "amount": 100.00,
  "currency": "USD",
  "country": "BR",
  "agent_id": "your-agent-id",
  "preferred_rail": "auto"
}
```

**Response:**
```json
{
  "transaction_id": "txn_xxxx",
  "selected_rail": "pix",
  "estimated_fee": 0.012,
  "estimated_latency_ms": 340,
  "status": "routing"
}
```

---

### GET /gateway/schema
Returns the full routing schema including all supported rails, countries, and protocols.

---

### POST /webhook/whatsapp
WhatsApp webhook integration endpoint for agent-triggered payment flows.

---

## Supported Protocols

- **ACP** — Agentic Commerce Protocol (Stripe)
- **UCP** — Universal Commerce Protocol (Google/Shopify)
- **MCP** — Model Context Protocol
- **REST** — Standard RESTful API
- **JSON-RPC** — Remote procedure calls
- **WebHook** — Event-driven integrations

---

## Authentication
Contact rick@rcmdigitalmedia.net for API access and credentials.

---

*Titan Global Connector is patent-protected technology owned by RCM Digital Media LLC.*
*Patents: 63/949,918 | 63/950,368 | 63/952,170 | 63/952,181*
