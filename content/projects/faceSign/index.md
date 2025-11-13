---
title: FaceSign
date: 2023-10-22
links:
  - type: site
    url: https://github.com/liuchenlili/FaceSign
tags:
  - face
  - cv
  - streamlit
---

# FaceSign - 智能人脸识别考勤系统

FaceSign是一个基于深度学习的人脸识别签到考勤系统，采用Streamlit框架开发，支持教师和学生两种角色。系统通过Dlib库实现人脸特征提取和识别，结合MySQL数据库实现考勤数据的存储和管理。


github地址：https://github.com/liuchenlili/FaceSign

**Bilibili演示视频demo:**:

{{< bilibili id="BV1zZtwzbE5P" >}}

## 📝 项目简介

FaceSign是一个基于深度学习的人脸识别签到考勤系统，采用Streamlit框架开发，支持教师和学生两种角色。系统通过Dlib库实现人脸特征提取和识别，结合MySQL数据库实现考勤数据的存储和管理。

## ✨ 主要功能

### 👨‍🏫 教师功能
- **人脸录入**: 为学生录入人脸信息，建立人脸特征数据库
- **课堂考勤**: 实时人脸识别签到，自动记录考勤数据
- **考勤统计**: 查看班级考勤情况，生成统计报表
- **数据管理**: 管理学生信息，修改学生资料
- **账户管理**: 修改个人密码和账户信息

### 👨‍🎓 学生功能
- **签到统计**: 查看个人考勤记录和统计数据
- **个人信息**: 管理个人资料和头像
- **密码修改**: 修改登录密码

## 🛠️ 技术栈

- **前端框架**: Streamlit
- **计算机视觉**: OpenCV + Dlib
- **数据库**: MySQL
- **图像处理**: PIL
- **数据分析**: Pandas + Plotly
- **UI组件**: streamlit-option-menu

## 📦 依赖包

```bash
streamlit
opencv-python
dlib
pymysql
pandas
plotly
pillow
streamlit-option-menu
numpy
```

## 🚀 安装和运行

### 1. 环境准备

```bash
# 安装依赖
pip install -r requirements.txt
```

### 2. 数据库配置

创建MySQL数据库并执行以下SQL语句：

```sql
-- 创建数据库
CREATE DATABASE face CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- 使用数据库
USE face;

-- 创建用户表
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('teacher', 'student') NOT NULL,
    name VARCHAR(100) NOT NULL,
    face_feature BLOB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- 创建考勤记录表
CREATE TABLE attendance (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    attendance_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('present', 'absent', 'late') DEFAULT 'present',
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);

-- 插入默认管理员账户
INSERT INTO users (username, password, role, name) VALUES 
('admin', 'admin123', 'teacher', '系统管理员');
```

### 3. 模型文件准备

下载Dlib预训练模型文件到 `data_dlib/` 目录：
- `dlib_face_recognition_resnet_model_v1.dat`
- `shape_predictor_68_face_landmarks.dat`

可从官方网站下载：http://dlib.net/files/

### 4. 运行应用

```bash
streamlit run app.py
```

## 📁 项目结构

```
FaceSign/
├── app.py                 # 主应用程序
├── dock_in.py            # 考勤签到模块
├── get_face.py           # 人脸录入模块
├── stu_statistics.py     # 学生统计模块
├── tea_statistics.py     # 教师统计模块
├── README.md             # 项目说明文档
├── requirements.txt      # 依赖包列表
├── data_dlib/           # Dlib模型文件目录
│   ├── dlib_face_recognition_resnet_model_v1.dat
│   └── shape_predictor_68_face_landmarks.dat
├── imgs/                # 用户头像存储目录
└── config/              # 配置文件目录(建议新增)
```

## 🔧 配置说明

### 数据库配置
在各个模块中修改数据库连接参数：
```python
DatabaseConnection('localhost', 3306, 'root', 'your_password', 'face')
```

建议将数据库配置抽取到独立的配置文件中。

## 📊 使用说明

### 首次使用流程

1. **管理员登录**: 使用默认账户 admin/admin123 登录
2. **学生注册**: 通过注册功能创建学生账户
3. **人脸录入**: 为每个学生录入人脸特征
4. **开始考勤**: 使用课堂考勤功能进行签到

### 考勤流程

1. 教师选择"课堂考勤"功能
2. 系统启动摄像头
3. 学生面向摄像头进行人脸识别
4. 系统自动识别并记录考勤信息

## 🔒 安全说明

- 密码采用明文存储，建议在生产环境中使用哈希加密
- 人脸特征数据已进行加密存储
- 建议定期备份数据库数据

## 🐛 故障排除

### 常见问题

1. **摄像头无法打开**
    - 检查摄像头权限
    - 确认摄像头未被其他程序占用

2. **人脸识别失败**
    - 确保光线充足
    - 检查Dlib模型文件是否正确加载

3. **数据库连接失败**
    - 检查MySQL服务是否启动
    - 验证数据库连接参数

## 🔄 更新日志

### v1.0.0 (当前版本)
- 基本的人脸识别考勤功能
- 用户管理系统
- 考勤统计功能
- Web界面交互

## 🎯 未来规划

- [ ] 增加批量导入学生功能
- [ ] 支持多课程管理
- [ ] 增加考勤报告导出功能
- [ ] 添加移动端支持
- [ ] 优化人脸识别算法
- [ ] 增加实时通知功能




## 📞 联系方式

如有问题或建议，请联系：
- 邮箱: 2464228500@qq.com


<!--more-->
