# ATPCO Product Catalog Bundles API Documentation

## Overview
The **ATPCO Product Catalog Bundles API** allows airlines and their partners to manage and retrieve bundle data efficiently. This API supports operations for creating, retrieving, updating, and deleting bundles within the ATPCO Product Catalog.

- **Base URL:** `https://virtserver.swaggerhub.com/ATPCO_APIS/pc-bundle-api/1.0.0`
- **Version:** `1.0.0`
- **Authentication:** API Key & Bearer Token (JWT)
- **Supported Content-Type:** `application/json`
- **Rate Limiting Headers:**
  - `X-Rate-Limit-Limit`: Maximum requests allowed
  - `X-Rate-Limit-Remaining`: Remaining requests
  - `X-Rate-Limit-Reset`: Time until rate limit reset
  - `Retry-After`: Indicates wait time before retrying

## Authentication
The API requires **API Key authentication** via the `x-api-key` header or **JWT-based Bearer Authentication**.

### Example: API Key Authentication
```http
GET /bundles/ABC-232-WS HTTP/1.1
Host: atpco.net
x-api-key: YOUR_API_KEY
```

### Example: Bearer Token Authentication
```http
GET /bundles/ABC-232-WS HTTP/1.1
Host: atpco.net
Authorization: Bearer YOUR_JWT_TOKEN
```

## Endpoints & Operations
### 1. Retrieve a Bundle by ID
- **Endpoint:** `GET /bundles/{recordIdentifier}`
- **Description:** Fetch bundle details using a unique identifier.
- **Response Example:**
```json
{
  "summary": {
    "transactionId": "34a64df551429fec1cs5"
  },
  "bundle": {
    "bundleName": "Premium Travel Package",
    "bundleCodeOwnerDefined": "BNDL123",
    "historyDescription": "Updated with additional services"
  }
}
```

### 2. Update a Bundle by ID
- **Endpoint:** `PUT /bundles/{recordIdentifier}`
- **Description:** Modify existing bundle data.
- **Request Body Example:**
```json
{
  "products": [],
  "bundleRules": []
}
```

### 3. Delete a Bundle by ID
- **Endpoint:** `DELETE /bundles/{recordIdentifier}`
- **Description:** Remove a bundle from the system.

### 4. Retrieve Bundles by Catalog Owner
- **Endpoint:** `GET /bundles?catalogOwner={owner}`
- **Description:** Fetch all bundles associated with a given catalog owner.

### 5. Create a New Bundle
- **Endpoint:** `POST /bundles`
- **Description:** Add a new bundle to the catalog.
- **Request Body Example:**
```json
{
  "summary": {
    "catalogOwner": {
      "type": "Airline",
      "code": "XYZ"
    }
  },
  "bundles": [
    {
      "bundleName": "Luxury Flight Package",
      "bundleCodeOwnerDefined": "BNDL999"
    }
  ]
}
```

## Error Handling
The API follows standardized **HTTP response codes** for errors.

| Status Code | Meaning |
|-------------|---------|
| **400** | Bad request – Invalid query parameters |
| **401** | Unauthorized – Authentication required |
| **403** | Forbidden – Access denied |
| **404** | Not Found – Resource does not exist |
| **429** | Too Many Requests – Rate limit exceeded |
| **500** | Internal Server Error – Unexpected issue |

## Security & Rate Limits
- **Rate Limiting:** The API enforces request limits to prevent abuse.
- **CORS Support:** Allows secure cross-origin API calls.
- **Data Encryption:** All data must be sent over `HTTPS`.

## Best Practices for Integration
✔ Use **pagination** when retrieving large data sets.  
✔ Handle **rate limits** by implementing retries with `Retry-After`.  
✔ Log **transaction IDs** for debugging (`Transaction-Id` header).  
✔ Keep **API keys secure**—never expose them in public repositories.  

## Support & Contact
For API-related queries, reach out to **ATPCO API Support**:
- 🌐 [API Documentation](https://atpco.net)
- 📧 Email: pcsupport@atpco.net

### 🚀 Start Integrating Today!
The **ATPCO Product Catalog Bundles API** enables airlines and partners to efficiently manage bundles and offer enhanced travel services.
