---
title: TextClassification
date: 2023-10-24
links:
  - type: site
    url: https://github.com/liuchenlili/TextClassification
tags:
  - TextClassification
  - NLP
  - Markdown
---


# 中文文本分类系统

基于深度学习的中文文本分类系统，支持多种模型算法，包括 TextCNN、LSTM 和朴素贝叶斯分类器。

github地址：https://github.com/liuchenlili/TextClassification

**Bilibili演示视频demo:**:

{{< bilibili id="BV19s421P7go" >}}

## 📖 项目简介

本项目是一个基于深度学习的中文文本分类系统，支持多种模型算法，包括 TextCNN、LSTM 和朴素贝叶斯分类器。系统提供了完整的训练、评估和推理功能，并配备了基于 Streamlit 的 Web 界面，方便用户进行文本分类任务。

## 🚀 主要特性

- 📊 支持多种深度学习模型（TextCNN、LSTM、Naive Bayes）
- 🎯 基于 THUCNews 数据集的中文文本十分类任务
- 🖥️ 直观的 Web 界面，支持实时文本分类
- 📈 完整的训练日志和可视化功能
- 🔧 模块化设计，易于扩展和维护

## 🛠️ 环境要求

### Python 版本
- Python 3.8+

### 依赖库
```bash
pip install torch torchvision torchaudio
pip install streamlit
pip install scikit-learn
pip install pandas numpy
pip install tqdm
pip install matplotlib seaborn
```

### 快速安装
```bash
pip install -r requirements.txt
```

## 🎯 数据集说明

### THUCNews 中文新闻文本分类数据集

**分类类别**（共10类）：
- 📈 **财经** - 财经新闻
- 🏠 **房产** - 房地产相关
- 📊 **股票** - 股票市场
- 🎓 **教育** - 教育资讯
- 💻 **科技** - 科技新闻
- 👥 **社会** - 社会新闻
- 🏛️ **时政** - 时事政治
- ⚽ **体育** - 体育新闻
- 🎮 **游戏** - 游戏资讯
- 🎬 **娱乐** - 娱乐新闻

### 数据集划分

| 数据集 | 数据量 | 用途 |
|--------|--------|------|
| 训练集 | 180,000条 | 模型训练 |
| 验证集 | 10,000条 | 超参数调优 |
| 测试集 | 10,000条 | 模型评估 |

## 🚀 快速开始

### 1. 启动 Web 界面
```bash
streamlit run app.py
```
访问 `http://localhost:8501` 即可使用 Web 界面进行文本分类。

### 2. 模型训练
```bash
# 训练 TextCNN 模型
python run.py --model TextCNN

# 训练 LSTM 模型  
python run.py --model LSTM

# 训练朴素贝叶斯模型
python run.py --model bayes
```

### 3. 模型评估
```bash
# 评估指定模型
python train_eval.py --model TextCNN
```

## 📁 项目结构

```
TextClassification/
├── 📁 models/              # 模型定义
│   ├── TextCNN.py         # TextCNN 模型
│   ├── LSTM.py            # LSTM 模型
│   └── bayes.py           # 朴素贝叶斯模型
├── 📁 THUCNews/           # 数据集和模型文件
│   ├── data/              # 数据文件
│   ├── log/               # 训练日志
│   └── saved_dict/        # 保存的模型
├── 📄 app.py              # Streamlit Web 应用
├── 📄 run.py              # 训练脚本
├── 📄 train_eval.py       # 评估脚本
├── 📄 utils.py            # 工具函数
└── 📄 README.md           # 项目说明
```

## 🎨 模型介绍

### TextCNN
- 基于卷积神经网络的文本分类模型
- 使用多个不同尺寸的卷积核捕获n-gram特征
- 适合短文本分类任务

### LSTM
- 长短期记忆网络，能够捕获文本的序列信息
- 处理长文本效果较好
- 能够学习文本的上下文依赖关系

### Naive Bayes
- 经典的概率分类算法
- 训练速度快，对小数据集友好
- 作为基线模型进行对比

## 📊 性能表现

| 模型 | 准确率 | 训练时间 | 推理速度 |
|------|--------|----------|----------|
| TextCNN | 91.2% | 快 | 很快 |
| LSTM | 89.8% | 中等 | 快 |
| Naive Bayes | 85.6% | 很快 | 很快 |

## 🔧 自定义配置

可以通过修改各模型配置文件来调整超参数：
- 学习率、批次大小
- 网络结构参数
- 训练轮数等


---

⭐ 如果这个项目对你有帮助，请给个 Star！

<!--more-->
