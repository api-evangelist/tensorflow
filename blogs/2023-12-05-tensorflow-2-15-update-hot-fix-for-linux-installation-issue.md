---
title: "TensorFlow 2.15 update: hot-fix for Linux installation issue"
url: "https://blog.tensorflow.org/2023/12/tensorflow-215-update-hot-fix-linux-installation-issue.html"
date: "2023-12-05T14:00:00.000-08:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/atom.xml"
---
Posted by the TensorFlow team We are releasing a hot-fix for an installation issue affecting the TensorFlow installation process. The TensorFlow 2.15.0 Python package was released such that it requested tensorrt -related packages that cannot be found unless the user installs them beforehand or provides additional installation flags. This dependency affected anyone installing TensorFlow 2.15 alongside NVIDIA CUDA dependencies via pip install tensorflow[and-cuda] .
