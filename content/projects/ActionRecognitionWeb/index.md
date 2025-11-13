---
title: ActionRecognitionWeb
date: 2023-10-26
links:
  - type: site
    url: https://github.com/liuchenlili/ActionRecognitionWeb
tags:
  - ActionRecognitionWeb
  - cv
  - AI
---
github地址：https://github.com/liuchenlili/ActionRecognitionWeb

**Bilibili演示视频demo:**:

{{< bilibili id="BV17V4y1Y7XQ" >}}

# 动作识别Web应用 (ActionRecognitionWeb)

基于Django和R3D模型的视频动作识别Web应用，支持实时监控、视频分析和异常行为检测。

## 项目简介

本项目是一个完整的Web应用系统，集成了深度学习模型（R3D）进行视频动作识别，主要功能包括：

- 🎥 视频上传与分析
- 📹 实时监控设备管理
- 🚨 异常行为检测与报警
- 📊 数据可视化展示
- 🔐 用户权限管理

### 核心技术栈

- **后端框架**: Django 3.2
- **深度学习**: PyTorch + R3D模型
- **数据库**: MySQL
- **前端**: Bootstrap + jQuery
- **UI框架**: SimpleUI

## 下载模型权重
下载模型权重放到R3D/weight文件夹里

谷歌网盘地址：https://drive.google.com/file/d/132DU_Ps1jh5zNLjKoiSgngCqv9AUHyUo/view?usp=drive_link

百度网盘地址： 链接: https://pan.baidu.com/s/1OPmMN0vNro41ZYff0vczag?pwd=5t6p 提取码: 5t6p

## 环境要求

### 系统要求
- Python 3.8.10
- CUDA ≥ 10.2 (GPU版本)
- MySQL 5.7+

### 硬件要求
- GPU: NVIDIA显卡（推荐GTX 1060以上）
- 内存: 8GB以上
- 存储: 10GB以上可用空间

## 快速开始

### 一键安装

```bash
# 1. 创建并激活虚拟环境
conda create -n pytorch python=3.8.10
conda activate pytorch

# 2. 安装PyTorch (选择适合你CUDA版本的命令)
# CUDA 11.1:
pip install torch==1.10.1+cu111 torchvision==0.11.2+cu111 torchaudio==0.10.1 -f https://download.pytorch.org/whl/cu111/torch_stable.html

# 3. 安装项目依赖
pip install -r requirements.txt

# 4. 配置数据库后运行
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

## 安装指南

### 1. 安装Anaconda

参考教程：[Anaconda安装指南](https://blog.csdn.net/m0_61607990/article/details/129531686)

### 2. 创建Python虚拟环境

```bash
conda create -n pytorch python=3.8.10
conda activate pytorch
```

### 3. 安装PyTorch

**注意**: 需要根据你的CUDA版本选择对应的PyTorch版本

#### CUDA 11.1
```bash
pip install torch==1.10.1+cu111 torchvision==0.11.2+cu111 torchaudio==0.10.1 -f https://download.pytorch.org/whl/cu111/torch_stable.html
```

#### CUDA 10.2
```bash
pip install torch==1.10.1+cu102 torchvision==0.11.2+cu102 torchaudio==0.10.1 -f https://download.pytorch.org/whl/cu102/torch_stable.html
```

#### CUDA 11.6 (高版本)
```bash
pip --default-timeout=300 install torch==1.13.1+cu116 torchvision==0.14.1+cu116 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu116
```

#### CPU版本
```bash
pip install torch==1.10.1+cpu torchvision==0.11.2+cpu torchaudio==0.10.1 -f https://download.pytorch.org/whl/cpu/torch_stable.html
```

**CUDA安装参考**: [CUDA安装教程](https://blog.csdn.net/qq_45956730/article/details/126600028)

### 4. 安装依赖包

#### 使用requirements.txt

```bash

# 或者使用清华镜像源加速
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```



**注意**: 如果安装过程中提示缺少某些包，请根据错误信息进行补充安装。

## 数据库配置

### 1. 创建MySQL数据库

```sql
SHOW DATABASES;
CREATE DATABASE action DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
```

### 2. 修改数据库配置

编辑 `ActionRecognitionWeb/settings.py` 文件中的数据库配置：

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'action',           # 数据库名
        'USER': 'your_username',    # 用户名
        'PASSWORD': 'your_password', # 密码
        'HOST': '127.0.0.1',        # 主机地址
        'PORT': '3306',             # 端口号
    }
}
```

### 3. 数据库迁移

```bash
python manage.py makemigrations
python manage.py migrate
```

## 运行应用

### 1. 创建管理员账号

```bash
python manage.py createsuperuser
```

### 2. 启动服务

```bash
python manage.py runserver
```

访问地址：http://127.0.0.1:8000

## 项目结构

```
ActionRecognitionWeb/
├── ActionRecognitionWeb/    # Django项目配置
│   ├── settings.py         # 项目设置
│   ├── urls.py            # URL路由
│   └── wsgi.py            # WSGI配置
├── devices/               # 设备管理应用
│   ├── models.py          # 数据模型
│   ├── views.py           # 视图函数
│   ├── EventViews.py      # 事件视图
│   ├── MonitorViews.py    # 监控视图
│   └── VideoViews.py      # 视频视图
├── R3D/                   # R3D模型模块
│   ├── model.py           # 模型定义
│   ├── inference.py       # 推理脚本
│   └── weight/            # 模型权重
├── static/                # 静态文件
├── templates/             # 模板文件
├── media/                 # 媒体文件
└── manage.py              # Django管理脚本
```

## 功能模块

### 设备管理
- 设备信息录入与编辑
- 设备状态监控
- 设备分组管理

### 视频分析
- 视频文件上传
- 动作识别分析
- 结果可视化展示

### 异常检测
- 实时异常行为检测
- 异常事件记录
- 报警信息管理

### 监控中心
- 实时视频流监控
- 多路视频同时监控
- 历史记录查询

## 模型信息

### R3D模型
- **架构**: ResNet3D-18
- **预训练**: 基于大规模视频数据集
- **支持动作类别**: 101种（UCF-101数据集）
- **模型文件**: `R3D/weight/R3D-ucf101_epoch-35.pth.tar`

### 检测类别
- 正常行为
- 打架
- 爆炸
- 车祸
- 抢劫

## 常见问题

### Q1: CUDA版本不匹配
**A**: 请根据你的GPU和CUDA版本选择对应的PyTorch版本，参考上述安装指令。

### Q2: 数据库连接错误
**A**: 检查MySQL服务是否启动，数据库配置是否正确。

### Q3: 模型加载失败
**A**: 确保模型权重文件存在于 `R3D/weight/` 目录下。

### Q4: 依赖包安装失败
**A**: 尝试使用国内镜像源，或者逐个安装依赖包。

## 开发指南

### 添加新的动作类别
1. 修改 `devices/models.py` 中的 `work_choices`
2. 更新模型标签文件 `R3D/weight/ucf_labels.txt`
3. 重新训练或调整模型输出层

### 自定义UI界面
- 修改 `templates/` 目录下的HTML模板
- 调整 `static/css/` 中的样式文件
- 使用SimpleUI配置自定义管理界面


## 联系方式

如有问题或建议，请联系项目维护者。

邮箱:2464228500@qq.com

---

**注意**: 首次运行前请确保已完成所有环境配置和数据库设置。
<!--more-->
