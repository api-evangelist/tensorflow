---
title: "Distributed Fast Fourier Transform in TensorFlow"
url: "https://blog.tensorflow.org/2023/08/distributed-fast-fourier-transform-in-tensorflow.html"
date: "2023-08-24T10:00:00.001-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/atom.xml"
---
Posted by Ruijiao Sun , Google Intern - DTensor team Fast Fourier Transform is an important method of signal processing, which is commonly used in a number of ways, including speeding up convolutions, extracting features, and regularizing models. Distributed Fast Fourier Transform (Distributed FFT) offers a way to compute Fourier Transforms in models that work with image-like datasets that are too large to fit into the memory of a single accelerator device. In a previous Google Research Paper, “ Large-Scale Discrete Fourier Transform on TPUs ” by Tianjian Lu, a Distributed FFT algorithm was…
