# 芝士猫视频帧无损提取工具

[English](README_EN.md) | 中文

## Cloudflare Pages部署指南

当在Cloudflare Pages上部署此项目时，请确保设置以下环境变量：

```
CI=false
```

这将确保ESLint警告不会被视为错误，从而允许构建过程成功完成。

## 项目介绍

本项目是一个基于Web的视频帧提取工具，允许用户上传视频文件，然后根据设定的参数（帧率、图像质量等）提取视频帧。

### 主要功能

1. 视频上传与处理
2. 自定义帧率提取
3. 控制图像质量和格式
4. 设置提取范围（开始和结束时间）
5. 预览和下载提取的帧
6. 批量选择和下载

## 技术栈

### 后端
- Flask (Python)
- OpenCV-Python
- Cloudflare R2 (存储服务)
- Cloudflare Workers (边缘计算)

### 前端
- React.js
- Modern JavaScript (ES6+)
- CSS3

## 架构概述

该应用采用前后端分离架构：

1. 前端通过React.js构建，提供友好的用户界面
2. 后端使用Flask API处理视频提取逻辑
3. 使用Cloudflare R2存储提取的帧
4. Cloudflare Workers用于内容分发和处理

## 部署指南

### 前端部署

1. 进入前端目录：
   ```
   cd frontend
   ```

2. 安装依赖：
   ```
   npm install
   ```

3. 构建生产版本：
   ```
   npm run build
   ```

4. 将`build`目录中的文件部署到网站托管服务

### 后端部署

1. 安装依赖：
   ```
   pip install -r requirements.txt
   ```

2. 配置环境变量或创建`.env`文件：
   ```
   R2_ACCOUNT_ID=your_account_id
   R2_ACCESS_KEY_ID=your_access_key
   R2_SECRET_ACCESS_KEY=your_secret_key
   R2_BUCKET_NAME=your_bucket_name
   WORKER_URL=your_worker_url
   ```

3. 运行应用：
   ```
   python web_app.py
   ```

## API文档

### POST /api/upload-video
上传视频文件。

### POST /api/extract-frames
提取视频帧。

请求体示例：
```json
{
  "videoPath": "path/to/video.mp4",
  "fps": 1,
  "quality": 90,
  "format": "jpg",
  "startTime": null,
  "endTime": null
}
```

## 开发指南

### 本地开发

1. 克隆仓库：
   ```
   git clone https://github.com/your-username/video-frame-extractor.git
   ```

2. 设置前后端开发环境：
   - 前端：`cd frontend && npm install && npm start`
   - 后端：`python web_app.py`

## 许可证

[MIT](LICENSE)
