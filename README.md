# AI私人助理项目

基于FastAPI、Gradio和LangChain构建的智能AI私人助手，支持知识库管理、文档检索、代码执行等功能。

## ✨ 功能特性

### 🤖 智能聊天
- 基于大语言模型的自然语言对话
- 支持多轮对话和历史上下文
- 集成多种工具（代码解释器、网页搜索、天气查询等）

### 📚 知识库管理
- 创建、删除知识库
- 上传PDF、TXT、MD、CSV等多种格式文档
- 自动向量化存储（FAISS向量库）
- AI自动检索相关知识库内容回答问题

### 🔧 工具集成
- 代码解释器：执行Python代码并返回结果
- 网页搜索：实时搜索互联网信息
- 天气查询：获取天气信息
- 时间查询：获取当前时间

## 🚀 快速开始

### 环境要求
- Python 3.11+
- Windows/Linux/macOS

### 安装步骤

1. **克隆项目**
```bash
git clone <repository-url>
cd AI私人助理项目
```

2. **安装依赖**
```bash
pip install -r requirements.txt
```

3. **配置API密钥**

在项目根目录创建 `.env` 文件，配置以下内容：
```env
# 大语言模型API配置（例如SiliconFlow）
SILICONFLOW_API_KEY=your_api_key_here

# 其他API配置（可选）
OPENAI_API_KEY=your_openai_key_here
```

4. **启动后端服务**
```bash
python app_server.py
```
后端服务将在 `http://127.0.0.1:6605` 启动

5. **启动前端界面**
```bash
python webui.py
```
前端界面将在 `http://127.0.0.1:7900` 启动

## 📖 使用说明

### 1. 知识库管理

**创建知识库：**
1. 切换到"📚 知识库管理"标签页
2. 输入知识库名称和描述
3. 点击"创建知识库"

**上传文档：**
1. 选择已创建的知识库
2. 点击上传文件，选择PDF/TXT/MD/CSV等格式
3. 上传成功后会显示详细的上传结果

### 2. 智能聊天

**使用知识库：**
- 提问时AI会自动检索所有知识库中的相关内容
- AI会在回答开头明确说明是否使用了知识库

**使用工具：**
- AI会根据问题自动调用相应工具
- 支持代码执行、网页搜索、天气查询等

## 📁 项目结构

```
AI私人助理项目/
├── app_server.py              # FastAPI后端服务入口
├── webui.py                   # Gradio前端界面
├── requirements.txt           # 依赖包列表
├── .env                       # 环境变量配置（需创建）
├── chat/                      # 聊天相关模块
│   └── chat_routes.py         # 聊天API路由
├── knowledgebase_server/      # 知识库服务
│   ├── knowledge_route.py     # 知识库API路由
│   └── loader/                # 文档加载器
├── tools/                     # AI工具集
│   ├── code_interpreter.py    # 代码解释器
│   ├── web_search.py          # 网页搜索
│   └── ...
├── config/                    # 配置文件
│   ├── setting.py             # 系统设置
│   └── prompt.py              # 提示词配置
├── db_server/                 # 数据库服务
│   └── knowledge_base_repository.py  # 知识库数据仓库
├── knowledgebases/            # 向量库存储目录
└── data/                      # 文档存储目录
```

## 🔧 技术栈

| 组件 | 技术选型 |
|------|----------|
| 后端框架 | FastAPI |
| 前端界面 | Gradio |
| 向量数据库 | FAISS |
| LLM框架 | LangChain |
| 文件处理 | PyMuPDF (fitz) |
| 数据库 | SQLite (SQLAlchemy) |

## 📝 注意事项

1. **API密钥配置**：必须在 `.env` 文件中配置有效的大语言模型API密钥
2. **首次使用**：首次上传文档时会自动创建向量库，可能需要一些时间
3. **向量分批**：大文档会自动分批处理，避免API限制
4. **浏览器缓存**：如遇界面问题，建议使用无痕模式打开

## 🤝 贡献

欢迎提交Issue和Pull Request！

## 📄 许可证

MIT License
