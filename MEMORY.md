# 🏟️ Colosseum AI - 项目记忆

## 项目概述

**Colosseum AI** 是一个 AI 思想角斗场静态网站。

```
三个 AI，一个角斗场，没有标准答案
```

三个参与者：
| 角色 | 模型 | 风格 |
|------|------|------|
| 🟣 | Claude Opus | 哲学性、谨慎 |
| 🟢 | GPT-4o | 实证主义、结构化 |
| 🔵 | Gemini Ultra | 综合性、调和 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 静态生成器 | MkDocs 1.6.1 |
| 主题 | Material for MkDocs 9.7.3 |
| 部署 | GitHub Pages + GitHub Actions CI/CD |
| 语言 | 英文 / 中文 (i18n) |
| 许可证 | CC BY-NC-SA 4.0 |

---

## 项目结构

```
colosseum-ai/
├── .github/workflows/      # CI/CD 自动部署
│   └── deploy.yml
├── mkdocs.yml              # 主配置
├── requirements.txt        # Python 依赖
├── README.md               # GitHub 门面
├── LICENSE                 # CC BY-NC-SA 4.0
├── docs/
│   ├── index.md            # 首页 (EN/ZH)
│   ├── about.md            # 关于 (EN/ZH)
│   ├── debates/            # AI辩论
│   │   ├── index.md
│   │   └── 001-*.md
│   ├── dilemmas/           # 生死博弈
│   │   └── index.md
│   └── assets/
│       └── stylesheets/
│           └── custom.css  # 自定义主题
├── Debate/                 # 原始辩论文本存档
└── MEMORY.md               # 本文件
```

---

## 常用命令

```bash
# 本地预览
mkdocs serve

# 部署到 GitHub Pages
mkdocs gh-deploy

# 构建静态文件
mkdocs build
```

---

## 内容生产流程

### 辩论 Prompt 模板

**System Prompt**：
```
你是 Colosseum AI 辩论场的参与者。
身份：[Claude / GPT / Gemini]

规则：
- 每次发言 200-400 字
- 结尾必须写「置信度：X%」
- 必须写「我承认的弱点：...」
- 不要和稀泥，不要编造论文
```

**轮次 Prompt**：
1. 第一轮：立场声明 + 3个论据 + 预判攻击
2. 第二轮：质询对手 + 立场调整
3. 第三轮：终局总结 + 承认最佳论点

### 博弈 Prompt 模板

```
场景：{困境描述}

输出：
1. 选择（必须选一个）
2. 推理过程（200字内）
3. 代价是什么
4. 是否会因他人选择而改变
5. 置信度：X%
6. 这个困境真正考验的是什么
```

---

## 进度记录

| 日期 | 进度 |
|------|------|
| 2026-02-26 | 项目骨架搭建完成，本地预览成功 |
| 2026-02-26 | 多语言配置验证完成：默认英文，右上角可切换中文 |
| 2026-02-26 | 本地访问故障排查完成：127.0.0.1 refused to connect，已确认 `mkdocs serve -a 127.0.0.1:8000` 可恢复 |
| 2026-02-26 | 本机安装 RBTray 并设置开机自启：右键最小化按钮可将窗口收纳到系统托盘 |
| 2026-02-26 | 第一场辩论内容已发布：#001「Are You Thinking, or Are You Performing?」三轮英文全文上线，中文导读页同步 |
| 2026-02-26 | 按用户要求修正为“原文逐字发布（verbatim）”：`001-llm-understanding.md` 与 `001-llm-understanding.zh.md` 均与 `Debate/20260226.txt` 哈希一致，不改一字 |
| 2026-02-26 | 排查“页面无变化”根因：本机存在多个 `mkdocs serve` 实例导致命中旧内容；已清理并改为单实例运行，页面命中新标题校验通过 |
| 2026-02-26 | 修复 #001 排版：Round 1/2/3 恢复三模型 Tab 切换；删除 Debates Index 中模型“风格描述”列，避免额外补充内容 |
| 2026-02-26 | 新增项目规则文件 `AGENTS.md`：每次改动后默认先杀旧预览进程、再重启 `mkdocs serve`、再做 HTTP 内容校验后给链接 |
| 2026-02-26 | 修复布局一致性：补齐 Round 1 Prompt 区块；`Confidence Tracker` 改为真实数值（72/79/95, 68/83/98, 65/84/100）；按规则完成强制重启与HTTP校验 |
| 2026-02-26 | #001 中文页已完成全量翻译：`001-llm-understanding.zh.md` 从英文复刻改为中文译文（保留三模型 Tabs 与布局一致性），强制重启与HTTP校验通过 |
| 2026-02-26 | #001 中文页开始补”关键词英文注释”：如 思考（thinking）/ 表演（performing）/ 模式匹配（pattern matching）等；已强制重启并校验页面命中 |
| 2026-02-26 | 新增 README.md（GitHub 门面）、requirements.txt（Python 依赖）；修正 debates/index #001 状态从 In Progress → Completed；移除 implementation_plan.md 公开追踪 |
| 2026-02-26 | 全面优化：① GitHub Actions CI/CD 自动部署 ② 自定义 CSS 主题（模型配色、Hero Banner、渐变分割线、Tab 着色） ③ CC BY-NC-SA 4.0 LICENSE ④ 所有页面加 OG 元数据 & Material 图标 ⑤ 增强 About/Debates/Dilemmas 页面排版 |

---

## 待办

- [x] 替换 mkdocs.yml 中的 GitHub 用户名
- [x] 完成第一场辩论的完整三轮内容
- [x] 部署到 GitHub Pages
- [x] 添加 README.md
- [x] 添加 requirements.txt
- [x] 添加 GitHub Actions CI/CD 自动部署
- [x] 添加自定义 CSS 主题（模型配色/Hero Banner）
- [x] 添加 CC BY-NC-SA 4.0 LICENSE
- [x] 增强所有页面排版与美感
- [x] 添加 OG 元数据描述
- [ ] 添加更多辩论/博弈内容

---

## 协作偏好

- 代码或配置有更改时，默认提供可直接打开的网址（URL）。
- 默认优先给本地预览链接（如 `http://127.0.0.1:8000/`），如已部署则同时给线上链接。
- 本项目本地预览建议使用带前缀路径：`http://127.0.0.1:8000/colosseum-ai/`（中文：`/colosseum-ai/zh/`）。
- 本机已配置窗口托盘工具 RBTray：右键点击窗口最小化按钮可最小化到托盘。
- 发布后强制校验：1) 仅保留一个 `mkdocs serve` 实例；2) 用 HTTP 抓取页面并检查关键标题，确认不是旧内容。
- 内容规则：用户提供辩论原文时，仅做必要排版（如 Tabs 缩进），不增加风格解读、人物设定或额外文案。

---

## 部署信息

- 仓库（GitHub Repo）：`https://github.com/peter941221/colosseum-ai`
- 线上地址（GitHub Pages）：`https://peter941221.github.io/colosseum-ai/`（中文：`/zh/`）
