# sensible-so (sensible-so)

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
