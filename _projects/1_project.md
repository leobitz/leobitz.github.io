---
layout: page
title: Boosting image retrieval with accurately labeled small data
description: The project investigates how multi-labeling images with detailed information would boost representation in an image retrieval task, thereby lowering compute need significantly.
img: assets/img/proj-boosting.png.jpg
importance: 1
category: work
---

**Abstract:** Image retrieval is an application of computer vision that, given an image, a system returns a set of images with similar content. Through the advancement of deep learning in recent years, image retrieval has gotten a significant boost in performance. However, such success is apparent through training deep models using massive amounts of data, incurring significant costs on compute and labeling. Several works investigated if feature vectors extracted from deep models can be used for image retrieval tasks, while others fine-tuned the deep models for better performance. In this work, we examine if detailed annotation of small sets of images can be used to induce more semantic information into the feature vectors through a simple shallow network with just 3k training data. We show that this simple technique can improve the richness of feature vectors extracted both from shallow models such as PCA and deep models such as ResNet and Vision Transformer. 

Typically, the representation of an image might be extracted from a deep learning model such as ResNet-18, ResNet-50, or ViT-B/16. This representation's quality mostly depends on the model size and the data it was trained on. Such representation embedding is extracted from the last layer (input to the classifier) of an image and using KNN or other techniques can be used to search for images that are similar to the current one.

*The question is, can we improve this representation so that our search algorithm becomes more accurate?*

Each image will have multiple labels. For example, in an e-commerce application, a shirt might have attributes such as color, shape (V-shape, O-shape), size (L, M, X, XL), season (winter, summer), and more. These detailed labels can be used to boost the representation embedding of that image. 

**Method:** Have a simple shallow network that takes the embedding of an image, and trains it so that it predicts each attribute in a multi-task fashion. Typically, in our model case, the network is a one-hidden layer feed-forward network. In this task, we used detailed labeling of 3k images. In the inference phase, while searching for similar images, instead of using the original embedding of an image, take the representation of the first layer of the shallow network.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj-boosting.png.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

**Result:** We tested the technique on various models starting from PCA, ResNet-18, ResNet-34, ResNet-50, ResNet-101, and ViT-B/16. First, we tested the performance of the raw embeddings from these models. Then we applied the shallow network on the embeddings and evaluated them. The ground truth is the similarity based on the labels provided with the dataset. Using that as a reference, we computed the mean average precision (mAP) of the raw and the boosted embeddings. The following table shows the two evaluations.

| Model | Raw | Ours |
| ------ | ---| -----|
|PCA | 5.99 | 6.09 | 
|Resnet18 | 10.34 | 13.05 | 
|Resnet34 | 9.9 | 12.04 | 
|Resnet50 | 10.04 | 13.26 | 
|Resnet101 | 11.05 | 14.9 | 
|ViT-B/16 | 12.08 | 16.24 | 

**Takeaways:**
- Have detailed labels for some images and even a small model with a shallow network performs much better than a larger one. 

- The deployment cost will be very small

- Example: As ResNet-18 is much cheaper than the ViT-B/16 model, instead of having the cost of running ViT-B/16, investing in detailed labeling of small data and fine-tuning ResNet-18 is much better in the long run. 

The following sample shows the performance of an embedding. The task is extracting the top 10 images similar to the first image. The vanilla pre-trained ViT model got the 9th image only. Our method only missed two. 

![shallow model](https://github.com/leobitz/boosting_image_retrieval/blob/main/sample.png?raw=true)
