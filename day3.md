# Day 3 · CSS 基础（2026-10-09）

## ✅ 今日完成

- 理解 CSS 的定位：HTML 管"有什么"，CSS 管"长什么样"
- 掌握外部样式表引入方式：`<link rel="stylesheet" href="style.css">`
- 掌握三种选择器：标签、class（`.`）、id（`#`）
- 学会 10+ 常用属性（颜色、字体、间距、边框、圆角、盒模型）
- 完成页面美化任务：背景、标题、列表卡片、表格单线边框、按钮、链接按钮
- 学会 `:hover` + `transition` 做出丝滑悬停效果
- 用"共用 class"重构了两个按钮（DRY 思想）

## 📚 今日知识点

### 1. CSS 是什么
一句话："点名 → 定规矩"。HTML 是骨架，CSS 是皮肤，JS 是大脑。

### 2. 三种引入方式

| 方式 | 写法 | 评价 |
|---|---|---|
| 行内 | `<p style="color:red">` | 应急用，正式项目禁止 |
| 内嵌 | `<head>` 里 `<style>` | 练习方便 |
| **外部文件** | `<link rel="stylesheet" href="style.css">` | ✅ 正式项目唯一正解 |

- `link` 是**单标签**
- `rel="stylesheet"` 告诉浏览器"这是样式表"
- `href` 用相对路径（规则同 `<img src>`）
- 路径写错 = 样式完全不生效，且**不报错**（新手第一大坑）

### 3. 选择器三兄弟

| 选择器 | 写法 | 选中谁 | 使用频率 |
|---|---|---|---|
| 标签 | `p { }` | 所有 `<p>` | 常用 |
| **class** | `.my-box { }` | `class="my-box"` 的元素 | **最高** |
| id | `#title { }` | `id="title"` 的元素 | 少用 |

**关键规则**：
- 逗号 `,` = 并列（"这些我都要"）：`table, th, td { }`
- 空格 = 后代（"里面的"）：`div p { }`
- `.` 和 `#` 只是 CSS 的**语法标记**，HTML 里不带符号：`<p class="my-box">` / `<h1 id="title">`

### 4. class vs id（重点）

| | class `.my-box` | id `#title` |
|---|---|---|
| 现实比喻 | 校服（可多人穿） | 身份证（唯一） |
| 能否重复 | ✅ 可重复、一元素可挂多个 | ❌ 全页面唯一 |
| CSS 优先级 | 中 | 高（会压过 class） |
| 用途 | 90% 的样式场景 | 锚点跳转、JS 定位 |

⚠️ **重复 id 浏览器不报错**，但 CSS 会全选中、JS/锚点只认第一个 → 隐藏 bug。
⚠️ CSS 里写 `title {}`（漏了 `#`）会偷偷命中 `<title>` 网页标题标签。

### 5. 常用属性速查

```css
body { background-color: #f5f6fa; font-family: "Microsoft YaHei", sans-serif; }
h1   { color: #2c3e50; text-align: center; }
.box { width: 300px; padding: 20px; margin: 10px auto;
       border: 2px solid #3498db; border-radius: 8px; background-color: white; }
table, th, td { border: 1px solid #ccc; }
table { border-collapse: collapse; }   /* 边框合并成单线，写在 table 里 */
```

### 6. 盒模型（一句话）
**margin（与邻居距离）→ border（围墙）→ padding（围墙到内容的垫层）→ content（内容）**

`margin: 10px auto` 里的 `auto` = 水平自动 → 元素水平居中。

### 7. display：为什么 `<a>` 直接设宽高没效果

| display | 谁 | 特点 |
|---|---|---|
| `block` | div、p、h1 | 独占一行，能设宽高 |
| `inline` | a、span | 跟文字排一行，**设宽高无效** |
| `inline-block` | 手动设置 | 既同行排布，又能设宽高 ← 按钮要的 |

### 8. 把 `<a>` 打扮成按钮

```css
.btn { display: inline-block; background-color: #3498db; color: #fff;
       border: none; padding: 10px 24px; border-radius: 4px;
       text-decoration: none; cursor: pointer;
       transition: background-color 0.3s ease; }
.btn:hover { background-color: #2980b9; }
```

- **语义规则**：要"跳走"用 `<a>`，要"干活"用 `<button>`
- **过渡三件套**：`transition`（过渡）必须有 `:hover`（变化的目标）配合，否则看不到效果
- **DRY 复用**：一套 class 同时用在 `<a>` 和 `<button>` 上，不重复写样式

## 🕳️ 今日踩坑记录

1. **`transition` 写了但没 `:hover`** → 没有"变化目标"，过渡效果看不见。
   教训：过渡需要"起点 + 终点"两个状态才生效。
2. **两个按钮样式不一致**（padding、font-size 各写一套）→ 用共用 class 合并。
   教训：重复的样式就是未来的维护负担（DRY 原则）。
3. **漏写 `.` 或 `#`** → CSS 静默失效，不报错。排查第一步永远是"选择器写对了吗"。

## 📌 明天计划（Day 4）

- [ ] CSS 布局核心：`display: flex`（后台管理页面的骨架基础）
- [ ] 用 Flex 做"侧边栏 + 主内容区"的经典后台布局
- [ ] 理解主轴/交叉轴、`justify-content`、`align-items`

---

## 📊 Day 3 学习评分（AI 教练评估 · 2026-10-09）

### 总分：90 / 100（优秀，达成"冲 90+"目标 🎉）

| 维度 | 得分 | 评语 |
|---|---|---|
| 知识点掌握 | 90 | 选择器、盒模型、display 全部落实到位，无重复错误 |
| 动手实践 | 90 | 完成任务并超额（width 居中、transition、DRY 重构） |
| 代码规范 | 84 | 有中文注释的好习惯；缩进一致性仍是主要扣分项 |
| 提问质量 | 93 | ⭐ 今天最大亮点：连问 `.` 的含义、id 唯一性、`td` 是什么、`<a>` 能否当按钮 |
| 时间效率 | 90 | 一天吃透 CSS 基础 + 页面美化，节奏稳定 |
| Git 工作流 | 90 | 完成第三次收工循环 |

- **学习效果分**：90（较 Day 2 的 88 提升）
- **学习效率分**：91

### 🌟 亮点

1. **提问质量极高**：不是被动接收，而是追问"为什么有点""为什么唯一"——这是真正的学习
2. **超额完成**：自己加了宽度、居中、过渡效果，还主动做了样式复用重构
3. **注释习惯**：CSS 每行都写中文注释，复习时一目了然

### 🎯 扣分点（明天改进）

1. **缩进一致性**：今天第三次提醒了 → 明天开工先按一次 `Shift+Alt+F` 格式化，养成肌肉记忆
2. **命名准确性**：`.btn-link` 现在也用在 `<button>` 上了，叫 `.btn` 更准确（命名要反映用途）
3. **顺序习惯**：建议"基础样式在前，`:hover` 状态在后"（今天顺序反了，虽然不影响效果）

### 🏁 明日目标

- 掌握 Flex 布局，做出后台管理页面的"侧边栏 + 内容区"经典骨架
- 开局使用 `Shift+Alt+F`，规范性评分冲 90
