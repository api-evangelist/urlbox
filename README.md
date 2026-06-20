# Urlbox (urlbox)

Urlbox is a website screenshot and rendering API that captures pixel-perfect screenshots, PDFs, and video (MP4/WebM) of any web page or raw HTML. Renders are requested synchronously, asynchronously (with polling or webhooks), or via signed HMAC render links, with hundreds of options for full-page capture, element selectors, PDF layout, ad/cookie-banner blocking, waiting, and S3 storage.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/urlbox/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/urlbox/refs/heads/main/apis.yml)

## Tags

- Screenshots
- Rendering
- PDF
- Video
- Web Capture

## Timestamps

- **Created:** 2026-06-20
- **Modified:** 2026-06-20

## APIs

### Urlbox Synchronous Render API

POST /render/sync renders a screenshot, PDF, or video of a URL or HTML and blocks until the asset is ready, returning a temporary renderUrl plus size, renderTime, queueTime, and bandwidth metrics.

- **Human URL:** [https://urlbox.com/docs/api](https://urlbox.com/docs/api)
- **Base URL:** `https://api.urlbox.com/v1`

#### Tags

- Screenshots
- PDF
- Video
- Sync

#### Properties

- [Documentation](https://urlbox.com/docs/api)
- [API Reference](https://urlbox.com/docs/api)
- [OpenAPI](openapi/urlbox-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/urlbox.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/urlbox.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Urlbox Asynchronous Render API

POST /render/async accepts the same render options and returns immediately with a renderId and statusUrl (201 Created); the render is processed in the background and results are retrieved by polling or via a webhook callback.

- **Human URL:** [https://urlbox.com/docs/guides/sync-vs-async](https://urlbox.com/docs/guides/sync-vs-async)
- **Base URL:** `https://api.urlbox.com/v1`

#### Tags

- Async
- Queue
- Webhooks

#### Properties

- [Documentation](https://urlbox.com/docs/guides/sync-vs-async)
- [OpenAPI](openapi/urlbox-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/urlbox.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/urlbox.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Urlbox Render Status API

GET /render/{renderId} polls the status of an asynchronous render, returning created, retrying, succeeded, failed, or not-found, along with the renderUrl and size once the render has succeeded.

- **Human URL:** [https://urlbox.com/docs/api](https://urlbox.com/docs/api)
- **Base URL:** `https://api.urlbox.com/v1`

#### Tags

- Status
- Polling

#### Properties

- [Documentation](https://urlbox.com/docs/api)
- [OpenAPI](openapi/urlbox-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/urlbox.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/urlbox.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Urlbox Render Links API

GET /{api_key}/{token}/{format} returns a render directly from a stateless, cacheable URL, where token is an HMAC-SHA256 signature of the URL-encoded options query string generated server-side with the project secret.

- **Human URL:** [https://urlbox.com/docs/render-links](https://urlbox.com/docs/render-links)
- **Base URL:** `https://api.urlbox.com/v1`

#### Tags

- Render Links
- HMAC
- Signed URL

#### Properties

- [Documentation](https://urlbox.com/docs/render-links)
- [OpenAPI](openapi/urlbox-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/urlbox.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/urlbox.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Urlbox Webhooks API

Async renders configured with a webhook_url receive a POST callback carrying render.succeeded or render.failed events with the result payload, verified via the X-Urlbox-Signature HMAC-SHA256 header.

- **Human URL:** [https://urlbox.com/docs/webhooks](https://urlbox.com/docs/webhooks)
- **Base URL:** `https://api.urlbox.com/v1`

#### Tags

- Webhooks
- Callbacks
- Events

#### Properties

- [Documentation](https://urlbox.com/docs/webhooks)
- [OpenAPI](openapi/urlbox-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Review](review.yml)

### Urlbox Usage API

Reports renders used, allowed, and remaining for the current billing period; usage is also surfaced on every render response via x-renders-used, x-renders-allowed, and x-renders-remaining headers.

- **Human URL:** [https://urlbox.com/docs/api/get-usage](https://urlbox.com/docs/api/get-usage)
- **Base URL:** `https://api.urlbox.com/v1`

#### Tags

- Usage
- Quota
- Account

#### Properties

- [Documentation](https://urlbox.com/docs/api/get-usage)
- [OpenAPI](openapi/urlbox-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [GitHub Organization](https://github.com/urlbox)
- [LinkedIn](https://www.linkedin.com/company/urlbox)
- [Website](https://urlbox.com)
- [Documentation](https://urlbox.com/docs)
- [Plans](plans/urlbox-plans-pricing.yml)
- [Rate Limits](rate-limits/urlbox-rate-limits.yml)
- [Fin Ops](finops/urlbox-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
