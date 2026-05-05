---
title: "What's new in TensorFlow 2.18"
url: "https://blog.tensorflow.org/2024/10/whats-new-in-tensorflow-218.html"
date: "2024-10-28T12:00:00.000-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVyX9h9jqUfN0LpVCwPg0iWNd4XDkKWd5hL7Wn9CwGLBZ5NyrEFTHHXu6yCxCaLL2szdaQMCkDuRdV4-JapbV329DYTjaH6ThpbzJlbvgunZK9dUgii1kAqcs-4zhyphenhyphenccaLsfffj7K3-8HFLybyOeaHjVl_n7jdPmD33o0TERamUgTdH7H3qhBLS2GuwtY/s1600/Tensorflow-septmber-update-social%20%282%29%20%281%29.png" style="display: none;" />

<em>Posted by the TensorFlow team</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png" /></a>

<a name="more"></a><p></p>

<p>TensorFlow 2.18 has been released! Highlights of this release (and 2.17) include NumPy 2.0, LiteRT repository, CUDA Update, Hermetic CUDA and more. For the full release notes, please click <a href="https://github.com/tensorflow/tensorflow/blob/r2.18/RELEASE.md" target="_blank">here</a>.</p>

<p><b>Note:</b> Release updates on the new multi-backend Keras will be published on <a href="http://keras.io" target="_blank">keras.io</a>, starting with Keras 3.0. For more information, please see <a href="https://keras.io/keras_3/" target="_blank">https://keras.io/keras_3/</a>.</p>

<h2><span style="font-size: x-large;">TensorFlow Core</span></h2>

<span style="font-size: large;"><b>NumPy 2.0</b></span>

<p>The upcoming TensorFlow 2.18 release will include support for <a href="https://numpy.org/doc/stable/release/2.0.0-notes.html" target="_blank">NumPy 2.0</a>. While the majority of TensorFlow APIs will function seamlessly with NumPy 2.0, this may break some edge cases of usage, e.g., out-of-boundary conversion errors and numpy scalar representation errors. You can consult the following <a href="https://github.com/tensorflow/tensorflow/pull/73730" target="_blank">common solutions</a>.</p>


<p>Note that NumPy's type promotion rules have been changed (See <a href="https://numpy.org/neps/nep-0050-scalar-promotion.html#nep50" target="_blank">NEP 50</a> for details). This may change the precision at which computations happen, leading either to type errors or to numerical changes to results. Please see <a href="https://numpy.org/devdocs/numpy_2_0_migration_guide.html#numpy-2-migration-guide" target="_blank">the NumPy 2 migration guide</a>.</p>

<p>We've updated some TensorFlow tensor APIs to maintain compatibility with NumPy 2.0 while preserving the out-of-boundary conversion behavior in NumPy 1.x.</p><br />

<span style="font-size: large;"><b>LiteRT Repository</b></span>

<p>We're making some changes to how <a href="https://github.com/google-ai-edge/LiteRT" target="_blank">LiteRT</a> (<a href="https://developers.googleblog.com/en/tensorflow-lite-is-now-litert/" target="_blank">formerly known as TFLite</a>) is developed. Over the coming months, we'll be gradually transitioning TFLite's codebase to LiteRT. Once the migration is complete, we'll start accepting contributions directly through the LiteRT repository. There will no longer be any binary TFLite releases and developers should switch to LiteRT for the latest updates.</p><br />

<span style="font-size: large;"><b>Hermetic CUDA</b></span>

<p>If you build TensorFlow from source, Bazel will now download specific versions of CUDA, CUDNN and NCCL distributions, and then use those tools as dependencies in various Bazel targets. This enables more reproducible builds for Google ML projects and supported CUDA versions because the build no longer relies on the locally installed versions. More details are provided <a href="https://github.com/openxla/xla/blob/main/docs/hermetic_cuda.md#environment-variables-controlling-the-hermetic-cudacudnn-versions" target="_blank">here</a>.</p><br />


<span style="font-size: large;"><b>CUDA Update</b></span>

<p>TensorFlow binary distributions now ship with dedicated CUDA kernels for GPUs with a compute capability of 8.9. This improves the performance on the popular Ada-Generation GPUs like NVIDIA RTX 40**, L4 and L40.</p>

<p>To keep Python wheel sizes in check, we made the decision to no longer ship CUDA kernels for compute capability 5.0. That means the oldest NVIDIA GPU generation supported by the precompiled Python packages is now the Pascal generation (compute capability 6.0). For Maxwell support, we either recommend sticking with TensorFlow version 2.16, or compiling TensorFlow from source. The latter will be possible as long as the used CUDA version still supports Maxwell GPUs.</p>
