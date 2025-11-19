---
title: 👩🏼‍🏫 A Survey on Knowledge Graphs 
summary:  Representation, Acquisition and Applications 笔记
date: 2025-09-11
math: true
authors:
  - admin
tags:
  - KGE
  - RotaE
  - Markdown
image:
  caption: 'Embed rich media such as videos and LaTeX math'
---

# A Survey on Knowledge Graphs: Representation, Acquisition and Applications 笔记

# 知识图谱嵌入  

Knowledge Representation Learning 知识表示学习又叫KGE  
pre  

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702798010956-144f8dd1-2dfe-47eb-aa62-29440551c65b.png)

KGL的流程  
1表示关系和实体的表示空间；  
2 衡量事实三元组合理性的评分函数；3用于表示和学习关系交互的编码模型；  
4要纳入嵌入方法的辅助信息。  
表示学习包括逐点空间、流形、复向量空间、高斯分布和离散空间。评分指标通常分为基于距离的评分函数和基于相似性匹配的评分函数。目前的研究重点是编码模型，包括线性/双线性模型、分解和神经网络。辅助信息考虑文本、视觉和类型信息。  
## 

![x3.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702818857336-758a5eac-b06a-4a3a-933c-1fc709a01f27.png)

表示空间  

表示学习的关键问题是学习实体和关系的低维分布式嵌入。目前文献主要使用实值逐点空间（图2（a）），包括向量、矩阵和张量空间，而其他类型的空间如复向量空间（图2（b））、高斯空间（图2（b）） . 2(c)) 和 manifold (图 2(d)) 也被使用。嵌入空间应遵循三个条件，即可微分性、计算可能性和评分函数的可定义性\[15\]。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702472558658-fbe35f5e-88cc-428c-ac68-1f553a243f9b.png)

### Point-Wise Space  

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702819424203-652ad868-2efe-48f5-b1e3-2ffe58c747cf.png)

许多其他翻译模型（例如 TransH \[20\]）也使用类似的表示空间，而语义匹配模型使用普通向量空间（例如 HolE \[21\]）和关系投影矩阵（例如 ANALOGY \[22\]  
### Complex Vector Space  

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702820687093-079c1100-9b15-4f70-adf7-76f5e29ba195.png)

### Gaussian Distribution  

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702820887927-1ccc27d7-aa99-48f5-8f3e-7c11daa81d34.png)

### Manifold and Group  

(见论文)  
## 评分函数  

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1702821134132-2e1f08de-2630-43e1-8ce9-4a343afd3252.png)

## Encoding Models  

### Linear/Bilinear Models  

（）  
### Neural Networks  

（）  
### Convolutional Neural Networks  

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1703426019717-7f48de96-ca47-43c7-a90e-7344f03e7a5b.png)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1703426028343-90b0ebab-87bb-4210-9935-bb00f9cfbe39.png)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/40806594/1703426037884-b44c9983-0f4f-4b78-9232-51333b793908.png)