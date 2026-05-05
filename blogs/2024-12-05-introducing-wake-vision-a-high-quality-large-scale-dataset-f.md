---
title: "Introducing Wake Vision: A High-Quality, Large-Scale Dataset for TinyML Computer Vision Applications"
url: "https://blog.tensorflow.org/2024/12/introducing-wake-vision-new-dataset-for-person-detection-in-tinyml.html"
date: "2024-12-05T09:00:00.000-08:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgO4WDCWDuV4LT0FtXw_qBaJKOFjEkHrFOBQ0z4WZaA6keEQEtFc4ZNwmZTyP2eCPHjN_qIA41VzgJeVCnYT6pTWCic-9gy5hjwknTEqGKfyWrJjtdH20lcxRkI7_N-UEPVgGxvDGvJDeeVm8h4QxVIa2mknX0l2WyG0WAs5Y259erSlTsQpbO8q3umCAI/s1600/TensorFlow-Training-model-on-temporal-data-with-TensorFlow-and-Temporian-header-social-v2.png" style="display: none;" />

<em>Posted by Colby Banbury, Emil Njor, Andrea Mattia Garavagno, Vijay Janapa Reddi – Harvard University</em>

<a href=""><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiXMzZM-8kD4Hv3XAwSxdZl1k5jAUCzDkfKdog5XWfPE8l-cfcDLmAPxhG8nd_ZbuGeyeulW9LsbSVsSkAQf3i_-DV6o71xrb57ZfVQ6cUClvMB-h1_rXjVIM4FK9V2GCRkWsIofgZ3hdaoJiYjRyzk-Mrf31-FEPJ6C4VhCoAjiCttPP1Sja53g-Tzz9Y/s1600/TensorFlow-Training-model-on-temporal-data-with-TensorFlow-and-Temporian-header-v2.png" /></a>

<a name="more"></a><p></p>

<p><b>TinyML</b> is an exciting frontier in machine learning, enabling models to run on extremely low-power devices such as microcontrollers and edge devices. However, the growth of this field has been stifled by a lack of tailored large and high-quality datasets. That's where <a href="https://wakevision.ai/" target="_blank">Wake Vision</a> comes in—a new dataset designed to accelerate research and development in TinyML.</p>

<div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjCy1LV1L66F-joAgx4igQMAX7g6jMDQsgd6vVd3pWLdSS9Cn96ZgP5aNumzwV1n8HP8JEvnjy-ra053wE2yIc0Rxped3pJfXkKt6XExOKqiVpzMoZqosS25KOpEpdiY4Un8lx_4DjdC6UIiTrjB1vIcWkCJv5NQRuKO0BH0E_rWbOhkJ03krsoQPmLNwA/s718/Screenshot%202024-12-02%20at%205.16.08%E2%80%AFPM.png" style="margin-left: 1em; margin-right: 1em;"><img alt="A vibrant, abstract representation of a human figure is formed by swirling lines and dots of rainbow colors. A large, bright blue eye is centrally located on the figure's torso." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjCy1LV1L66F-joAgx4igQMAX7g6jMDQsgd6vVd3pWLdSS9Cn96ZgP5aNumzwV1n8HP8JEvnjy-ra053wE2yIc0Rxped3pJfXkKt6XExOKqiVpzMoZqosS25KOpEpdiY4Un8lx_4DjdC6UIiTrjB1vIcWkCJv5NQRuKO0BH0E_rWbOhkJ03krsoQPmLNwA/s16000/Screenshot%202024-12-02%20at%205.16.08%E2%80%AFPM.png" /></a></div>

<h3>Why TinyML Needs Better Data</h3>

<p>The development of TinyML requires compact and efficient models, often only a few hundred kilobytes in size. The applications targeted by standard machine learning datasets, like ImageNet, are not well-suited for these highly constrained models.</p>

<p>Existing datasets for TinyML, like <a href="https://arxiv.org/abs/1906.05721" target="_blank">Visual Wake Words (VWW)</a>, have laid the groundwork for progress in the field. However, their smaller size and inherent limitations pose challenges for training production-grade models. Wake Vision builds upon this foundation by providing a large, diverse, and high-quality dataset specifically tailored for person detection—the cornerstone vision task for TinyML.</p>


<h3>What Makes Wake Vision Different?</h3>

<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiIiZ0YZ6zmdEIbuzsJVyRVinjmWXMr4_PJ_hSPnUvORKH0noke506j_GK6wUB4f_Zjk1Uwxnkew_EJMuHReOpB-mXsowZXaWCfz2-avSeiNRMUspvvVGP8uuyUPSmB4VWtdruDPpBTHlGIC8OGkr-U-pikoAt7jPqohj3-TJtGIy1FKR-sDe5ECTGFOIY/s1600/Screenshot%202024-12-02%20at%202.35.59%E2%80%AFPM.png" style="display: block; padding: 1em 0px; text-align: center;"><img alt="A table displaying the number of images used for training, validation, and testing different datasets, including Wake Vision, Visual Wake Words, CIFAR-100, and PASCAL VOC 2012. The table shows the total number of images and the number of person images in each dataset split." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiIiZ0YZ6zmdEIbuzsJVyRVinjmWXMr4_PJ_hSPnUvORKH0noke506j_GK6wUB4f_Zjk1Uwxnkew_EJMuHReOpB-mXsowZXaWCfz2-avSeiNRMUspvvVGP8uuyUPSmB4VWtdruDPpBTHlGIC8OGkr-U-pikoAt7jPqohj3-TJtGIy1FKR-sDe5ECTGFOIY/s1600/Screenshot%202024-12-02%20at%202.35.59%E2%80%AFPM.png" /></a></div>


<p><a href="https://wakevision.ai/" target="_blank">Wake Vision</a> is a new, large-scale dataset with roughly <b>6 million images</b>, almost <b>100 times larger</b> than VWW, the previous state-of-the-art dataset for person detection in TinyML. 
  The dataset provides two distinct training sets:</p>
<ul>
<li><b>Wake Vision (Large):</b> Prioritizes dataset size.</li>
<li><b>Wake Vision (Quality):</b> Prioritizes label quality.</li>
</ul>

<p>Wake Vision's comprehensive filtering and labeling process significantly enhances the dataset's quality.</p>


<h3>Why Data Quality Matters for TinyML Models</h3>

<p>In traditional overparameterized models, it is widely believed that data quantity matters more than data quality, as an overparameterized model can adapt to errors in the training data. But according to the image below, TinyML tells a different story:</p>


<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto;"><tbody><tr><td style="text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj2yOthWHyZ2ypKziH9FQNwHJK4i3gvE7uqhwyzSANsKmoMRxJRLSJwet9XXdPbDqXTfedaY16N3yYMz0gsdLhCDdpQGl_JcXGmg_F88TAJ8Y9v76avonwwDNUzVCZh3wd3j5bfLVG528kT9kWn2bqq81Wg61kDYcCR4IjLDROo8sTgCkQWfDiBVhzQNj0/s1600/image6.png" style="display: block; margin-left: auto; margin-right: auto; padding: 1em 0px; text-align: center;"><img alt="Five line graphs illustrate the Wake Vision Test Score with varying percentages of training data quality used, comparing models by parameter count (78K, 309K, 1.2M, 4.9M, and 11M) and  error rate (7%, 15%, and 30%)." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj2yOthWHyZ2ypKziH9FQNwHJK4i3gvE7uqhwyzSANsKmoMRxJRLSJwet9XXdPbDqXTfedaY16N3yYMz0gsdLhCDdpQGl_JcXGmg_F88TAJ8Y9v76avonwwDNUzVCZh3wd3j5bfLVG528kT9kWn2bqq81Wg61kDYcCR4IjLDROo8sTgCkQWfDiBVhzQNj0/s1600/image6.png" /></a></td></tr></tbody></table>

<p>The figure above shows that <b>high-quality labels</b> (less error) are more beneficial for under-parameterized models than simply having more data. Larger, error-prone datasets can still be valuable when paired with <b>fine-grained techniques</b>.</p>

<p>By providing two versions of the training set, Wake Vision enables researchers to explore the balance between dataset size and quality effectively.</p>


<h3>Real-World Testing: Wake Vision's Fine-Grained Benchmarks</h3>

<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEA0BqcN0Jw-SSy_dp_JNPr84oLJZF0T6ceGofGbCYmYsY7fjeJmk7LZ7JYJM_NOzoojuQbFADoTVc_8XyzAtSl_XB1yNNIOFlLVdE4QJ94WHNOx5tH-_0o7zyj151eUvhR_NAzeqqDf82sC2SNpMUfsfXj3Dnd-Q5Gs_nzGTxRiuR_6bVs6orbMtKEEU/s1600/Screenshot%202024-12-02%20at%202.47.48%E2%80%AFPM.png" style="display: block; padding: 1em 0px; text-align: center;"><img alt="Five images are shown, each with text underneath describing the content as Perceived Older Person, Near Person, Bright Image, Perceived Female Person, and Depicted Person." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEA0BqcN0Jw-SSy_dp_JNPr84oLJZF0T6ceGofGbCYmYsY7fjeJmk7LZ7JYJM_NOzoojuQbFADoTVc_8XyzAtSl_XB1yNNIOFlLVdE4QJ94WHNOx5tH-_0o7zyj151eUvhR_NAzeqqDf82sC2SNpMUfsfXj3Dnd-Q5Gs_nzGTxRiuR_6bVs6orbMtKEEU/s1600/Screenshot%202024-12-02%20at%202.47.48%E2%80%AFPM.png" /></a></div>

<p>Unlike many open-source datasets, Wake Vision offers <b>fine-grained benchmarks</b> and detailed tests for real-world applications like those shown in the above figure. These enable the evaluation of model performance in real-world scenarios, such as:</p>
<ul>
<li><b>Distance:</b> How well the model detects people at various distances from the camera.</li>
<li><b>Lighting Conditions:</b> Performance in well-lit vs. poorly-lit environments.</li>
<li><b>Depictions:</b> Handling of varied representations of people (e.g., drawings, sculptures).</li>
<li><b>Perceived Gender and Age:</b> Detecting biases across genders and age groups.</li>
</ul>

<p>These benchmarks give researchers a nuanced understanding of model performance in specific, real-world contexts and help identify potential biases and limitations early in the design phase.</p>

<h3>Key Performance Gains With Wake Vision</h3>

<p>The performance gains achieved using Wake Vision are impressive:</p>
<ul>
<li><b>Up to a 6.6% increase in accuracy</b> over the established VWW dataset.</li>
<li><b>Error rate reduction from 7.8% to 2.2%</b> with manual label validation on evaluation sets.</li>
<li><b>Robustness across various real-world conditions</b>, from lighting to perceived age and gender.</li>
</ul>

<p>Furthermore, combining the two Wake Vision training sets, using the larger set for pre-training and the quality set for fine-tuning, yields the best results, highlighting the value of both datasets when used in sophisticated training pipelines.</p>

<h3>Wake Vision Leaderboard: Track and Submit New Top-Performing Models</h3>

<p>The Wake Vision website features a <a href="https://wakevision.ai/#leaderboard" target="_blank">Leaderboard</a>, providing a dedicated platform to assess and compare the performance of models trained on the Wake Vision dataset.</p>

<p>The leaderboard enables a clear and detailed view of how models perform under various conditions, with performance metrics like accuracy, error rates, and robustness across diverse real-world scenarios. It’s an excellent resource for both seasoned researchers and newcomers looking to improve and validate their approaches.</p>

<p>Explore the leaderboard to see the current rankings, learn from high-performing models, and submit your own to contribute to advancing the state of the art in TinyML person detection.</p>


<h3>Making Wake Vision Easy to Access</h3>

<p>Wake Vision is available through popular dataset services such as:</p>
<ul>
<li><a href="https://www.tensorflow.org/datasets/catalog/wake_vision" target="_blank">TensorFlow Datasets (TFDS)</a></li>
<li><a href="https://huggingface.co/datasets/Harvard-Edge/Wake-Vision" target="_blank">Hugging Face Datasets</a></li>
<li><a href="https://edgeai.modelnova.ai/" target="_blank">Edge AI Labs</a></li>
</ul>

<p>With its <b>permissive license</b> (<a href="https://creativecommons.org/licenses/by/4.0/deed.en" target="_blank">CC-BY 4.0</a>), researchers and practitioners can freely use and adapt Wake Vision for their TinyML projects.</p>

<h2>Get Started with Wake Vision Today!</h2>
<p>The Wake Vision team has made the <b>dataset, code, and benchmarks</b> publicly available to accelerate TinyML research and enable the development of better, more reliable person detection models for ultra-low-power devices.</p>

<p>To learn more and access the dataset, visit <a href="https://wakevision.ai/" target="_blank">Wake Vision’s website</a>, where you can also check out a leaderboard of top-performing models on the Wake Vision dataset - and see if you can create better performing models!</p>
