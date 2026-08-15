---
name: Send a message via Kno2 Direct Secure Messaging
description: Authenticate, validate a recipient Direct address, draft a message with a clinical document attachment, and send it through the Kno2 Communication API.
api: openapi/kno2-messaging-api-openapi.yml
operations:
  - createToken
  - validateAddresses
  - createMessageDraft
  - uploadAttachment
  - sendMessage
---

# Send a message via Kno2 Direct Secure Messaging

Ground every call in the real `operationId`s below - they come straight out of
`openapi/kno2-authentication-api-openapi.yml`, `openapi/kno2-directory-api-openapi.yml`,
`openapi/kno2-messaging-api-openapi.yml`, and `openapi/kno2-attachments-api-openapi.yml`.

## 1. Authenticate (`createToken`)

`POST /api/token` with HTTP Basic `base64(client_id:client_secret)` and
`grant_type=client_credentials`. Response is an `AuthResponse` with
`access_token`, `token_type`, and `expires_in`. Use `Authorization: Bearer <access_token>`
on every subsequent call. See `authentication/kno2-authentication.yml` - your
public IP must be allowlisted by a Kno2 admin before any call succeeds.

## 2. Validate the recipient address (`validateAddresses`)

`GET /api/directory/validate?addresses=<direct-address>` before drafting a
message. The response is a map of address to boolean validity - do not draft
or send to an address that comes back `false`.

## 3. Create a message draft (`createMessageDraft`)

`PUT /api/messages` with a `Message` body (`subject`, `patient`, `recipients`,
`documentType`). The response carries the new message `id` and `status: draft`.

## 4. Attach the clinical document (`uploadAttachment`)

`POST /api/messages/{id}/attachments/{attachmentId}` with the document bytes
and `mediaType` (e.g. `application/pdf`). Repeat for each attachment.

## 5. Send the message (`sendMessage`)

`POST /api/messages/{id}/send`. There is no idempotency-key parameter
documented on this operation (see `conventions/kno2-conventions.yml`) - do not
retry a send blindly on a timeout; check message `status` via `getMessage`
before resending.

## Error handling

Every call above can return `401 Unauthorized` (token missing/expired -
re-authenticate) with only a plain description, no structured error body -
see `errors/kno2-problem-types.yml`. There is no documented rate-limit
response header; back off and retry with jitter on repeated failures per
`rate-limits/kno2-rate-limits.yml`.
