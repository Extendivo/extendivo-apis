# Extendivo — API Infrastructure for Autonomous AI Agents

Secure, machine-readable, pay-per-request API services designed for autonomous AI agents, developers and automated workflows.

Extendivo provides infrastructure for secure web access, request validation, content verification, response validation, document processing, data transformation and API routing.

**No API keys. No subscriptions. Pay per request with x402.**

## API Catalog

All paid endpoints use HTTP POST with JSON request bodies.

| API | Endpoint | Price (USDC) |
|---|---|---:|
| SafeFetch | `/v1/safe-fetch` | $0.005 |
| SafeFetch Secure | `/v1/safe-fetch-secure` | $0.015 |
| ContractGuard + CallRepair | `/v1/contract-guard` | $0.002 |
| ChangeProof | `/v1/change-proof` | $0.003 |
| ResultGuard | `/v1/result-guard` | $0.003 |
| SafeDoc | `/v1/safe-doc` | $0.010 |
| DataShape | `/v1/data-shape` | $0.005 |
| AgentRoute | `/v1/agent-route` | $0.001 |

**Base URL:** `https://api.extendivo.com`

## Services

### SafeFetch

Securely fetch and extract content from public HTTP and HTTPS URLs.

- SSRF protection
- Redirect revalidation
- Clean content extraction
- Structured metadata
- Machine-readable JSON responses

### SafeFetch Secure

Secure web content retrieval with additional prompt-injection risk detection.

- Secure URL fetching
- Prompt-injection risk signals
- Content extraction
- Structured security information
- Designed for autonomous agent workflows

Risk signals assist agent decisions but do not guarantee that retrieved content is safe.

### ContractGuard + CallRepair

Validate proposed API requests before paying for the target service.

- OpenAPI contract validation
- Required parameter detection
- x402 payment requirement analysis
- Deterministic request repair suggestions
- Machine-readable validation results
- No execution of the target API

### ChangeProof

Detect, compare and cryptographically document changes in public web content, documentation and API specifications.

- SHA-256 content hashes
- Snapshot comparison
- Content differences
- Ed25519 signed proofs
- 30-day snapshot retention

Public verification key:
https://api.extendivo.com/change-proof/public-key.json

### ResultGuard

Validate API responses against JSON Schema Draft 2020-12.

- Required field validation
- Data type validation
- Empty response detection
- Structural inconsistency detection
- Machine-readable validation reports

ResultGuard validates structure. It does not modify data or perform factual verification.

### SafeDoc

Securely retrieve and extract information from public PDF documents.

- PDF text extraction
- Document metadata extraction
- Secure remote document retrieval
- Structured JSON output

### DataShape

Transform JSON data into a required target structure using explicit mappings.

- JSON Pointer field mappings
- Schema-based type conversion
- Nested objects and arrays
- JSON Schema validation
- Missing field and error reporting
- Deterministic processing without invented values

### AgentRoute

Discover the appropriate Extendivo API based on required capabilities.

- Capability-based service selection
- Price-aware routing
- Alternative endpoint recommendations
- Machine-readable payment information
- Extendivo catalog discovery

AgentRoute recommends endpoints within the Extendivo catalog. It does not automatically execute or pay for the recommended services.

## Payment Protocol

| Property | Value |
|---|---|
| Protocol | x402 v2 |
| Network | Base Mainnet |
| Network identifier | `eip155:8453` |
| Currency | USDC |
| Token decimals | 6 |
| Payment scheme | `exact` |
| Billing | Pay per request |
| Subscription | Not required |
| API key | Not required |

USDC contract on Base:

`0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`

Clients should validate the payment requirements returned by the endpoint before authorizing a payment.

## Quick Start

Request the payment requirements for SafeFetch:

```bash
curl -i -X POST \
  https://api.extendivo.com/v1/safe-fetch \
  -H "Content-Type: application/json" \
  -d '{"url":"https://example.com"}'
```

A valid unpaid request returns HTTP 402 with x402 payment requirements.

An x402-compatible client can then authorize the payment and retry the request with the required payment signature.

## OpenAPI Specification

The complete Extendivo API portfolio is available through a unified OpenAPI specification.

- [Portfolio OpenAPI JSON](https://api.extendivo.com/portfolio/openapi.json)
- [SafeFetch integration example](https://github.com/Extendivo/extendivo-safefetch-example)

Clients should use the current OpenAPI specification for endpoint-specific request and response schemas.

## Designed for AI Agents

Extendivo services can be combined into automated workflows:

1. Select an appropriate service with AgentRoute.
2. Validate the proposed API request with ContractGuard.
3. Retrieve web content or documents with SafeFetch or SafeDoc.
4. Assess prompt-injection risks with SafeFetch Secure.
5. Validate returned data with ResultGuard.
6. Transform data into the required structure with DataShape.
7. Detect and document content changes with ChangeProof.

Each service is independently accessible and priced per request.

## Security and Reliability

Extendivo is designed around explicit validation, structured responses and security-aware processing.

Security controls and validation results reduce operational risks but do not eliminate every possible threat. Agents remain responsible for validating payment requirements, interpreting results and enforcing their own security policies.

## Official Resources

- Website: https://extendivo.com
- API: https://api.extendivo.com
- GitHub: https://github.com/Extendivo
- Contact: hello@extendivo.com
- x402 Protocol: https://www.x402.org

## Repository Scope

This repository provides public API documentation and integration resources.

The hosted Extendivo API services and their server-side implementations are not distributed through this repository.

---

**Extendivo — Secure infrastructure for the autonomous agent economy.**
