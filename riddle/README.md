# 🏮 灯谜答案查询器

一个轻量的灯谜答案在线查询工具，支持关键词实时搜索、一键复制答案，可部署到 GitHub Pages，纯前端、零依赖。

**在线访问**：https://laowaigua.github.io/riddle

---

## ✨ 功能特性

| 功能 | 说明 |
|------|------|
| 🔍 **实时搜索** | 输入即筛选，同时匹配**题目**、**提示**、**答案**三列 |
| 📋 **表格展示** | 编号 / 题目 / 提示 / 答案 四列，表头吸顶，内容单行不换行 |
| 🎯 **单击选中** | 底部答案区显示两行：`【提示】题目` 和 `✅ 答案` |
| 📄 **一键复制** | 点击「复制答案」按钮，或**双击列表行**即可复制到剪贴板 |
| 💬 **Toast 提示** | 复制成功后底部弹出提示，1.8 秒自动消失 |
| ⌨️ **快捷键** | 按 `Esc` 快速清空搜索 |
| 📱 **响应式** | 移动端自动隐藏「提示」列，全屏显示 |
| 🚀 **零依赖** | 单个 HTML 文件，无需构建、无需框架 |

---

## 🖼️ 界面预览

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│                 🏮 灯谜答案查询器               v260927   │
│                                                          │
├──────────────────────────────────────────────────────────┤
│  🔍 [ 输入关键词搜索题目、提示或答案… ]        [ 清空 ]   │
│  共 311 条灯谜                                            │
├──────────────────────────────────────────────────────────┤
│  编号 │ 题目                 │ 提示         │ 答案        │
│   1   │ 五句话。             │ 猜一句成语   │ 三言两语    │
│   2   │ 心无二用。           │ 猜一句成语   │ 一心一意    │
│   3   │ 爬楼梯。             │ 猜一句成语   │ 步步高升    │
│  ...                                                      │
├──────────────────────────────────────────────────────────┤
│  答案详情                                                 │
│  【猜一句成语】 五句话。                                   │
│  ✅ 三言两语                             [ 📋 复制答案 ]  │
└──────────────────────────────────────────────────────────┘
                  laowaigua.github.io
```

---

## 📁 目录结构

```
your-repo/
├── index.html          # 主页面（含样式、脚本）
├── riddleConfig.json   # 灯谜数据
└── README.md           # 本文件
```

---

## 🚀 部署到 GitHub Pages

### 1. 克隆或创建仓库

```bash
git clone https://github.com/laowaigua/laowaigua.github.io.git
cd laowaigua.github.io
```

### 2. 放入文件

把 `index.html`、`riddleConfig.json` 放到仓库根目录。

### 3. 提交推送

```bash
git add index.html riddleConfig.json README.md
git commit -m "Add 灯谜答案查询器"
git push origin main
```

### 4. 开启 Pages

进入仓库 **Settings → Pages**：

- **Source**：`Deploy from a branch`
- **Branch**：`main`，目录选 `/ (root)`
- 点击 **Save**

等待 1~2 分钟，访问 `https://laowaigua.github.io/` 即可。

---

## 💻 本地运行

由于浏览器对 `file://` 协议下的 `fetch` 有安全限制，**不能直接双击打开 `index.html`**，需要用本地 HTTP 服务：

### Python

```bash
# Python 3
python -m http.server 8000
```

### Node.js

```bash
npx serve
# 或
npx http-server -p 8000
```

然后访问 `http://localhost:8000`。

---

## 📖 数据格式

`riddleConfig.json` 是一个对象数组，每条记录包含以下字段：

```json
[
  {
    "type": 1,
    "pcontent": "五句话。",
    "hint": "猜一句成语",
    "answer": "三言两语",
    "param": "0"
  }
]
```

| 字段 | 类型 | 说明 |
|------|------|------|
| `type` | number | 唯一编号（用于列表显示与定位） |
| `pcontent` | string | 题目内容 |
| `hint` | string | 提示（如「猜一句成语」「打一动物」） |
| `answer` | string | 答案 |
| `param` | string | 预留字段，当前未使用 |

### 添加新灯谜

直接在 `riddleConfig.json` 数组末尾追加一条，保证 `type` 不重复即可：

```json
{
  "type": 312,
  "pcontent": "你的新题目",
  "hint": "猜一字",
  "answer": "谜底",
  "param": "0"
}
```

刷新页面即生效。

---

## 🎨 自定义

### 修改标题 / 版本号

编辑 `index.html`：

```html
<h1 class="page-title"><span class="lantern">🏮</span>灯谜答案查询器</h1>
<span class="version-badge">v260927</span>
```

### 修改底部链接

```html
<footer class="page-footer">
  <a href="https://laowaigua.github.io" target="_blank" rel="noopener">laowaigua.github.io</a>
</footer>
```

### 修改主题色

编辑 `<style>` 顶部的 CSS 变量：

```css
:root {
  --primary: #0066cc;    /* 主色：按钮、答案高亮 */
  --accent: #c0392b;     /* 强调色 */
  --bg: #f5f7fa;         /* 背景色 */
}
```

### 更换 Favicon

目前使用内嵌的 🏮 emoji SVG，如需换成图片：

```html
<link rel="icon" href="favicon.ico" sizes="any">
```

然后把 `favicon.ico` 放到根目录即可（PNG 转 ICO 可用 [favicon.io](https://favicon.io)）。

---

## 🛠️ 技术栈

- **HTML5 + CSS3 + 原生 JavaScript**，无任何框架 / 构建工具
- **CSS 变量**做主题管理
- **`table-layout: fixed` + `text-overflow: ellipsis`** 实现单行不换行
- **`position: sticky`** 实现表头吸顶
- **`navigator.clipboard`** 复制，兼容回退到 `execCommand`
- **`DocumentFragment`** 批量渲染，避免频繁回流

---

## 📌 版本历史

| 版本 | 日期 | 说明 |
|------|------|------|
| `v260927` | 2026-09-27 | 顶部标题、版本号、页脚；标题与统计改为「灯谜」 |
| — | — | 初版：查询、搜索、复制功能 |

---

## 📄 License

MIT License — 可自由使用、修改、分发。

---

## 🙏 致谢

谜语数据整理自公开网络资源，仅供学习娱乐使用。
