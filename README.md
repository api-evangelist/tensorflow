# TensorFlow (tensorflow)

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

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/tensorflow/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/tensorflow/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- AI
- Deep Learning
- JavaScript
- Machine Learning
- Model Serving
- Neural Networks
- Open Source
- Python

## Timestamps

- **Created:** 2024-01-15
- **Modified:** 2026-05-19

## APIs

### TensorFlow Serving REST API

A flexible, high-performance serving system for machine learning models designed for production environments. Provides REST endpoints for model status, metadata, classification, regression, and prediction inference.

- **Human URL:** [https://www.tensorflow.org/tfx/serving/api_rest](https://www.tensorflow.org/tfx/serving/api_rest)
- **Base URL:** `http://host:8501`

#### Tags

- Inference
- Model Serving
- Production
- REST API

#### Properties

- [Documentation](https://www.tensorflow.org/tfx/serving/api_rest)
- [Git Hub](https://github.com/tensorflow/serving)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/tensorflow/refs/heads/main/openapi/tensorflow-serving-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/tensorflow-serving.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/tensorflow-serving.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### TensorFlow Core API

The foundational Python and C++ API for building and training machine learning models using TensorFlow.

- **Human URL:** [https://www.tensorflow.org/api_docs/python/tf](https://www.tensorflow.org/api_docs/python/tf)
- **Base URL:** `https://www.tensorflow.org/api_docs`

#### Tags

- Core API
- Machine Learning
- Python

#### Properties

- [Documentation](https://www.tensorflow.org/api_docs/python/tf)
- [Tutorial](https://www.tensorflow.org/tutorials)
- [Git Hub](https://github.com/tensorflow/tensorflow)
- [Guide](https://www.tensorflow.org/guide)
- [Postman Collection](collections/tensorflow-serving.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/tensorflow-serving.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### TensorFlow.js API

A JavaScript library for training and deploying ML models in the browser and on Node.js.

- **Human URL:** [https://js.tensorflow.org/](https://js.tensorflow.org/)
- **Base URL:** `https://cdn.jsdelivr.net/npm/@tensorflow/tfjs`

#### Tags

- Browser
- JavaScript
- Node.js

#### Properties

- [Documentation](https://js.tensorflow.org/api/latest/)
- [Tutorial](https://js.tensorflow.org/tutorials/)
- [Git Hub](https://github.com/tensorflow/tfjs)
- [N P M](https://www.npmjs.com/package/@tensorflow/tfjs)
- [Postman Collection](collections/tensorflow-serving.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/tensorflow-serving.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### TensorFlow Lite API

Lightweight solution for ML inference on mobile and embedded devices, optimized for on-device model execution.

- **Human URL:** [https://www.tensorflow.org/lite](https://www.tensorflow.org/lite)
- **Base URL:** `https://www.tensorflow.org/lite/api_docs`

#### Tags

- Edge Computing
- Embedded
- Mobile
- On-Device AI

#### Properties

- [Documentation](https://www.tensorflow.org/lite/api_docs)
- [Guide](https://www.tensorflow.org/lite/guide)
- [Examples](https://www.tensorflow.org/lite/examples)
- [Git Hub](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite)
- [Postman Collection](collections/tensorflow-serving.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/tensorflow-serving.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### TensorFlow Hub API

A library and repository of reusable pre-trained machine learning modules, enabling transfer learning across text, image, video, and audio domains.

- **Human URL:** [https://tfhub.dev/](https://tfhub.dev/)
- **Base URL:** `https://tfhub.dev/`

#### Tags

- Model Repository
- Pre-Trained Models
- Transfer Learning

#### Properties

- [Documentation](https://www.tensorflow.org/hub/api_docs/python/hub)
- [Models](https://tfhub.dev/)
- [Git Hub](https://github.com/tensorflow/hub)
- [Postman Collection](collections/tensorflow-serving.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/tensorflow-serving.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### TensorBoard API

TensorFlow's visualization toolkit for experiment tracking, model debugging, and performance profiling via an embedded web server with REST endpoints.

- **Human URL:** [https://www.tensorflow.org/tensorboard](https://www.tensorflow.org/tensorboard)

#### Tags

- Model Debugging
- Monitoring
- Visualization

#### Properties

- [Documentation](https://www.tensorflow.org/tensorboard/get_started)
- [Git Hub](https://github.com/tensorflow/tensorboard)
- [Postman Collection](collections/tensorflow-serving.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/tensorflow-serving.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/showcase/tensorflowdev)
- [Blog](https://blog.tensorflow.org/)
- [Git Hub  Org](https://github.com/tensorflow)
- [Twitter](https://twitter.com/tensorflow)
- [YouTube](https://www.youtube.com/tensorflow)
- [License](https://github.com/tensorflow/tensorflow/blob/master/LICENSE)
- [Forum](https://discuss.tensorflow.org/)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/tensorflow)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/tensorflow/refs/heads/main/openapi/tensorflow-serving-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Vocabulary](https://raw.githubusercontent.com/api-evangelist/tensorflow/refs/heads/main/vocabulary/tensorflow-vocabulary.yml)

## Maintainers

**FN:** Google Brain Team
**Email:** tensorflow@googlegroups.com
**URL:** https://www.tensorflow.org/
