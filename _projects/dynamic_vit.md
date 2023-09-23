---
layout: page
title: Making Vision Transformer faster through layer skipping
description: A layer-skipping dynamic vision transformer (ViT) network that skips layers for each sample based on decisions given by a reinforcement learning agent
img: assets/img/scheme.png
importance: 1
category: work
---

**Abstract:** Recent deep learning breakthroughs in language and vision tasks can be mainly attributed to large-scale transformers. Unfortunately, the massive size and high compute requirement of these models have limited their use in resource-constrained environments. Dynamic neural networks present a unique opportunity to reduce the amount of compute requirement as these models enable dynamically adjusting the computational path given an input. We propose a layer-skipping dynamic vision transformer (ViT) network that skips layers for each sample based on decisions given by a reinforcement learning agent. Extensive experiments on CIFAR-10 and CIFAR-100 showed that this dynamic ViT model gains an average of 40% throughput increase in the inference phase when evaluated on different batch sizes ranging from 1 to 1024.

**Problem Statement**
Recent advancements in deep learning for language and vision tasks have largely been driven by large-scale transformers. However, their immense size and computational requirements limit their applicability in resource-constrained environments. To address this, we propose a novel approach called DynamicViT, which leverages dynamic neural networks to adaptively adjust computational paths for each input sample. By training an agent to make decisions on skipping layers, we aim to reduce computational overhead while maintaining high accuracy.

**Method**
DynamicViT introduces a reinforcement learning agent that determines whether a given input should pass through a transformer layer or skip it. This decision is based on the content of the input, enabling a more efficient computational path. The agent is trained using a policy gradient algorithm, learning to maximize accuracy while minimizing computational processing. The resulting model dynamically adjusts its processing based on input characteristics.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/rl-scheme.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/scheme.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
**Results**
Extensive experiments on CIFAR-10 and CIFAR-100 datasets demonstrated the effectiveness of DynamicViT. Compared to a standard ViT model, DynamicViT achieved an average throughput increase of 40% across a range of batch sizes (1 to 1024). This means that for applications like self-driving cars, DynamicViT can significantly improve speed and reduce deployment costs, leading to lower environmental impact.

**Conclusion**
DynamicViT presents a promising solution to the computational challenges faced by large-scale transformers in resource-constrained environments. By dynamically adjusting processing based on input characteristics, the model achieves substantial throughput gains without sacrificing accuracy. This has wide-ranging implications for real-time applications in vision tasks, making systems more efficient and environmentally friendly.



Full Report: ![PDF](https://drive.google.com/file/d/1HURVjernhAookwLChTRO8-ZiClAwgfEN/view)
Code: ![https://github.com/leobitz/DistillEmb](https://github.com/leobitz/DistillEmb)