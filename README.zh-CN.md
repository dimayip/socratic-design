# Socratic Design

<p align="left">
  <a href="./README.md">English</a> ·
  <a href="./README.zh-CN.md"><b>简体中文</b></a>
</p>

<p align="left">
  <a href="https://github.com/dimayip/socratic-design/stargazers"><img src="https://img.shields.io/github/stars/dimayip/socratic-design?style=flat-square" alt="Stars"></a>
  <a href="https://github.com/dimayip/socratic-design/network/members"><img src="https://img.shields.io/github/forks/dimayip/socratic-design?style=flat-square" alt="Forks"></a>
  <a href="https://github.com/dimayip/socratic-design/issues"><img src="https://img.shields.io/github/issues/dimayip/socratic-design?style=flat-square" alt="Issues"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/github/license/dimayip/socratic-design?style=flat-square" alt="License"></a>
</p>

> **从模糊想法到决策锁定的设计文档——一个通用、领域无关、自给自足的 Socratic facilitation skill。**

`socratic-design` 把"做设计"这件事显式化为一套**可重复、可传授**的方法论：当用户带着一个模糊的想法走进来（新产品功能、内部工具、平台改造、AI 能力、数据流水线、工作流、治理机制……），这个 skill 不会立刻输出方案，而是先用 Socratic 追问把**关键决策锁定下来**，再按**真实消费者**选择的 schema（PRD / RFC / Design Doc / Kickoff / ADR / One-Pager）把决策组织成交付物。

---

## 定位声明

`socratic-design` 是一个**通用**的 facilitation 框架，**不绑定任何特定领域、技术栈或方法论**。它的价值来自三件事：

1. **提问纪律**——先问再写、每轮一维、A/B/C/D 候选、魔鬼代言人、决策锁定回顾
2. **依赖排序**——后面的决策依赖前面的决策，按拓扑顺序问，不跳步
3. **产物 schema 库**——6 类主流设计文档的完整模板，按消费者选形态

它**不提供**任何行业最佳实践判据——那是别的事情，不是这个 skill 要做的。如果你想要基于特定领域方法论的硬性约束来引导设计，那属于另一套工作，本 skill 不负责。

---

## 为什么需要这个 skill

绝大多数设计失败都不是"写得不好"，而是**决策还没锁定就开始写**：

- 方案写到一半才发现成功标准没定 → 推倒重来
- 文档交付后评审问"为什么不是方案 B" → 因为从没显式对比过
- 给执行团队的 Kickoff 清单粒度太粗 → 跑偏
- 一份 PRD 想同时服务管理层和开发团队 → 两边都不满意
- 关键命名（系统名、模块名、核心概念名）被擅自决定 → 后期改不动

`socratic-design` 通过把**决策锁定**和**产物书写**显式分离，并强制决策按依赖拓扑顺序推进，解决上面这一整类问题。

---

## 何时触发

用户的需求有以下任一特征时，就该用这个 skill：

- 想设计一个新产品 / 新功能 / 新系统 / 新流程，但**关键决策还不清楚**（范围、边界、接口、角色、成功标准……）
- 说"我有个想法"、"帮我想明白"、"帮我把这事理清楚"、"帮我设计 XX"
- 想要 PRD / RFC / 技术方案 / 设计文档 / Kickoff 清单 / 里程碑规划 / ADR / One-Pager 中的任一种
- 需要把一个涉及多利益相关方的复杂设计**分节锁定、逐节批准**再交付

**什么时候不该用**：用户只是想把**已经想清楚的东西**按固定格式记录下来（比如纯 CRUD 需求文档），按常规模板直接写即可。

---

## 最终产物不是"PRD"一种

本 skill 的输出**按真实消费者选择**，不是固定格式：

| 场景 | 建议产物 | 主要消费者 |
|------|----------|-----------|
| 从 0 到 1 设计新系统（工程为主） | **Design Doc + Kickoff 清单** | 开发者 + AI coding agent |
| 产品立项 / 对上汇报 | **PRD + One-Pager** | 产品评审 + 管理层 |
| 内部技术改造 / 跨团队协作 | **RFC / 技术方案** | 工程团队 + 架构评审 |
| 需求仍在探索 / 决策未完全锁定 | **ADR + 待办问题清单** | 自己 + 后续推进 |
| 已有方案需落地 | **里程碑计划 + 分工表** | 执行团队 |

多种产物可以**并行交付**（例如 PRD + One-Pager + Kickoff 三件套，给不同受众看）。详细模板与选择决策树见 [`references/deliverables.md`](./references/deliverables.md)。

---

## 核心方法论：4 层叠加框架

```
Layer 1: Capture Context —— 方法论锚点（可选）+ 业务现状 + 产物消费者
   ↓
Layer 2: Brainstorming 纪律（已内化）—— 6 条硬纪律约束节奏
   ↓
Layer 3: Socratic 追问 —— A/B/C/D 候选 + 依赖拓扑 + 一致性校验
   ↓
Layer 4: 产物组织 —— 按消费者选 schema，把锁定的决策摆进去
```

每一层都不能跳，但强度可按任务复杂度调节。

### Layer 1 · Capture Context
一次性问清楚 4 件事：**方法论锚点**（若无可显式声明"无"，不要自己造）、**业务现状关键数字**、**产物形态**、**产物消费者**。然后**复述理解**让用户校验——花 30 秒避免一整轮歧义。

### Layer 2 · 6 条硬纪律（内化在 skill 内部）
1. 关键决策锁定前不写产物（锁定 → 书写，单向流程）
2. 每轮只问 1 个维度（避免认知过载）
3. 方案分节呈现，逐节 Approve
4. 每 3 轮做一次决策锁定回顾
5. 关键决策上扮演魔鬼代言人（主动提反驳视角）
6. 命名不擅自决定（系统名 / 仓库名 / 核心概念名都给候选让用户选）

### Layer 3 · Socratic 追问
标准提问公式：

```
❓ 关于 <某维度>，有几个候选方案：

A. <方案 A> — <优缺点>
B. <方案 B> — <优缺点>
C. <方案 C> — <优缺点>
D. <方案 D> — <优缺点>

💡 我的建议：__ （明确倾向 + 为什么）

请问您选哪个？或者排个优先级？
```

并且按**依赖拓扑顺序**问——后面的决策依赖前面的决策，警戒信号是用户开始说"这个我还没想好，跟 XX 有关"，说明你问了一个**依赖未满足**的问题，应立即回退到前置依赖项。

每轮用户做完决策后，心里做 3 项一致性校验：**对方法论锚点**、**对先前决策**、**对业务现实**。

### Layer 4 · 产物组织（6 个 schema）
决策全部锁定后，按用户选定的产物类型组织：**PRD / Design Doc / RFC / Kickoff Checklist / ADR / One-Pager**。完整 schema 见 [`SKILL.md`](./SKILL.md) 第 Layer 4 节与 [`references/deliverables.md`](./references/deliverables.md)。

---

## 标准工作流

```
Step 0  识别是否需要本 skill（30 秒）
   │
   ▼
Step 1  Capture Context（第 1 轮：现状 + 锚点 + 产物形态 + 消费者，复述校验）
   │
   ▼
Step 2  Socratic 追问（N 轮，按依赖拓扑，每 3 轮做一次决策锁定回顾）
   │
   ▼
Step 3  方案分节呈现（2–5 节，每节结束问 "approve 还是调整？"）
   │
   ▼
Step 4  按选定 schema 组织产物（多产物并行交付 + 说明各自消费者）
   │
   ▼
Step 5  复盘（可选，强烈推荐）—— 诚实回答"你用了什么框架"
```

---

## 仓库结构

```
socratic-design/
├── SKILL.md                               # 完整 skill 规范——4 层框架 + 6 纪律 + 工作流 + 反模式
├── README.md                              # （本文件）面向人类的入口与总览
├── assets/                                # 预留：后续可放架构图、流程图等配图
└── references/
    ├── decision-checklists.md             # 按系统类型的决策清单
    └── deliverables.md                    # 6 类产物（PRD / Design Doc / RFC / Kickoff / ADR / One-Pager）详细模板与选择决策树
```

- **[`SKILL.md`](./SKILL.md)** — Canonical spec。AI agent 真正加载执行的文件。想用或想移植这个 skill 从这里入手。
- **[`references/decision-checklists.md`](./references/decision-checklists.md)** — Socratic 追问时**不遗漏关键维度**的清单。按系统类型分块，加上成本、风险、命名 3 个通用维度。
- **[`references/deliverables.md`](./references/deliverables.md)** — 6 类产物的完整模板 + Capture 阶段的产物选择决策树。**这是 Layer 4 书写阶段的弹药库。**

---

## 反模式（绝对不要做）

| ❌ 反模式 | ✅ 正确做法 |
|----------|-----------|
| 用户刚说完想法，立即输出整套方案 | 先 Capture Context，再 Socratic 追问 |
| 一次问 5 个维度 | 每轮只问 1 个维度 |
| 用开放式问题（"你希望怎么设计？"） | 用 A/B/C/D 候选 + 推荐 + 理由 |
| 接受决策不做一致性校验 | 每轮都对照方法论和先前决策校验 |
| 方案一次性甩给用户 | 分节呈现，逐节 Approve |
| 用 MUST / NEVER 硬约束 | 用"因为 X 所以建议 Y"的理由式表述 |
| 跳过锁定直接写文档 | 先锁再写，单向流程 |
| 擅自命名仓库 / 模块 / 概念 | 给 2–3 个候选让用户选 |
| 假定用户一定要 PRD | 先问清楚产物形态 |
| 依赖其他 skill 做最终产出 | 本 skill 自给自足，直接按 Layer 4 schema 输出 |

---

## 自给自足原则（为什么不拆成多个 skill）

`socratic-design` 内化了 Socratic brainstorming 纪律 + 6 类主流文档的 schema 知识，**不依赖其他 skill**。原因：

1. **完整方法论在一个 skill 内**便于传授、演化、复盘；
2. **避免调度失败风险**——依赖的外部 skill 未命中触发条件，整条链就断了；
3. **允许跨阶段引用**——Capture 阶段锁定的决策，Layer 4 书写阶段能直接使用，不丢上下文。

---

## 如何在 AI agent 中使用这个 skill

支持 skill 加载的平台（CodeBuddy / Claude skills 等）：

1. 把整个目录放到平台的 skills 文件夹下（例如 `.codebuddy/skills/socratic-design/`）；
2. 当用户的请求匹配 skill 描述（"帮我设计 XX"、"help me think this through"、想要 PRD/RFC/Design Doc/Kickoff/ADR/One-Pager 等）时，agent 会自动加载 `SKILL.md`；
3. `references/` 下的文件**按需加载**——agent 只在当前对话真正需要决策清单或产物模板时才读，让 `SKILL.md` 本身保持精简。

如果你是想自己当 facilitator：完整读一遍 `SKILL.md` 把 6 条纪律内化，把两份 reference 文件在对话时开在旁边随时查。

---

## 元原则

> **本 skill 最重要的不是让 Agent 更会"写"，而是让 Agent 更会"问"。**
>
> 因为 **好问题 = 好决策 = 好产物**（无论它最终是 PRD、RFC、Design Doc 还是别的）。
> 用户永远是决策的所有者，Agent 只是帮助用户把决策表达出来。

---

## License

除非单独文件另有说明，本仓库内容遵循 MIT License。详见仓库中的 `LICENSE`（若有）。

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=dimayip/socratic-design&type=Date)](https://star-history.com/#dimayip/socratic-design&Date)

---

## Credits

由 [@bellchen](https://github.com/bellchen) 设计并维护。融合了 Socratic 引导纪律、依赖拓扑排序、决策一致性校验，以及主流设计文档体系（PRD / RFC / ADR / Design Doc / Kickoff / One-Pager），最终压缩成一套**可在真实对话里跑起来**、**领域无关**的规则集。

---

> 本中文版本由维护者手工撰写，未来英文 README 的更新可能由 GitHub Action 自动翻译同步；若两版内容出现不一致，**以英文版 [`README.md`](./README.md) 为准**。
