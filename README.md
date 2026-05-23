# 小崔 AI 分身 — 网页聊天应用

与小崔（19岁、陕西科技大学计算机大一学生）的 AI 分身聊天。

---

## 本地测试

```bash
# 1. 安装依赖
npm install

# 2. 设置 API Key
# Windows (CMD):
set DEEPSEEK_API_KEY=你的DeepSeek_API_Key

# Windows (PowerShell):
$env:DEEPSEEK_API_KEY="你的DeepSeek_API_Key"

# Mac / Linux:
export DEEPSEEK_API_KEY="你的DeepSeek_API_Key"

# 或者创建 .env 文件（复制 .env.example 并填入真实 Key）

# 3. 启动服务器
npm start

# 4. 打开浏览器访问
# http://localhost:3000
```

---

## 部署到 Render（免费，推荐）

Render 是最简单的选择，免费额度足够日常使用。

### 第一步：准备代码

1. 把整个项目文件夹上传到 GitHub（新建一个仓库，把所有文件 push 上去）。
2. 确保仓库根目录有这 5 个文件：`server.js`、`package.json`、`public/index.html`、`.env.example`、`README.md`。

### 第二步：在 Render 创建 Web Service

1. 打开 [render.com](https://render.com)，用 GitHub 账号注册/登录。
2. 点右上角 **"New +"** → 选择 **"Web Service"**。
3. 授权 Render 访问你的 GitHub，选择你刚才上传的仓库。
4. 填写配置：
   - **Name**：随便起，比如 `xiaocui-chat`
   - **Runtime**：Node
   - **Build Command**：`npm install`
   - **Start Command**：`npm start`
   - **Free Instance Type**：选择 Free（免费）

### 第三步：设置环境变量

在 Web Service 页面左侧菜单找到 **"Environment"**，添加：

| Key | Value |
|-----|-------|
| `DEEPSEEK_API_KEY` | 你的 DeepSeek API Key |

### 第四步：部署

1. 点页面底部的 **"Create Web Service"**。
2. 等 2-3 分钟，部署完成后页面顶部会显示一个 `https://xxx.onrender.com` 的链接。
3. 打开这个链接，就可以和小崔聊天了！

> **注意**：免费 Render 实例 15 分钟无访问会自动休眠，下次访问需要等 30-60 秒启动。这是正常的。

---

## 部署到 Railway（免费，备选）

### 第一步：准备代码

同上，先把代码上传到 GitHub。

### 第二步：在 Railway 部署

1. 打开 [railway.app](https://railway.app)，用 GitHub 账号注册/登录。
2. 点 **"New Project"** → **"Deploy from GitHub repo"**。
3. 选择你的仓库，Railway 会自动检测 Node.js 项目并部署。

### 第三步：设置环境变量

1. 进入项目 Dashboard，点 **"Variables"** 标签。
2. 添加 `DEEPSEEK_API_KEY`，值填你的 API Key。
3. Railway 会自动重新部署。

### 第四步：获取公网链接

1. 在项目 Dashboard 的 **"Settings"** 中，点 **"Generate Domain"**。
2. 会得到一个 `xxx.up.railway.app` 的公开链接。

---

## 获取 DeepSeek API Key

1. 打开 [platform.deepseek.com](https://platform.deepseek.com)
2. 注册/登录
3. 在 **"API Keys"** 页面创建一个新的 Key
4. 复制保存（只显示一次）
5. DeepSeek 新用户有免费额度，收费很低（约 1 元/百万 tokens）

---

## 自定义角色

如果你想改成其他角色，编辑 `server.js` 中 `SYSTEM_PROMPT` 变量的内容即可。系统提示词完全存放在后端，前端用户无法看到。

---

## 文件说明

| 文件 | 作用 |
|------|------|
| `server.js` | 后端主程序，处理聊天请求，调用 DeepSeek API |
| `public/index.html` | 前端聊天界面（单页面） |
| `package.json` | 项目依赖和启动脚本 |
| `.env.example` | 环境变量模板 |
| `README.md` | 本文件 |

---

## 技术栈

- **后端**：Node.js + Express
- **AI**：DeepSeek API（`deepseek-chat` 模型）
- **流式传输**：Server-Sent Events (SSE)
- **前端**：原生 HTML/CSS/JS，无框架
