---
title: "What's new in TensorFlow 2.20"
url: "https://blog.tensorflow.org/2025/08/whats-new-in-tensorflow-2-20.html"
date: "2025-08-19T09:00:00.000-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhmNSPAvdllwEU84VcRAoDi6LsJlt5V2RqrHcUpHDU3qQH-BGHjvwFMMbN2-6hacXxkEIh-xCrL_rZHn9v5BvUJzcB6NhcRM6WM_w0pyVeYWki3kw7kVgQHsWZq1S3cgYA9slKWNKvE8635jg4SOKPXU43NeTcvwBK-raNeiWzo3lAWWOTLwrPpB0kZ_DE/s1600/TensorFlow-Metadatal_Alt-RD1-V01.jpg" style="display: none;" />

<em>Posted by the TensorFlow team</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEioO3__lwnX6PlmUJKDzDku-niQLWlKjlGrjqXJGic4QAWvsHiQHYqRkb-PcrcQQn9v6dVaJJ4HEa5oVu0Ebt7qwN00jvv0ZYRJrBQSi8t3g6qRX-AKwV4pHMrovsKe629s-HPWrhS9Xr3Dgvvb2tWGFH6z6QuN9QU1nscisYSmjD9kirmHeLJgrm0X4pM/s1600/TensorFlow-Wagtial_Alt-RD1-V01.jpg"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEioO3__lwnX6PlmUJKDzDku-niQLWlKjlGrjqXJGic4QAWvsHiQHYqRkb-PcrcQQn9v6dVaJJ4HEa5oVu0Ebt7qwN00jvv0ZYRJrBQSi8t3g6qRX-AKwV4pHMrovsKe629s-HPWrhS9Xr3Dgvvb2tWGFH6z6QuN9QU1nscisYSmjD9kirmHeLJgrm0X4pM/s1600/TensorFlow-Wagtial_Alt-RD1-V01.jpg" /></a>

<a name="more"></a><p></p>

<p>TensorFlow 2.20 has been released! For ongoing updates related to the multi-backend Keras, please note that all news and releases, starting with Keras 3.0, are now published directly on <a href="https://keras.io/keras_3/" target="_blank">keras.io</a>. You can find a complete list of all changes in the <a href="https://github.com/tensorflow/tensorflow/blob/r2.20/RELEASE.md" target="_blank">full release notes on GitHub</a>.</p>

<h2>tf.lite is being replaced by LiteRT</h2>

<p>The <span style="color: #0d904f ; font-family: courier ;">tf.lite</span> module will be deprecated with development for on-device inference moving to a new, independent repository: <a href="https://github.com/google-ai-edge/LiteRT" target="_blank">LiteRT</a>. The new APIs are available in Kotlin and C++. This code base will decouple from the TensorFlow repository and tf.lite will be removed from future TensorFlow Python packages, so we encourage migration of projects to LiteRT to receive the latest updates. More details to follow.</p>
  
  
<p>As announced at Google I/O ‘25, LiteRT improves upon TFLite, particularly for NPU and GPU hardware acceleration and performance for on-device ML and AI applications.</p>

<p>LiteRT provides a unified interface for Neural Processing Units (NPUs), removing the need to navigate vendor-specific compilers or libraries. This approach avoids many device-specific complications, boosts performance for real-time and large-model inference, and minimizes memory copies through zero-copy hardware buffer usage.</p>

<p>For more information on the new repository and to sign up for the NPU Early Access Program, please reach out to the team at <a href="https://g.co/ai/LiteRT-NPU-EAP" target="_blank">g.co/ai/LiteRT-NPU-EAP</a>.</p>


<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg87dnMBmiP_90gHANcFCbfW4Ecm7F34Q_h7n9HZyH5eoJauhlXa1Ucw4h_8Rge94fpvbI6Bi74w0ZvwmIF8x7CzHCSidE4Lcoe1f2e4RlTaUdzzkNV_Wi0J1OGhUlJP4KBuqPeSQdIamGuDMeKd_cB0dbMRiJSqBMSvw5Zt2yiC2QYkCmu1QV_PoE61co/s1600/LiteRT_BlogGraphics_4209x1253px_1.jpg" style="display: block; padding: 1em 0; text-align: center;"><img alt="" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg87dnMBmiP_90gHANcFCbfW4Ecm7F34Q_h7n9HZyH5eoJauhlXa1Ucw4h_8Rge94fpvbI6Bi74w0ZvwmIF8x7CzHCSidE4Lcoe1f2e4RlTaUdzzkNV_Wi0J1OGhUlJP4KBuqPeSQdIamGuDMeKd_cB0dbMRiJSqBMSvw5Zt2yiC2QYkCmu1QV_PoE61co/s1600/LiteRT_BlogGraphics_4209x1253px_1.jpg" width="100%" /></a></div>

<h2>Faster input pipeline warm-up with tf.data</h2>

<p>To help reduce latency, especially the time it takes for your model to process the first element of a dataset, we've added <span style="color: #0d904f ; font-family: courier ;">autotune.min_parallelism</span> in <span style="font-family: courier ;"><a href="https://www.tensorflow.org/api_docs/python/tf/data/Options" target="_blank">tf.data.Options</a></span>. This new option allows asynchronous dataset operations like <span style="color: #0d904f ; font-family: courier ;">.map</span> and <span style="color: #0d904f ; font-family: courier ;">.batch</span> to immediately start with a specified minimum level of parallelism, speeding up the initial warm-up time for your input pipelines.</p>

<h2>Changes to I/O GCS filesystem package</h2>

<p>The <span style="color: #0d904f ; font-family: courier ;">tensorflow-io-gcs-filesystem</span> package for Google Cloud Storage support is now optional. Previously, it was installed, by default, with TensorFlow. If your workflow requires access to GCS, you must now explicitly install this package by running: <span style="color: #0d904f ; font-family: courier ;">pip install "tensorflow[gcs-filesystem]"</span>.</p>
  
<p>Note that the package has recently received limited support, and there is currently no guarantee it will be available for newer Python versions.</p>
