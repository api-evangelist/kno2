---
name: Process an inbound Kno2 message
description: Authenticate, poll for new inbound messages, retrieve and read attachments, and mark the message processed on the Kno2 Communication API.
api: openapi/kno2-intake-api-openapi.yml
operations:
  - createToken
  - searchMessages
  - getMessage
  - getAttachment
  - markAttachmentRead
  - processMessage
---

# Process an inbound Kno2 message

Ground every call in the real `operationId`s below - from
`openapi/kno2-authentication-api-openapi.yml`, `openapi/kno2-intake-api-openapi.yml`,
and `openapi/kno2-attachments-api-openapi.yml`.

## 1. Authenticate (`createToken`)

Same client-credentials flow as `skills/kno2-send-a-message.md` - see
`authentication/kno2-authentication.yml`.

## 2. Poll for new messages (`searchMessages`)

`GET /api/messages`. There is no cursor/offset pagination documented (see
`conventions/kno2-conventions.yml`) - Kno2's own reference client
(`Kno2.ApiTestClient`) polls this endpoint in a loop with a ~10 second wait
between empty polls. Mirror that cadence; do not poll continuously.

## 3. Retrieve the message (`getMessage`)

`GET /api/messages/{id}`. Returns the full `Message` object, including
`patient` demographics and the `attachments` array. Can return `404` if the
message id no longer exists.

## 4. Retrieve and mark each attachment (`getAttachment`, `markAttachmentRead`)

For each entry in `attachments`: `GET /api/messages/{id}/attachments/{attachmentId}`
to fetch the clinical document, then `PUT /api/messages/{id}/attachments/{attachmentId}/read`
once your system has consumed it.

## 5. Mark the message processed (`processMessage`)

`POST /api/messages/{id}/process` once every attachment has been retrieved and
handled. This is the terminal step in the RECEIVE flow.

## Error handling

`401 Unauthorized` (re-authenticate) and `404 Not Found` (message no longer
exists) are the only documented error statuses, each a plain description with
no structured body - see `errors/kno2-problem-types.yml`.
