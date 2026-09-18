---
name: sensible-so-publish-configuration
description: Create or update a SenseML extraction configuration under a Sensible document type and publish a version to an environment — including how to unpublish it again.
api: sensible-so
generated: '2026-09-17'
method: generated
source: openapi/sensible-so-configuration-api-openapi.yml, openapi/sensible-so-document-type-api-openapi.yml, arazzo/sensible-so-create-document-type-and-configuration-workflow.yml
operations:
  - create-document-type
  - list-document-types
  - create-configuration
  - update-configuration
  - list-configurations
  - get-configuration-versions
  - get-configuration-by-version
  - delete-configuration-by-version
base_url: https://api.sensible.so/v0
auth: Authorization Bearer <SENSIBLE_API_KEY>
---

# Create and publish an extraction configuration

## Steps

1. **Find or create the document type.** `list-document-types` — `GET /document_types`; if it
   is absent, `create-document-type` — `POST /document_types`. Keep the returned UUID: every
   configuration operation addresses the document type by `{type-id}` UUID.
2. **Write the configuration.** `create-configuration` —
   `POST /document_types/{type-id}/configurations` — with the SenseML config as stringified
   JSON. It must validate against <https://schema.sensible.so/configuration.schema.json>.
   `update-configuration` — `PUT /document_types/{type-id}/configurations/{config-name}` —
   replaces a draft or published version.
3. **Publish to an environment.** There is **no** `publish-configuration-by-version` operation,
   despite the docs page of that name. Publishing is `update-configuration` —
   `PUT /document_types/{type-id}/configurations/{config-name}` — with `publish_as` set to
   `development` or `production`. Omitting `publish_as` saves the version as the current draft
   instead. A version published to an environment must validate against the SenseML schema.
4. **Verify.** `get-configuration-versions` —
   `GET /document_types/{type-id}/configurations/{config-name}/versions` — then
   `get-configuration-by-version` to read back exactly what is live.

## Reversing a publish

This is the one write surface in the Sensible API with a documented reversal:
`delete-configuration-by-version` — `DELETE /document_types/{type-id}/configurations/{config-name}/{version}`
— **unpublishes** when you pass the environment name (for example `development`) in the
`version` parameter, and deletes a draft when you pass a version name.

**No window is stated in the docs, so do not assume one.** And note what is *not* reversible:
`delete-configuration`, `delete-document-type` and `delete-reference-document` have no
published restore. Read back with `get-configuration-by-version` before deleting anything.
