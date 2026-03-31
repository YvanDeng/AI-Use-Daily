# 🎓 AI 学习路线图 - 程序员必备

## 📚 学习阶段总览

### 第一阶段：基础知识储备 (1-2月)
### 第二阶段：机器学习入门 (2-3月)  
### 第三阶段：深度学习进阶 (1-2月)
### 第四阶段：大语言模型 (LLM) (1-2月)
### 第五阶段：实践与项目 (持续)
### 第六阶段：进阶主题 (持续)

---

## 第一阶段：基础知识储备

### 1.1 数学基础

#### 线性代数
- 矩阵运算、行列式
- 特征值与特征向量
- 奇异值分解 (SVD)
- 资源: 3Blue1Brown《线性代数的本质》

#### 概率论与统计学
- 概率分布 (正态/泊松/二项)
- 条件概率与贝叶斯定理
- 最大似然估计 (MLE)
- 资源: 《概率论与数理统计》- 浙大版

#### 微积分
- 导数与梯度
- 链式法则
- 资源: Khan Academy Calculus

### 1.2 编程基础

#### Python (必须)
- 基础语法、数据结构
- NumPy (数值计算)
- Pandas (数据分析)
- Matplotlib (可视化)
- 资源: 《Python Crash Course》

#### 数学库
- SciPy
- SymPy (符号计算)

#### 开发环境
- Jupyter Notebook / Lab
- VS Code + Python 扩展
- Cursor / Trae AI 编程

### 1.3 AI 概述
- 什么是人工智能
- AI 发展历史 (图灵测试 → 深度学习)
- AI 分支: CV / NLP / RL / Expert System
- 资源: 公众号: 机器之心、AI科技大本营

---

## 第二阶段：机器学习入门

### 2.1 机器学习基础
- 监督学习 / 无监督学习 / 强化学习
- 线性回归、逻辑回归
- 支持向量机 (SVM)
- 决策树与随机森林
- K-means 聚类
- 梯度下降与优化

### 2.2 深度学习基础
- 神经网络原理
- 反向传播算法
- CNN (卷积神经网络)
- RNN / LSTM
- 资源: 3Blue1Brown《神经网络》系列

### 2.3 实践
- PyTorch 基础
- TensorFlow 基础
- Kaggle 入门比赛
- 资源: 吴恩达 ML 课程

---

## 第三阶段：深度学习进阶

### 3.1 进阶网络结构
- ResNet / Transformer
- Attention 注意力机制
- GAN (生成对抗网络)
- 自编码器

### 3.2 模型优化
- 正则化与 Dropout
- Batch Normalization
- 学习率调度
- 模型评估与调优

### 3.3 框架进阶
- PyTorch Lightning
- Hugging Face Transformers
- 模型部署基础

---

## 第四阶段：大语言模型 (LLM)

### 4.1 LLM 基础

#### Transformer 架构
- Attention 机制 (Self-Attention, Multi-Head)
- Encoder-Decoder 结构
- 位置编码 (Positional Encoding)
- 资源: Jay Alammar《The Illustrated Transformer》

#### GPT 系列
- GPT-1/2/3/4 发展历程
- Prompt Engineering 基础
- Fine-tuning 简介

#### 开源 LLM
- LLaMA 系列 (Meta)
- Qwen (阿里)
- GLM (智谱)
- DeepSeek (深度求索)
- Yi (零一万物)

### 4.2 Prompt Engineering (提示词工程)

#### 基础技巧
- 清晰具体的指令
- 分步思考 (Chain of Thought)
- Few-Shot Learning
- 系统提示词 vs 用户提示词

#### 高级技巧
- ReAct (推理+行动)
- CoT (思维链)
- ToT (思维树)
- Self-Consistency
- 资源: https://www.promptingguide.ai

### 4.3 LLM 应用开发

#### API 调用
- OpenAI API
- Anthropic Claude API
- 国内 API (DeepSeek/GLM/Qwen/硅基流动)
- OpenAI-Compatible API

#### 框架与工具
- LangChain
- LlamaIndex
- AutoGen
- OpenAI SDK

#### RAG (检索增强生成)
- 向量数据库 (Chroma, Milvus, Pinecone)
- 文本分割策略
- Embedding 模型

#### Agent 原理
- Tool Use
- Memory (短期/长期)
- Planning

---

## 第五阶段：实践与项目

### 5.1 实战项目推荐

#### 入门级
- AI 对话助手 (接入 LLM API)
- 文本分类器 (IMDB 情感分析)
- 聊天机器人 (微信/钉钉/飞书)
- 资源: 吴恩达《AI for Everyone》

#### 进阶级
- RAG 知识库问答系统
- Agent 自动化工作流 (OpenClaw)
- AI 写作助手
- 代码助手 (Cursor/Trae)

#### 高级
- 自建 LLM 微调
- Agent 多智能体系统
- 多模态应用 (图像生成/语音识别)

### 5.2 AI 工具生态

#### 编程辅助
- Cursor (AI IDE)
- Trae (字节跳动 AI IDE)
- Windsurf (Codeium)
- Claude Code (Anthropic)
- GitHub Copilot

#### LLM 客户端
- ChatGPT / Claude App
- Kimi / 智谱清言 /通义千问
- Cherry Studio (聚合客户端)

#### 本地 LLM
- Ollama
- LM Studio
- vLLM
- llama.cpp

#### AI Agent 平台
- OpenClaw (开源)
- Coze (字节)
- AgentQL

#### 部署工具
- Docker / Docker Compose
- Railway / Vercel / Render
- 阿里云 / 腾讯云 / GPU 服务器

---

## 第六阶段：进阶主题

### 6.1 AI Agent (智能体)

#### Agent 核心概念
- Perception (感知)
- Reasoning (推理)
- Action (行动)
- Memory (记忆)

#### 主流 Agent 框架
- AutoGen (Microsoft)
- LangChain Agents
- CrewAI
- MetaGPT

#### MCP (Model Context Protocol)
- 什么是 MCP
- MCP Server 开发
- MCP 生态

#### 实践
- 用 OpenClaw 打造个人 AI 助手

### 6.2 多模态 (Multimodal)

#### 图像生成
- Midjourney
- DALL-E
- Stable Diffusion
- FLUX

#### 视频生成
- Sora / Runway / Pika
- 可灵 (快手) / 海螺 (字节)

#### 语音处理
- Whisper (语音转文本)
- ElevenLabs (文本转语音)
- GPT-4o 音频

#### 多模态 LLM
- GPT-4V / Claude Vision
- Gemini Multimodal
- Qwen-VL / GLM-4V

### 6.3 AI 安全与伦理
- Prompt Injection
- 数据隐私保护
- AI 生成内容检测
- 深伪 (Deepfake) 识别
- AI 伦理与责任

---

## 学习资源汇总

### 📺 在线课程
- 吴恩达 CS229 (ML)
- 吴恩达《AI for Everyone》
- 李宏毅 ML/DL 课程
- Fast.ai
- DeepLearning.AI
- 3Blue1Brown 神经网络
- karpathy (Andrej Karpathy)

### 📚 书籍
- 《机器学习》- 周志华
- 《深度学习》- Ian Goodfellow
- 《动手学深度学习》- 李沐
- 《Python机器学习》
- 《大模型应用开发实践》
- 《Prompt Engineering Guide》
- 《The Illustrated LM》

### 🌐 网站与社区
- Hugging Face
- GitHub
- 知乎 AI 话题
- 机器之心
- AI科技大本营
- V2EX AI 节点
- Reddit r/MachineLearning

---

## 学习建议

### 🎯 学习路径建议

**阶段 1 (1-2月): Python + 数学基础 + AI 概论**
- 目标: 掌握 Python 基础，理解基本数学概念

**阶段 2 (2-3月): 机器学习基础**
- 目标: 理解常见算法 (LR, SVM, 决策树, CNN)
- 实践: 完成 Kaggle 入门比赛

**阶段 3 (1-2月): 大语言模型 + Prompt Engineering**
- 目标: 理解 Transformer 原理，掌握提示词技巧
- 实践: 接入 LLM API 开发小应用

**阶段 4 (持续): Agent 实战 + 项目**
- 目标: 用 OpenClaw / Coze 等打造自动化工作流
- 实践: 参与开源项目，持续学习最新技术

### ⚡ 快速上手建议
1. 先会用 AI 工具 (Cursor/Trae) 提升工作效率
2. 学会 Prompt Engineering 充分发挥 LLM 能力
3. 接入 API 做小工具加深理解
4. 逐步深入底层原理

---

## 常用工具速查

### 🖥️ 开发环境
- Cursor / Trae
- VS Code
- Jupyter
- PyCharm
- Docker Desktop

### 🔌 API 聚合
- 硅基流动 (2000万token免费)
- OpenRouter (聚合)
- LLM-API (国内聚合)
- One-API

### ☁️ 部署平台
- Railway
- Vercel
- Render
- 阿里云函数计算
- 腾讯云 SCF

---

📅 更新时间: 2026-02-28
👤 整理: OpenCode AI
