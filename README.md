# TensorFlow

TensorFlow is an end-to-end open source machine learning platform developed by Google. It provides a comprehensive ecosystem of tools, libraries, and community resources for building and deploying ML-powered applications, including model training, serving, mobile/edge deployment, and a hub of pre-trained models. TensorFlow Serving exposes REST and gRPC APIs for production model inference.

**Type:** opensource  
**Website:** [https://www.tensorflow.org/](https://www.tensorflow.org/)  
**GitHub Org:** [https://github.com/tensorflow](https://github.com/tensorflow)

## Tags

AI, Deep Learning, JavaScript, Machine Learning, Model Serving, Neural Networks, Open Source, Python

## APIs

### TensorFlow Serving REST API
A flexible, high-performance serving system for machine learning models designed for production environments. Provides REST endpoints for model status, metadata, classification, regression, and prediction inference.

- **Documentation:** [https://www.tensorflow.org/tfx/serving/api_rest](https://www.tensorflow.org/tfx/serving/api_rest)
- **GitHub:** [https://github.com/tensorflow/serving](https://github.com/tensorflow/serving)
- **OpenAPI:** [openapi/tensorflow-serving-openapi.yml](openapi/tensorflow-serving-openapi.yml)

### TensorFlow Core API
The foundational Python and C++ API for building and training machine learning models.

- **Documentation:** [https://www.tensorflow.org/api_docs/python/tf](https://www.tensorflow.org/api_docs/python/tf)
- **GitHub:** [https://github.com/tensorflow/tensorflow](https://github.com/tensorflow/tensorflow)

### TensorFlow.js API
A JavaScript library for training and deploying ML models in the browser and on Node.js.

- **Documentation:** [https://js.tensorflow.org/api/latest/](https://js.tensorflow.org/api/latest/)
- **NPM:** [https://www.npmjs.com/package/@tensorflow/tfjs](https://www.npmjs.com/package/@tensorflow/tfjs)

### TensorFlow Lite API
Lightweight solution for ML inference on mobile and embedded devices.

- **Documentation:** [https://www.tensorflow.org/lite/api_docs](https://www.tensorflow.org/lite/api_docs)

### TensorFlow Hub API
A library and repository of reusable pre-trained machine learning modules for transfer learning.

- **Models:** [https://tfhub.dev/](https://tfhub.dev/)

### TensorBoard API
TensorFlow's visualization toolkit for experiment tracking and model debugging.

- **Documentation:** [https://www.tensorflow.org/tensorboard/get_started](https://www.tensorflow.org/tensorboard/get_started)

## OpenAPI Specifications

| Spec | Description |
|---|---|
| [tensorflow-serving-openapi.yml](openapi/tensorflow-serving-openapi.yml) | TensorFlow Serving REST API - model status, metadata, classify, regress, predict |

## Spectral Rules

| Ruleset | Description |
|---|---|
| [tensorflow-serving-rules.yml](rules/tensorflow-serving-rules.yml) | Spectral rules enforcing TensorFlow Serving API conventions |

## Naftiko Capabilities

### Shared Definitions

| File | Description |
|---|---|
| [capabilities/shared/tensorflow-serving.yaml](capabilities/shared/tensorflow-serving.yaml) | TensorFlow Serving REST API consumed definition |

### Workflow Capabilities

| File | Description |
|---|---|
| [capabilities/model-inference.yaml](capabilities/model-inference.yaml) | ML model inference workflow (status, metadata, classify, regress, predict) |

## JSON Schemas

| Schema | Description |
|---|---|
| [tensorflow-serving-prediction-request-schema.json](json-schema/tensorflow-serving-prediction-request-schema.json) | Prediction request schema (row/column formats) |
| [tensorflow-serving-prediction-response-schema.json](json-schema/tensorflow-serving-prediction-response-schema.json) | Prediction response schema |
| [tensorflow-serving-model-status-schema.json](json-schema/tensorflow-serving-model-status-schema.json) | Model status response schema |

## JSON Structures

| Structure | Description |
|---|---|
| [tensorflow-serving-prediction-request-structure.json](json-structure/tensorflow-serving-prediction-request-structure.json) | Prediction request field documentation |

## JSON-LD

| Context | Description |
|---|---|
| [tensorflow-context.jsonld](json-ld/tensorflow-context.jsonld) | JSON-LD context for TensorFlow ML concepts |

## Examples

| Example | Description |
|---|---|
| [tensorflow-serving-predict-example.json](examples/tensorflow-serving-predict-example.json) | Prediction request/response example |
| [tensorflow-serving-model-status-example.json](examples/tensorflow-serving-model-status-example.json) | Model status request/response example |

## Vocabulary

| Vocabulary | Description |
|---|---|
| [tensorflow-vocabulary.yml](vocabulary/tensorflow-vocabulary.yml) | TensorFlow ML domain vocabulary and taxonomy |

## Links

- **Forum:** [https://discuss.tensorflow.org/](https://discuss.tensorflow.org/)
- **Blog:** [https://blog.tensorflow.org/](https://blog.tensorflow.org/)
- **Stack Overflow:** [https://stackoverflow.com/questions/tagged/tensorflow](https://stackoverflow.com/questions/tagged/tensorflow)
- **License:** [Apache 2.0](https://github.com/tensorflow/tensorflow/blob/master/LICENSE)

## Maintainers

**FN:** Google Brain Team  
**Email:** tensorflow@googlegroups.com
