---
layout: page
title: DistillEmb: Distilling Word Embeddings via Contrastive Learning
description: A method to distill or compress word embeddings into a four-layer CNN.
img: assets/img/distill-emb.png
importance: 1
category: work
---

**Abstract:** Word embeddings powered the early days of neural network-based NLP research. Their effectiveness in small data regimes makes them still relevant in low-resource environments. However, they are limited in two critical ways: linearly increasing memory requirements and out-of-vocabulary token handling. In this work, we present a distillation technique of word embeddings into a CNN network using contrastive learning. This method allows embeddings to be regressed given the characters of a token. It is then used as a pretrained layer, replacing word embeddings. Low-resource languages are the primary beneficiary of this method and hence, we show its effectiveness on two morphology-rich Semitic languages, and in a multilingual NER task comprised of 10 African languages. Apart from being data and memory efficient, the model significantly increases performance across several benchmarks and is capable of transferring word representations.

Most languages, especially African ones are under-resourced - either low dataset or low compute. Hence word embeddings are still relevant. However, word embeddings have many limitations:

Linear memory requirement with respect to the number of tokens
Out-of-vocabulary issues
Hardly transferrable.
These problems become even more challenging in morphologically complex languages

**Method:** Compressing the entire embedding list into a fixed neural network takes little memory. Furthermore, as neural networks are good approximators, the CNN network can generate embeddings for unseen tokens. Finally, we can use the network with a similar language and benefit from the out-of-the-box cross-lingual transferability. Use contrastive learning as a distillation loss. The anchor is what the CNN generates. The positive embedding is our target token. The negative one was extracted by picking the most similar embedding to the positive embedding out of a randomly sliced 32-length sequence. The CNN network is fed the characters and from the embeddings of these characters, CNN learns word features.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/distill-emb.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

**Result:** We tested the method on a variety of tasks and languages. Amharic, Tigrigna, 10 African languages and a cross-linguality test were made. Overall, it achieved a 7% accuracy over the previous method and beat a 97M parameter model despite being less than 3M. 

Full Report: ![PDF](https://leobitz.github.io/assets/pdf/distill-emb.pdf)
Code: ![https://github.com/leobitz/DistillEmb](https://github.com/leobitz/DistillEmb)