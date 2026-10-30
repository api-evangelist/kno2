# Kno2

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Kno2 provides Interoperability as a Service for healthcare - a single Communication API to SEND, RECEIVE, and FIND patient information across the healthcare ecosystem. One connection reaches Direct Secure Messaging, clinical document exchange, HL7 FHIR resources, HL7 V2.x, cloud fax, and national record location and retrieval through Kno2's private network, Carequality, eHealth Exchange, and TEFCA (Kno2 is a federally designated QHIN). API access is partner/enterprise gated - integrators are provisioned a per-subscription tenant host with OAuth2 client-credentials keys and an IP allowlist; a staging sandbox is available through the Kno2 Developer Program.

**Areas:** Interoperability · Clinical Records · Health Information Exchange · Direct Secure Messaging · FHIR · Clinical Documents · Patient Records · Healthcare · HIE · Care Coordination · QHIN · TEFCA

## Kno2 on APIs.io

Everything profiled for Kno2 is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/kno2/](https://apis.io/providers/kno2/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [Kno2 FHIR API](https://apis.io/apis/kno2/kno2-fhir-api/) — HL7 FHIR (DSTU3/R4) resource query and retrieval at scale, including USCDI data classes and patient demographic search, brokered through Kno2's gateway to…
- [Kno2 Patient Record Query API](https://apis.io/apis/kno2/kno2-record-query-api/) — On-demand patient record location and retrieval across national networks - Kno2's private network, Carequality, eHealth Exchange, and TEFCA (Kno2 is a…
- [Kno2 Attachments API](https://apis.io/apis/kno2/kno2-attachments-api/) — Upload, retrieve, and mark clinical document attachments.
- [Kno2 Authentication API](https://apis.io/apis/kno2/kno2-authentication-api/) — OAuth2 client-credentials token issuance.
- [Kno2 Directory API](https://apis.io/apis/kno2/kno2-directory-api/) — Validate Direct addresses and list document types.
- [Kno2 Intake API](https://apis.io/apis/kno2/kno2-intake-api/) — RECEIVE surface - search, retrieve, and process inbound messages.
- [Kno2 Messaging API](https://apis.io/apis/kno2/kno2-messaging-api/) — SEND surface - draft, populate, attach, and send messages.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [kno2](https://apis.io/servers/kno2/kno2/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Kno2 Agentic Access](https://apis.io/agentic-access/kno2/kno2-agentic-access/)

#### Collections (6)

Postman and Open Collection request collections.

- [Kno2 Communication API](https://apis.io/collections/kno2/open-kno2/)
- [Kno2 Communication Attachments API](https://apis.io/collections/kno2/open-kno2-attachments-api/)
- [Kno2 Communication Attachments Authentication API](https://apis.io/collections/kno2/open-kno2-authentication-api/)
- [Kno2 Communication Attachments Directory API](https://apis.io/collections/kno2/open-kno2-directory-api/)
- [Kno2 Communication Attachments Intake API](https://apis.io/collections/kno2/open-kno2-intake-api/)
- [Kno2 Communication Attachments Messaging API](https://apis.io/collections/kno2/open-kno2-messaging-api/)

#### Overlays (5)

OpenAPI overlays, including conversational phrasing for each operation.

- [Kno2 Attachments Api Overlay](https://apis.io/overlays/kno2/kno2-attachments-api-overlay/)
- [Kno2 Authentication Api Overlay](https://apis.io/overlays/kno2/kno2-authentication-api-overlay/)
- [Kno2 Directory Api Overlay](https://apis.io/overlays/kno2/kno2-directory-api-overlay/)
- [Kno2 Intake Api Overlay](https://apis.io/overlays/kno2/kno2-intake-api-overlay/)
- [Kno2 Messaging Api Overlay](https://apis.io/overlays/kno2/kno2-messaging-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Kno2 Authentication](https://apis.io/security/kno2/kno2-authentication/)
- [Kno2 Domain Security](https://apis.io/security/kno2/kno2-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Kno2 Plans Pricing](https://apis.io/plans/kno2/kno2-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Kno2 Rate Limits](https://apis.io/rate-limits/kno2/kno2-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Kno2 Finops](https://apis.io/finops/kno2/kno2-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://kno2.com)
- [Documentation](https://developer.kno2.com)
- [API reference](https://developer.kno2.com)
- [Sign up](https://kno2.com/request-a-demo/)
- [Support](https://kno2.com/contact/)
- [Blog](https://kno2.com/resources/blog/)
- [Terms of service](https://kno2.com/terms/)
- [Privacy policy](https://kno2.com/privacy-policy/)
- [GitHub](https://github.com/Kno2)
- [Status](https://status.kno2.com)

## API Evangelist rating

**Kin Score 36.2** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 50.9 |
| Contract governance | 4.5 |
| Operational transparency | 26.3 |
| Developer ergonomics | 38.7 |
| Access clarity | 22.4 |

**Agent readiness 22.0** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 16.4** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/kno2/](https://apis.io/providers/kno2/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Kno2: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/kno2/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
