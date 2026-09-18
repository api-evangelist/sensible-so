---
name: sensible-so-extract-portfolio
description: Split a multi-document PDF into member documents with Sensible and extract each one, then collect the results as a spreadsheet.
api: sensible-so
generated: '2026-09-17'
method: generated
source: openapi/sensible-so-portfolio-api-openapi.yml, openapi/sensible-so-get-excel-from-documents-api-openapi.yml, arazzo/sensible-so-portfolio-extract-from-url-and-poll-workflow.yml
operations:
  - provide-a-download-url-for-a-pdf-portfolio
  - generate-an-upload-url-for-a-pdf-portfolio
  - retrieving-results
  - get-excel-extraction
  - get-csv-extraction
base_url: https://api.sensible.so/v0
auth: Authorization Bearer <SENSIBLE_API_KEY>
---

# Extract a multi-document PDF (portfolio)

Use this for a bundle — a loan file, a claim packet, a closing package — where one PDF
contains several distinct documents.

## Steps

1. **Submit the portfolio.** Either
   `provide-a-download-url-for-a-pdf-portfolio` — `POST /extract_from_url` with
   `{"document_url": ..., "document_types": [...], "segment_documents_with": ...}` — or
   `generate-an-upload-url-for-a-pdf-portfolio` — `POST /generate_upload_url` — when you must
   upload the bytes yourself. Both return an extraction `id`.
2. **Wait.** Poll `retrieving-results` — `GET /documents/{id}` — or take the webhook. The
   portfolio response carries a `documents` array; each member has its own classification,
   parsed document, validations and coverage.
3. **Collect.** `get-excel-extraction` — `GET /generate_excel/{ids}` — or `get-csv-extraction`
   — `GET /generate_csv/{ids}` — with comma-separated extraction ids, to compile one
   spreadsheet across documents.

## Rules that apply

- **Billing is per member document, not per file.** Sensible defines a billed document as one
  extraction result, and each document inside a portfolio counts as one.
- **The spreadsheet download URL expires after 15 minutes.** Fetch it immediately; do not
  store it and come back.
- For a clean compiled spreadsheet, the configs behind the member document types must emit
  identically named fields.
