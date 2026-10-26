# Urlbox (urlbox)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
