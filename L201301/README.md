# TENSOR FLOW

## What is Tensor flow?

TensorFlow is a free and open-source software library for machine learning and 
artificial intelligence. It can be used across a range of tasks but has a particular focus 
on training and inference of deep neural networks. TensorFlow makes it easy for 
beginners and experts to create machine learning models for desktop, mobile, web, 
and cloud.

## What is Core of Tensor flow?

The TensorFlow Core APIs provide a set of comprehensive, composable, 
and extensible low-level APIs for high-performance (distributed & accelerated) 
computation, primarily aimed at building machine learning (ML) models as well as 
authoring ML workflow tools and frameworks within the TensorFlow platform


## Modular TensorFlow: 

This project aims to split the TensorFlow codebase into smaller, more focused, 
repositories that can be released and managed separately. These modules will talk 
to each other using well defined APIs. Thanks to the module APIs, these modules 
are now managed/owned/released independently

## Modules: 

To do machine learning in TensorFlow, you are likely to need to define, 
save, and restore a model.
A model is, abstractly:
• A function that computes something on tensors (a forward pass) 
• Some variables that can be updated in response to trainin

#### Defining Models and layers in Tensor Flow:

Most models are made of layers. Layers are functions with a known 
mathematical structure that can be reused and have trainable variables. In 
TensorFlow, most high-level implementations of layers and models, such as 
Keras or Sonnet, are built on the same foundational class: tf.Module.

```
class SimpleModule(tf.Module): 
def __init__(self, name=None): 
super().__init__(name=name) 
self.a_variable = tf.Variable(5.0, name="train_me") 
self.non_trainable_variable = tf.Variable(5.0, 
trainable=False, name="do_not_train_me") 
def __call__(self, x): 
return self.a_variable * x + self.non_trainable_variable 
simple_module = SimpleModule(name="simple") 
simple_module(tf.constant(5.0))
```


## Reusability: 

Tensor flow provide facility of reuse parts of machine learning modules. By a 
module, we mean a self-contained piece of a TensorFlow graph, along with its 
weights, that can be reused across other, similar tasks. By reusing a module, a 
developer can train a model using a smaller dataset, improve generalization, or 
simply speed up training. Let’s look at a couple examples to make this concrete.

TensorFlow Hub hosts Saved Models for TensorFlow 2, among other assets. 
They can be loaded back into a Python program with obj = hub .load ( url ). The 
returned obj is the result of tf. saved model. load(). This object can have arbitrary 
attributes that are tf. functions, tf. Variables (initialized from their pre-trained values), 
other resources and, recursively, more such objects.

An interface to be implemented by the loaded obj in order to be reused in a 
TensorFlow Python program. Saved Models conforming to this interface are 
called Reusable Saved Models. 

The TensorFlow Hub team recommends you to implementing the Reusable 
Saved Model interface in all Saved Models that are meant to be reused in the 
above sense. Many utilities from the tensor flow_ hub library, notably hub. Keras _ 
layer, require Saved Models to implement it


## Architecture:

TensorFlow Serving is a flexible, high-performance serving system for 
machine learning models, designed for production environments. TensorFlow 
Serving makes it easy to deploy new algorithms and experiments, while keeping the 
same server architecture and APIs. TensorFlow Serving provides out of the box 
integration with TensorFlow models, but can be easily extended to serve other types 
of models.

#### Models: 

TensorFlow Serving represents a model as one or more servables. A 
machine-learned model may include one or more algorithms (including learned 
weights) and lookup or embedding tables.
You can represent a composite model as either of the following:
• multiple independent servables
• single composite servable

## Extensibility:

TensorFlow Serving provides several extension points where you can add 
new functionality.
TensorFlow Serving includes two policies that accommodate most known usecases. 
1) Availability Preserving Policy 
2) Resource Preserving Polic

#### Simple usage:

For simple usage of TensorFlow Serving where the serving availability of a 
model is important and the resource costs low, the Availability Preserving Policy will 
ensure that the new version is loaded and ready before unloading the old one.


#### Sophisticated usage:

For sophisticated usage of TensorFlow Serving, for example managing 
versions across multiple server instances, the Resource Preserving Policy requires 
the least resources (no extra buffer for loading new versions)


## Optimization Requirements:

#### Optimization:

The TensorFlow Model Optimization Toolkit is a suite of tools for optimizing 
ML models for deployment and execution. Among many uses, the toolkit supports 
techniques used to:
1) Reduce latency and inference cost for cloud and edge devices (e.g. mobile, 
IoT).

2) Deploy models to edge devices with restrictions on processing, memory, 
power-consumption, network usage, and model storage space.

#### Constant folding optimizer: 

Statically infers the value of tensors when possible by 
folding constant nodes in the graph and materializes the result using constants.

#### Arithmetic optimizer:

Simplifies arithmetic operations by eliminating common 
subexpressions and simplifying arithmetic statements.

#### Layout optimizer:

Optimizes tensor layouts to execute data format dependent 
operations such as convolutions more efficiently.

#### Remapper optimizer:

Remaps subgraphs onto more efficient implementations by 
replacing commonly occurring subgraphs with optimized fused monolithic kernels.

#### Memory optimizer:

Analyzes the graph to inspect the peak memory usage for each 
operation and inserts CPU-GPU memory copy operations for swapping GPU 
memory to CPU to reduce the peak memory usage.

#### Dependency optimizer:

Removes or rearranges control dependencies to shorten 
the critical path for a model step or enables other optimizations. Also removes nodes 
that are effectively no-ops such as Identit


## Security Requirements: 

#### Security: 

TensorFlow Security is determined by the computational graph, whether 
the user-provided checkpoint is safe or not. Generally, creating a computational 
graph with malicious inspections can trigger uncommon and insecure behavior. 

#### TensorFlow Models As Programs: 

TensorFlow programs are encoded as computation graphs. The model's 
parameters are often stored separately in checkpoints. 
At runtime, TensorFlow executes the computation graph using the parameters 
provided. Note that the behavior of the computation graph may change depending 
on the parameters provided. TensorFlow itself is not a sandbox. When executing 
the computation graph, TensorFlow may read and write files, send and receive data 
over the network, and even spawn additional processes. All these tasks are 
performed with the permission of the TensorFlow process. Allowing for this flexibility 
makes for a powerful machine learning platform, but it has security implications

#### Vulnerabilities in TensorFlow: 

TensorFlow is a large and complex system. It also depends on a large set of 
third party libraries. It is possible that TensorFlow or its dependencies may contain 
vulnerabilities that would allow triggering unexpected or dangerous behavior with 
specially crafted inputs.
Given TensorFlow's flexibility, it is possible to specify computation graphs 
which exhibit unexpected or unwanted behavior. The fact that TensorFlow models 
can perform arbitrary computations means that they may read and write files, 
communicate via the network, produce deadlocks and infinite loops, or run out of 
memory.


## Reliability Requirements: 

#### Scalability:

In scalable machine learning, the components of the system have their own 
work or task which helps the whole system to lead towards the solution of the 
problem rapidly. 
When the size of data becomes very large, the performance of machine learning 
models becomes a concern. In such situations, the machine learning models need to 
be scaled which not only helps in saving time and memory but also helps in 
improving the performance of the model. TensorFlow provides features to scale 
machine learning models easily and effectively.

## Fault Tolerance: 

#### Fault tolerance

refers to a mechanism of periodically saving the states of 
trackable objects, such as parameters and models. This enables you to recover 
them in the event of a program/machine failure during training. 
You will learn how to implement fault tolerance for training in Tensorflow 2 in two 
ways: 
1. If you use the Keras Model.fit API, you can pass the
tf.keras.callbacks.BackupAndRestore callback to it. 
2. If you use a custom training loop (with tf.GradientTape), you can arbitrarily 
save checkpoints using the tf.train.Checkpoint 
and tf.train.CheckpointManager APIs

## Open-source contribution requirements 

#### for developers: 

The TensorFlow ecosystem can only grow through the contributions of 
developers.

You can contribute code, make improvements to the TensorFlow API 
documentation, or add your Jupyter notebooks to the tensorflow/examples repo. This 
guide provides everything you need to get started. Our most common contributions 
include code, documentation, and community support. 
1. Write code. 
2. Improve tests.
3. Improve Documentation.
4. Answer questions on Stack Overflow.
5. Participate in the discussion on our mailing lists.
6. Contribute example notebooks.
7. Investigate bugs and issues on GitHub.
8. Review and comment on pull requests from other developers.
9. Report an issue.


##Documentation Requirements: 

#### INSTALLATION:

Here is the installation link of document of tensor flow:
https://www.tensorflow.org/api_docs

#### Tutorials:

Here is the link to official You-tube channel of tensor flow.
https://www.youtube.com/tensorflow

#### User Manual:

Here is the link of user manual of tensor flow.
https://www.tensorflow.org/guid
