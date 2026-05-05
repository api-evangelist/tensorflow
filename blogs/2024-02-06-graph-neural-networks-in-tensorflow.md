---
title: "Graph neural networks in TensorFlow"
url: "https://blog.tensorflow.org/2024/02/graph-neural-networks-in-tensorflow.html"
date: "2024-02-06T11:00:00.000-08:00"
author: "TensorFlow Blog (noreply@blogger.com)"
feed_url: "https://blog.tensorflow.org/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjmB2uY1xF7sEeT_0hkfCj1oQypkcE9ksjrPXfoOS6hWe6MjNa6OdIZLdu8m8Z2IAx0gk4EhD6fQH5EpOobdT4z0E4w1iSw5YCI7IaRU6jUIL9RpHaU-BEufRlz5Cw2bF6ww4mF6_0N43tSFSkKXVTuy2hvmcx6xYd_hPKzJ_1QvYnKdt3kLNH2iffSmbs/s1600/TFgraph-netural-networks-social.png" style="display: none;" />

<em>Posted by Dustin Zelle – Software Engineer, Research and Arno Eigenwillig – Software Engineer, CoreML</em>

<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFzx_P7ogIv5kpZcabEMbL5hkABibribiGZtH-aiI6UPSBeXFD392VF7p30Aq57Jj4LxIxVcpeOQdpm-5pGDzk1kLG5Dj85pktgsNX1f7FC8sbTWnR6iS8H2WkW0ESZAn30OcDvWRcaUA1e7FgTKD0PzHRk-8Yn73eiePFnoN78uB2tmIF06ySty1_N3I/s1600/TFgraph-netural-networks-header.png"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFzx_P7ogIv5kpZcabEMbL5hkABibribiGZtH-aiI6UPSBeXFD392VF7p30Aq57Jj4LxIxVcpeOQdpm-5pGDzk1kLG5Dj85pktgsNX1f7FC8sbTWnR6iS8H2WkW0ESZAn30OcDvWRcaUA1e7FgTKD0PzHRk-8Yn73eiePFnoN78uB2tmIF06ySty1_N3I/s1600/TFgraph-netural-networks-header.png" /></a>

<a name="more"></a><p></p>

<p><em>This article is also shared on the&nbsp;<a href="https://blog.research.google/2024/02/graph-neural-networks-in-tensorflow.html" target="_blank">Google Research Blog</a></em></p><p><em><br /></em></p>



<p>Objects and their relationships are ubiquitous in the world around us, and relationships can be as important to understanding an object as its own attributes viewed in isolation — for example: transportation networks, production networks, knowledge graphs, or social networks.  Discrete mathematics and computer science have a long history of formalizing such networks them as <a href="https://en.wikipedia.org/wiki/Graph_%28discrete_mathematics%29" target="_blank"><i>graphs</i></a>, consisting of <i>nodes</i> arbitrarily connected by <i>edges</i> in various irregular ways. Yet most machine learning (ML) algorithms allow only for regular and uniform relations between input objects, such as a grid of pixels, a sequence of words, or no relation at all.</p> 
  
<p><a href="https://distill.pub/2021/gnn-intro/" target="_blank">Graph neural networks</a>, or GNNs for short, have emerged as a powerful technique to leverage both the graph’s connectivity (as in the older algorithms <a href="http://perozzi.net/projects/deepwalk/" target="_blank">DeepWalk</a> and <a href="https://snap.stanford.edu/node2vec/" target="_blank">Node2Vec</a>) and the input features on the various nodes and edges. GNNs can make predictions for graphs as a whole (Does this molecule react in a certain way?), for individual nodes (What’s the topic of this document, given its citations?) or for potential edges (Is this product likely to be purchased together with that product?). Apart from making predictions about graphs, GNNs are a powerful tool used to bridge the chasm to more typical neural network use cases. They encode a graph's <i>discrete</i>, <i>relational</i> information in a <i>continuous</i> way so that it can be included naturally in another deep learning system.</p>


<p>We are excited to announce the release of <a href="https://github.com/tensorflow/gnn" target="_blank">TensorFlow GNN 1.0</a>&nbsp;(TF-GNN), a production-tested library for building GNNs at large scale. It supports both modeling and training in TensorFlow as well as the extraction of input graphs from huge data stores. TF-GNN is built from the ground up for heterogeneous graphs where types and relations are represented by distinct sets of nodes and edges. Real-world objects and their relations occur in distinct types and TF-GNN's heterogeneous focus makes it natural to represent them.</p>

<p>Inside TensorFlow, such graphs are represented by objects of type <code>tfgnn.GraphTensor</code>. This is a composite tensor type (a collection of tensors in one Python class) accepted as a <a href="https://en.wikipedia.org/wiki/First-class_citizen" target="_blank">first-class citizen</a> in <code>tf.data.Dataset</code>,&nbsp;<code>tf.function</code>, etc. It stores both the graph structure and its features attached to nodes, edges and the graph as a whole. Trainable transformations of GraphTensors can be defined as Layers objects in the high-level <a href="https://www.tensorflow.org/guide/keras" target="_blank">Keras API</a>, or directly using the <code>tfgnn.GraphTensor</code> primitive.</p>

<h2>GNNs: Making predictions for an object in context</h2>


<p>For illustration, let’s look at one typical application of TF-GNN: predicting a property of a certain type of node in a graph defined by cross-referencing tables of a huge database. For example, a citation database of Computer Science (CS) arXiv papers with one-to-many cites and many-to-one cited relationships where we would like to predict the subject area of each paper.</p>

<p>Like most neural networks, a GNN is trained on a dataset of many labeled examples (~millions), but each training step consists only of a much smaller batch of training examples (say, hundreds). To scale to millions, the GNN gets trained on a stream of reasonably small subgraphs from the underlying graph. Each subgraph contains enough of the original data to compute the GNN result for the labeled node at its center and train the model. This process — typically referred to as subgraph sampling — is extremely consequential for GNN training. Most existing tooling accomplishes sampling in a batch way, producing static subgraphs for training. TF-GNN provides tooling to improve on this by sampling dynamically and interactively. </p>

<div><table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><center><img alt="moving image illustrating the process of subgraph sampling where small, tractable subgraphs are sampled from a larger graph to create input examples for GNN training." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgdcxMo1kRE6OY7Xi_6sz1iah067JWj5Ic4-myeZwcwpqOVH9raRXhuxxp3xkra5arDS_IZHB6H_Aiwyjd-4daydjwFxtD9YohzAd7axB3260lTjwLo7PuQ1BxIBGZ83IK8WGKcwDyXJlGIPLOivTqG8FR3kzRUi8vOhlwxF-URAts2Vbc8ZXoEAwBxq50/s1600/image2.gif" style="width: auto;" /></center></td></tr><tr><td class="tr-caption" style="text-align: center;"><i>Pictured, the process of subgraph sampling where small, tractable subgraphs are sampled from a larger graph to create input examples for GNN training.</i></td></tr></tbody></table></div>


<p>TF-GNN 1.0 debuts a flexible Python API to configure dynamic or batch subgraph sampling at all relevant scales: interactively in a Colab notebook (like <a href="https://colab.research.google.com/github/tensorflow/gnn/blob/master/examples/notebooks/ogbn_mag_e2e.ipynb" target="_blank">this one</a>), for efficient sampling of a small dataset stored in the main memory of a single training host, or distributed by <a href="https://beam.apache.org/" target="_blank">Apache Beam</a> for huge datasets stored on a network filesystem (up to hundreds of millions of nodes and billions of edges). For details, please refer to our user guides for <a href="https://github.com/tensorflow/gnn/blob/main/tensorflow_gnn/docs/guide/inmemory_sampler.md" target="_blank">in-memory</a> and <a href="https://github.com/tensorflow/gnn/blob/main/tensorflow_gnn/docs/guide/beam_sampler.md" target="_blank">beam-based</a> sampling, respectively.</p>

<p>On those same sampled subgraphs, the GNN’s task is to compute a hidden (or latent) state at the root node; the hidden state aggregates and encodes the relevant information of the root node's neighborhood. One classical approach is <a href="https://research.google/pubs/neural-message-passing-for-quantum-chemistry/" target="_blank">message-passing neural networks</a>. In each round of message passing, nodes receive messages from their neighbors along incoming edges and update their own hidden state from them. After <i>n</i> rounds, the hidden state of the root node reflects the aggregate information from all nodes within <i>n</i> edges (pictured below for <i>n</i> = 2). The messages and the new hidden states are computed by hidden layers of the neural network. In a heterogeneous graph, it often makes sense to use separately trained hidden layers for the different types of nodes and edges.</p>

<div><table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><center><img alt="moving image illustrating the process of subgraph sampling where small, tractable subgraphs are sampled from a larger graph to create input examples for GNN training." border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjtpQadw1OPvgGJC11NfogydDRpg6-XBK_Cm3E9qq-9J5MYSe7_P8IR-0Yn8puV0Xmq4PifMOZtuKWxfran3yMuYK5YwBRV8Ut_3MNFlxdB-9-L7OTePqy3fUQi3X5PptSyiUjhgihynm5r3NBH0mrjbmW4B3j7H08xXruud7tLFhR-1FE_wQifcLt9ku8/s1600/image1.gif" style="width: auto;" /></center></td></tr><tr><td class="tr-caption" style="text-align: center;"><i>Pictured, a simple message-passing neural network where, at each step, the node state is propagated from outer to inner nodes where it is pooled to compute new node states. Once the root node is reached, a final prediction can be made.</i></td></tr></tbody></table></div>

<p>The training setup is completed by placing an output layer on top of the GNN’s hidden state for the labeled nodes, computing the loss (to measure the prediction error), and updating model weights by backpropagation, as usual in any neural network training.</p> 

<p>Beyond supervised training (i.e., minimizing a loss defined by labels), GNNs can also be trained in an unsupervised way (i.e., without labels). This lets us compute a <i>continuous</i> representation (or <i>embedding</i>) of the <i>discrete</i> graph structure of nodes and their features. These representations are then typically utilized in other ML systems. In this way, the discrete, relational information encoded by a graph can be included in more typical neural network use cases. TF-GNN supports a fine-grained specification of unsupervised objectives for heterogeneous graphs.</p>

<h2>Building GNN architectures</h2>

<p>The TF-GNN library supports building and training GNNs at various levels of abstraction.</p>

<p>At the highest level, users can take any of the predefined models bundled with the library that are expressed in Keras layers. Besides a small collection of models from the research literature, TF-GNN comes with a highly configurable model template that provides a curated selection of modeling choices that we have found to provide strong baselines on many of our in-house problems. The templates implement GNN layers; users need only to initialize the Keras layers.</p>


<div style="background: rgb(248, 248, 248); border: 0px; overflow: auto; width: auto;"><pre style="line-height: 125%; margin: 0px;"><span style="color: #444444; font-family: courier;">import tensorflow_gnn as tfgnn
from tensorflow_gnn<span>.</span>models import mt_albis

def model_fn(graph_tensor_spec<span>:</span> tfgnn<span>.</span>GraphTensorSpec)<span>:</span>
  """Builds a GNN as a Keras model<span>."""</span>
  graph <span>=</span> inputs <span>=</span> tf<span>.</span>keras<span>.</span>Input(type_spec<span>=</span>graph_tensor_spec)

  # Encode input features (callback omitted <span>for</span> brevity)<span>.</span>
  graph <span>=</span> tfgnn<span>.</span>keras<span>.</span>layers<span>.</span>MapFeatures(
      node_sets_fn<span>=</span>set_initial_node_states)(graph)

  # <span>For</span> each <span>round</span> of message passing<span>...</span>
  <span>for</span> _ in range(<span>2</span>)<span>:</span>
    # <span>...</span> create <span>and</span> apply a Keras layer<span>.</span>
    graph <span>=</span> mt_albis<span>.</span>MtAlbisGraphUpdate(
        units<span>=128</span>, message_dim<span>=64</span>,
        attention_type<span>="</span>none", simple_conv_reduce_type<span>=</span><span>"mean"</span>,
        normalization_type<span>=</span><span>"layer"</span>, next_state_type<span>=</span><span>"residual"</span>,
        state_dropout_rate<span>=0.2</span>, l2_regularization<span>=1e-5</span>,
    )(graph)

  <span>return</span> tf<span>.</span>keras<span>.</span>Model(inputs, graph)</span>
</pre></div>

<p>At the lowest level, users can write a GNN model from scratch in terms of primitives for passing data around the graph, such as broadcasting data from a node to all its outgoing edges or pooling data into a node from all its incoming edges (e.g., computing the sum of incoming messages). TF-GNN’s graph data model treats nodes, edges and whole input graphs equally when it comes to features or hidden states, making it straightforward to express not only node-centric models like the MPNN discussed above but also more general forms of <a href="https://arxiv.org/abs/1806.01261" target="_blank">GraphNets</a>. This can, but need not, be done with Keras as a modeling framework on the top of core TensorFlow. For more details, and intermediate levels of modeling, see the TF-GNN <a href="https://github.com/tensorflow/gnn/blob/main/tensorflow_gnn/docs/guide/gnn_modeling.md" target="_blank">user guide</a> and <a href="https://github.com/tensorflow/gnn/tree/main/tensorflow_gnn/models" target="_blank">model collection</a>.</p>

<h2>Training orchestration</h2>

<p>While advanced users are free to do custom model training, the <a href="https://github.com/tensorflow/gnn/blob/main/tensorflow_gnn/docs/guide/runner.md" target="_blank">TF-GNN Runner</a> also provides a succinct way to orchestrate the training of Keras models in the common cases. A simple invocation may look like this:</p>

<div style="background: rgb(248, 248, 248); border: 0px; overflow: auto; width: auto;"><pre style="line-height: 125%; margin: 0px;"><span style="color: #444444; font-family: courier;">from tensorflow_gnn import runner

runner<span>.</span><span>run</span>(
   task<span>=</span>runner<span>.</span>RootNodeBinaryClassification("papers", <span>...</span>),
   model_fn<span>=</span>model_fn,
   trainer<span>=</span>runner<span>.</span>KerasTrainer(tf<span>.</span>distribute<span>.</span>MirroredStrategy(), model_dir<span>=</span><span>"</span><span>/</span>tmp<span>/</span>model"),
   optimizer_fn<span>=</span>tf<span>.</span>keras<span>.</span>optimizers<span>.</span>Adam,
   epochs<span>=10</span>,
   global_batch_size<span>=128</span>,
   train_ds_provider<span>=</span>runner<span>.</span>TFRecordDatasetProvider("<span>/</span>tmp<span>/</span>train<span>*"</span>),
   valid_ds_provider<span>=</span>runner<span>.</span>TFRecordDatasetProvider("<span>/</span>tmp<span>/</span>validation<span>*"</span>),
   gtspec<span>=...</span>,
)</span>
</pre></div>

<p>The Runner provides ready-to-use solutions for ML pains like distributed training and <code>tfgnn.GraphTensor</code> padding for fixed shapes on Cloud TPUs. Beyond training on a single task (as shown above), it supports joint training on multiple (two or more) tasks in concert. For example, unsupervised tasks can be mixed with supervised ones to inform a final continuous representation (or embedding) with application specific inductive biases. Callers only need substitute the task argument with a mapping of tasks:</p>

<div style="background: rgb(248, 248, 248); border: 0px; overflow: auto; width: auto;"><pre style="line-height: 125%; margin: 0px;"><span style="color: #444444; font-family: courier;">from tensorflow_gnn import runner
from tensorflow_gnn<span>.</span>models import contrastive_losses

runner<span>.</span><span>run</span>(
     task<span>=</span>{
        <span>"classification"</span><span>:</span> runner<span>.</span>RootNodeBinaryClassification("papers", <span>...</span>),
        <span>"dgi"</span><span>:</span> contrastive_losses<span>.</span>DeepGraphInfomaxTask(<span>"papers"</span>),
      },
    <span>...</span>
)</span>
</pre></div>

<p>Additionally, the TF-GNN Runner also includes an implementation of <a href="https://www.tensorflow.org/tutorials/interpretability/integrated_gradients" target="_blank">integrated gradients</a> for use in model attribution. Integrated gradients&nbsp;output is a GraphTensor with the same connectivity as the observed GraphTensor but its features replaced with gradient values where larger values contribute more than smaller values in the GNN prediction. Users can inspect gradient values to see which features their GNN uses the most.</p> 

<h2>Conclusion</h2>

<p>In short, we hope TF-GNN will be useful to advance the application of GNNs in TensorFlow at scale and fuel further innovation in the field. If you’re curious to find out more, please try our <a href="https://colab.sandbox.google.com/github/tensorflow/gnn/blob/master/examples/notebooks/ogbn_mag_e2e.ipynb" target="_blank">Colab demo</a> with the popular OGBN-MAG benchmark (in your browser, no installation required), browse the rest of our <a href="https://github.com/tensorflow/gnn/blob/main/tensorflow_gnn/docs/guide/overview.md" target="_blank">user guides and Colabs</a>, or take a look at our <a href="https://arxiv.org/abs/2207.03522" target="_blank">paper</a>.</p>


<h3>Acknowledgements</h3>
<p><em>The TF-GNN release 1.0 was developed by a collaboration between <b>Google Research</b> (Sami Abu-El-Haija, Neslihan Bulut, Bahar Fatemi, Johannes Gasteiger, Pedro Gonnet, Jonathan Halcrow, Liangze Jiang, Silvio Lattanzi, Brandon Mayer, Vahab Mirrokni, Bryan Perozzi, Anton Tsitsulin, Dustin Zelle), <b>Google Core ML</b> (Arno Eigenwillig, Oleksandr Ferludin, Parth Kothari, Mihir Paradkar, Jan Pfeifer, Rachael Tamakloe), and <b>Google DeepMind</b> (Alvaro Sanchez-Gonzalez and Lisa Wang).</em></p>
