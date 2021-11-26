---
layout: post
comments: true
title: "How to Train Really Large Models on Many GPUs?"
date: 2021-09-24 12:00:00
tags: architecture transformer
---


> [PLACE-HOLDER POST, COPYRIGHT LILIAN WENG] How to train large and deep neural networks is challenging, as it demands a large amount of GPU memory and a long horizon of training time. This post reviews several popular training parallelism paradigms, as well as a variety of model architecture and memory saving designs to make it possible to train very large neural networks across a large number of GPUs.


<!--more-->

[PLACE-HOLDER POST, COPYRIGHT LILIAN WENG] In recent years, we are seeing better results on many NLP benchmark tasks with larger pre-trained [language models]({{ site.baseurl }}{% post_url 2021-09-25-train-large-neural-networks %}). How to train large and deep neural networks is challenging, as it demands a large amount of GPU memory and a long horizon of training time. 

However an individual GPU worker has limited memory and the sizes of many large models have grown beyond a single GPU. There are several parallelism paradigms to enable model training across multiple GPUs, as well as a variety of model architecture and memory saving designs to help make it possible to train *very large* neural networks.


{: class="table-of-content"}
* TOC
{:toc}


## Training Parallelism

The main bottleneck for training very large neural network models is the intense demand for a large amount of GPU memory, way above what can be hosted on an individual GPU machine. Besides the model weights (e.g. tens of billions of floating point numbers), it is usually even more expensive to store intermediate computation outputs such as gradients and optimizer states (e.g. momentums & variations in Adam). Additionally training a large model often pairs with a large training corpus and thus a single process may just take forever.

As a result, parallelism is necessary. Parallelism can happen at different dimensions, including data, model architecture, and tensor operation.


---
Cited as:
```
@article{weng2021large,
  title   = "How to Train Really Large Models on Many GPUs?",
  author  = "Weng, Lilian",
  journal = "lilianweng.github.io/lil-log",
  year    = "2021",
  url     = "https://lilianweng.github.io/lil-log/2021/09/24/train-large-neural-networks.html"
}
```


## References

[1] Li et al. [“PyTorch Distributed: Experiences on Accelerating Data Parallel Training”](https://arxiv.org/abs/2006.15704) VLDB 2020.

[2] Cui et al. [“GeePS: Scalable deep learning on distributed GPUs with a GPU-specialized parameter server”](https://www.pdl.cmu.edu/PDL-FTP/CloudComputing/GeePS-cui-eurosys16.pdf) EuroSys 2016 

[3] Shoeybi et al. [“Megatron-LM: Training Multi-Billion Parameter Language Models Using Model Parallelism.”](https://arxiv.org/abs/1909.08053) arXiv preprint arXiv:1909.08053 (2019).

[4] Narayanan et al. [“Efficient Large-Scale Language Model Training on GPU Clusters Using Megatron-LM.”](https://arxiv.org/abs/2104.04473) arXiv preprint arXiv:2104.04473 (2021).

[5] Huang et al. [“GPipe: Efficient Training of Giant Neural Networks using Pipeline Parallelism.”](https://arxiv.org/abs/1811.06965) arXiv preprint arXiv:1811.06965 (2018).

[6] Narayanan et al. ["PipeDream: Generalized Pipeline Parallelism for DNN Training."](https://cs.stanford.edu/~matei/papers/2019/sosp_pipedream.pdf) SOSP 2019.

[7] Narayanan et al.  [“Memory-Efficient Pipeline-Parallel DNN Training.”](https://arxiv.org/abs/2006.09503) ICML 2021.

[8] Shazeer et al. [“The Sparsely-Gated Mixture-of-Experts Layer Noam.”](https://arxiv.org/abs/1701.06538) arXiv preprint arXiv:1701.06538 (2017).

[9] Lepikhin et al. [“GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding.”](https://arxiv.org/abs/2006.16668) arXiv preprint arXiv:2006.16668 (2020).

[10] Fedus et al. [“Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity.”](https://arxiv.org/abs/2101.03961) arXiv preprint arXiv:2101.03961 (2021).

[11] Narang & Micikevicius, et al.  [“Mixed precision training.”](https://arxiv.org/abs/1710.03740) ICLR 2018.

[12] Chen et al. 2016 [“Training Deep Nets with Sublinear Memory Cost.”](https://arxiv.org/abs/1604.06174) arXiv preprint arXiv:1604.06174 (2016).

[13] Jain et al. [“Gist: Efficient data encoding for deep neural network training.”](https://www.microsoft.com/en-us/research/uploads/prod/2018/04/fiddle-gist-isca18.pdf) ISCA 2018.

[14] Shazeer & Stern. [“Adafactor: Adaptive learning rates with sublinear memory cost.”](https://arxiv.org/abs/1804.04235) arXiv preprint arXiv:1804.04235 (2018).

[15] Anil et al. [“Memory-Efficient Adaptive Optimization.”](https://arxiv.org/abs/1901.11150) arXiv preprint arXiv:1901.11150 (2019).

[16] Rajbhandari et al. [“ZeRO: Memory Optimization Towards Training A Trillion Parameter Models Samyam.”](https://arxiv.org/abs/1910.02054) arXiv preprint arXiv:1910.02054 (2019).











