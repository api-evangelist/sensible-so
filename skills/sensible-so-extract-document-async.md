---
name: sensible-so-extract-document-async
description: Extract structured data from a document with Sensible using the asynchronous URL flow, then poll or receive a webhook for the result.
api: sensible-so
generated: '2026-09-17'
method: generated
source: openapi/sensible-so-document-api-openapi.yml, openapi/sensible-so-retrieve-extractions-api-openapi.yml, arazzo/sensible-so-extract-from-url-and-poll-workflow.yml
operations:
  - provide-a-download-url-with-config
  - retrieving-results
base_url: https://api.sensible.so/v0
auth: Authorization Bearer <SENSIBLE_API_KEY>
---

# Extract data from a document (asynchronous)

Use this when the document lives at a URL the Sensible service can reach, and you do not
want to hold a connection open while extraction runs.

## Before you start

- You need a document type that already exists in the account. List them with
  `list-document-types` (`GET /document_types`) rather than guessing a name.
- Extraction endpoints address the document type by **name**, not by UUID. The management
  endpoints use the UUID. Do not mix them up.
- Every completed extraction is a billed document. See `plans/sensible-so-plans-pricing.yml`.

## Steps

1. **Start the extraction.** `provide-a-download-url-with-config` —
   `POST /extract_from_url/{document_type}/{config_name}` with
   `{"document_url": "<https url>"}`. Add a `webhook` object
   (`{"url": "...", "payload": "..."}`) if you want a push instead of a poll.
   The response carries an extraction `id`.
2. **Wait for the result.** Either:
   - **Poll** `retrieving-results` — `GET /documents/{id}` — until `status` is `COMPLETE`
     or `FAILED`. Status moves `WAITING` → `PROCESSING` → `COMPLETE` | `FAILED`.
   - **Receive the webhook** — Sensible POSTs `parsed_document` plus your `webhook` object
     when status reaches `COMPLETE` or `FAILED`.
3. **Read the result.** `parsed_document` holds the extracted fields. Also read
   `validations`, `coverage` and `errors` before trusting the values. Fields can be null —
   the Sensible go-live checklist calls this out explicitly.
4. **If review is required**, `reviewStatus` is `NEEDS_REVIEW`. A second webhook fires when
   it changes to `APPROVED` or `REJECTED`.

## Rules that apply

- **No idempotency.** There is no `Idempotency-Key` header. A retried POST starts a second
  extraction and bills for it. Record the extraction `id` from the first response before
  retrying anything.
- **No reversal.** There is no cancel, void or refund operation for an extraction.
- **Errors are text/plain**, not RFC 9457 — branch on the HTTP status, not on a body field.
  `429` means *either* a transient throttle *or* a monthly quota that is spent, and the two
  are distinguishable only by reading the prose. See `errors/sensible-so-problem-types.yml`.
- **No Retry-After header.** Back off on your own schedule.
