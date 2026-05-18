# realtime-vision-chat
一个面向vlm视觉推理的轻量框架
# AI 视觉助手

**你的桌面AI伴侣 —— 看得见、说得出、动得起来的本地AI**
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)

---

## 这是什么

一个运行在你电脑上的**桌面AI伴侣系统**。它能通过摄像头看到你、通过麦克风/文字与你对话、识别你的身份、记住你们的互动、操作电脑完成任务、陪玩游戏。

**本地运行、无需联网、开源免费。**

---
注意：处于早期阶段，其实就是个验证想法的玩具，框架由deepseek v4pro编写。

## 核心能力

### 视觉感知
- **摄像头实时对话**：AI 看到画面后描述、评论、互动
- **屏幕观察**：AI 观察你的屏幕内容，提供帮助
- **人脸识别**：认出不同用户，自动切换个性化态度

### 智能交互
- **文字/语音对话**：支持 TTS 语音合成，说出的话逐句播放
- **记忆系统**：自动记录和回忆与你相关的事件、人物、物品
- **持续思考**：后台自主思考，像人类一样有内心独白
- **自主行为**：检测到你长时间不说话时，会主动打招呼、发表评论

### 电脑操控
- **AI 操作桌面**：帮你打开软件、搜索网页、播放视频
- **游戏伙伴**：内置打飞机游戏，AI 可以自己玩给你看
- **白板涂鸦**：随时画画，AI 能看到并评论

### 动态桌宠
- **静态图变活**：一张角色图加锚点就能产生呼吸、拉伸、旋转等动态
- **表情合成**：口型+眼睛+动作自由组合
- **情绪响应**：AI 在对话中通过 `[PET:开心]` 指令实时控制角色表情
- **角色包系统**：导入 zip 角色包即可换角色，支持自定义动态

---

## 技术架构

| 层 | 技术栈 |
|----|--------|
| 后端 | Python / Flask / Socket.IO |
| AI 推理 | LM Studio (本地 OpenAI 兼容 API) |
| TTS 语音 | GPT-SoVITS |
| 视觉 | OpenCV / Pillow |
| 前端 | 原生 HTML/CSS/JS + Canvas |
| 记忆 | SQLite + FTS5 全文检索 + jieba 分词 |
| 人脸识别 | OpenCV LBPH |
| 桌面操控 | pyautogui / mss |
| 打包 | PyInstaller |

---

## 快速开始

### 1. 省心版使用
- 下载 [LM Studio](https://lmstudio.ai/)
- 加载视觉模型（如 qwen2.5-vl）
- 下载压缩包
- 解压至非中文路径
- 双击bat脚本自动安装环境
- 等待进入。


### 2. 常规使用
-安装依赖

```bash
git clone https://github.com/yourname/ai-vision-assistant.git
cd ai-vision-assistant
pip install -r requirements.txt
```

- 下载 [LM Studio](https://lmstudio.ai/)
- 加载视觉模型（如 qwen2.5-vl）
- 启动本地服务（默认 http://localhost:1234）

-（可选）启动 TTS 服务
- 部署 [GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)
- 启动 API 服务（默认 http://localhost:9880）

-启动本系统

```bash
python server.py
```

浏览器打开 `http://127.0.0.1:5000`

## 项目结构

```
├── server.py               # 主服务
├── models/
│   ├── lm_studio_client.py # AI 推理客户端
│   ├── memory.py           # 记忆系统 (SQLite+FTS5)
│   └── tts_client.py       # 语音合成客户端
├── utils/
│   ├── camera.py           # 摄像头管理
│   ├── face_manager.py     # 人脸识别
│   ├── screen_capture.py   # 屏幕截图
│   ├── computer_agent.py   # 电脑操控代理
│   ├── game_ai.py          # 游戏 AI
│   ├── continuous_thinker.py # 持续思考引擎
│   ├── auto_responder.py   # 自主对话
│   └── pet/                # 桌宠系统
│       ├── pet_manager.py
│       ├── pet_controller.py
│       ├── pet_editor.py
│       ├── pet_import.py
│       └── pet_lip_sync.py
├── templates/
│   └── index.html          # 前端单页应用
├── static/
│   └── socket.io.min.js
└── data/                   # 用户数据（外置）
    ├── 角色/
    ├── uploads/
    └── settings/
```

---

## 优点

- **完全本地运行**：不联网、不上传数据、隐私安全
- **功能高度集成**：对话+视觉+操控+游戏+桌宠一体化
- **模块化架构**：视觉模型可替换，功能可选开关
- **可扩展角色**：角色包即插即用，锚点编辑器精细控制动态
- **记忆持久化**：AI 能记住与你交互的细节
- **开源免费**：MIT 协议，随意修改分发

---

## 缺点与限制

- **仅支持中文**：TTS 和分词目前只适配中文
- **前端古老**：原生 JS+HTML，没有使用 Vue/React 等现代框架，界面不够精美
- **代码狗屎**：大量使用deepseek生成来实现想法
- **Windows 优先**：电脑操控、屏幕截图等功能依赖 Windows API，Linux/macOS 兼容性有限

---

## 贡献

欢迎提 Issue 和 PR！无论是功能建议、Bug 修复、文档改进还是角色包分享。


## 协议

Apache License 2.0

---

**如果你喜欢这个项目，请给个 ⭐ Star 支持一下！**
