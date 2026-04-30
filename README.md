<div align="center">

# 🧩 Requirements Structuring

**把零散需求一键整理成可决策的结构化简报**

*A Codex skill for turning scattered requirements into a structured, decision-ready brief.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Codex Skill](https://img.shields.io/badge/Codex-Skill-000000?logo=openai&logoColor=white)](https://github.com/openai/codex)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/Friday-Up/requirements-structuring/pulls)
[![GitHub Stars](https://img.shields.io/github/stars/Friday-Up/requirements-structuring?style=social)](https://github.com/Friday-Up/requirements-structuring)

[简介](#-简介) • [适用场景](#-适用场景) • [输出结构](#-输出结构) • [快速开始](#-快速开始) • [使用方法](#-使用方法) • [示例](#-示例) • [设计原则](#-设计原则)

</div>

---

## 📖 简介

**Requirements Structuring** 是一个 [Codex](https://github.com/openai/codex) Skill，专为产品、研发和项目管理场景设计。它能把对话、会议纪要、零散需求或临时方案讨论，**快速整理成统一的六段式结构**，方便继续评估、确认和推进。

它的核心目标不是简单"复述需求"，而是：

- 🔍 **从零散信息里提炼真正的问题定义**
- 🧭 **区分已知事实、分析判断和待确认项**
- ⚠️ **暴露推进中的关键卡点和决策点**
- 📋 **输出一份可以继续沟通和拍板的结构化简报**

> 把"开了一小时会还不知道下一步干啥"变成"五分钟出一份能拍板的简报"。

---

## 🎯 适用场景

| 场景 | 痛点 | Skill 能做什么 |
| --- | --- | --- |
| 📝 **需求很散** | 多方反馈混在一起，没有统一理解 | 收敛成统一结构，统一认知起点 |
| 🗣️ **讨论模糊** | 边界、目标、方案都不清晰 | 区分事实/判断/待确认，暴露盲点 |
| 🎙️ **口头沟通** | 会议结束后只剩流水账 | 整理成可执行的结构化文档 |
| 🛠️ **设计/开发前** | 直接动手风险大 | 先做需求梳理 + 方案预评估 |
| 🤝 **跨角色协作** | 各方关注点不同，难对齐 | 把问题、价值和卡点说清楚 |

---

## 📑 输出结构

Skill 会严格按以下**六段式**结构输出，便于跨场景复用：

| 栏目 | 作用 |
| --- | --- |
| **1. 需求描述** | 归纳用户真正想解决的问题、目标结果和期望产出 |
| **2. 现状** | 总结当前背景、已有做法、限制条件和依赖关系（不混入方案） |
| **3. 需求评估** | 评估需求是否清晰、范围是否完整、是否存在歧义/风险 |
| **4. 待确认清单** | 列出必须进一步确认的问题，优先覆盖影响方案/边界/排期的部分 |
| **5. 方案说明** | 给出推荐方案或可选方案，说明思路、前提、影响范围和取舍 |
| **6. 【价值点】卡点&关键点** | 价值点（收益）+ 卡点（阻塞）+ 关键点（优先拍板项） |

---

## 🚀 快速开始

### 前置依赖

- [Codex CLI](https://github.com/openai/codex) 已安装并完成登录

### 安装

把仓库放到 Codex 的 `skills` 目录下即可：

```bash
git clone https://github.com/Friday-Up/requirements-structuring.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/requirements-structuring"
```

如果目录已存在，可直接更新：

```bash
git -C "${CODEX_HOME:-$HOME/.codex}/skills/requirements-structuring" pull
```

---

## 💬 使用方法

### 显式调用

```text
Use $requirements-structuring to turn the current conversation into a structured requirement brief.
```

### 自然语言触发

```text
请根据这段对话，整理成需求描述、现状、需求评估、待确认清单、方案说明、【价值点】卡点&关键点。
```

### 常用提示词模板

```text
请把下面的需求讨论整理成结构化简报，并明确哪些内容是待确认项。
```

```text
根据这次会议纪要，帮我拆成需求描述、现状、方案和关键卡点。
```

```text
不要只复述内容，帮我评估这个需求目前是否足够清晰，缺什么信息。
```

---

## 🧪 示例

<details open>
<summary><b>📥 输入</b></summary>

```text
我们想把异常工单页面改成更适合排查问题的形式，现在字段很多但重点不清楚。
希望先帮我梳理需求、现状和可选方案，再列出需要业务确认的问题。
```

</details>

<details open>
<summary><b>📤 输出</b></summary>

```markdown
### 需求描述
- 需要将异常工单页面从"字段展示导向"调整为"问题排查导向"，提升定位问题的效率。

### 现状
- 当前页面字段较多，但信息层级不清，重点不突出。
- 现有展示方式更偏向信息平铺，不利于按排查路径快速定位问题。

### 需求评估
- 目标方向明确，但缺少核心用户角色、主要排查场景和关键字段优先级等输入。
- 如果这些信息不先明确，页面改版容易停留在视觉调整，无法真正改善排查效率。

### 待确认清单
- 页面主要使用角色是谁。
- 用户最常见的排查路径是什么。
- 排查时最关键的 3 到 5 个字段是什么。
- 是否存在必须保留但低频使用的字段。

### 方案说明
- 推荐先基于排查路径重组页面信息分区，再决定字段取舍、默认展示顺序和交互方式。
- 如果信息层级暂时无法完全重构，可先做轻量方案：突出关键字段、折叠次要字段、增加状态分组。

### 【价值点】卡点&关键点
- 价值点：降低排查成本，提高问题定位效率和页面可用性。
- 卡点：缺少核心用户、典型场景和关键字段优先级输入。
- 关键点：先明确排查路径，再决定页面结构和字段编排。
```

</details>

---

## 🗂️ 仓库结构

```text
requirements-structuring/
├── SKILL.md              # 技能定义与执行规则（核心）
├── README.md             # 项目说明（你正在看的文件）
├── LICENSE               # MIT 协议
├── agents/
│   └── openai.yaml       # Codex 平台 UI 展示元数据
└── .gitignore
```

---

## 🧠 设计原则

这个技能遵循几个明确原则：

- ❌ **不把推断写成事实** —— 三类信息严格区分
- 🔍 **信息不足时显式列出缺口** —— 不要硬补
- 🎯 **输出重点是帮助决策和推进** —— 不是堆叠描述
- ⚡ **优先暴露影响方案选择的关键问题**
- 📐 **保持结构统一** —— 方便复用到不同需求场景

---

## ⚠️ 能力边界

这个技能擅长「梳理和评估」，**不直接替代**以下产物：

| ❌ 不替代 | 原因 |
| --- | --- |
| 完整 PRD 编写 | 缺少用户故事、详细流程、验收标准等环节 |
| 详细交互设计 | 不输出页面流、状态机、组件级规范 |
| 技术方案实现文档 | 不输出代码结构、接口契约、数据模型 |
| 项目排期拆解 | 不做 WBS、人力估算、依赖图 |

> 当输入信息严重不足时，输出会更偏向"结构化澄清清单"，**这是预期行为，不是能力缺失**。

---

## ❓ 常见问题

<details>
<summary><b>Q1：和直接让 LLM "总结需求" 有什么区别？</b></summary>

直接让 LLM 总结，输出风格因模型/提示词而异，常常变成"会议纪要复述"。这个 Skill 用固定六段结构 + 严格的事实/判断/待确认区分，输出的是**可推进的简报**，而不是流水账。
</details>

<details>
<summary><b>Q2：如果输入只有一两句话能用吗？</b></summary>

可以。信息不足时，Skill 会把 80% 的输出放在「待确认清单」里，相当于自动生成一份**结构化澄清问题集**，引导你补全上下文。
</details>

<details>
<summary><b>Q3：能定制输出栏目吗？</b></summary>

可以。直接编辑 [`SKILL.md`](./SKILL.md) 的「Standard Structure」与「Response Template」段，调整后立即生效。
</details>

<details>
<summary><b>Q4：支持其他 AI Agent 平台（Claude / Cursor / 通义）吗？</b></summary>

[`SKILL.md`](./SKILL.md) 本身是平台无关的提示词规范。其他平台只需把 SKILL.md 的内容作为系统提示词或 Skill 定义引入即可。
</details>

---

## 🤝 贡献

欢迎任何形式的贡献！

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/amazing-feature`
3. 提交变更：`git commit -m 'feat: add amazing feature'`
4. 推送分支：`git push origin feature/amazing-feature`
5. 提交 Pull Request

提交信息请遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范。

---

## 📜 License

本项目基于 [MIT License](./LICENSE) 开源协议发布。

---

## 🌟 致谢

- [Codex CLI](https://github.com/openai/codex) —— OpenAI 官方编码助手
- 所有为本项目提供反馈和建议的小伙伴 ❤️

<div align="center">

**如果这个 Skill 帮到了你，欢迎点一个 ⭐ Star 支持一下！**

</div>