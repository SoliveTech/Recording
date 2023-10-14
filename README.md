# Recording-of-diffusion-model-learning
My study of diffusion began in July 2023 and went through a series of "spiraling" awareness processes. 
Diffusion is not my main research area before, so I can only say that it is still learning. And I try to follow some relevant works now,so I restart to record the learning progress.

The biggest impression of diffusion in the early learning process includes two points: 1. The gap between mathematical theory and programming implementation is very large. 2. The blogs that come out of each diffusion search are too varied and are about different papers, and the relationships between these papers are not clear.

## Table of Contents 
- [1. Main Article]
- [2. Brief History]


## 1. Main Article

[1-1 Frame work]<br>  
【1*】Diffusion-Original（2015）：Deep Unsupervised Learning using Nonequilibrium Thermodynamics<br>  
【2】NCSN（2019-Yang Song）：Generative Modeling by Estimating Gradients of the Data Distribution<br>  
【3*】NCSN-improved（2020-Yang Song）：Improved Techniques for Training Score-Based Generative Models<br>  
【4】DDPM（2020-6-UCB）：Denoising Diffusion Probabilistic Models<br>  
【5】SDE-Framework（2020-10-Yang Song）：Score-Based Generative Modeling through Stochastic Differential Equations<br>  

[1-2 Improvement work]<br>  
【6】DDIM（2020-10-Jiaming Song）：Denoising Diffusion Implicit Models<br>  
【7】IDDPM（2021-2-OpenAI）：Improved Denoising Diffusion Probabilistic Models<br>  
【8*】Diffusion-Beat-GANs（2021-5-OpenAI）：Diffusion Models Beat GANs on Image Synthesis<br>  

[1-3 condition/guide relevant work]<br>  

From iterative denoising, explicit classifiers, to implicit classifiers (without classifier guidance). Implicit classifiers, without classifier guidance, are one of the direct foundations of typical works like GLIDE/Stable-Diffusion/Imagen, which also renders previous works based on explicit classifiers only of reference significance. The landmark achievement is the Stable Diffusion model in August 2022, with the core being latent diffusion (by then, Robin Rombach from CompVis had already joined Stability-AI). The discussion was very intense at the time because it was open-source.

从迭代去噪，显式分类器，到隐式分类器（无分类器引导）。无分类器引导是典型工作GLIDE/Stable-Diffusion/Imagen的直接奠基之一，也使得之前基于显式分类器的工作只剩下借鉴意义。标志性的成果是2022年8月份的Stable Diffusion模型，核心是latent diffusion（这时候CompVis的Robin Rombach已经加入了Stability-AI）。因为是开源的，所以当时讨论非常热烈。

## 2. Brief History
### 2-1 diffusion model
**扩散模型**（diffusion model）主要有两个过程组成，前向扩散过程，反向去噪过程，前向扩散过程主要是将一张图片变成随机噪音（标准高斯分布），而逆向去噪过程则是将一张随机噪音的图片还原为一张完整的图片。

**前向扩散**过程就是在原始图像上，随机添加高斯噪声。通过 T 步迭代，最终将原始图片的分布变成标准高斯分布。这个过程中没有需要学习的参数，高斯噪声的参数都是定义好的。

**逆向过程**就是还原的过程，也就是从高斯噪声中恢复原始分布的过程。

前向扩散可以理解成多步编码过程，得到“中间向量”  ；逆向扩散是一个多步解码的过程，目的是重新构建原始输入。

![image](https://github.com/SoliveTech/Recording/assets/56882057/e2002360-a778-4df9-acb0-362e1ae16e22)

所以关键在于如何构建逆向扩散，即如何通过求出  。由于每个时间步的图像大小都是一样的，所以可以采用U-net结构——先downsampling，再upsampling，使得输出与输入的尺寸一致。

逆向扩散不同时间步使用同一个 U-net 模型，参数共享，类似于RNN结构。所以还需要给模型提供一个具有时间信息的输入——time embedding，类似于Transformer 里的positional embedding.

![image](https://github.com/SoliveTech/Recording/assets/56882057/8ef1e574-a8e9-46f0-9b3c-90893eee3efa)

