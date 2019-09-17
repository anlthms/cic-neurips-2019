# Cellular Image Classification - NeurIPS 2019

This repository has code for training a classification model for the [Cellular Image Classification Challenge](https://www.kaggle.com/c/recursion-cellular-image-classification). It is adapted from [this notebook](https://www.kaggle.com/yhn112/resnet18-baseline-pytorch-ignite)


The main additions are:

* Make use of the negative control image. The image to be classified as well as its negative control are passed through ResNet. The features thus obtained are combined (by subtraction) and used for classification.
```
                          ________
                          |      |
              image ----> |resnet|  \
                          ________   \
                                      \
                                    ________           _______
                                    | minus |  ---->  | head  | ---->
                                    _________          _______
                                       /
                                      /
                                     /
                          ________
                          |      |
    negative control ---> |resnet|
                          ________
```
* Train the model on random 384x384 crops. Inference is done using a center crop of the same size.
