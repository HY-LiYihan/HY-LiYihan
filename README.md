# Your Project

> 面向复杂场景的自主导航与操作系统

## 快速开始

```bash
git clone https://github.com/your-org/your-project.git
cd your-project
docker compose up dev
```

详细文档见 👉 [docs/](docs/)

## 项目结构

```
your-project/
├── docs/              ← 项目文档站点（GitHub Pages）
├── src/               ← 源代码
├── config/            ← 配置文件
├── launch/            ← 启动文件
└── README.md
```

## 文档

文档网站位于 `docs/` 目录，使用 GitHub Pages 部署。

本地预览：
```bash
cd docs && python3 -m http.server 8000
```

## License

MIT
