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
