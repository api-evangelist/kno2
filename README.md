# Kno2 (kno2)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
