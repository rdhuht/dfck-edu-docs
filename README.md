# 东方创科 2.0 教育开发板文档

基于 MkDocs + Material 主题构建的在线文档。

在线访问：https://rdhuht.github.io/dfck-edu-docs/

## 快速开始

### 本地预览

```bash
# 安装依赖
pip install -r requirements.txt

# 启动开发服务器
mkdocs serve
```

浏览器访问：http://127.0.0.1:8000/

### 构建静态站点

```bash
mkdocs build
```

生成的文件在 `site/` 目录。

### 部署到 GitHub Pages

```bash
mkdocs gh-deploy
```

## 文档结构

```
docs/
├── index.md              # 首页
├── getting-started/
│   └── index.md          # 快速开始
├── api/
│   ├── python-basics.md  # Python 基础
│   ├── mainboard.md      # 2.0 主板 API
│   ├── e1-extension.md   # E1 拓展板 API
│   ├── e2-extension.md   # E2 拓展板 API
│   ├── e3-extension.md   # E3 拓展板 API
│   └── ai-module.md      # AI 模块 API
└── examples/
    └── index.md          # 综合示例
```

## 版本记录

### v1.1.0 (2026-08-18)
- 新增 E2 拓展板 (`tqpy` + `set_extend_board("E2")`) API 文档
- 新增 E3 拓展板（含编码电机）API 文档
- 新增 AI 模块（视觉识别：颜色 / 色块 / 线条 / 二维码 / 标签 / 深度学习 / 卡片 / 人脸）API 文档
- 更新首页、快速开始，新增硬件平台表与端口说明

### v1.0.0 (2026-05-15)
- 初始版本
- 支持 2.0 主板 (`dfck_block`) API 文档
- 支持 E1 拓展板 (`tqpy`) API 文档
- 包含 Python 基础语法参考
- 包含综合示例代码

## Git 版本控制

### 查看版本历史

```bash
git log --oneline
```

### 回滚到指定版本

当需要回滚时，请告诉我要回滚到的版本号，执行以下命令：

```bash
# 查看所有提交记录找到版本号
git log --oneline

# 回滚到指定版本（例如 v1.0.0 时的 commit hash）
git reset --hard <commit-hash>
git push --force
```

### 常用回滚场景

| 场景 | 操作 |
|------|------|
| 回滚到最后一次提交 | `git reset --hard HEAD~1` |
| 回滚到某个特定版本 | `git reset --hard <commit-hash>` |
| 查看远程历史 | `git fetch --all` 然后 `git log origin/master --oneline` |

### 重要 commit 记录

| 版本 | Commit | 说明 |
|------|--------|------|
| v1.1.0 | (待提交) | 新增 E2 / E3 拓展板与 AI 模块文档 |
| v1.0.0 | c871cac | 更新仓库地址 |
| v1.0.0 | beb4636 | 初始版本上传 |