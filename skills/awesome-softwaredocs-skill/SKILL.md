---
name: awesome-softwaredocs-skill
description: 帮助零基础用户生成专业软件工程文档和UML图表（触发词：生成文档、软件开发、一步步做、一步到位、做个软件、开发App、构建软件、软件工程）
version: 1.1.0
---

# awesome-softwaredocs-skill

专业的软件工程文档生成技能，帮助零基础用户生成符合工业标准的软件工程文档和UML图表。

## 技能启动

当用户触发此技能时，**首先必须询问用户界面语言偏好**，然后根据用户选择进入对应的工作流程。

### 第一步：语言选择（必须）

```
您好！欢迎使用 awesome-softwaredocs-skill！

请选择您希望使用的语言 / Please select your preferred language:
1. 中文 (Chinese)
2. English

请输入数字 1 或 2：
```

- 如果用户选择 `1` 或 `中文`，后续所有交互使用**中文**
- 如果用户选择 `2` 或 `English`，后续所有交互使用**英文**

### 第二步：工作模式选择

根据用户选择的语言，显示对应的工作模式选项：

**中文：**
```
【语言已设置为中文】

现在请选择工作模式：

模式一：一步步走模式
  - 每个阶段完成后才进入下一阶段
  - 共7个阶段：立项 → 需求 → 概要设计 → 详细设计 → 单元测试 → 系统测试 → 部署

模式二：一步到位模式
  - 适合快速启动
  - 一次性生成完整项目结构和所有文档

请输入 "1" 选择一步步走模式，或 "2" 选择一步到位模式：
```

**English：**
```
【Language set to English】

Now please select your work mode:

Mode 1: Step-by-Step Mode
  - Complete each phase before moving to the next
  - 7 phases: Project Initiation → Requirements → Architecture Design → Detailed Design → Unit Testing → System Testing → Deployment

Mode 2: One-Click Mode
  - Suitable for quick start
  - Generate complete project structure and all documents at once

Please enter "1" for Step-by-Step Mode, or "2" for One-Click Mode:
```

---

## 模式一：一步步走模式 (Step-by-Step Mode)

### 阶段流程

**中文版本：**

| 阶段 | 名称 | 产出物 |
|------|------|--------|
| 阶段1 | 项目立项 | `docs/PP.md` (项目计划)、`docs/0-立项报告.md` |
| 阶段2 | 需求分析 | `docs/SRS.md` (需求规格说明书)、`diagrams/用例图.md` |
| 阶段3 | 概要设计 | `docs/SDS.md` (软件设计说明书)、`diagrams/架构图.md` |
| 阶段4 | 详细设计 | `docs/DD.md` (数据库设计)、`docs/ID.md` (接口设计)、`diagrams/类图.md`、`diagrams/序列图.md` |
| 阶段5 | 单元测试 | `docs/TP.md` (测试计划) |
| 阶段6 | 系统测试 | `docs/TR.md` (测试报告) |
| 阶段7 | 部署运维 | `docs/UM.md` (用户手册)、部署文档 |

**English version:**

| Phase | Name | Outputs |
|-------|------|---------|
| Phase 1 | Project Initiation | `docs/PP.md` (Project Plan), `docs/0-Project-Charter.md` |
| Phase 2 | Requirements Analysis | `docs/SRS.md` (Software Requirements Specification), `diagrams/Use-Case-Diagram.md` |
| Phase 3 | Architecture Design | `docs/SDS.md` (Software Design Specification), `diagrams/Architecture-Diagram.md` |
| Phase 4 | Detailed Design | `docs/DD.md` (Database Design), `docs/ID.md` (Interface Design), `diagrams/Class-Diagram.md`, `diagrams/Sequence-Diagram.md` |
| Phase 5 | Unit Testing | `docs/TP.md` (Test Plan) |
| Phase 6 | System Testing | `docs/TR.md` (Test Report) |
| Phase 7 | Deployment | `docs/UM.md` (User Manual), Deployment documentation |

### 阶段交互示例

**中文版本：**
```
【阶段1：项目立项】

欢迎进入项目立项阶段！请提供以下信息：

1. 项目名称：（例如：学生成绩管理系统）
2. 项目背景：（例如：学校需要管理学生成绩）
3. 项目目标：（例如：实现成绩的录入、查询、统计、分析）
4. 预期用户：（例如：教师、教务管理员、学生）
5. 项目周期：（例如：3个月）

请按顺序回答以上问题，完成后我将为您生成项目计划文档。
```

**English version:**
```
【Phase 1: Project Initiation】

Welcome to the Project Initiation phase! Please provide the following information:

1. Project Name: (e.g., Student Grade Management System)
2. Project Background: (e.g., School needs to manage student grades)
3. Project Objectives: (e.g., Implement grade entry, query, statistics, and analysis)
4. Expected Users: (e.g., Teachers, Academic Administrators, Students)
5. Project Duration: (e.g., 3 months)

Please answer the questions above in order. After completion, I will generate the project plan document for you.
```

---

## 模式二：一步到位模式 (One-Click Mode)

### 交互流程

**中文版本：**
```
【一步到位模式】

请提供以下基本信息来完成文档生成：

1. 项目名称：（例如：图书管理系统）
2. 项目类型：（Web / 桌面应用 / 移动应用 / 命令行工具）
3. 核心功能描述：（例如：图书的增删改查、用户管理、借阅管理）

示例输入：
图书管理系统, Web, 图书增删改查和用户管理

请输入您的项目信息：
```

**English version:**
```
【One-Click Mode】

Please provide the following basic information to generate documents:

1. Project Name: (e.g., Library Management System)
2. Project Type: (Web / Desktop / Mobile / CLI)
3. Core Features: (e.g., Book CRUD, User Management, Borrowing Management)

Example input:
Library Management System, Web, Book CRUD and User Management

Please enter your project information:
```

---

## 项目结构

生成的项目结构如下：

```
[项目名称]/
├── docs/                          # 软件工程文档 / Software Engineering Documents
│   ├── 0-项目概述.md              # 项目概述 / Project Overview
│   ├── 1-需求规格说明书.md         # SRS (中文版)
│   ├── 1-Software-Requirements-Specification.md  # SRS (English)
│   ├── 2-软件设计说明书.md         # SDS (中文版)
│   ├── 2-Software-Design-Specification.md        # SDS (English)
│   ├── 3-数据库设计说明书.md       # DD (中文版)
│   ├── 3-Database-Design-Specification.md         # DD (English)
│   ├── 4-接口设计说明书.md         # ID (中文版)
│   ├── 4-Interface-Design-Specification.md       # ID (English)
│   ├── 5-测试计划说明书.md         # TP (中文版)
│   ├── 5-Test-Plan-Specification.md              # TP (English)
│   ├── 6-测试报告.md              # TR (中文版)
│   ├── 6-Test-Report.md                        # TR (English)
│   ├── 7-用户手册.md              # UM (中文版)
│   ├── 7-User-Manual.md                        # UM (English)
│   ├── 8-项目计划.md              # PP (中文版)
│   ├── 8-Project-Plan.md                       # PP (English)
│   └── 9-配置管理计划.md          # CMP (中文版)
│   └── 9-Configuration-Management-Plan.md     # CMP (English)
├── diagrams/                       # UML图表 / UML Diagrams (Mermaid)
│   ├── 用例图模板.md              # Use Case Diagram (Chinese)
│   ├── 1-Use-Case-Diagram-Template.md        # Use Case Diagram (English)
│   ├── 类图模板.md                # Class Diagram (Chinese)
│   ├── 2-Class-Diagram-Template.md           # Class Diagram (English)
│   ├── 序列图模板.md              # Sequence Diagram (Chinese)
│   ├── 3-Sequence-Diagram-Template.md        # Sequence Diagram (English)
│   ├── 活动图模板.md              # Activity Diagram (Chinese)
│   ├── 4-Activity-Diagram-Template.md        # Activity Diagram (English)
│   ├── 状态图模板.md              # State Diagram (Chinese)
│   ├── 5-State-Diagram-Template.md           # State Diagram (English)
│   ├── 组件图和部署图模板.md      # Component Diagram (Chinese)
│   └── 6-Component-and-Deployment-Diagram-Template.md       # Component Diagram (English)
└── README.md
```

---

## 文档语言规则

### 重要规则

1. **语言选择是第一优先级** - 技能启动后必须首先询问语言
2. **所有输出使用同一语言** - 一旦确定语言，所有后续交互必须使用该语言
3. **文档模板成对生成** - 每个中文文档都有对应的英文版本
4. **模板引用根据语言选择** - 根据用户选择的语言，使用对应语言版本的模板

### 模板文件对应关系

| 中文模板 | 英文模板 |
|---------|---------|
| `1-需求规格说明书.md` | `1-Software-Requirements-Specification.md` |
| `2-软件设计说明书.md` | `2-Software-Design-Specification.md` |
| `3-数据库设计说明书.md` | `3-Database-Design-Specification.md` |
| `4-接口设计说明书.md` | `4-Interface-Design-Specification.md` |
| `5-测试计划说明书.md` | `5-Test-Plan-Specification.md` |
| `6-测试报告.md` | `6-Test-Report.md` |
| `7-用户手册.md` | `7-User-Manual.md` |
| `8-项目计划.md` | `8-Project-Plan.md` |
| `9-配置管理计划.md` | `9-Configuration-Management-Plan.md` |

---

## UML图表支持

使用 Mermaid 语法生成以下图表：

| 图表类型 | 中文模板 | 英文模板 |
|---------|---------|---------|
| 用例图 | `用例图模板.md` | `1-Use-Case-Diagram-Template.md` |
| 类图 | `类图模板.md` | `2-Class-Diagram-Template.md` |
| 序列图 | `序列图模板.md` | `3-Sequence-Diagram-Template.md` |
| 活动图 | `活动图模板.md` | `4-Activity-Diagram-Template.md` |
| 状态图 | `状态图模板.md` | `5-State-Diagram-Template.md` |
| 组件图/部署图 | `组件图和部署图模板.md` | `6-Component-and-Deployment-Diagram-Template.md` |

---

## 与用户交互原则

1. **语言优先** - 每次启动首先确认语言
2. **循序渐进** - 在一步步走模式中，每完成一个阶段才进入下一阶段
3. **解释清晰** - 用用户选择的语言通俗易懂地解释专业术语
4. **引导思考** - 不直接给出答案，而是通过提问引导用户思考
5. **即时反馈** - 每个阶段完成后展示产出物，确认后再继续
6. **灵活适应** - 根据用户的具体需求调整文档和代码模板
7. **主动保存** - 每个阶段完成后，主动告知用户当前进度已保存，可随时中断

---

## 技能执行流程

当技能被触发时，AI 应按以下步骤执行：

### 标准执行步骤

```
1. 解析用户输入
   ├── 识别项目名称
   ├── 识别项目类型（Web/桌面/移动/CLI）
   ├── 识别核心功能需求
   └── 识别技术栈偏好

2. 选择模板
   ├── 根据语言选择 zh/ 或 en/
   ├── 根据文档类型选择对应模板
   └── 读取模板文件内容

3. 填充变量
   ├── 替换 {{projectName}} 为实际项目名称
   ├── 替换 {{projectCode}} 为项目代号（大写，无空格）
   ├── 替换 {{createdDate}} 为当前日期（YYYY-MM-DD）
   ├── 替换 {{author}} 为用户指定作者名
   └── 保留 [instruction] 格式的占位符，供用户自行填写

4. 生成输出
   ├── 创建目标目录结构
   ├── 将填充后的内容写入目标文件
   └── 向用户展示生成结果摘要

5. 保存进度（如适用）
   └── 更新 docs/.progress.json
```

### 变量替换规则

| 变量 | 替换规则 | 示例 |
|------|---------|------|
| `{{projectName}}` | 直接替换，无空格处理 | 学生成绩管理系统 |
| `{{projectCode}}` | 转大写，空格变下划线 | STUDENT_GRADE_SYSTEM |
| `{{createdDate}}` | 格式：YYYY-MM-DD | 2026-04-09 |
| `{{author}}` | 用户输入的作者名 | 张三 |
| `[xxx]` | 保留，作为用户填写指导 | [填写日期] |

### 错误处理

| 错误场景 | 处理方式 |
|---------|---------|
| 模板文件不存在 | 提示用户模板缺失，返回错误信息 |
| 变量缺失 | 使用空字符串替换，继续生成 |
| 目录创建失败 | 提示权限问题，建议手动创建 |
| 文件写入失败 | 提示写入错误，展示可复制的内容 |

### 文件生成位置

```
[用户指定目录]/
├── docs/                              # 文档目录
│   ├── 1-需求规格说明书.md            # 或 1-Software-Requirements-Specification.md
│   ├── 2-软件设计说明书.md
│   └── ...
└── diagrams/                          # 图表目录（可选）
    ├── 用例图.md
    └── ...
```

---

### 常见输入错误处理

| 错误场景 | 处理方式 |
|---------|---------|
| 输入无效选项 | 提示有效选项范围，邀请重新输入 |
| 信息不完整 | 列出已提供/缺失信息，请补充缺失项 |
| 语言选择模糊 | 友好提示"请输入 1 或 2"，不强制中断 |
| 跳过必填项 | 温和提醒这是必填项，不允许留空 |

### 错误提示示例

**中文版本：**
```
【输入无效】

您输入的选项 "X" 不在有效范围内（1 或 2）。

请重新输入：
1. 中文 (Chinese)
2. English

请输入数字 1 或 2：
```

**English version:**
```
【Invalid Input】

Your input "X" is not within the valid range (1 or 2).

Please try again:
1. Chinese
2. English

Please enter 1 or 2:
```

### 中断与恢复

当用户中断后再次启动技能：
1. 首先询问是否恢复之前的项目
2. 如果用户确认，读取 `docs/.progress.json` 恢复进度
3. 如果用户选择新项目，清除旧进度并重新开始

### 进度持久化文件

```
[项目名称]/docs/.progress.json    # 保存当前阶段和用户输入摘要
```

进度文件格式：
```json
{
  "projectName": "项目名称",
  "currentPhase": 3,
  "language": "zh",
  "mode": "step-by-step",
  "savedAt": "2026-04-09T10:30:00Z",
  "userInputs": {
    "phase1": { ... },
    "phase2": { ... }
  }
}
```

---

---

## 文档标准

所有文档模板基于以下标准：

- GB/T 8566-2007 《软件生存周期过程》
- GB/T 9385-2008 《计算机软件需求规格说明规范》
- GB/T 8567-2006 《计算机软件设计说明规范》
- ISO/IEC 25010 软件质量模型

---

## 模板文件路径

技能使用预定义的文档模板，路径如下：

| 文档类型 | 中文模板 | 英文模板 |
|---------|---------|---------|
| 需求规格说明书 | `templates/zh/docs/1-需求规格说明书.md` | `templates/en/docs/1-Software-Requirements-Specification.md` |
| 软件设计说明书 | `templates/zh/docs/2-软件设计说明书.md` | `templates/en/docs/2-Software-Design-Specification.md` |
| 数据库设计说明书 | `templates/zh/docs/3-数据库设计说明书.md` | `templates/en/docs/3-Database-Design-Specification.md` |
| 接口设计说明书 | `templates/zh/docs/4-接口设计说明书.md` | `templates/en/docs/4-Interface-Design-Specification.md` |
| 测试计划说明书 | `templates/zh/docs/5-测试计划说明书.md` | `templates/en/docs/5-Test-Plan-Specification.md` |
| 测试报告 | `templates/zh/docs/6-测试报告.md` | `templates/en/docs/6-Test-Report.md` |
| 用户手册 | `templates/zh/docs/7-用户手册.md` | `templates/en/docs/7-User-Manual.md` |
| 项目计划 | `templates/zh/docs/8-项目计划.md` | `templates/en/docs/8-Project-Plan.md` |
| 配置管理计划 | `templates/zh/docs/9-配置管理计划.md` | `templates/en/docs/9-Configuration-Management-Plan.md` |

### UML图表模板

| 图表类型 | 中文模板 | 英文模板 |
|---------|---------|---------|
| 用例图 | `templates/zh/uml-diagrams/用例图模板.md` | `templates/en/uml-diagrams/1-Use-Case-Diagram-Template.md` |
| 类图 | `templates/zh/uml-diagrams/类图模板.md` | `templates/en/uml-diagrams/2-Class-Diagram-Template.md` |
| 序列图 | `templates/zh/uml-diagrams/序列图模板.md` | `templates/en/uml-diagrams/3-Sequence-Diagram-Template.md` |
| 活动图 | `templates/zh/uml-diagrams/活动图模板.md` | `templates/en/uml-diagrams/4-Activity-Diagram-Template.md` |
| 状态图 | `templates/zh/uml-diagrams/状态图模板.md` | `templates/en/uml-diagrams/5-State-Diagram-Template.md` |
| 组件图/部署图 | `templates/zh/uml-diagrams/组件图和部署图模板.md` | `templates/en/uml-diagrams/6-Component-and-Deployment-Diagram-Template.md` |

生成文档时，将模板内容中的 `{{变量名}}` 替换为用户提供的实际信息。

### 模板变量说明

| 变量名 | 说明 | 示例 |
|--------|------|------|
| `{{projectName}}` | 项目名称 | 学生成绩管理系统 |
| `{{createdDate}}` | 创建日期 | 2026-04-09 |
| `{{description}}` | 功能描述 | 实现成绩的录入、查询 |
| `{{priority}}` | 优先级 | 高/中/低 |
