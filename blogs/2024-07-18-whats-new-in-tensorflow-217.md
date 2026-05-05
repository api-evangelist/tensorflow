---
title: "What's new in TensorFlow 2.17"
url: "https://blog.tensorflow.org/2024/07/whats-new-in-tensorflow-217.html"
date: "2024-07-18T09:00:00.000-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVyX9h9jqUfN0LpVCwPg0iWNd4XDkKWd5hL7Wn9CwGLBZ5NyrEFTHHXu6yCxCaLL2szdaQMCkDuRdV4-JapbV329DYTjaH6ThpbzJlbvgunZK9dUgii1kAqcs-4zhyphenhyphenccaLsfffj7K3-8HFLybyOeaHjVl_n7jdPmD33o0TERamUgTdH7H3qhBLS2GuwtY/s1600/Tensorflow-septmber-update-social%20%282%29%20%281%29.png" style="display: none;" />

<em>Posted by the TensorFlow team</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png" /></a>

<a name="more"></a><p></p>

<p>TensorFlow 2.17 has been released! Highlights of this release (and 2.16) include CUDA update, upcoming Numpy 2.0, and more. For the full release notes, please click <a href="https://github.com/tensorflow/tensorflow/blob/r2.17/RELEASE.md" target="_blank">here</a>.</p>

<p>Note: Release updates on the new multi-backend Keras will be published on <a href="http://keras.io" target="_blank">keras.io</a>, starting with Keras 3.0. For more information, please see <a href="https://keras.io/keras_3/" target="_blank">https://keras.io/keras_3/</a>.</p>

<h2>TensorFlow Core</h2>

<h3><span style="font-weight: normal;">CUDA Update</span></h3>

<p>TensorFlow binary distributions now ship with dedicated CUDA kernels for GPUs with a compute capability of 8.9. This improves the performance on the popular Ada-Generation GPUs like NVIDIA RTX 40**, L4 and L40.</p>

<p>To keep Python wheel sizes in check, we made the decision to no longer ship CUDA kernels for compute capability 5.0. That means the oldest NVIDIA GPU generation supported by the precompiled Python packages is now the Pascal generation (compute capability 6.0). For Maxwell support, we either recommend sticking with TensorFlow version 2.16, or compiling TensorFlow from source. The latter will be possible as long as the used CUDA version still supports Maxwell GPUs.</p>

<h3><span style="font-weight: normal;">Numpy 2.0</span></h3>

<p>Upcoming TensorFlow 2.18 release will include support for Numpy 2.0. This may break some edge cases of TensorFlow API usage.</p>

<h3><span style="font-weight: normal;">Drop TensorRT support</span></h3>

<p>Starting with TensorFlow 2.18, support for TensorRT will be dropped. TensorFlow 2.17 will be the last version to include it.</p>
