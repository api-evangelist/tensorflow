---
title: "MLSysBook.AI: Principles and Practices of Machine Learning Systems Engineering"
url: "https://blog.tensorflow.org/2024/11/mlsysbookai-principles-and-practices-of-machine-learning-systems-engineering.html"
date: "2024-11-19T09:00:00.000-08:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiCrY0ybsygB35ZxLoYErMW4s26SSiF_pHCKXTSO2poVyVL2-zlIr0WC6yugLgtnQzi7m_OlgnzUKEMG50g6tDH_CrClBqDK_Py8BXjHcZxWFprthF6uRcOzI1EaXSRhYl-xpUyTycUA6vXmjWPNWsYjOvCcBxsjbZ3TcsN7kNUW8dfVrEJuGY_gYjqi1Y/s1600/social-Practices-of-ML-systems-engineering.png" style="display: none;" />

<em>Posted by Jason Jabbour, Kai Kleinbard and <a href="http://scholar.harvard.edu/vijay-janapa-reddi/" target="_blank">Vijay Janapa Reddi</a> (Harvard University)</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjWzldLNhl1RyM2-V8XdUtlf4P5__oJdAaN9GxyGvic4K8RCtOH8KpixLS-oQF5ZB5zn89d3QX-lX_6rn2eqeCJ-evLJKfo7unJRL8sGFodqswVywDYmc9sRTkf-Bo3ToOgECA7nElSXroZBsNFh_o2chlCuipwlWAwyJ4gLvxiosMQcU-8iRpf5jaUuxk/s1600/header-Practices-of-ML-systems-engineering.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjWzldLNhl1RyM2-V8XdUtlf4P5__oJdAaN9GxyGvic4K8RCtOH8KpixLS-oQF5ZB5zn89d3QX-lX_6rn2eqeCJ-evLJKfo7unJRL8sGFodqswVywDYmc9sRTkf-Bo3ToOgECA7nElSXroZBsNFh_o2chlCuipwlWAwyJ4gLvxiosMQcU-8iRpf5jaUuxk/s1600/header-Practices-of-ML-systems-engineering.png" /></a>

<a name="more"></a><p></p>

<h2>Everyone wants to do the modeling work, but no one wants to do the engineering.</h2>

<p><i>If ML developers are like astronauts exploring new frontiers, ML systems engineers are the rocket scientists designing and building the engines that take them there.</i></p>

<h3>Introduction</h3>

<p>"Everyone wants to do modeling, but no one wants to do the engineering," highlights a stark reality in the machine learning (ML) world: the allure of building sophisticated models often overshadows the critical task of engineering them into robust, scalable, and efficient systems.</p>
  
<p>The reality is that ML and systems are inextricably linked. Models, no matter how innovative, are computationally demanding and require substantial resources—with the rise of generative AI and increasingly complex models, understanding how ML infrastructure scales becomes even more critical. Ignoring the system's limitations during model development is a recipe for disaster.</p>
  
<p>Unfortunately, educational resources on the systems side of machine learning are lacking. There are plenty of textbooks and materials on <a href="https://www.tensorflow.org/resources/learn-ml#books" target="_blank">deep learning theory and concepts</a>. However, we truly need more resources on the infrastructure and systems side of machine learning. Critical questions—such as how to optimize models for specific hardware, deploy them at scale, and ensure system efficiency and reliability—are still not adequately understood by ML practitioners. This lack of understanding is not due to disinterest but rather a gap in available knowledge.</p> 
  
<p>One significant resource addressing this gap is <a href="http://MLSysBook.ai" target="_blank">MLSysBook.ai</a>. This blog post explores key ML systems engineering concepts from MLSysBook.ai and maps them to the TensorFlow ecosystem to provide practical insights for building efficient ML systems.</p> 


<h3>The Connection Between Machine Learning and Systems</h3>

<p>Many think machine learning is solely about extracting patterns and insights from data. While this is fundamental, it’s only part of the story. Training and deploying these "deep" neural network models often necessitates vast computational resources, from powerful GPUs and TPUs to massive datasets and distributed computing clusters.</p> 

<p>Consider the recent wave of large language models (LLMs) that have pushed the boundaries of natural language processing. These models highlight the immense computational challenges in training and deploying large-scale machine learning models. Without carefully considering the underlying system, training times can stretch from days to weeks, inference can become sluggish, and deployment costs can skyrocket.</p> 

<p>Building a successful machine-learning solution involves the entire system, not just the model. This is where ML systems engineering takes the reins, allowing you to optimize model architecture, hardware selection, and deployment strategies, ensuring that your models are not only powerful in theory but also efficient and scalable.</p> 

<p>To draw an analogy, if developing algorithms is like being an astronaut exploring the vast unknown of space, then ML systems engineering is similar to the work of rocket scientists building the engines that make those journeys possible. Without the precise engineering of rocket scientists, even the most adventurous astronauts would remain earthbound.</p> 


<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjsH_zM77JldWBIbYLEZWoocfBzqhBA0iul9s9ZUHsAYmSYoUIEN6aWoUFe3woWvHLgFRNsUiUkKGWcYS4nDjBqiMI3o-DMgIxmLIH-wURGkvfwox5NF5oDtczINYqcisbOUJhUDGuw2KtZAly-wiMS7_nHLy2FkJCtTXyT3hcmPExZnxk1Hgz6vwwvaYs/s1600/MLSysbook-AI-cover-image.png" style="display: block; padding: 1em 0px; text-align: center;"><img alt="An abstract circular design resembling a network or neural pathways consisting of interconnected nodes and lines in shades of blue, pink, and gray, against a white background" border="0" height="640" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjsH_zM77JldWBIbYLEZWoocfBzqhBA0iul9s9ZUHsAYmSYoUIEN6aWoUFe3woWvHLgFRNsUiUkKGWcYS4nDjBqiMI3o-DMgIxmLIH-wURGkvfwox5NF5oDtczINYqcisbOUJhUDGuw2KtZAly-wiMS7_nHLy2FkJCtTXyT3hcmPExZnxk1Hgz6vwwvaYs/s1600/MLSysbook-AI-cover-image.png" width="100%" /></a></div>



<h3>Bridging the Gap: MLSysBook.ai and System-Level Thinking</h3>

<p>One important new resource this blog post offers for insights into ML systems engineering is an open-source "textbook" — <a href="http://MLSysBook.ai" target="_blank">MLSysBook.ai</a> —developed initially as part of Harvard University's <a href="https://sites.google.com/g.harvard.edu/cs249-tinyml-2023" target="_blank">CS249r Tiny Machine Learning</a> course and <a href="https://www.edx.org/certificates/professional-certificate/harvardx-tiny-machine-learning" target="_blank">HarvardX's TinyML</a> online series. This project, which has expanded into an open, collaborative initiative, dives deep into the end-to-end ML lifecycle.</p>
  
<p>It highlights that the principles governing ML systems, whether designed for tiny embedded devices or large data centers, are fundamentally similar. For instance, while tiny machines might employ INT8 for numeric operations to save resources, larger systems often utilize FP16 for higher precision—the fundamental concepts, such as quantization, span across both scenarios.</p>

<p>Key concepts covered in this resource include:</p>

<ul><ol>
<li><b>Data Engineering:</b> Setting the foundation by efficiently collecting, preprocessing, and managing data to prepare it for the machine learning pipeline.</li>
<li><b>Model Development:</b> Crafting and refining machine learning models to meet specific tasks and performance goals.</li>
<li><b>Optimization:</b> Fine-tuning model performance and efficiency, ensuring effective use of hardware and resources within the system.</li>
<li><b>Deployment:</b> Transitioning models from development to real-world production environments while scaling and adapting them to existing infrastructure.</li>
<li><b>Monitoring and Maintenance:</b> Continuously tracking system health and performance to maintain reliability, address issues, and adapt to evolving data and requirements.</li>
</ol></ul>

<p>In an efficient ML system, data engineering lays the groundwork by preparing and organizing raw data, which is essential for any machine learning process. This ensures data can be transformed into actionable insights during model development, where machine learning models are created and refined for specific tasks. Following development, optimization becomes critical for enhancing model performance and efficiency, ensuring that models are tuned to run effectively on the designated hardware and within the system's constraints.</p>

<p>The seamless integration of these steps then extends into the deployment phase, where models are brought into real-world production environments. Here, they must be scaled and adapted to function effectively within existing infrastructure, highlighting the importance of robust ML systems engineering. However, the lifecycle of an ML system continues after deployment; continuous monitoring and maintenance are vital. This ongoing process ensures that ML systems remain healthy, reliable and perform optimally over time, adapting to new data and requirements as they arise.</p>

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto;"><tbody><tr><td style="text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEikJkY7JpFbxDQ_j0CRSad_aP9CJHu9a9NxEq6eVK50_tcdJLum-gBeWKd1bUTVf8e9yk6zsIgleXvX8j2nQBcY7WVrWe7cutfuiRHAh3fODXrv-j4ye-FnGkGs5SQqZyojTbhQtNqkyKHwkksLVtgh-Mspfzj1PSqN71ULNhdiQ_qXj_F4rpVzHvqtFQA/s1600/image1.png" style="display: block; margin-left: auto; margin-right: auto; padding: 1em 0px; text-align: center;"><img alt="A flowchart diagrams the dependencies between different machine learning concepts, tools, and systems.  Beige boxes represent concepts like 'Data Engineering' and tools like 'TensorFlow Data', while blue boxes indicate higher-level systems like 'ML Systems Engineering Principles' and 'Efficient ML Systems'.  Arrows and dotted lines illustrate the relationships and workflow between these elements." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEikJkY7JpFbxDQ_j0CRSad_aP9CJHu9a9NxEq6eVK50_tcdJLum-gBeWKd1bUTVf8e9yk6zsIgleXvX8j2nQBcY7WVrWe7cutfuiRHAh3fODXrv-j4ye-FnGkGs5SQqZyojTbhQtNqkyKHwkksLVtgh-Mspfzj1PSqN71ULNhdiQ_qXj_F4rpVzHvqtFQA/s1600/image1.png" /></a></td></tr><tr><td class="tr-caption" style="text-align: center;"><span style="text-align: start;"><i>A mapping of MLSysBook.AI's core ML systems engineering concepts to the TensorFlow ecosystem, illustrating how specific TensorFlow tools support each stage of the machine learning lifecycle, ultimately contributing to the creation of efficient ML systems.</i></span></td></tr></tbody></table>

<h3>SocratiQ: An Interactive AI-Powered Generative Learning Assistant</h3>

<p>One of the exciting innovations we’ve integrated into MLSysBook.ai is SocratiQ—an AI-powered learning assistant designed to foster a deeper and more engaging connection with content focused on machine learning systems. By leveraging a Large Language Model (LLM), SocratiQ turns learning into a dynamic, interactive experience that allows students and practitioners to engage with and co-create their educational journey actively.</p>

<p>With SocratiQ, readers transition from passive content consumption to an active, personalized learning experience. Here’s how SocratiQ makes this possible:</p>


<ul>
<li><b>Interactive Quizzes:</b> SocratiQ enhances the learning process by automatically generating quizzes based on the reading content. This feature encourages active reflection and reinforces understanding without disrupting the learning flow. Learners can test their comprehension of complex ML systems concepts.</li>
  
<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh2kTEI9cc1EC8cT3TZOQOlOjid4Stn6HUw6u_lMJhzlyFjN9uUhEiAF7KgdLt4Kkx-WsrD6h2qD2SXYixq3mhNBHcofRNjirj5YBGkIakL88shHyLDPWF42XXFU6S3pZrY8jSaoA617qSo96w68yc1mfCTdxxpGMX2dmMuR2Aq6TEAIsMtAjVGMlQzzwA/s1600/image1.gif" style="display: block; padding: 1em 0; text-align: center;"><img alt="moving image of an interactive quiz in SocratiQ" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh2kTEI9cc1EC8cT3TZOQOlOjid4Stn6HUw6u_lMJhzlyFjN9uUhEiAF7KgdLt4Kkx-WsrD6h2qD2SXYixq3mhNBHcofRNjirj5YBGkIakL88shHyLDPWF42XXFU6S3pZrY8jSaoA617qSo96w68yc1mfCTdxxpGMX2dmMuR2Aq6TEAIsMtAjVGMlQzzwA/s1600/image1.gif" /></a></div>
  
<li><b>Adaptive, In-Content Learning:</b> SocratiQ offers real-time conversations with the LLM without pulling learners away from the content they're engaging with. Acting as a personalized Teaching Assistant (TA), it provides tailored explanations.</li>
  
<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjUay_zDBbYIRqjdZURADOmGhOddBRBVCFpavhrLd58U_DPVO6svaHDWdZt1v79OBztkIGX8YX5HUsIwsTZH7GdW41UvB2tBN9pFh_F7ndV3GRypiXSFdur-Urzbk7ADgGnMVwpAyGDiChNwX3tHQSlbXxz2QMT1qlt1JFeNdm95_FOHrjo0uRPIK9iD84/s1600/image2.gif" style="display: block; padding: 1em 0; text-align: center;"><img alt="moving image of an real-time conversation with the LLM in SocratiQ" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjUay_zDBbYIRqjdZURADOmGhOddBRBVCFpavhrLd58U_DPVO6svaHDWdZt1v79OBztkIGX8YX5HUsIwsTZH7GdW41UvB2tBN9pFh_F7ndV3GRypiXSFdur-Urzbk7ADgGnMVwpAyGDiChNwX3tHQSlbXxz2QMT1qlt1JFeNdm95_FOHrjo0uRPIK9iD84/s1600/image2.gif" /></a></div>  
  
  
<li><b>Progress Assessment and Gamification:</b> Learners’ progress is tracked and stored locally in their browser, providing a personalized path to developing skills without privacy concerns. This allows for evolving engagement as the learner progresses through the material.</li>
  
<div class="separator" style="clear: both;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjhn8OGbgDk-LadioL-JftNCi3Dzc8g0t46yHHiXEOwK07fynDdsdGTbBVfA8DuHtd72ygnpuWw3dk6hQmAbaIFT590IHtTyCZdFzRoNtriU07Ww4p4rV3sFaHcM6bvO2VLphGyDhZ0wLX3Po4VGJ69aXehtbaJWArUxDIqkrQGXftB3CYR2RBzV_lLdJs/s1600/image5.png" style="display: block; padding: 1em 0; text-align: center;"><img alt="A Quiz Performance Dashboard in SocratiQ" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjhn8OGbgDk-LadioL-JftNCi3Dzc8g0t46yHHiXEOwK07fynDdsdGTbBVfA8DuHtd72ygnpuWw3dk6hQmAbaIFT590IHtTyCZdFzRoNtriU07Ww4p4rV3sFaHcM6bvO2VLphGyDhZ0wLX3Po4VGJ69aXehtbaJWArUxDIqkrQGXftB3CYR2RBzV_lLdJs/s1600/image5.png" /></a></div>
  
</ul>

<p>SocratiQ strives to be a supportive guide that respects the primacy of the content itself. It subtly integrates into the learning flow, stepping in when needed to provide guidance, quizzes, or explanations—then stepping back to let the reader continue undistracted. This design ensures that SocratiQ works harmoniously within the natural reading experience, offering support and personalization while keeping the learner immersed in the content.</p>

<p>We plan to integrate capabilities such as research lookups and case studies. The aim is to create a unique learning environment where readers can study and actively engage with the material. This blend of content and AI-driven assistance transforms MLSysBook.ai into a living educational resource that grows alongside the learner's understanding.</p>


<h3>Mapping MLSysBook.ai's Concepts to the TensorFlow Ecosystem</h3>

<p>MLSysBook.AI focuses on the core concepts in ML system engineering while providing strategic tie-ins to the TensorFlow ecosystem. The TensorFlow ecosystem offers a rich environment for realizing many of the principles discussed in MLSysBook.AI. This makes the TensorFlow ecosystem a perfect match for the key ML systems concepts covered in MLSysBook.AI, with each tool supporting a specific stage of the machine learning process:</p>

<ul>
<li><b><a href="https://www.tensorflow.org/datasets" target="_blank">TensorFlow Data</a> (Data Engineering):</b> Supports efficient data preprocessing and input pipelines.</li>
<li><b><a href="https://www.tensorflow.org/tutorials" target="_blank">TensorFlow Core</a> (Model Development):</b> Central to model creation and training.</li>
<li><b><a href="https://www.tensorflow.org/lite" target="_blank">TensorFlow Lite</a> (Optimization):</b> Enables model optimization for various deployment scenarios, especially critical for edge devices.</li>
<li><b><a href="https://www.tensorflow.org/tfx/guide/serving" target="_blank">TensorFlow Serving</a> (Deployment):</b> Facilitates smooth model deployment in production environments.
</li>
<li><b><a href="https://www.tensorflow.org/tfx" target="_blank">TensorFlow Extended</a> (Monitoring and maintenance):</b> Offers comprehensive tools for ongoing system health and performance.</li>
</ul>

<p>Note that MLSysBook.AI does not explicitly teach or focus on TensorFlow-specific concepts or implementations. The book's primary goal is to explore fundamental ML system engineering principles. The connections drawn in this blog post to the TensorFlow ecosystem are simply intended to illustrate how these core concepts align with tools and practices used by industry practitioners, providing a bridge between theoretical understanding and real-world application.</p>

<h3>Support ML Systems Education: Every Star Counts 🌟</h3>

<p>If you find this blog post valuable and want to improve ML systems engineering education, please consider giving the MLSysBook.ai <a href="https://github.com/harvard-edge/cs249r_book" target="_blank">GitHub repository</a> a star ⭐.</p>

<p>Thanks to our sponsors, each ⭐ added to the MLSysBook.ai GitHub repository translates to donations supporting students and minorities globally by funding their research scholarships, empowering them to drive innovation in machine learning systems research worldwide.</p> 

<p>Every star counts—help us reach the generous funding cap!</p>


<h3>Conclusion</h3>

<p>The gap between ML modeling and system engineering is closing, and understanding both aspects is important for creating impactful AI solutions. By embracing ML system engineering principles and leveraging powerful tools like those in the TensorFlow ecosystem, we can go beyond building models to creating complete, optimized, and scalable ML systems.</p>

<p>As AI continues to evolve, the demand for professionals who can bridge the gap between ML algorithms and systems implementation will only grow. Whether you're a seasoned practitioner or just starting your ML journey, investing time in understanding ML systems engineering will undoubtedly pay dividends in your career and the impact of your work. If you’d like to learn more, listen to our MLSysBook.AI <a href="https://notebooklm.google.com/notebook/bae2e128-7926-4ba9-8503-2b54ff3237f9/audio" target="_blank">podcast</a>, generated by Google’s NotebookLM.</p>

<p>Remember, even the most brilliant astronauts need skilled engineers to build their rockets!</p>

<h4>Acknowledgments</h4>
<p><i>We thank Josh Gordon for his suggestion to write this blog post and for encouraging and sharing ideas on how the book could be a useful resource for the TensorFlow community.</i></p>
