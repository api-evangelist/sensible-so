# sensible-so (sensible-so)

Sensible is a document-automation API platform that extracts structured data from PDFs, images, spreadsheets, and emails using a hybrid of deterministic layout-based methods and LLM-based query methods. SenseML, Sensible's config language, lets engineers declare what to pull and where. The platform ships with 150+ open-source pre-built configurations across financial services, insurance, logistics, real estate, and healthcare. Sensible exposes sync and async extraction, classification, portfolio segmentation, CSV/Excel export, human review, coverage statistics, configuration versioning, and webhook delivery, all behind a bearer-auth REST surface plus a Postman collection, an MCP server, and Python / JavaScript SDKs.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/sensible-so/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sensible-so/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming

## Timestamps

- **Created:** 2026-05-25T00:00:00.000Z
- **Modified:** 2026-05-25

## APIs

### Sensible Extractions API

Extract structured data from documents synchronously or asynchronously. Supports sync `POST /extract/{document_type}`, async `POST /extract_from_url`, async via Sensible-signed `POST /generate_upload_url`, portfolio (multi-document) extractions, CSV and Excel output, `/extractions` listing and `/documents/{id}` retrieval, daily coverage statistics, and review auth-token issuance for human-in-the-loop workflows. All endpoints are bearer-auth and webhook-capable.

- **Human URL:** [https://docs.sensible.so/reference/extract-data-from-a-document](https://docs.sensible.so/reference/extract-data-from-a-document)

#### Tags

- Document Extraction
- IDP
- Extractions
- Async
- Webhooks

#### Properties

- [Documentation](https://docs.sensible.so/reference/extract-data-from-a-document)
- [Documentation](https://docs.sensible.so/reference/extract-from-url)
- [Documentation](https://docs.sensible.so/reference/generate-an-upload-url)
- [Documentation](https://docs.sensible.so/reference/retrieving-results)
- [Documentation](https://docs.sensible.so/docs/api-tutorial-webhook)
- [OpenAPI](openapi/sensible-extractions-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensible-extractions-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensible-extractions-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/sensible-so-extraction-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/sensible-so-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Example](examples/sensible-so-extract-sync-example.json)
- [Example](examples/sensible-so-extract-from-url-example.json)
- [Example](examples/sensible-so-list-extractions-example.json)

### Sensible Classification API

Classify a document into one of the document types defined in the account, either synchronously (testing) or asynchronously (production). Useful both as a routing step in an extraction workflow and as a standalone labeling service.

- **Human URL:** [https://docs.sensible.so/reference/classify-document](https://docs.sensible.so/reference/classify-document)

#### Tags

- Document Extraction
- Classification
- Routing

#### Properties

- [Documentation](https://docs.sensible.so/reference/classify-document)
- [Documentation](https://docs.sensible.so/reference/classify-document-sync)
- [Documentation](https://docs.sensible.so/docs/classify)
- [OpenAPI](openapi/sensible-classification-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensible-classification-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensible-classification-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Example](examples/sensible-so-classify-async-example.json)

### Sensible Document Types and Configurations API

Manage Sensible document types and SenseML configurations. Create, list, fetch, update, and delete document types; create, list, fetch, update, publish, version, and delete SenseML configurations; list versions for a configuration; promote drafts through development and production environments.

- **Human URL:** [https://docs.sensible.so/reference/list-document-types](https://docs.sensible.so/reference/list-document-types)

#### Tags

- Document Extraction
- Document Types
- Configurations
- SenseML
- Versioning

#### Properties

- [Documentation](https://docs.sensible.so/reference/list-document-types)
- [Documentation](https://docs.sensible.so/reference/create-configuration)
- [Documentation](https://docs.sensible.so/reference/publish-configuration-by-version)
- [Documentation](https://docs.sensible.so/docs/senseml-reference-introduction)
- [JSON Schema](https://schema.sensible.so/configuration.schema.json) — [JSON Schema](https://json-schema.org/specification)
- [OpenAPI](openapi/sensible-document-types-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensible-document-types-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensible-document-types-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/sensible-so-document-type-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Example](examples/sensible-so-create-document-type-example.json)

### Sensible Reference Documents API

Manage reference PDFs ("goldens") associated with document types. Create with a pre-signed upload URL, list, get metadata, update metadata, delete, associate or unassociate with a configuration, and extract all standardized text lines from a reference document for layout tuning.

- **Human URL:** [https://docs.sensible.so/reference/list-reference-documents](https://docs.sensible.so/reference/list-reference-documents)

#### Tags

- Document Extraction
- Reference Documents
- Goldens

#### Properties

- [Documentation](https://docs.sensible.so/reference/list-reference-documents)
- [Documentation](https://docs.sensible.so/reference/create-reference-document)
- [Documentation](https://docs.sensible.so/reference/extract-all-text-from-reference-document)
- [OpenAPI](openapi/sensible-reference-documents-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensible-reference-documents-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensible-reference-documents-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Portal](https://www.sensible.so)
- [Documentation](https://docs.sensible.so)
- [Documentation](https://docs.sensible.so/reference)
- [Changelog](https://docs.sensible.so/changelog)
- [Authentication](https://docs.sensible.so/reference/authentication)
- [Getting Started](https://docs.sensible.so/docs/quickstart)
- [Getting Started](https://docs.sensible.so/docs/api-tutorial)
- [Documentation](https://docs.sensible.so/llms.txt)
- [Status Page](https://sensible.statuspage.io)
- [Sign Up](https://app.sensible.so/register)
- [Account](https://app.sensible.so/account)
- [Pricing](https://www.sensible.so/pricing)
- [Documentation](https://docs.sensible.so/reference/mcp)
- [M C P Server](https://docs.sensible.so/mcp)
- [GitHub Organization](https://github.com/sensible-hq)
- [SDK](https://github.com/sensible-hq/sensible-api-py)
- [SDK](https://github.com/sensible-hq/sensible-api-js)
- [SDK](https://github.com/sensible-hq/sensible-code-examples)
- [Samples](https://github.com/sensible-hq/sensible-configuration-library)
- [Samples](https://github.com/sensible-hq/sensible-sample-documents)
- [Integrations](https://github.com/sensible-hq/sensible-salesforce-py)
- [Integrations](https://github.com/sensible-hq/sensible-quickbooks-py)
- [Postman](https://god.gw.postman.com/run-collection/16839934-45339059-3fec-4c31-a891-9a12a3e1c22b) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Integrations](https://docs.sensible.so/docs/zapier)
- [Plans](plans/sensible-so-plans-pricing.yml)
- [Rate Limits](rate-limits/sensible-so-rate-limits.yml)
- [Fin Ops](finops/sensible-so-finops.yml)
- [Vocabulary](vocabulary/sensible-so-vocabulary.yml)
- [Spectral Rules](rules/sensible-so-rules.yml)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
