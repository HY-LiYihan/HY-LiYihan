# 仓库说明

这个仓库是李溢涵 / Yihan Li 的个人公开资料仓库，主要承担三个相关但不同的职责：

1. 作为 GitHub 个人主页的首页内容来源。
2. 维护个人 GitHub Pages / GitHub.io 网站。
3. 长期保存不同版本的 CV，尤其是 LaTeX 格式的可维护版本。

顶层 `README.md` 会被 GitHub 直接展示为账号首页，因此它只用于 GitHub 首页展示，不作为本仓库的完整说明文档。本文件用于记录仓库的整体定位、内容边界和后续维护约定。

## 仓库定位

这个仓库不是传统意义上的代码项目仓库，也不是某一个论文或工程项目的源码仓库。它更接近一个个人学术与工程履历的中心仓库，用来统一维护：

- GitHub 首页展示内容。
- 个人网站内容。
- 论文、项目、研究方向和奖项信息。
- 中文、英文、学术版、工业版等不同 CV。
- 未来可能需要公开下载的简历 PDF、论文链接和展示资产。

整体目标是让外部访问者可以快速理解个人背景，同时让自己在长期维护时有清晰的文件结构和更新规则。

## GitHub 首页

顶层 `README.md` 是 GitHub 账号首页，应保持简洁、公开、精炼。

建议用途：

- 简短个人介绍。
- 核心研究方向。
- 代表论文或项目。
- GitHub.io 网站、邮箱和其他公开链接。

不建议放入：

- 仓库内部维护说明。
- 文件结构说明。
- 详细 CV 管理规则。
- 临时草稿、TODO 或未整理资产说明。

换句话说，`README.md` 是给访客看的首页，不是给自己看的仓库手册。

## 个人网站

`docs/` 目录用于维护个人 GitHub Pages 网站。当前仓库使用 Jekyll，并通过 GitHub Actions 从 `docs/` 构建和部署。

建议用途：

- 更完整的中英文个人介绍。
- Publications 页面。
- Projects 页面。
- News / Timeline 更新。
- CV 下载入口。
- 个人照片、项目图片、论文链接等公开展示资产。

GitHub 首页应当是一个轻量入口，而 GitHub.io 网站应当是更完整、更正式、更可扩展的个人主页。

## CV 管理

这个仓库后续应当保存不同版本的 CV。长期维护时，建议以 LaTeX 源文件为主，PDF 作为导出结果保存。

推荐未来结构：

```text
cv/
  README.md
  academic/
    en/
      main.tex
      Yihan_Li_Academic_CV_EN.pdf
    zh/
      main.tex
      Li_Yihan_Academic_CV_ZH.pdf
  industry/
    en/
      main.tex
      Yihan_Li_Industry_CV_EN.pdf
    zh/
      main.tex
      Li_Yihan_Industry_CV_ZH.pdf
  short/
    en/
      main.tex
      Yihan_Li_Short_CV_EN.pdf
    zh/
      main.tex
      Li_Yihan_Short_CV_ZH.pdf
  application-specific/
    README.md
```

建议维护的 CV 类型：

- `academic`：面向导师、实验室、博士申请、科研机会的学术 CV。
- `industry`：面向企业实习、工程岗位、技术岗位的工业简历。
- `short`：一页版或短版简历。
- `application-specific`：针对特定项目、奖学金、会议、申请场景定制的版本。

LaTeX 源文件是主要维护对象。PDF 只有在需要被网站下载、发送给他人、或记录某个稳定版本时才应保留。

## 当前结构

当前仓库的大致结构如下：

```text
.
├── README.md                 # GitHub 个人首页，不用于仓库说明
├── REPOSITORY.md             # 当前文件，记录仓库定位和维护约定
├── docs/                     # GitHub Pages / Jekyll 网站源码
│   ├── _config.yml
│   ├── _data/navigation.yml
│   ├── _layouts/default.html
│   ├── index.md
│   ├── publications.md
│   ├── projects.md
│   ├── Chinese_CV.md
│   └── English_CV.md
└── .github/workflows/        # GitHub Pages 自动部署 workflow
```

当前仓库根目录中还存在一些 CV、论文 PDF 和图片类资产。后续建议逐步整理到更稳定的目录中，例如：

- `cv/`：LaTeX CV 源文件和稳定导出的 PDF。
- `docs/assets/`：个人网站需要公开引用的图片、PDF 和其他静态资源。
- `papers/`：如果需要保存论文草稿或公开版本，可单独建立论文目录。

## 维护原则

- 不修改 `README.md` 的职责：它只作为 GitHub 首页。
- 仓库级说明放在 `REPOSITORY.md` 或未来的专门文档中。
- 网站源码统一放在 `docs/`。
- CV 优先维护 LaTeX 源文件，PDF 作为导出版本。
- 公开下载的文件应使用稳定命名，避免网站链接失效。
- 临时草稿、论文 PDF、图片和 CV 副本不要长期散落在仓库根目录。
- 重要公开信息应尽量在 GitHub 首页、个人网站和 CV 之间保持一致。

## 建议下一步

1. 新建 `cv/` 目录，放置 LaTeX 格式的 CV 源文件。
2. 将现有 Markdown CV 逐步迁移或重写为 LaTeX 版本。
3. 在 `docs/assets/` 中放置网站需要引用的正式 CV PDF。
4. 更新网站中的 CV 链接，使其指向稳定的 PDF 路径。
5. 将根目录中的论文 PDF、图片和临时文件整理到专门目录。
6. 保持顶层 `README.md` 精炼，用作 GitHub 账号首页。
