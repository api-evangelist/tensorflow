# TensorFlow

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

TensorFlow is an end-to-end open source machine learning platform developed by Google. It provides a comprehensive ecosystem of tools, libraries, and community resources for building and deploying ML-powered applications, including model training, serving, mobile/edge deployment, and a hub of pre-trained models. TensorFlow Serving exposes REST and gRPC APIs for production model inference.

**Areas:** Artificial Intelligence · Deep Learning · JavaScript · Machine Learning · Model Serving · Neural Networks · Open Source · Python

## TensorFlow on APIs.io

Everything profiled for TensorFlow is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/tensorflow/](https://apis.io/providers/tensorflow/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [TensorFlow Core API](https://apis.io/apis/tensorflow/tensorflow-core/) — The foundational Python and C++ API for building and training machine learning models using TensorFlow.
- [TensorFlow.js API](https://apis.io/apis/tensorflow/tensorflow-js/) — A JavaScript library for training and deploying ML models in the browser and on Node.js.
- [TensorFlow Lite API](https://apis.io/apis/tensorflow/tensorflow-lite/) — Lightweight solution for ML inference on mobile and embedded devices, optimized for on-device model execution.
- [TensorFlow Hub API](https://apis.io/apis/tensorflow/tensorflow-hub/) — A library and repository of reusable pre-trained machine learning modules, enabling transfer learning across text, image, video, and audio domains.
- [TensorBoard API](https://apis.io/apis/tensorflow/tensorboard/) — TensorFlow's visualization toolkit for experiment tracking, model debugging, and performance profiling via an embedded web server with REST endpoints.
- [TensorFlow Inference API](https://apis.io/apis/tensorflow/tensorflow-inference-api/) — Model inference operations including classify, regress, and predict
- [TensorFlow Models API](https://apis.io/apis/tensorflow/tensorflow-models-api/) — Model status and metadata operations

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (7)

Multi-step workflows that chain operations into a business task.

- [TensorFlow Serving Preflight and Classify](https://apis.io/arazzos/tensorflow/tensorflow-classify-preflight-workflow/)
- [TensorFlow Serving Route Inference by Version Label](https://apis.io/arazzos/tensorflow/tensorflow-label-routed-inference-workflow/)
- [TensorFlow Serving Pinned Reproducible Example Scoring](https://apis.io/arazzos/tensorflow/tensorflow-pinned-example-scoring-workflow/)
- [TensorFlow Serving Preflight and Predict](https://apis.io/arazzos/tensorflow/tensorflow-predict-preflight-workflow/)
- [TensorFlow Serving Preflight and Regress](https://apis.io/arazzos/tensorflow/tensorflow-regress-preflight-workflow/)
- [TensorFlow Serving Gate a Rollout on Version Readiness](https://apis.io/arazzos/tensorflow/tensorflow-rollout-readiness-workflow/)
- [TensorFlow Serving Compare a Candidate Version Against the Default](https://apis.io/arazzos/tensorflow/tensorflow-version-canary-compare-workflow/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [tensorflow-serving](https://apis.io/servers/tensorflow/tensorflow-serving/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Tensorflow Agentic Access](https://apis.io/agentic-access/tensorflow/tensorflow-agentic-access/)

#### JSON Schema (3)

The data models the API reads and writes.

- [TensorFlow Serving Model Status Response](https://apis.io/schemas/tensorflow/tensorflow-serving-model-status/)
- [TensorFlow Serving Prediction Request](https://apis.io/schemas/tensorflow/tensorflow-serving-prediction-request/)
- [TensorFlow Serving Prediction Response](https://apis.io/schemas/tensorflow/tensorflow-serving-prediction-response/)

#### JSON Structure (1)

Data models expressed in JSON Structure.

- [Tensorflow Serving Prediction Request Structure](https://apis.io/json-structure/tensorflow/tensorflow-serving-prediction-request-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Tensorflow Context](https://apis.io/jsonld/tensorflow/tensorflow-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [TensorFlow Vocabulary](https://apis.io/vocabularies/tensorflow/tensorflow-vocabulary/)

#### Examples (2)

Example requests and responses.

- [Tensorflow Serving Model Status Example](https://apis.io/examples/tensorflow/tensorflow-serving-model-status-example/)
- [Tensorflow Serving Predict Example](https://apis.io/examples/tensorflow/tensorflow-serving-predict-example/)

#### Collections (3)

Postman and Open Collection request collections.

- [TensorFlow Serving REST Inference API](https://apis.io/collections/tensorflow/open-tensorflow-inference-api/)
- [TensorFlow Serving REST Inference Models API](https://apis.io/collections/tensorflow/open-tensorflow-models-api/)
- [TensorFlow Serving REST API](https://apis.io/collections/tensorflow/open-tensorflow-serving/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Tensorflow Serving Overlay](https://apis.io/overlays/tensorflow/tensorflow-serving-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [TensorFlow — jsonschema rules](https://apis.io/rules/tensorflow/tensorflow-jsonschema-spectral-rules/)
- [TensorFlow — serving rules](https://apis.io/rules/tensorflow/tensorflow-serving-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Tensorflow Authentication](https://apis.io/security/tensorflow/tensorflow-authentication/)
- [Tensorflow Domain Security](https://apis.io/security/tensorflow/tensorflow-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Tensorflow Plans Pricing](https://apis.io/plans/tensorflow/tensorflow-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Tensorflow Rate Limits](https://apis.io/rate-limits/tensorflow/tensorflow-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Tensorflow Finops](https://apis.io/finops/tensorflow/tensorflow-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://tensorflow.org)
- [Blog](https://blog.tensorflow.org/)

## API Evangelist rating

**Kin Score 35.1** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 52.6 |
| Contract governance | 31.8 |
| Operational transparency | 26.3 |
| Developer ergonomics | 42.9 |
| Access clarity | 5.3 |

**Agent readiness 24.9** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | — |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 15.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/tensorflow/](https://apis.io/providers/tensorflow/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for TensorFlow: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/tensorflow/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
