---
title: "What's new in TensorFlow 2.19"
url: "https://blog.tensorflow.org/2025/03/whats-new-in-tensorflow-2-19.html"
date: "2025-03-13T09:00:00.000-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVyX9h9jqUfN0LpVCwPg0iWNd4XDkKWd5hL7Wn9CwGLBZ5NyrEFTHHXu6yCxCaLL2szdaQMCkDuRdV4-JapbV329DYTjaH6ThpbzJlbvgunZK9dUgii1kAqcs-4zhyphenhyphenccaLsfffj7K3-8HFLybyOeaHjVl_n7jdPmD33o0TERamUgTdH7H3qhBLS2GuwtY/s1600/Tensorflow-septmber-update-social%20%282%29%20%281%29.png" style="display: none;" />

<em>Posted by the TensorFlow team</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png" /></a>

<a name="more"></a><p></p>

<p>TensorFlow 2.19 has been released! Highlights of this release include changes to the C++ API in LiteRT, bfloat16 support for tflite casting, discontinue of releasing libtensorflow packages. Learn more by reading the <a href="https://github.com/tensorflow/tensorflow/blob/r2.19/RELEASE.md" target="_blank">full release notes</a>.</p>

<p><b>Note:</b> Release updates on the new multi-backend Keras will be published on <a href="http://keras.io" target="_blank">keras.io</a>, starting with Keras 3.0. For more information, please see <a href="https://keras.io/keras_3/" target="_blank">https://keras.io/keras_3/</a>.</p>

<h2><span style="font-size: x-large;">TensorFlow Core</span></h2>

<h3><span style="font-size: large;">LiteRT</span></h3>

<p>The public constants <code>tflite::Interpreter:kTensorsReservedCapacity</code> and <code>tflite::Interpreter:kTensorsCapacityHeadroom</code> are now const references, rather than constexpr compile-time constants. (This is to enable better API compatibility for TFLite in Play services while preserving the implementation flexibility to change the values of these constants in the future.)

<h3><span style="font-size: large;">TF-Lite</span></h3>

<p>tfl.Cast op is now supporting bfloat16 in the runtime kernel. <code>tf.lite.Interpreter</code> gives a deprecation warning redirecting to its new location at <code>ai_edge_litert.interpreter</code>, as the API <code>tf.lite.Interpreter</code> will be deleted in TF 2.20. See the <a href="https://ai.google.dev/edge/litert/migration" target="_blank">migration guide</a> for details.</p>

<h3><span style="font-size: large;">Libtensorflow</span></h3>

<p>We have stopped publishing libtensorflow packages but it can still be unpacked from the PyPI package.</p>
