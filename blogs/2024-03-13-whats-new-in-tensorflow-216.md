---
title: "What's new in TensorFlow 2.16"
url: "https://blog.tensorflow.org/2024/03/whats-new-in-tensorflow-216.html"
date: "2024-03-13T13:11:00.000-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVyX9h9jqUfN0LpVCwPg0iWNd4XDkKWd5hL7Wn9CwGLBZ5NyrEFTHHXu6yCxCaLL2szdaQMCkDuRdV4-JapbV329DYTjaH6ThpbzJlbvgunZK9dUgii1kAqcs-4zhyphenhyphenccaLsfffj7K3-8HFLybyOeaHjVl_n7jdPmD33o0TERamUgTdH7H3qhBLS2GuwtY/s1600/Tensorflow-septmber-update-social%20%282%29%20%281%29.png" style="display: none;" />

<em>Posted by the TensorFlow team</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png" /></a>

<a name="more"></a><p></p>

<p>TensorFlow 2.16 has been released! Highlights of this release (and 2.15) include Clang as default compiler for building TensorFlow CPU wheels on Windows, Keras 3 as default version, support for Python 3.12, and much more! For the full release note, please click <a href="https://github.com/tensorflow/tensorflow/blob/r2.16/RELEASE.md" target="_blank">here</a>.</p>

<p><b>Note:</b> Release updates on the new multi-backend Keras will be published on <a href="http://keras.io" target="_blank">keras.io</a> starting with Keras 3.0. For more information, please see <a href="https://keras.io/keras_3/" target="_blank">https://keras.io/keras_3/</a>.</p> 

<h3>TensorFlow Core</h3>

<h4>Clang 17</h4>

<p>Clang is now the preferred compiler to build TensorFlow CPU wheels on the Windows Platform starting with this release. The currently supported version is LLVM/clang 17. The official Wheels-published on PyPI will be based on Clang; however, users retain the option to build wheels using the MSVC compiler <a href="https://www.tensorflow.org/install/source_windows" target="_blank">following the steps mentioned</a>, as has been the case before. Intel owned the implementation and delivery of this change within the 3P Official Build program.</p> 

<h4>Keras 3</h4>

<p>Keras 3 will be the default Keras version for TensorFlow 2.16 onwards. You may need to update your script to use Keras 3. Please refer to the new Keras documentation for Keras 3 (<a href="https://keras.io/keras_3" target="_blank">https://keras.io/keras_3</a>). Keras 2 will continue to be released alongside TensorFlow as <code>tf_keras</code>. To continue using Keras 2 with TensorFlow 2.16+:</p>
<ul>
<li>Install <code>tf-keras</code> vía <code>pip install tf-keras~=2.16</code></li>
<li>Switch <code>tf.keras</code> to use <code>Keras 2 (tf-keras)</code>, by setting environment variable <code>TF_USE_LEGACY_KERAS=1</code> directly or in your Python program by doing <code>import os;os.environ["TF_USE_LEGACY_KERAS"]=”1”</code>. Please note that this needs to be set before importing TensorFlow and will set it for all packages in your Python runtime program.</li>
</ul>

<h4>Estimator API</h4>

<p><code>tf.estimator</code> API is removed. If you need to use the estimator API, you need to use TF 2.15 or an earlier version.</p> 	

<h4>Apple Silicon</h4>

<p>If you previously installed TensorFlow using <code>pip install tensorflow-macos</code>, please update your installation method. Use <code>pip install tensorflow</code> from now on. <code>tensorflow-macos</code> package will no longer receive updates. Future updates will be released to <code>tensorflow</code>.</p>
