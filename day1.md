# Day 1 · 环境搭建（2026-10-09）

## ✅ 今日完成

| 事项 | 结果 |
|---|---|
| 环境检查 | Node.js v24.21.0 + npm 11.19.0（E:\） |
| 环境检查 | Git 2.56.0.windows.2（F:\Git） |
| 环境检查 | VS Code 1.141.0 |
| 注册 GitHub | 用户名 `Anontokyo111` |
| Git 身份配置 | user.name + user.email 已写入 `.gitconfig` |
| 创建本仓库 | git init → add → commit → push |

## 📚 今日知识点

### 1. PATH 环境变量是什么
终端输入 `node` 时，系统会沿着 PATH 列表里的目录逐个查找 `node.exe`。
PATH 里没有的目录，命令就"找不到"。装软件后提示"不是内部或外部命令"，
99% 是 PATH 问题。

### 2. Git 是什么（一句话理解）
**代码的"存档 + 后悔药"**。每次 `commit` 就像游戏存档，
改坏了随时可以回到任意存档点。AI 时代尤其重要——
AI 帮你大改代码前先 commit，等于买了保险。

### 3. 向 AI 提问的四要素（Vibe Coding 核心技能）
1. **背景**：我在做什么（什么项目、什么环境）
2. **目标**：我想达成什么效果
3. **约束**：有什么限制（版本、不能用什么）
4. **报错信息**：完整粘贴错误日志（不要只发一句话"帮我修一下"）

❌ 错误示范：「npm 报错了怎么办」
✅ 正确示范：「我在 Windows 11 上装 Node.js 到 E:\，终端运行 `npm --version` 报错
"无法加载文件 E:\npm.ps1，因为在此系统上禁止运行脚本"，我希望能正常使用 npm，已装 Node v24.21.0」

### 4. Git 基本命令速查

| 命令 | 作用 |
|---|---|
| `git init` | 把当前目录变成 Git 仓库 |
| `git status` | 查看哪些文件有改动 |
| `git add .` | 暂存所有改动（放入"待提交区"） |
| `git commit -m "说明"` | 存档（提交），说明写清楚改了什么 |
| `git log` | 查看提交历史 |
| `git remote add origin <地址>` | 关联 GitHub 远程仓库 |
| `git push -u origin main` | 推送到 GitHub（首次加 -u） |
| `git pull` | 拉取远程更新 |

## 🕳️ 今日踩坑记录

1. **winget 是"假"的**：系统里的 winget.exe 是 0 字节存根，任何命令都无输出。
   教训：工具"存在"不等于"能用"，先 `--version` 验证。
2. **Node 装到 E:\ 根目录的连锁反应**：PowerShell 优先匹配到 `npm.ps1` 脚本，
   被执行策略 Restricted 拦截 → 解决：`Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`。
3. **GitHub 注册人机验证卡住**：刷新重试即可，别慌。

## 📌 明天计划（Day 2）

- [ ] 学习 Markdown 常用语法（本笔记就是 Markdown 写的）
- [ ] 在 VS Code 里打开本仓库，尝试自己改一行文字再 commit
- [ ] 开始 HTML 基础：标签、结构
