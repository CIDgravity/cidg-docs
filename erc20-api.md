# API Documentation – ERC20 Integration

This API provides endpoints for managing and reporting on service/payment contracts.  
All requests require **API Key authentication**.

---

## Authentication
Each request must include an API key via the `Authorization` header:

```http
X-API-KEY: <<YOUR_API_KEY>
````

---

## Base URL

All endpoints are prefixed with:

```
https://service.cidgravity.com
```

---

## Endpoints

### 1. Get SLA

**Endpoint:**
`POST /v1/contracts/get-sla`

**Description:**
Retrieve the SLA for a given provider/client over a specific month and year.

**Request Body:**

```json
{
  "month": 8,
  "year": 2025,
  "provider": "f010479",
  "client": "f01859221"
}
```

**Response (200):**

```json
{
  "error": {},
  "result": {
    "paymentDecision": "yes",
    "reason": ""
  }
}
```

**Valid values for `paymentDecision`:**

* `yes` → SLA is met, payments can proceed.
* `no` → SLA is not met, payments must not proceed.
* `notYet` → SLA decision is pending.

**cURL Example:**

```bash
curl -X POST "https://service.cidgravity.com/private/v1/contracts/get-sla" \
  -H "X-API-KEY: <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
        "month": 8,
        "year": 2025,
        "provider": "f010479",
        "client": "f01859221"
      }'
```

**Errors:**

* `400 Bad request` – Invalid parameters.

---

### 2. Get On-Chain Deals

**Endpoint:**
`POST /v1/get-on-chain-deals-erc20`

**Description:**
Retrieve all on-chain deals filtered by an ERC20 label.
Results are paginated (10,000 items per page).

**Request Body:**

```json
{
  "next": "1714002848.0971982"
}
```

* `next` (optional): Cursor for pagination.

  * Use `null` for the first page.
  * Use a valid Unix timestamp (milliseconds) to fetch updated records.

**Response (200):**

```json
{
  /* ValidResponseSchema */
}
```

**cURL Example:**

```bash
curl -X POST "https://service.cidgravity.com/private/v1/get-on-chain-deals-erc20" \
  -H "X-API-KEY: <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{ "next": "0" }'
```

**Errors:**

* `400 Bad request` – Invalid parameters.

---

### 3. Update Client Balances

**Endpoint:**
`POST /v1/contracts/update-client-balances`

**Description:**
Update balances for a client in a contract.

**Request Body:**

```json
{
  "address": "f01859221",
  "contractAddress": "0xf",
  "balances": [
    {
      "tokenAddress": "0xf",
      "balance": 0,
      "securityDeposit": 0
    }
  ]
}
```

**Response (200):**

```json
{
  "message": "Balances updated"
}
```

**cURL Example:**

```bash
curl -X POST "https://service.cidgravity.com/private/v1/contracts/update-client-balances" \
  -H "X-API-KEY: <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
        "address": "f01859221",
        "contractAddress": "0xf",
        "balances": [
          {
            "tokenAddress": "0xf",
            "balance": 0,
            "securityDeposit": 0
          }
        ]
      }'
```

**Errors:**

* `400 Bad request` – Invalid request format.

---

### 4. Update Provider Balances

**Endpoint:**
`POST /v1/contracts/update-provider-balances`

**Description:**
Update balances for a provider in a contract.

**Request Body:**

```json
{
  "address": "f010479",
  "contractAddress": "0xf",
  "balances": [
    {
      "tokenAddress": "0xf",
      "balance": 0
    }
  ]
}
```

**Response (200):**

```json
{
  "message": "Balances updated"
}
```

**cURL Example:**

```bash
curl -X POST "https://service.cidgravity.com/private/v1/contracts/update-provider-balances" \
  -H "X-API-KEY: <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
        "address": "f010479",
        "contractAddress": "0xf",
        "balances": [
          {
            "tokenAddress": "0xf",
            "balance": 0
          }
        ]
      }'
```

**Errors:**

* `400 Bad request` – Invalid request format.

---

## Notes

* Timestamps for pagination must be in **milliseconds**
