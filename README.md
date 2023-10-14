# Recording-of-diffusion-model-learning
My study of diffusion began in July 2023 and went through a series of "spiraling" awareness processes. 
Diffusion is not my main research area before, so I can only say that it is still learning. And I try to follow some relevant works now,so I restart to record the learning progress.

The biggest impression of diffusion in the early learning process includes two points: 1. The gap between mathematical theory and programming implementation is very large. 2. The blogs that come out of each diffusion search are too varied and are about different papers, and the relationships between these papers are not clear.

## Table of Contents 
- [1. Main Article](#1-Main Article)


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
