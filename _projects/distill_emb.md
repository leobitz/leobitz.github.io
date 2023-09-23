---
layout: page
title: DistillEmb: Distilling Word Embeddings via Contrastive Learning
description: A method to distill or compress word embeddings into a four-layer CNN.
img: assets/img/distill-emb.png
importance: 1
category: work
---

**Abstract**
Word embeddings have played a pivotal role in early neural network-based NLP research. Their efficacy in small data environments remains relevant, especially in low-resource settings. However, they face critical limitations, including linearly escalating memory requirements and challenges with out-of-vocabulary tokens. This work introduces a novel distillation technique utilizing a CNN network and contrastive learning to address these issues. This method enables the regression of embeddings based on token characters, subsequently replacing traditional word embeddings as a pretrained layer. Primarily benefiting low-resource languages, we demonstrate its effectiveness on two morphology-rich Semitic languages and in a multilingual Named Entity Recognition (NER) task encompassing 10 African languages. Besides its data and memory efficiency, the model significantly enhances performance across various benchmarks while retaining the capability of transferring word representations.

**Motivation**
In the context of language processing, many languages, particularly African ones, face resource scarcity, whether in terms of limited datasets or computational resources. Word embeddings remain a relevant solution to these challenges. However, conventional word embeddings exhibit several limitations, notably linear memory requirements, out-of-vocabulary issues, and a lack of transferability. These challenges are even more pronounced in morphologically complex languages.

**Method**
This approach involves compressing the entire embedding list into a fixed neural network, which consumes minimal memory. Leveraging the approximating power of neural networks, the CNN network can generate embeddings for previously unseen tokens. Additionally, the network can be applied to similar languages for out-of-the-box cross-lingual transferability. The distillation process employs contrastive learning as a loss function. The anchor represents the output of the CNN, while the positive embedding corresponds to our target token. The negative embedding is derived by selecting the most similar embedding to the positive one from a randomly sampled 32-length sequence. The CNN network processes the characters, learning word features from the resulting embeddings.

**Results**
Extensive testing was conducted across a range of tasks and languages, including Amharic, Tigrigna, 10 African languages, and a cross-lingual evaluation. The proposed method achieved a notable 7% increase in accuracy compared to the previous approach. Impressively, it surpassed a 97-million-parameter model while utilizing less than 3 million parameters.

This work represents a significant advancement in overcoming the challenges posed by low-resource languages in NLP. By distilling word embeddings through contrastive learning, we have demonstrated substantial gains in both efficiency and performance. This repository contains the codebase and resources needed to implement this technique in similar contexts.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/distill-emb.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Full Report: ![PDF](https://leobitz.github.io/assets/pdf/distill-emb.pdf)
Code: ![https://github.com/leobitz/DistillEmb](https://github.com/leobitz/DistillEmb)