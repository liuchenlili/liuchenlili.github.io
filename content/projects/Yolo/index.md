---
title: Yolo-AI
date: 2025-08-22
links:
  - type: site
    url: https://github.com/liuchenlili/yoloaiv3
tags:
  - Yolo
  - Ai
  - CV

---
# YOLO目标检测系统

基于yolo的智能目标检测系统，支持图片、视频和实时摄像头检测。

github地址：https://github.com/liuchenlili/yoloaiv3

**Bilibili演示视频demo:**:

{{< bilibili id="BV1u4t8zsEz2" >}}


## 项目概述

这是一个完整的目标检测解决方案，包含以下组件：

- **AI检测服务** (Python Flask + YOLOv8)
- **后端API服务** (Java Spring Boot + MySQL)
- **前端界面** (Vue3 + TypeScript + Element Plus)
- **数据库** (MySQL + Redis)

## 技术栈

### AI检测服务
- Flask 2.3.3
- YOLOv8 (Ultralytics)
- OpenCV
- WebSocket (Flask-SocketIO)
- Celery (异步任务处理)
- Redis (缓存和任务队列)

### 后端服务
- Spring Boot 3.2.0
- Spring Security + JWT
- Spring Data JPA
- MySQL 8.0
- Redis
- Swagger/OpenAPI

### 前端界面
- Vue 3.3.8
- TypeScript
- Element Plus 2.4.2
- Vue Router 4
- Pinia (状态管理)
- ECharts (数据可视化)
- Axios (HTTP客户端)

## 功能特性

### 🎯 检测功能
- **图片检测**: 支持多种图片格式，批量检测
- **视频检测**: 逐帧分析，生成结果视频
- **实时检测**: 摄像头实时画面检测

### 🤖 模型管理
- **模型上传**: 支持上传自定义训练的.pt模型文件
- **模型列表**: 卡片式展示所有可用模型，显示名称和大小
- **模型切换**: 一键激活不同的模型进行检测
- **模型详情**: 查看模型架构、类别数量、参数等详细信息

### 🎓 模型训练
- **自定义训练**: 使用自己的数据集训练YOLO模型
- **训练参数配置**:
- **实时监控**: WebSocket实时显示训练进度和指标
- **训练日志**: 详细的训练过程日志记录
- **指标可视化**: 实时图表显示损失、精度、召回率等

### 🔒 用户管理
- 用户注册/登录/权限管理
- JWT认证和刷新机制
- 角色分离 (管理员/普通用户)

### 📊 数据分析
- 检测结果统计和可视化
- 实时仪表板
- 历史记录查询和筛选

### ⚙️ 系统管理
- 多模型支持 (YOLOv8n/s/m/l/x) 支持自定义训练模型和架构
- 文件存储和清理
- 系统日志和监控

## 快速开始

### 环境要求

- Python 3.8+
- Java 17+
- Node.js 16+
- MySQL 8.0

### 1. 数据库设置

```bash
# 创建数据库
mysql -u root -p
CREATE DATABASE yolo_detection_system;

# 导入数据库结构
mysql -u root -p yolo_detection_system < database/schema.sql
```

### 2. AI检测服务

```bash
cd ai-service

# 安装依赖
pip install -r requirements.txt

# 启动服务
python app.py
```

### 3. 后端服务

```bash
cd backend-service

# 修改数据库配置
# 编辑 src/main/resources/application.yml

# 构建和运行
mvn spring-boot:run
```

### 4. 前端界面

```bash
cd frontend

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```



## 服务端口

- **前端**: http://localhost:3000
- **后端API**: http://localhost:8080
- **AI服务**: http://localhost:5000
- **Swagger文档**: http://localhost:8080/swagger-ui.html

## 使用说明

### 1. 系统登录
或注册新用户账号

### 2. 图片检测
1. 进入"图片检测"页面
2. 拖拽或点击上传图片
3. 调整检测参数
4. 查看检测结果

### 3. 视频检测
1. 进入"视频检测"页面
2. 上传视频文件
3. 等待处理完成
4. 下载结果视频

### 4. 实时检测
1. 进入"摄像头检测"页面
2. 允许摄像头权限
3. 开始实时检测
4. 查看检测框和结果

### 5. 模型管理
1. 进入"模型管理"页面
2. 查看当前所有可用模型
3. 上传新模型:
4. **切换模型**:
    - 点击模型卡片上的"激活"按钮
    - 系统会加载新模型用于后续检测
5. 管理模型:


### 6. 模型训练
1. 进入"模型训练"页面
2. **准备数据集**:
    - 确保数据集在`ai-service/datasets/`目录下
    - 数据集应包含`data.yaml`配置文件
3. **配置训练参数**:
    - 选择基础模型（yolov8n.pt、yolov8s.pt等）
    - 配置图像尺寸（320/416/512/640/832）
    - 调整批量大小和学习率
4. **开始训练**:
    - 点击"开始训练"按钮
    - 实时查看训练进度和指标
    - 监控损失值、精度、召回率等
5. **训练完成**:
    - 最佳模型自动保存到`runs/train/`目录
    - 可将训练好的模型移动到`models/`目录使用

## API文档

访问 http://localhost:8080/swagger-ui.html 查看完整的API文档。

### 主要接口

#### 认证接口
- `POST /api/auth/login` - 用户登录
- `POST /api/auth/register` - 用户注册
- `POST /api/auth/refresh` - 刷新令牌

#### 检测接口
- `POST /api/detect/image` - 图片检测
- `POST /api/detect/video` - 视频检测
- `GET /api/tasks/{taskId}/status` - 查询任务状态

#### 模型管理接口
- `GET /api/models/management` - 获取模型管理列表
- `POST /api/models/upload` - 上传模型文件
- `PUT /api/models/{id}/rename` - 重命名模型
- `DELETE /api/models/{id}/delete` - 删除模型
- `POST /api/models/{id}/activate` - 激活模型
- `GET /api/models/{id}/info` - 获取模型详细信息
- `GET /api/models` - 获取可用模型列表

#### 模型训练接口
- `POST /api/training/start` - 开始训练
- `GET /api/training/status` - 获取训练状态
- `POST /api/training/stop` - 停止训练
- `GET /api/training/models` - 获取可用预训练模型

#### 用户管理
- `GET /api/users` - 获取用户列表
- `PUT /api/users/{id}` - 更新用户信息
- `DELETE /api/users/{id}` - 删除用户

## 部署说明


### 生产环境配置

1. **数据库优化**: 调整MySQL配置参数
2. **Redis集群**: 使用Redis Cluster提高可用性
3. **负载均衡**: 使用Nginx进行负载均衡
4. **SSL证书**: 配置HTTPS
5. **监控告警**: 集成Prometheus + Grafana

## 开发指南

### 项目结构

```
yolo-detection-system/
├── ai-service/          # AI检测服务
│   ├── app.py          # Flask应用主文件
│   ├── requirements.txt # Python依赖
│   ├── models/         # YOLO模型存储 
│   ├── datasets/       # 训练数据集存储 
│   ├── runs/           # 训练结果存储 
│   └── uploads/        # 上传文件存储
├── backend-service/     # Spring Boot后端
│   ├── src/main/java/  # Java源码
│   ├── pom.xml         # Maven配置
│   └── application.yml # 应用配置
├── frontend/           # Vue3前端
│   ├── src/           # 源码
│   │   ├── api/       # API接口
│   │   │   ├── model-management.ts # 模型管理API 
│   │   │   └── training.ts         # 训练API
│   │   ├── views/     # 页面组件
│   │   │   ├── model/              # 模型管理页面 
│   │   │   └── training/           # 训练页面 
│   │   └── router/    # 路由配置
│   ├── package.json   # npm配置
│   ├── vite.config.ts # Vite配置
├── database/          # 数据库脚本
│   └── schema.sql     # 数据库结构
```

### 代码规范

1. **Python**: 遵循PEP 8规范
2. **Java**: 使用Google Java Style
3. **TypeScript**: 使用ESLint + Prettier
4. **Git**: 使用约定式提交规范

### 测试

```bash
# 后端测试
cd backend-service
mvn test

# 前端测试
cd frontend
npm run test

# AI服务测试
cd ai-service
python -m pytest
```

## 常见问题

### Q: 模型下载慢怎么办？
A: 可以手动下载YOLO模型文件到 `ai-service/models/` 目录。

### Q: 摄像头检测连接失败？
A: 检查浏览器权限和摄像头设备状态。

### Q: 文件上传失败？
A: 检查文件大小限制和服务器磁盘空间。

### Q: 数据库连接失败？
A: 检查MySQL服务状态和连接配置。

### Q: 历史记录中不存在视频和图片
A: 查看后端spring启动路径

修改backend-service/src/main/resources/application.yml

upload-path:
results-path:





## 更新日志

### v1.0.0 (2025-06-27)
- 初始版本发布
- 支持图片、视频、实时检测
- 用户权限管理
- 基础数据可视化

### v2.0.1 (2025-08-01)
- 优化数据可视化
- 优化界面ui
- 修复检测记录bug
- 增加统计指标

### v3.1.0 (2025-08-10)
- 🆕 **模型管理功能**:
- 🆕 **模型训练功能**:
- 🔧 **系统优化**:


## 联系方式

- 邮箱: 2464228500@qq.com

## 致谢

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- [Element Plus](https://element-plus.org/)
- [Spring Boot](https://spring.io/projects/spring-boot)
- [Vue.js](https://vuejs.org/)

## 检测记录功能完成状态

### ✅ 已完成功能

#### 1. 数据库设计
- ✅ detection_tasks表：包含user_id字段，支持用户数据隔离
- ✅ detection_results表：通过task_id关联，间接支持用户隔离
- ✅ 索引优化：添加user_id、task_id、status等关键字段索引
- ✅ 外键约束：确保数据一致性

#### 2. 后端API实现
- ✅ DetectionRecordController：用户检测记录CRUD操作
    - 获取检测记录列表（分页、排序、筛选）
    - 获取检测记录详情
    - 获取检测结果列表
    - 获取统计信息
    - 删除检测记录
    - 批量删除检测记录
    - 获取用户概览统计
- ✅ InternalDetectionController：供AI服务使用的内部API
    - 创建检测任务
    - 更新任务状态
    - 保存检测结果
    - 获取任务信息
- ✅ 权限控制：所有用户API基于@AuthenticationPrincipal验证
- ✅ 数据隔离：确保用户只能访问自己的检测记录

#### 3. 前端界面实现
- ✅ 检测记录列表页面（/history）
    - 用户概览统计卡片
    - 搜索和筛选功能
    - 表格和卡片两种视图模式
    - 分页功能
    - 批量选择和删除
    - 操作按钮（查看详情、下载、删除）
- ✅ 检测记录详情页面（/history/detail/:taskId）
    - 基本信息展示
    - 文件预览功能
    - 统计图表（类别分布、置信度分布）
    - 检测结果列表（分页、筛选）
- ✅ 路由配置：支持详情页面访问
- ✅ 权限验证：自动登录测试用户功能

#### 4. AI服务集成
- ✅ 后端API客户端：与后端服务通信
- ✅ 检测任务创建：自动创建数据库记录
- ✅ 状态更新：实时更新任务处理状态
- ✅ 结果保存：检测完成后保存结果到数据库
- ✅ 图片检测集成：完整的检测流程
- ✅ 错误处理：异常情况的状态更新

#### 5. 文件管理
- ✅ FileController：文件下载和预览API
- ✅ 文件上传：支持图片和视频文件
- ✅ 结果文件：处理后的文件存储和访问
- ✅ 缩略图：任务缩略图生成和显示

#### 6. 安全配置
- ✅ 内部API：不需要认证，供AI服务使用
- ✅ 用户API：需要JWT认证
- ✅ CORS配置：支持跨域访问
- ✅ 权限隔离：用户数据完全隔离

### 🔧 技术特性

#### 用户权限隔离
- 每个用户只能查看自己的检测记录
- 所有查询均基于当前登录用户
- 数据库级别的权限控制

#### 性能优化
- 分页查询：避免大数据量加载
- 索引优化：提高查询效率
- 懒加载：图片和文件按需加载

#### 用户体验
- 响应式设计：支持多种屏幕尺寸
- 实时反馈：操作状态提示
- 快速搜索：关键词和条件筛选
- 批量操作：提高管理效率

### 📊 支持的检测类型
- ✅ 图片检测：单张图片处理
- ✅ 视频检测：视频文件处理
- ✅ 实时检测：摄像头检测
- ✅ 模型管理：自定义模型上传和管理 (新增)
- ✅ 模型训练：自定义数据集训练 (新增)

## 🚀 新功能详细说明

### 🤖 模型管理系统

#### 功能特性
- **智能模型识别**: 自动识别YOLO模型格式和架构
- **可视化管理**: 美观的卡片式界面展示所有模型
- **模型信息**: 显示模型大小、类别数量、修改时间等
- **一键切换**: 快速切换不同模型进行检测
- **安全管理**: 防止删除正在使用的模型

#### 支持的模型格式
- YOLOv8 系列: yolov8n.pt, yolov8s.pt, yolov8m.pt, yolov8l.pt, yolov8x.pt
- YOLOv11 系列: yolov11n.pt 及其他变体
- 自定义训练模型: 支持用户训练的所有YOLO格式模型

#### 使用流程
1. 📁 将模型文件上传到系统
2. ✅ 系统自动验证模型有效性
3. 📋 查看模型详细信息和架构
4. 🔄 一键激活模型用于检测
5. 🗑️ 管理不需要的模型文件

### 🎓 模型训练系统

#### 训练能力
- **多GPU支持**: 自动检测和使用可用GPU
- **断点续训**: 支持从检查点恢复训练
- **实时监控**: WebSocket实时推送训练状态
- **自动调优**: 智能调整训练参数
- **结果保存**: 自动保存最佳模型权重

#### 训练参数配置
```yaml
训练参数:
  - 数据集路径: datasets/your_dataset/
```

#### 实时监控指标
- 📈 **损失函数**: 训练损失和验证损失
- 🎯 **精度指标**: Precision, Recall, F1-Score
- 🏆 **mAP指标**: mAP@50, mAP@50-95
- ⏱️ **进度信息**: 当前轮次、剩余时间、ETA
- 💾 **资源使用**: GPU使用率、内存占用

#### 数据集格式要求
```
datasets/your_dataset/
├── data.yaml          # 数据集配置文件
├── images/            # 图像文件
│   ├── train/         # 训练图像
│   └── val/           # 验证图像
└── labels/            # 标注文件
    ├── train/         # 训练标注 (.txt格式)
    └── val/           # 验证标注 (.txt格式)
```

#### 训练输出
- 🏆 **最佳模型**: `runs/train/exp_xxx/weights/best.pt`
- 📊 **训练曲线**: 损失和指标变化图表
- 📝 **训练日志**: 完整的训练过程记录
- 🔍 **验证结果**: 验证集上的检测结果示例

### 🎯 用户功能
1. **查看检测记录**：分页浏览所有检测任务
2. **筛选搜索**：按类型、状态、时间、关键词筛选
3. **查看详情**：详细信息、文件预览、统计图表
4. **管理记录**：删除单个或批量删除记录
5. **统计分析**：个人检测数据统计和可视化
6. **下载结果**：下载处理后的文件

### 🚀 部署说明
- 前端：Vue3 + TypeScript + Element Plus
- 后端：Spring Boot + JPA + MySQL
- AI服务：Flask + YOLOv8
- 数据库：MySQL 8.0+
- 认证：JWT Token

---

## 测试指南

### 启动服务
```bash
# 启动后端服务
cd backend-service && mvn spring-boot:run

# 启动AI服务  
cd ai-service && python app.py

# 启动前端服务
cd frontend && npm run dev
```

### 访问地址
- 前端界面：http://localhost:3000
- 后端API文档：http://localhost:8080/swagger-ui.html


检测记录功能已完全实现，支持完整的用户隔离和记录管理功能！

<!--more-->
