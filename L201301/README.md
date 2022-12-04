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
