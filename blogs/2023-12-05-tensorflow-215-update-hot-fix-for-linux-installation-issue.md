---
title: "TensorFlow 2.15 update: hot-fix for Linux installation issue"
url: "https://blog.tensorflow.org/2023/12/tensorflow-215-update-hot-fix-linux-installation-issue.html"
date: "2023-12-05T14:00:00.000-08:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVyX9h9jqUfN0LpVCwPg0iWNd4XDkKWd5hL7Wn9CwGLBZ5NyrEFTHHXu6yCxCaLL2szdaQMCkDuRdV4-JapbV329DYTjaH6ThpbzJlbvgunZK9dUgii1kAqcs-4zhyphenhyphenccaLsfffj7K3-8HFLybyOeaHjVl_n7jdPmD33o0TERamUgTdH7H3qhBLS2GuwtY/s1600/Tensorflow-septmber-update-social%20%282%29%20%281%29.png" style="display: none;" />

<em>Posted by the TensorFlow team</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja7X29KGgTQBVvr3Xl2pyRZ-KQZJOM1-rq5XUr7AKu1vc_umj40H8y3mMoYq3wccQlA9XZ8OPtSx8SFJOOy8uSeX_MpoIAz7x44Cov-P95v9h85TLGgWCW2gqL6x3fbFfL1Xg6gZYkhylQKMQG7_8ilCTsm81bG87vT-3ttwn8IGdCPU1KfVVDjatuofs/s1600/Tensorflow-septmber-update-header%20%284%29.png" /></a>

<a name="more"></a><p></p>

<p>We are releasing a hot-fix for an installation issue affecting the TensorFlow installation process. The TensorFlow 2.15.0 Python package was released such that it requested <code>tensorrt</code>-related packages that cannot be found unless the user installs them beforehand or provides additional installation flags. This dependency affected anyone installing TensorFlow 2.15 alongside NVIDIA CUDA dependencies via <code>pip install tensorflow[and-cuda]</code>. Depending on the installation method, TensorFlow 2.14 would be installed instead of 2.15, or users could receive an installation error due to those missing dependencies.</p>
  
<p>To solve this issue as quickly as possible, we have released TensorFlow 2.15.0.post1 for the Linux x86_64 platform. This version removes the <code>tensorrt</code> Python package dependencies from the <code>tensorflow[and-cuda]</code> installation method. Support for TensorRT is otherwise unaffected as long as TensorRT is already installed on the system. Now, <code>pip install tensorflow[and-cuda]</code> works as originally intended for TensorFlow 2.15.</p>
  
<p>Using .post1 instead of a full minor release allowed us to push this release out quickly. However, please be aware of the following caveat: for users wishing to pin their Python dependency in a requirements file or other situation, under Python's version specification rules, <code>tensorflow[and-cuda]==2.15.0</code> will not install this fixed version. Please use <code>==2.15.0.post1</code> to specify this exact version on Linux platforms, or a fuzzy version specification, such as <code>==2.15.<sup>*</sup></code>, to specify the most recent compatible version of TensorFlow 2.15 on all platforms.</p>
