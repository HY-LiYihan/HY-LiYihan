# GitHub Pages 部署指南

## 什么是 GitHub Pages？

GitHub Pages 是 GitHub 提供的**免费静态网站托管服务**。你把 HTML/CSS/JS 文件推送到仓库，GitHub 自动帮你发布成网站。

- 🆓 免费
- 🔒 支持 HTTPS
- 🌐 支持自定义域名
- 📦 每个仓库可以有一个 Pages 站点

---

## 方法一：最简单的方式（推荐新手）

### 1. 创建仓库

在 GitHub 上新建一个仓库，名字**必须是**：

```
你的用户名.github.io
```

例如你的用户名是 `liyihan-xyz`，仓库名就是 `liyihan-xyz.github.io`。

### 2. 推送代码

```bash
cd github_page_test
git init
git add .
git commit -m "init: GitHub Pages site"
git remote add origin https://github.com/liyihan-xyz/liyihan-xyz.github.io.git
git push -u origin main
```

### 3. 等待生效

推送后等 1-2 分钟，访问 `https://liyihan-xyz.github.io` 即可看到网站。

---

## 方法二：从仓库的 docs 目录发布（适合项目文档）

如果你不想用专门的仓库，也可以在任何仓库里开启 Pages：

### 1. 把网站文件放到 `docs/` 目录

```
your-project/
├── docs/              ← 网站文件放这里
│   ├── index.html
│   ├── projects.html
│   └── style.css
├── src/
└── README.md
```

### 2. 在 GitHub 开启 Pages

1. 打开仓库 → **Settings** → **Pages**
2. Source 选 **Deploy from a branch**
3. Branch 选 **main**，目录选 **/docs**
4. 点 **Save**

等 1-2 分钟生效，地址是 `https://你的用户名.github.io/仓库名/`

---

## 方法三：GitHub Actions 自动部署（最灵活）

适合需要构建步骤的项目（比如用 VitePress、MKDocs 等）。

在仓库里创建 `.github/workflows/pages.yml`：

```yaml
name: Deploy to Pages
on:
  push:
    branches: [main]
permissions:
  contents: read
  pages: write
  id-token: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: .
      - uses: actions/deploy-pages@v4
```

然后在 Settings → Pages → Source 选 **GitHub Actions**。

---

## 自定义域名

1. 在仓库根目录创建 `CNAME` 文件，写入你的域名：
   ```
   docs.liyihan.xyz
   ```
2. 在域名 DNS 设置中添加 CNAME 记录指向 `liyihan-xyz.github.io`
3. GitHub 会自动配置 HTTPS 证书

---

## 本项目结构说明

```
github_page_test/
├── index.html              ← 首页
├── projects.html           ← 项目列表
├── about.html              ← 关于页面
├── style.css               ← 全局样式
└── projects/               ← 项目文档子页面
    ├── rmul-rl.html        ← RMUL 强化学习
    ├── vision-nav.html     ← 视觉导航
    └── uav.html            ← 无人机项目
```

## 本地预览

```bash
# 方法一：Python 内置服务器
python3 -m http.server 8000
# 打开 http://localhost:8000

# 方法二：npx
npx serve .
```

## 小贴士

- GitHub Pages 只支持**静态网站**（HTML/CSS/JS），不支持服务端代码
- 每次推送后等 1-2 分钟才能看到更新
- 如果样式没更新，可能是浏览器缓存，试试 Ctrl+Shift+R 强刷
- 想用 Markdown 写文档的话，可以考虑 **VitePress** 或 **MKDocs**，它们会生成静态 HTML 再部署
