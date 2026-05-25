# Sensible (sensible-so)
Sensible is a document-automation API platform that extracts structured data from PDFs, images, spreadsheets, and emails using a hybrid of deterministic layout-based methods and LLM-based query methods. SenseML, Sensible's config language, lets engineers declare what to pull and where. The platform ships with 150+ open-source pre-built configurations across financial services, insurance, logistics, real estate, and healthcare. Sensible exposes sync and async extraction, classification, portfolio segmentation, CSV/Excel export, human review, coverage statistics, configuration versioning, and webhook delivery, all behind a bearer-auth REST surface plus a Postman collection, an MCP server, and Python / JavaScript SDKs.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/sensible-so/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Document Extraction, IDP, SenseML, Classification, OCR, LLM, Webhooks, Document Types, Configurations, Reference Documents

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Sensible Extractions API
Extract structured data from documents synchronously or asynchronously. Sync `POST /extract/{document_type}` for testing; async `POST /extract_from_url` and `POST /generate_upload_url` for production. Portfolio extractions segment a packaged PDF into multiple document types. CSV and Excel output for one or many extractions. Daily coverage statistics per configuration. Webhook delivery on COMPLETE or human-review APPROVED.

**Human URL:** [https://docs.sensible.so/reference/extract-data-from-a-document](https://docs.sensible.so/reference/extract-data-from-a-document)

- [Documentation — Sync extract](https://docs.sensible.so/reference/extract-data-from-a-document)
- [Documentation — Async from URL](https://docs.sensible.so/reference/extract-from-url)
- [Documentation — Async upload URL](https://docs.sensible.so/reference/generate-an-upload-url)
- [Documentation — Retrieve by id](https://docs.sensible.so/reference/retrieving-results)
- [Documentation — Webhooks tutorial](https://docs.sensible.so/docs/api-tutorial-webhook)
- [OpenAPI](openapi/sensible-extractions-api-openapi.yml)
- [JSON Schema — Extraction](json-schema/sensible-so-extraction-schema.json)
- [JSON-LD](json-ld/sensible-so-context.jsonld)
- [Naftiko Capability — Extractions](capabilities/extractions-extractions.yaml)
- [Example — Sync extract](examples/sensible-so-extract-sync-example.json)
- [Example — Async extract from URL](examples/sensible-so-extract-from-url-example.json)
- [Example — List extractions](examples/sensible-so-list-extractions-example.json)

### Sensible Classification API
Classify a document into one of the document types defined in the account. Sync `POST /classify` for testing; async `POST /classify/async` for production. Useful both as a routing step ahead of extraction and as a standalone labeling service.

**Human URL:** [https://docs.sensible.so/reference/classify-document](https://docs.sensible.so/reference/classify-document)

- [Documentation — Async](https://docs.sensible.so/reference/classify-document)
- [Documentation — Sync](https://docs.sensible.so/reference/classify-document-sync)
- [OpenAPI](openapi/sensible-classification-api-openapi.yml)
- [Naftiko Capability — Classification](capabilities/classification-classification.yaml)
- [Example — Classify async](examples/sensible-so-classify-async-example.json)

### Sensible Document Types and Configurations API
Manage Sensible document types and SenseML configurations. Create, list, fetch, update, and delete document types; create, list, fetch, update, publish, version, and delete SenseML configurations; list versions; promote drafts through development and production environments.

**Human URL:** [https://docs.sensible.so/reference/list-document-types](https://docs.sensible.so/reference/list-document-types)

- [Documentation — Document types](https://docs.sensible.so/reference/list-document-types)
- [Documentation — Configurations](https://docs.sensible.so/reference/create-configuration)
- [Documentation — Publish configuration](https://docs.sensible.so/reference/publish-configuration-by-version)
- [SenseML reference](https://docs.sensible.so/docs/senseml-reference-introduction)
- [Configuration schema (Sensible)](https://schema.sensible.so/configuration.schema.json)
- [OpenAPI](openapi/sensible-document-types-api-openapi.yml)
- [JSON Schema — Document Type](json-schema/sensible-so-document-type-schema.json)
- [Naftiko Capability — Document Types](capabilities/document-types-document-types.yaml)
- [Example — Create document type](examples/sensible-so-create-document-type-example.json)

### Sensible Reference Documents API
Manage reference PDFs ("goldens") associated with document types. Create with pre-signed upload URL, list, get metadata, update metadata, delete, associate or unassociate with a configuration, and extract all standardized text lines from a reference document for layout tuning.

**Human URL:** [https://docs.sensible.so/reference/list-reference-documents](https://docs.sensible.so/reference/list-reference-documents)

- [Documentation — List goldens](https://docs.sensible.so/reference/list-reference-documents)
- [Documentation — Create golden](https://docs.sensible.so/reference/create-reference-document)
- [Documentation — Extract all text](https://docs.sensible.so/reference/extract-all-text-from-reference-document)
- [OpenAPI](openapi/sensible-reference-documents-api-openapi.yml)
- [Naftiko Capability — Reference Documents](capabilities/reference-documents-reference-documents.yaml)

## Common Properties

- [Portal](https://www.sensible.so)
- [Documentation home](https://docs.sensible.so)
- [API reference](https://docs.sensible.so/reference)
- [Changelog](https://docs.sensible.so/changelog)
- [Authentication](https://docs.sensible.so/reference/authentication)
- [Getting started — Quickstart](https://docs.sensible.so/docs/quickstart)
- [Getting started — API tutorial](https://docs.sensible.so/docs/api-tutorial)
- [llms.txt](https://docs.sensible.so/llms.txt)
- [Status page](https://sensible.statuspage.io)
- [Sign up](https://app.sensible.so/register)
- [Account & API keys](https://app.sensible.so/account)
- [Pricing](https://www.sensible.so/pricing)
- [Sensible MCP server (docs)](https://docs.sensible.so/reference/mcp)
- [Sensible MCP endpoint](https://docs.sensible.so/mcp)
- [GitHub organization — sensible-hq](https://github.com/sensible-hq)
- [Python SDK](https://github.com/sensible-hq/sensible-api-py)
- [JavaScript / TypeScript SDK](https://github.com/sensible-hq/sensible-api-js)
- [Code examples](https://github.com/sensible-hq/sensible-code-examples)
- [SenseML configuration library (150+ types)](https://github.com/sensible-hq/sensible-configuration-library)
- [Sample documents](https://github.com/sensible-hq/sensible-sample-documents)
- [Salesforce integration example](https://github.com/sensible-hq/sensible-salesforce-py)
- [QuickBooks integration example](https://github.com/sensible-hq/sensible-quickbooks-py)
- [Postman collection](https://god.gw.postman.com/run-collection/16839934-45339059-3fec-4c31-a891-9a12a3e1c22b)
- [Zapier app](https://docs.sensible.so/docs/zapier)
- [Plans & pricing (API Commons)](plans/sensible-so-plans-pricing.yml)
- [Rate limits (API Commons)](rate-limits/sensible-so-rate-limits.yml)
- [FinOps (FOCUS-aligned)](finops/sensible-so-finops.yml)
- [Vocabulary](vocabulary/sensible-so-vocabulary.yml)
- [Spectral ruleset](rules/sensible-so-rules.yml)

## Plans

| Plan | Monthly | Annual | Included Extractions | Overage | API Calls/sec | Human Review |
|---|---|---|---|---|---|---|
| Free Trial | $0 | — | Growth allotment for 14 days | — | 1 | — |
| Growth | $499 | $449 | 750 | $0.50 / doc | 1 | — |
| Scale | $1,499 | $1,349 | 3,200 | $0.50 / doc | 10 | Included |
| Enterprise | Custom | Custom | 10,000+ tiered | Tiered | 25+ | Included |

All plans include unlimited document layouts and data fields, unlimited reference documents, automatic and selective OCR, computer vision-enhanced table detection, invoice recognition, and document splitting. Enterprise adds HIPAA, custom data retention, custom region, custom SLA, and a dedicated CSM.

## Authentication

Bearer API key. Create keys at [https://app.sensible.so/account](https://app.sensible.so/account). Pass as `Authorization: Bearer <YOUR_API_KEY>`. Optional recoverable / nonrecoverable key tiers.

## Base URL

`https://api.sensible.so/v0`

## Sample call (sync extract)

```bash
curl --request POST \
     --url "https://api.sensible.so/v0/extract/bank_statement" \
     --header "Authorization: Bearer YOUR_API_KEY" \
     --header "Content-Type: application/pdf" \
     --data-binary "@your_doc.pdf"
```

## Maintainer

- **FN:** Kin Lane
- **Email:** info@apievangelist.com
- **URL:** [https://apievangelist.com](https://apievangelist.com)
