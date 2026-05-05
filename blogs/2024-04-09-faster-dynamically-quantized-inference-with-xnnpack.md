---
title: "Faster Dynamically Quantized Inference with XNNPack"
url: "https://blog.tensorflow.org/2024/04/faster-dynamically-quantized-inference-with-xnnpack.html"
date: "2024-04-09T09:00:00.000-07:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgb_J0gvQboeZswAJu8KAIJ1ekS5NK9-DOZzLpKRn7E4CpdjOqqq2Mvv1e2DYIumB3GYqmqUAA6iSQIDJTLzWRmC0mcOEahy1LbsXyEgbQIKJKjGa12BuuV130zfnrqx4f0CKcbSV7DRw-JZVM6D2YH8FHYVjV-MBMmDtBZXJFxGyg0kCF2-QfjXzWuGzw/s1600/TensorFlow_HalfPrecisionInference_1024x512.png" style="display: none;" />

<em>Posted by <a href="https://www.linkedin.com/in/alanjkelly" target="_blank">Alan Kelly</a>, Software Engineer</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHT0UddYXED7iZEDQXMJmhQbji0OueyNeH2K7xuGh4kIazdL52xtISoZ8k1ZgNJGpUw6tzELxHSjmXSdQCfCE1PFOb-hI4S30q31RZoPp29rRQ1dPXed7Ym7FnGJqA6eco7wgiOQ_kxz_5HQZiQcu0hOgrSx5fDqbsVqIsRrGKVqRmCU-Fs0NCw5j6pUc/s1600/TensorFlow_HalfPrecisionInference_4209x1253.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHT0UddYXED7iZEDQXMJmhQbji0OueyNeH2K7xuGh4kIazdL52xtISoZ8k1ZgNJGpUw6tzELxHSjmXSdQCfCE1PFOb-hI4S30q31RZoPp29rRQ1dPXed7Ym7FnGJqA6eco7wgiOQ_kxz_5HQZiQcu0hOgrSx5fDqbsVqIsRrGKVqRmCU-Fs0NCw5j6pUc/s1600/TensorFlow_HalfPrecisionInference_4209x1253.png" /></a>

<a name="more"></a><p></p>

<p>We are excited to announce that XNNPack’s Fully Connected and Convolution 2D operators now support dynamic range quantization. XNNPack is TensorFlow Lite’s CPU backend and CPUs deliver the widest reach for ML inference and remain the default target for TensorFlow Lite. Consequently, improving CPU inference performance is a top priority. We <b>quadrupled</b> inference performance in TensorFlow Lite’s XNNPack backend compared to the <a href="https://en.wikipedia.org/wiki/Single-precision_floating-point_format" target="_blank">single precision</a> baseline by adding support for dynamic range quantization to the Fully Connected and Convolution operators. This means that more AI powered features may be deployed to older and lower tier devices.</p>

<p>Previously, XNNPack offered users the choice between either full integer quantization, where the weights and activations are stored as signed 8-bit integers, or half-precision (fp16) or single-precision (fp32) floating-point inference. In this article we demonstrate the benefits of dynamic range quantization.</p>

<h3>Dynamic Range Quantization</h3>

<p><a href="https://www.tensorflow.org/lite/performance/post_training_quant#:~:text=Dynamic%20range%20quantization%20achieves%20a,for%20faster%20implementation%20when%20available." target="_blank">Dynamically quantized</a> models are similar to fully-quantized models in that the weights for the Fully Connected and Convolution operators are quantized to 8-bit integers during model conversion. All other tensors are not quantized, they remain as float32 tensors. During model inference, the floating-point layer activations are converted to 8-bit integers before being passed to the Fully Connected and Convolution operators. The quantization parameters (the zero point and scale) for each row of the activation tensor are calculated dynamically based on the observed range of activations. This maximizes the accuracy of the quantization process as the activations make full use of the 8 quantized bits. In fully-quantized models, these parameters are fixed during model conversion, based on the range of the activation values observed using a representative dataset. The second difference between full quantization and dynamic range quantization is that the output of the Fully Connected and Convolution operators is in 32-bit floating-point format, as opposed to 8-bit integer for fully-quantized operators. With dynamic range quantization, we get most of the performance gains of full quantization, yet with higher overall accuracy.</p>

<p>Traditionally the inference of such models was done using TensorFlow Lite’s native operators. Now dynamically quantized models can benefit from XNNPack’s highly-optimized per-architecture implementations of the Fully Connected and Convolution2D operators. These operators are optimized for all architectures supported by XNNPack (ARM, ARM64, x86 SSE/AVX/AVX512 and WebAssembly), including the latest ArmV9 processors such as the Pixel 8’s Tensor G3 CPU or the One Plus 11’s SnapDragon 8 Gen 2 CPU.</p>

<h3>How can you use it?</h3>

<p>Two steps are required to use dynamic range quantization. You must first convert your model from TensorFlow with support for dynamic range quantization. Existing models already converted using dynamic range quantization do not need to be reconverted. Dynamic range quantization can be enabled during model conversion by enabling the 
  <code>converter.optimizations = [tf.lite.Optimize.DEFAULT]</code> <a href="https://www.tensorflow.org/lite/performance/post_training_quantization#dynamic_range_quantization" target="_blank">converter flag</a>. Unlike full integer quantization, no representative dataset is required and unsupported operators do not prevent conversion from succeeding. Dynamic range quantization is therefore far more accessible to non-expert users than full integer quantization.</p>

<p>From TensorFlow 2.17, dynamically quantized XNNPack inference will be enabled by default in prebuilt binaries. If you want to use it sooner, the nightly TensorFlow  builds may be used.</p> 

<h3>Mixed Precision Inference</h3>

<p>In our <a href="https://blog.tensorflow.org/2023/11/half-precision-inference-doubles-on-device-inference-performance.html" target="_blank">previous article</a> we presented the impressive performance gains from using half precision inference. Half-precision and dynamic range quantization may now be combined within XNNPack to get the best possible on-device CPU inference performance on devices which have hardware fp16 support (most phones on sale today do). The Fully Connected and Convolution 2D operators can output fp16 data instead of fp32. The Pixel 3, released in 2018, was the first Pixel model with fp16 support. fp16 uses half as many bits to store a floating-point value compared to fp32, meaning that the relative accuracy of each value is reduced due to the significantly shorter mantissa (10 vs 23 bits). Not all models support fp16 inference, but if a model supports it, the computational cost of vectorized floating-point operators can be reduced by half as the CPU can process twice as much data per instruction. Dynamically quantized models with compute-intensive floating point operators, such as Batch Matrix Multiply and Softmax, can benefit from fp16 inference as well.</p>

<h3>Performance Improvements</h3>

<p>Below, we present benchmarks on four public models covering common computer vision tasks:</p>
<ol>
<li><a href="https://www.kaggle.com/models/google/efficientnet-v2" target="_blank">EfficientNetV2</a> - image classification and feature extraction</li>
<li><a href="https://www.kaggle.com/models/google/inception-v3" target="_blank">Inception-v3</a> - image classification</li>
<li><a href="https://www.kaggle.com/models/google/deeplab-edgetpu/frameworks/tensorFlow2" target="_blank">Deeplab-v3</a> - semantic segmentation</li>
<li><a href="https://github.com/keras-team/keras-cv/blob/1b4e2ab27085792fe9fa526c874c93bc985cb9e0/keras_cv/models/stable_diffusion/stable_diffusion.py#L48" target="_blank">Stable Diffusion</a> - image generation (diffusion model)</li>
</ol>
  
<p>Each model was converted three times where possible: full float, full 8 bit signed integer quantization and dynamic range quantization. Stable Diffusion’s diffusion model could not be converted using full integer quantization due to unsupported operators. The speed-up versus the original float32 model using TFLite’s kernels is shown below.</p>
<ul>
<li>FP32 refers to the baseline float32 model.</li>
<li>QS8 refers to full signed 8 bit integer quantization using XNNPack.</li>
<li>QD8-F32 refers to dynamically quantized 8 bit integers with fp32 activations using XNNPack.</li>
<li>QD8-F16 refers to dynamically quantized 8 bit integers with fp16 activations using XNNPack.</li>

<div><table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><center><img alt="Graph showing speed-up versus float32 on pixel 8" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgPDH1jOCsdo9shNTu2AAGAN86P3na4w0DOy8uf1wF5Pn6kH3wy4EqZyNJnQz1sDJp5inV0UFnMpKs_k1uyCU5dS53ElzRl60DWe1kYXTbatU5hcNFELNwamJpIEMd6KwvOek4uUMPdsq5omUqa_3oRUL6EQrD-C8mH1O_xID-OpWUOuKlpwWBSX5MQR-U/s1600/image1.png" style="width: 100%;" /></center></td></tr></tbody></table></div>
  
<p>The speed-up versus TFLite’s dynamically quantized Fully Connected and Convolution operators are shown below. By simply using the latest version of TensorFlow Lite, you can benefit from these speed-ups.</p>

<div><table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><center><img alt="Graph showing speed-up versus TFLite DQ on Pixel 8" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiq8N7A2YrFpdg7zUfnI0tHBjzt5qKiScoX-SceQLiQ0WoyLMWeAAu_ic0Fgqp8_Npeqi-Ql_oWERpu8BmI6ysekzsZyIU5Dpfhf5mEGHxR1DGchDK5eLLp3jAWHek5N6hHE5_tMRSLJz7ZA6uTLz5qdSuaswkz1Vul7HgP5bS76f3frGZJbtHJUZDx6F4/s1600/image2.png" style="width: 100%;" /></center></td></tr></tbody></table></div>
  
 
<p>We can clearly see that dynamic range quantization is competitive with, and in some cases can exceed, the performance of full integer quantization. Stable Diffusion’s diffusion model runs up to 6.2 times faster than the original float32 model! This is a game changer for on-device performance.</p>

<p>We would expect that full integer quantization would be faster than dynamic range quantization as all operations are calculated using integer arithmetic. Furthermore, dynamic range quantization has the additional overhead of converting the floating point activations to quantized 8 bit integers. Surprisingly, in two of the three models tested, this is not true. Profiling the models using <a href="https://blog.tensorflow.org/2022/06/Profiling-XNNPACK-with-TFLite.html" target="_blank">TFLite’s profiler</a> solves the mystery. These models are slower due to a combination of quantization artifacts — quantized arithmetic is more efficient when the ratio of the input and output scales fall within a certain range and missing op support in XNNPack. These quantization parameters are determined during model conversion based on a provided representative dataset. Since the ratio of the scales falls outside the optimal range, a less optimal path must be taken and performance suffers.</p>

<p>Finally, we demonstrate that model precision is mostly preserved when using mixed precision inference, we compare the image generated by the dynamically quantized Stable Diffusion model using fp32 activations with that generated using fp16 activations with the random number generator seeded with the same number to verify that using fp16 activations for the diffusion model does not impact the quality of the generated image.</p>

<div><table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><center><img alt="side by side comparison of images generated using fp16 inference on the left and fp32 inference on the right" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhYC0JXklv2VGPmSCzcUOrNo5Zfcfw0EER6PNb4iytEQ9A3NlvdgrhiA18pg0Xv2RhpqVFf9xrgrW56PQ8QNjTXQyOwKXt3vCloiYft5SWHpAQy6cfE0iILxtx53y1QmUVEd7NPehSXSqtzF_kfUtqMlMNmSA_MMe643OOpanRkWNm7CGuY23nTyHeeRL0/s1600/XNNPack-Inline.png" style="width: 100%;" /></center></td></tr><tr><td class="tr-caption" style="text-align: center;"><i>Image generated using fp16 inference (left) and fp32 inference (right)</i></td></tr></tbody></table></div>
  
<p>Both generated images are indeed lovely cats, corresponding to the given prompt. The images are indistinguishable which is a very strong indication that the diffusion model is suited to fp16 inference. Of course, as for all neural networks, any quantization strategy should be validated using a large validation dataset, and not just a single test. </p>
  
  
<h3>Conclusions</h3>

<p>Full integer quantization is hard, converting models is difficult, error prone and accuracy is not guaranteed. The representative dataset must be truly representative to minimize quantization errors. Dynamic range quantization offers a compromise between full integer quantization and fp32 inference: the models are of similar size to the fully-quantized model and performance gains are often similar and sometimes exceeds that of fully-quantized models. Using Stable Diffusion, we showed that dynamic range quantization and fp16 inference can be combined giving game changing performance improvements. XNNPack’s dynamic range quantization is now powering <a href="https://developers.googleblog.com/2024/03/running-large-language-models-on-device-with-mediapipe-andtensorflow-lite.html" target="_blank">Gemini</a>, Google Meet, and Chrome OS audio denoising and will launch in many other products this year. This same technology is now available to our open source users so try it for yourself using the models linked above and following the instructions in the How can I use it section!</p>


<h4>Acknowledgements</h4>
<p><em>We would like to thank Frank Barchard and Quentin Khan for contributions towards dynamic range quantization inference in TensorFlow Lite and XNNPack.</em></p>
