# Kno2 (kno2)

Kno2 provides **Interoperability as a Service** for healthcare - a single Communication API to **SEND, RECEIVE, and FIND** patient information across the healthcare ecosystem. One connection reaches Direct Secure Messaging, clinical document exchange, HL7 FHIR resources, HL7 V2.x, cloud fax, and national record location and retrieval through Kno2's private network, Carequality, eHealth Exchange, and TEFCA. Kno2 is a federally designated Qualified Health Information Network (QHIN) and a Carequality implementor.

## Access model (read first)

Kno2's API is **partner / enterprise gated - there is no self-service public API host and no public base URL.** Onboarding runs through the **Kno2 Developer Program** and the login-walled developer portal at [developer.kno2.com](https://developer.kno2.com) (ReadMe-hosted).

- **Per-subscription tenant host.** Each integrator is provisioned its own tenant, e.g. `https://{subscription}.kno2fy.com` in production and `https://{subscription}.kno2-stage.com` in the staging sandbox.
- **OAuth2 client credentials.** You are issued a client id, client secret, and app id. You exchange `base64(client_id:client_secret)` at `POST /api/token` (grant_type `client_credentials`) for a Bearer access token; a `refresh_token` grant is also supported.
- **IP allowlist.** Your calling machine's public IP address must be allowlisted by a Kno2 admin. TLS 1.2 or higher is required.
- **HIPAA / regulated exchange.** This is protected health information (PHI) exchange. Use is governed by HIPAA and Kno2's network/QHIN participation agreements.

## How this entry was sourced

The endpoint paths, HTTP verbs, and OAuth2 token flow below are **confirmed** from Kno2's own open-source integrator reference, the [Kno2.ApiTestClient](https://github.com/Kno2/Kno2.ApiTestClient) (its `app.config` URI templates and `ApiHelper.cs`). Request/response **schemas are modeled** from that client plus Kno2 product documentation, because field-level contracts live behind the login-walled developer portal. Kno2's **FHIR** resource query and **cross-network record retrieval** (Carequality / eHealth Exchange / TEFCA) are real documented products, but their specific endpoint paths are partner-provisioned and not public, so they are described here without invented paths.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/kno2/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/kno2/refs/heads/main/apis.yml)

## Tags

- Healthcare Interoperability
- Clinical Records
- Health Information Exchange
- Direct Secure Messaging
- FHIR
- Clinical Documents
- Patient Records
- Healthcare
- HIE
- Care Coordination
- QHIN
- TEFCA
- Carequality

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Kno2 Messaging API (confirmed)

The SEND surface. Request a draft message, populate it with the patient, recipient Direct address, document type, and metadata, attach one or more clinical documents (CCDA, PDF, images, HL7), then send it as Direct Secure Messaging or document exchange.

- **Base URL:** `https://{subscription}.kno2fy.com`
- `PUT /api/messages` — request a new draft message
- `PUT /api/messages/{id}` — populate/update the draft (patient, recipients, document type)
- `POST /api/messages/{id}/attachments/{attachmentId}` — upload a clinical document (multipart)
- `POST /api/messages/{id}/send` — send/release the message

### Kno2 Intake and Retrieval API (confirmed)

The RECEIVE / FIND surface. Poll the intake queue for inbound messages awaiting EMR export, retrieve messages and attachment content, mark attachments read, and process messages.

- `GET /api/messages?statuses=processed&processedtypes=AwaitingEMRExport` — find intake messages
- `GET /api/messages/{id}` — retrieve a message
- `GET /api/messages/{id}/attachments/{attachmentId}` — retrieve attachment metadata/content
- `PUT /api/messages/{id}/attachments/{attachmentId}/read` — mark attachment read
- `POST /api/messages/{id}/process` — process / record read event

### Kno2 Directory API (confirmed)

- `GET /api/directory/validate?addresses=...` — validate Direct Secure Messaging addresses
- `GET /api/documenttypes` — list document types available to the subscription

### Kno2 FHIR API (modeled)

HL7 FHIR (DSTU3 / R4) resource query and retrieval at scale, including USCDI data classes and patient demographic search, brokered through Kno2's gateway to Carequality and national FHIR endpoints. Documented as a product capability of the Communication API; specific FHIR base URL and resource paths are partner-provisioned and not publicly documented.

- **Reference:** [Kno2 FHIR connectivity brief](https://kno2.com/wp-content/uploads/2022/09/Kno2-Connectivity-FHIR-2.1.pdf)

### Kno2 Patient Record Query API (modeled)

On-demand patient record location and retrieval across national networks - Kno2's private network, Carequality, eHealth Exchange, and TEFCA (Kno2 is a designated QHIN). Documented product capability; specific query/retrieve endpoint paths are partner-provisioned and not publicly documented.

## Common Properties

- [Domain Security](security/kno2-domain-security.yml)
- [Authentication](authentication/kno2-authentication.yml)
- [GitHub Organization](https://github.com/Kno2)
- [LinkedIn](https://www.linkedin.com/company/kno2)
- [Website](https://kno2.com)
- [Documentation](https://developer.kno2.com)
- [Plans](plans/kno2-plans-pricing.yml)
- [Rate Limits](rate-limits/kno2-rate-limits.yml)
- [Fin Ops](finops/kno2-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
