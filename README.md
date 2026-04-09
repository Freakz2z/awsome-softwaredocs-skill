<div align="center">

# awsome-softwaredocs-skill

**专业的软件工程技能** — 从零开始构建符合工业标准的软件项目

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![UML 2.5](https://img.shields.io/badge/UML-2.5-green)]()

[简体中文](README.md)｜[English](README_EN.md)

*适用于 Claude Code · 支持中英文 · 9份专业文档 · 6种UML图表*

</div>

---

## 为什么使用 awsome-softwaredocs-skill？

| 场景 | 没有它 | 使用它 |
|------|--------|--------|
| **学习软件工程** | 理论枯燥、难以实践 | 边做边学，文档即教材 |
| **毕业设计** | 不知从何入手 | 完整模板，快速启动 |
| **团队项目** | 文档不规范、不完整 | 工业级标准文档一键生成 |
| **接外包项目** | 客户要文档不会写 | 专业模板，高效交付 |

## 两种工作模式

```
┌─────────────────────────────────────────────────────────────┐
│  模式一：一步步走模式 (学习场景)                               │
│  ─────────────────────────────────────────────               │
│  阶段1 项目立项 → 阶段2 需求分析 → 阶段3 概要设计              │
│  → 阶段4 详细设计 → 阶段5 编码实现 → 阶段6 单元测试            │
│  → 阶段7 系统测试 → 阶段8 部署运维                           │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  模式二：一步到位模式 (快速启动)                               │
│  ─────────────────────────────────────────────               │
│  你提供：项目名称 + 类型 + 核心功能                             │
│  自动生成：完整项目结构 + 全部文档 + 可运行代码框架             │
└─────────────────────────────────────────────────────────────┘
```

## 安装方式

### 方式一：从源码安装

```bash
# 克隆仓库
git clone https://github.com/Freakz2z/awsome-softwaredocs-skill.git

# 安装技能
mkdir -p ~/.claude/skills
cp -r awsome-softwaredocs-skill/skills/awsome-softwaredocs-skill ~/.claude/skills/
```

### 方式二：从插件市场安装

```bash
# 1. 添加插件市场
/plugin marketplace add https://github.com/Freakz2z/awsome-softwaredocs-skill

# 2. 安装技能
/plugin install awsome-softwaredocs-skill@awsome-softwaredocs-market
```

## 使用方法

在 Claude Code 中直接对话：

```
用户: 帮我创建一个任务管理系统
用户: 使用一步到位模式
用户: 生成需求规格说明书
```

## 项目结构

```
awsome-softwaredocs-skill/
├── .claude-plugin/
│   ├── marketplace.json      # 市场配置
│   └── plugin.json           # 插件配置
├── skills/
│   └── awsome-softwaredocs-skill/
│       ├── SKILL.md          # 技能定义
│       └── templates/         # 模板目录
│           ├── zh/            # 中文模板
│           │   ├── docs/      # 9份文档模板
│           │   └── uml-diagrams/  # UML图表模板
│           └── en/           # 英文模板
│               ├── docs/
│               └── uml-diagrams/
├── README.md
├── README_EN.md
├── CONTRIBUTING.md
├── CONTRIBUTING_EN.md
├── LICENSE
└── .gitignore
```

## 核心功能

### 📄 软件工程文档 (9份)

| 文档 | 编号 |
|------|------|
| 需求规格说明书 | SRS |
| 软件设计说明书 | SDS |
| 数据库设计说明书 | DD |
| 接口设计说明书 | ID |
| 测试计划说明书 | TP |
| 测试报告 | TR |
| 用户手册 | UM |
| 项目计划 | PP |
| 配置管理计划 | CMP |

### 📊 UML 图表 (6种)

| 图表 | 适用场景 |
|------|----------|
| 用例图 | 系统功能建模 |
| 类图 | 面向对象设计 |
| 序列图 | 对象交互时序 |
| 活动图 | 业务流程 |
| 状态图 | 状态机设计 |
| 部署图 | 系统架构 |

### 💻 支持的技术栈

| 层级 | 技术选项 |
|------|----------|
| **后端** | Java Spring Boot, Python Django, Go Gin, Node.js Express |
| **前端** | React, Vue 3, 原生 HTML/JS |
| **数据库** | MySQL, PostgreSQL, MongoDB, Redis |

## 参考标准

| 标准 | 说明 |
|------|------|
| GB/T 8566-2007 | 软件生存周期过程 |
| GB/T 9385-2008 | 计算机软件需求规格说明规范 |
| GB/T 8567-2006 | 计算机软件设计说明规范 |
| ISO/IEC 25010 | 软件质量模型 |
| UML 2.5 | 统一建模语言规范 |

---

详细开发指南请参阅 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 许可证

MIT License · Copyright (c) 2026

## 如果有帮助，请给个 ⭐

如果你觉得 awsome-softwaredocs-skill 对你有帮助，欢迎给个 Star！
