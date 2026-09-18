---
name: sensible-so-classify-document
description: Identify which Sensible document type a document matches, with a confidence score, before spending an extraction on it.
api: sensible-so
generated: '2026-09-17'
method: generated
source: openapi/sensible-so-document-api-openapi.yml, arazzo/sensible-so-classify-then-extract-workflow.yml
operations:
  - classify-document-sync
  - classify-document
  - list-document-types
  - extract-data-from-a-document
base_url: https://api.sensible.so/v0
auth: Authorization Bearer <SENSIBLE_API_KEY>
---

# Classify a document, then extract

Use this when you receive documents of mixed or unknown type and need to route them.

## Steps

1. **Know the candidate types.** `list-document-types` — `GET /document_types` — returns the
   document types configured in the account.
2. **Classify.**
   - Synchronous: `classify-document-sync` — `POST /classify` with the document body.
   - Asynchronous: `classify-document` — `POST /classify/async`, then poll or take the webhook.
   The response carries a `Classification` with a document type name and a `Score`.
3. **Decide with the score, not just the label.** Set your own threshold. A low score means
   route to a human, not extract-and-hope.
4. **Extract against the matched type.** `extract-data-from-a-document` —
   `POST /extract/{document_type}` — using the name the classifier returned.

## Rules that apply

- Classification and extraction are **separate billed calls**. Classifying first costs
  something; it buys you not extracting against the wrong config.
- For a multi-document PDF, do not classify page by page — use the portfolio flow
  (`provide-a-download-url-for-a-pdf-portfolio`), which segments and classifies each member
  document. See `skills/sensible-so-extract-portfolio.md`.
- Same no-idempotency rule as every other mutating call here.
