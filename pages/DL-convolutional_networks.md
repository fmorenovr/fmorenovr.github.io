---
layout: post
title: "Convolutional Neural Networks"
subtitle: "Convolutional Neural Networks algorithms"
description: "CNN Algorithms"
date:   2019-05-20 12:15:12 -0500
permalink: /dl/convolutional_networks
---

# Convolutional Neural Networks

Is a class of [ANN](/ml/neural_networks) where connections between nodes form a directed graph along a temporal sequence.  
RNNs can use their internal state (memory) to process sequences of inputs.


## Definitions

* Zero-Padding: Sometimes, it is convenient to pad the input matrix with zeros around the border, so that we can apply the filter to bordering elements of our input image matrix. A nice feature of zero padding is that it allows us to control the size of the feature maps. Adding zero-padding is also called `wide convolution`, and not using zero-padding would be a `narrow convolution`.

* Stride: Stride is the number of pixels by which we slide our filter matrix over the input matrix. When the stride is 1 then we move the filters one pixel at a time. When the stride is 2, then the filters jump 2 pixels at a time as we slide them around. Having a larger stride will produce smaller feature maps.

## Applications


## References

* [Understanding CNN](http://colah.github.io/posts/2014-07-Understanding-Convolutions/).

* https://grzegorzgwardys.wordpress.com/2016/04/22/8/

* https://www.jefkine.com/general/2016/09/05/backpropagation-in-convolutional-neural-networks/

* https://medium.com/@2017csm1006/forward-and-backpropagation-in-convolutional-neural-network-4dfa96d7b37e

* https://becominghuman.ai/back-propagation-in-convolutional-neural-networks-intuition-and-code-714ef1c38199

* https://adventuresinmachinelearning.com/convolutional-neural-networks-tutorial-tensorflow/

* [Derivation intuition](https://pdfs.semanticscholar.org/5d79/11c93ddcb34cac088d99bd0cae9124e5dcd1.pdf).

* [Deconvolution](https://distill.pub/2016/deconv-checkerboard/).

* [An Intuitive Explanation of Convolutional Neural Networks](https://ujjwalkarn.me/2016/08/11/intuitive-explanation-convnets/).
