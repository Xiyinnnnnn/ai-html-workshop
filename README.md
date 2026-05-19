

# AI TOOLKIT v5.0 -- RAW SINGLE-FILE APPS

A collection of six zero-dependency, single-HTML-file AI applications. No build step. No framework. No npm. Just open in browser.

> Toggle language: [中文](#chinese) | [English](#english)

---

## English

### Overview

| # | File | Name | Description | Agents | Lines |
|---|------|------|-------------|--------|-------|
| 1 | `穷举.html` | Inference Grid | Multi-angle exhaustive reasoning via parallel AI agents | Scalable | 2,958 |
| 2 | `群策.html` | Multi-Agent Chat | AI group chat with role-based agents, voting, and file system | 25+ | 8,577 |
| 3 | `小说.html` | NovelCraft | Full novel pipeline: seed -> worldview -> chars -> outline -> write -> review | 21 (A0-A20) | 1,056 |
| 4 | `游戏.html` | Game Engine | Text RPG engine with 108 specialized agents across 5 layers | 108 (L0-L5) | 3,388 |
| 5 | `色色.html` | NSFW Drive Pro | Adult narrative engine with character cards and style training | 1+ | 1,379 |
| 6 | `脏话.html` | Roast Generator | AI insult/roast generator with species classifier and quote library | 1 | 810 |

### Common Architecture

All six applications share the same architectural DNA:

```
Single HTML File
  |-- CSS: Dark theme, CSS variables, no frameworks
  |-- HTML: Minimal DOM, modal overlays, panel system
  |-- JS: Vanilla JavaScript, no dependencies (except Dexie.js in NovelCraft)
  |-- Storage: localStorage + IndexedDB dual-layer persistence
  |-- API: DeepSeek API unified client with retry/backoff/abort
  |-- Debug: Built-in debug log panels with filtering
```

### Prerequisites

- A DeepSeek API key ([platform.deepseek.com](https://platform.deepseek.com))
- A modern browser (Chrome / Firefox / Edge / Safari)
- That's it.

### Usage

1. Open any `.html` file directly in your browser.
2. Click the settings/gear button to configure your API key.
3. Use the test connection feature to verify.
4. Start using the application.

No server required. Data persists in your browser's localStorage and IndexedDB.

---

### Project Details

#### 1. Inference Grid (`穷举.html`)

**Purpose:** Exhaustive decision reasoning through combinatorial dimension exploration.

**Core Mechanism:**
- Define a situation, hard constraints, and multi-dimensional viewpoints (roles, assumptions, frameworks, stances).
- The system generates N reasoning agents, each operating from a unique angle in the Cartesian product of all dimension values.
- Agents run in parallel with adaptive concurrency control.
- Results are clustered and visualized as a heatmap.

**Levels (L0-L9):** Progressively scales from 10 agents at L0 up to full combinatorial coverage at L9. L4+ enables adversarial attack agents that stress-test reasoning results.

**Domains:** Business/Career, Personal Life, Relationships, Ethics, Technology/Engineering -- each with custom dimension sets.

**Technical Highlights:**
- Latin Hypercube Sampling for angle generation (non-exhaustive mode)
- Full Cartesian product generation with batch processing (exhaustive mode)
- IndexedDB persistence for agent results, session snapshots, and settings
- Adaptive concurrency with throttle/backoff on rate limits
- JSON parsing with 3-tier fallback (direct parse -> tail fix -> AI repair)
- Constraint probe system to validate feasibility before full run

#### 2. Multi-Agent Chat (`群策.html`)

**Purpose:** Create AI group chats where multiple agents with distinct roles debate, vote, and collaborate.

**Key Features:**
- Group creation with configurable agent rosters
- Role system: Host (full control), Admin (moderation), Member (basic)
- Command protocol: propose, vote, mute, unmute, invite, remove, stop
- One-vote veto mechanism on proposals
- File system: agents can createFile, readFile, listFiles
- Context compression with summary generation to prevent overflow
- @mention system for targeted communication
- Message history with IndexedDB archival and localStorage hot cache
- File content lazy-loading from IndexedDB for large files (>500KB)
- localStorage quota monitoring with automatic compression triggers
- Search fallback: agents can search the web, results auto-archived as files

**Built-in Agent Types:** A curated set of 25+ pre-configured agents covering architecture, algorithms, systems, creative writing, data science, and more.

#### 3. NovelCraft (`小说.html`)

**Purpose:** Complete AI-driven novel writing pipeline with 21 specialized sub-agents.

**Workflow (9 Phases):**
```
Seed -> Requirement Alignment -> Worldview -> Characters -> Outline
  -> Outline Review -> Chapter Writing -> Chapter Review -> Finished
```

**Agent Roster (A0-A20):**
- A0: Requirement Parser
- A1: Worldview Builder
- A2: Character Designer
- A3: Plot Outliner
- A4: Chapter Writer
- A5: Style Polisher
- A6: Summary Slicer
- A7: Memory Retriever
- A8: Fact Checker
- A9: Conflict Resolver
- A10: Reviewer (10-dimension scoring)
- A11: Task Brief Writer
- A12: State Synchronizer
- A13: Review Advisor
- A14: Phase Advisor
- A15: Outline Extender
- A16: Character Scout
- A17: Plot Diagnostician
- A18: Message Polisher
- A19: Context Assembler
- A20: Project Auditor

**Technical Highlights:**
- Dexie.js IndexedDB wrapper for multi-project persistence
- Master editor agent orchestrates all sub-agents via JSON command protocol
- 8 command types: ask_user, present_to_user, call_subagent, evaluate_result, move_phase, request_user_decision, complete, update_state
- Auto state writing for worldview/characters/outline agents
- Checkpoint system for rollback
- Context compression when messages exceed 1,050,000 characters
- Word count milestone checks at 25%/50%/75% with deviation alerts
- Multi-tab collision detection via BroadcastChannel API

#### 4. Game Engine (`游戏.html`)

**Purpose:** Text-based RPG engine with 108 specialized AI agents driving a persistent world.

**Agent Hierarchy:**
```
L0: Master Controller (1 agent)
  |
  +-- L1: Domain Agents (11 agents)
  |     Dialogue, Combat, Exploration, Atmosphere, Economy,
  |     Strategy, World Simulation, World Creation, Intimacy,
  |     Violence, Politics
  |
  +-- L2: Functional Agents (25 agents)
  |     Dialogue beats, NPC roleplay, Combat rounds, Scene rendering,
  |     Horror atmosphere, Emotional atmosphere, Economy events,
  |     Battle reports, Diplomacy, Time advancement, Faction dynamics,
  |     NPC behavior, Narrative lines, Pacing control, World framework,
  |     Race setting, Geography setting, History setting,
  |     Intimacy pacing, Body narrative, Erotic atmosphere,
  |     Combat trauma, Death scenes, Totalitarian rule, Purge operations
  |
  +-- L3: Atomic Agents (54 agents)
  |     Dialogue chain (4), Combat chain (7), Exploration chain (6),
  |     Atmosphere (2), Fear climax (1), Sensory (4), Economy chain (4),
  |     Strategy atoms (2), Espionage/Faction (2), Intimacy chain (10),
  |     Gore chain (6), Politics chain (6)
  |
  +-- L4: Data Agents (12 agents)
  |     Pure data queries, no creative output
  |
  +-- L5: Tool Agents (5 agents)
        Dice roller, Name generator, Grammar checker, Translator, Summarizer
```

**Command Protocol:**
- QUERY: Read world state
- RESPOND: Fast-food round (direct response without sub-agents)
- DISPATCH: Delegate to sub-agents
- REVISE: Modify sub-agent output
- FINALIZE: Integrate sub-agent results into final output
- SYSTEM: Export/Import/Clear/Settings/New Game

**Technical Highlights:**
- IndexedDB cold storage for old memories and narrative lines
- Agent timeout management with per-type budgets and max limits
- Creation mode with multi-stage world building workflow
- HP/Sanity tracking with UI bars
- Typewriter text effect for narrative delivery

#### 5. NSFW Drive Pro (`色色.html`)

**Purpose:** Adult narrative engine with trainable writing style and character card system.

**Key Features:**
- Character card system with AI generation and import/export
- Narrative module training: feed reference text to learn style and vocabulary
- Multiple narrative presets for different writing styles
- Outline generation with preference configuration
- Context slicing when token budget exceeds threshold
- Option generation from current scene context
- Full export/import of all data (narrative modules, cards, history, preferences)

**Preference Options:** Story mode (narrative/dialogue/hybrid), length limits, scene preferences, play preferences, position preferences, additional limits, orgasm requirements, ejaculation preferences.

#### 6. Roast Generator (`脏话.html`)

**Purpose:** AI-powered insult/roast generator targeting Chinese internet content.

**Multi-Phase Pipeline:**
```
Phase 1: Species Classification -> Phase 2: Skill Loading -> Phase 3: Deep Thinking -> Phase 4: Output
```

**Species Classifier:** Categorizes target text into 20+ persona types (A1-A4, B1-B6, C1-C5, D1-D4, E1-E4, F1-F4).

**Atomic Skills (22):**
- Category A: Animal degradation, Garbage analogy, Intelligence denial, Appearance destruction, Origin curse, Death sentence, Existence negation
- Category B: Reverse parody, Surface praise/actual disparagement, Reductio ad absurdum, Data crushing, Contrast humiliation
- Category C: Original metaphor, Parallel acceleration, Xiehouyu construction, Couplet generation, Doggerel verse
- Category D: Street cursing, Passive-aggressive, One-line kill, Chaotic evil
- Category E: Progressive acceleration, Finishing blow
- Category H: Slang substitution (harmony filter for low-intensity mode)

**Intensity System (0-10):** Determines which skills are loaded. Low intensity (<5) activates harmony filter that replaces sensitive words with homophones/abbreviations.

**Role Styles:** Street fighter, Fangirl parody, Conclusion king, Sarcasm master, Xiehouyu master, Couplet maniac, Chaotic evil.

**Quote Library:** 369 pre-built insult entries, each with AI-generated 4-dimensional tags (intensity, style, target, emotion). Supports manual addition and AI batch tagging.

---

### Storage Architecture

All applications use a dual-layer persistence model:

```
[Application]
     |
     +-- localStorage (hot cache)
     |     Active data, settings, recent messages
     |     Fast read/write, limited to ~5-10MB
     |
     +-- IndexedDB (cold storage)
           Archived messages, snapshots, file contents
           Large capacity, async access
           Automatic archival when localStorage exceeds thresholds
```

### API Integration

All applications connect to the DeepSeek API with a shared pattern:

- Unified fetch wrapper with retry logic (2-3 attempts)
- AbortController for user-initiated cancellation
- Rate limit handling: exponential backoff on HTTP 429
- Token budget management per request
- JSON response parsing with multi-tier fallback
- Chinese language enforcement in system prompts

---

## Chinese

### 总览

| # | 文件 | 名称 | 描述 | Agent数 | 行数 |
|---|------|------|------|---------|------|
| 1 | `穷举.html` | 穷举推理网格 | 多Agent并行穷举推理决策 | 可扩展 | 2,958 |
| 2 | `群策.html` | Multi-Agent群聊 | AI角色群聊，含投票/文件系统 | 25+ | 8,577 |
| 3 | `小说.html` | NovelCraft | 全流程AI小说创作管线 | 21 (A0-A20) | 1,056 |
| 4 | `游戏.html` | 游戏引擎 5.0 | 文本RPG引擎，108个Agent分层调度 | 108 (L0-L5) | 3,388 |
| 5 | `色色.html` | 色色驱动 Pro | 成人叙事引擎，可训练文风 | 1+ | 1,379 |
| 6 | `脏话.html` | 脏话生成 v6.0 | AI攻击/脏话生成器，含语录库 | 1 | 810 |

### 通用架构

六个应用共享相同的架构基因：

```
单个HTML文件
  |-- CSS: 暗色主题，CSS变量，零框架
  |-- HTML: 极简DOM，模态遮罩，面板系统
  |-- JS: 原生JavaScript，零依赖（NovelCraft除外，使用Dexie.js）
  |-- 存储: localStorage + IndexedDB 双层持久化
  |-- API: DeepSeek API统一客户端，带重试/退避/中断
  |-- 调试: 内置调试日志面板，支持过滤
```

### 前置条件

- DeepSeek API Key ([platform.deepseek.com](https://platform.deepseek.com))
- 现代浏览器 (Chrome / Firefox / Edge / Safari)
- 仅此而已

### 使用方式

1. 直接在浏览器中打开任意 `.html` 文件。
2. 点击设置/齿轮按钮配置API Key。
3. 使用测试连接功能验证。
4. 开始使用。

无需服务器。数据持久化在浏览器的localStorage和IndexedDB中。

---

### 项目详情

#### 1. 穷举推理网格 (`穷举.html`)

**用途:** 通过组合维度探索进行穷举式决策推理。

**核心机制:**
- 定义情境、硬约束和多维视角（角色、假设、框架、立场）。
- 系统生成N个推理Agent，每个从维度笛卡尔积中的唯一角度出发。
- Agent并行运行，带自适应并发控制。
- 结果聚类并以热力图可视化。

**等级 (L0-L9):** 从L0的10个Agent逐步扩展到L9的全组合覆盖。L4+启用对抗性攻击Agent对推理结果进行压力测试。

**领域:** 商业/职业、个人生命、关系/情感、伦理/道德、技术/工程 -- 各有自定义维度集。

**技术亮点:**
- 拉丁超立方采样生成角度（非穷举模式）
- 完整笛卡尔积生成带分批处理（穷举模式）
- IndexedDB持久化Agent结果、会话快照和设置
- 自适应并发，速率限制时触发节流/退避
- JSON解析三级回退（直接解析 -> 尾部修复 -> AI修复）
- 约束探测系统在完整运行前验证可行性

#### 2. Multi-Agent群聊 (`群策.html`)

**用途:** 创建AI群聊，多个不同角色的Agent进行辩论、投票和协作。

**核心功能:**
- 群组创建，可配置Agent名单
- 角色系统: 群主（完全控制）、管理员（审核）、成员（基础）
- 命令协议: 提议、表决、禁言、解除禁言、拉人、踢人、终止
- 一票否决表决机制
- 文件系统: Agent可创建文件、读取文件、列出文件
- 上下文压缩带摘要生成，防止溢出
- @提及系统用于定向通信
- 消息历史IndexedDB归档 + localStorage热缓存
- 大文件(>500KB)从IndexedDB懒加载
- localStorage配额监控带自动压缩触发
- 搜索兜底: Agent可搜索网络，结果自动归档为文件

**内置Agent类型:** 25+预配置Agent，覆盖架构、算法、系统、创意写作、数据科学等领域。

#### 3. NovelCraft (`小说.html`)

**用途:** 完整的AI驱动小说写作管线，21个专业子Agent。

**工作流（9阶段）:**
```
种子 -> 需求对齐 -> 世界观 -> 角色 -> 大纲 -> 大纲审阅 -> 章节写作 -> 章节评审 -> 完成
```

**Agent阵容 (A0-A20):**
- A0: 需求解析 / A1: 世界观构建 / A2: 角色设计 / A3: 大纲生成
- A4: 章节写作 / A5: 风格润色 / A6: 摘要切片 / A7: 记忆检索
- A8: 事实核查 / A9: 冲突调解 / A10: 评审反馈(10维评分)
- A11: 任务书撰写 / A12: 状态同步 / A13: 评审顾问 / A14: 阶段顾问
- A15: 大纲扩展 / A16: 角色检测 / A17: 剧情诊断
- A18: 消息润色 / A19: 上下文组装 / A20: 项目审计

**技术亮点:**
- Dexie.js IndexedDB封装，多项目持久化
- 主编Agent通过JSON命令协议编排所有子Agent
- 8种命令类型
- 世界观/角色/大纲Agent自动写入状态
- 检查点系统支持回滚
- 消息超1,050,000字符时上下文压缩
- 25%/50%/75%字数里程碑检查带偏差告警
- BroadcastChannel API多标签页碰撞检测

#### 4. 游戏引擎 5.0 (`游戏.html`)

**用途:** 文本RPG引擎，108个专业AI Agent驱动持久化世界。

**Agent层级:**
```
L0: 主控Agent (1个)
  |
  +-- L1: 领域Agent (11个) - 对话/战斗/探索/氛围/经营/战略/全局推演/创世/亲密/暴力/政治
  |
  +-- L2: 功能Agent (25个) - 对话编排/NPC扮演/战斗回合/场景呈现/氛围/经营/战报/外交等
  |
  +-- L3: 原子Agent (54个) - 各领域细化执行单元
  |
  +-- L4: 数据Agent (12个) - 纯数据查询
  |
  +-- L5: 工具Agent (5个) - 骰子/名称/语法/翻译/摘要
```

**命令协议:** QUERY / RESPOND / DISPATCH / REVISE / FINALIZE / SYSTEM

**技术亮点:**
- IndexedDB冷存储归档旧记忆和叙事线
- Agent超时管理，按类型分预算和上限
- 创建模式多阶段世界构建工作流
- HP/Sanity追踪带UI状态栏
- 打字机效果叙事输出

#### 5. 色色驱动 Pro (`色色.html`)

**用途:** 成人叙事引擎，可训练写作风格和角色卡系统。

**核心功能:**
- 角色卡系统，AI生成和导入导出
- 叙事模块训练：输入参考文本学习文风和词汇
- 多个叙事档位切换不同写作风格
- 大纲生成带偏好配置
- Token预算超阈值时上下文自动切片
- 从当前场景上下文生成选项
- 完整导出导入（叙事模块、角色卡、历史、偏好）

#### 6. 脏话生成 v6.0 (`脏话.html`)

**用途:** AI驱动的攻击/脏话生成器，针对中文互联网内容。

**多阶段流水线:**
```
阶段1: 成分分析 -> 阶段2: 技能装载 -> 阶段3: 深度思考 -> 阶段4: 输出
```

**成分分类器:** 将目标文本归类为20+人格标签（A1-A4, B1-B6, C1-C5, D1-D4, E1-E4, F1-F4）。

**原子技能 (22个):**
- A类: 动物降级、垃圾类比、智力否定、外貌粉碎、出身诅咒、死刑宣判、存在否定
- B类: 反串寄生、表面夸实际贬、归谬引爆、数据碾压、对比羞辱
- C类: 原创比喻、排比加速、歇后语构造、对联生成、打油诗
- D类: 街骂直喷、阴阳怪气、一句封喉、混乱邪恶
- E类: 递进加速、暴击收尾
- H类: 黑话和谐（低强度模式敏感词替换）

**强度系统 (0-10):** 决定加载哪些技能。低强度(<5)激活和谐过滤器，将敏感词替换为同音字/缩写。

**角色风格:** 战斗型喷子、反串型喷子、总结型喷子、阴阳大师、歇后语大师、对联狂魔、混乱邪恶型。

**语录库:** 369条预置攻击语录，每条含AI生成的四维标签（强度、风格、目标、情绪）。支持手动添加和AI批量标注。

---

### 存储架构

所有应用使用双层持久化模型：

```
[应用]
     |
     +-- localStorage (热缓存)
     |     活跃数据、设置、最近消息
     |     快速读写，限制~5-10MB
     |
     +-- IndexedDB (冷存储)
           归档消息、快照、文件内容
           大容量，异步访问
           localStorage超阈值时自动归档
```

### API集成

所有应用以共享模式连接DeepSeek API：

- 统一fetch封装带重试逻辑（2-3次）
- AbortController用户取消
- 速率限制处理：HTTP 429指数退避
- 每请求Token预算管理
- JSON响应解析多级回退
- 系统提示中强制中文输出

---

## License

MIT. Do whatever you want.

## Disclaimer

These are raw tools. They connect to external AI APIs. They store data in your browser. They contain adult content options (files 5 and 6). Use responsibly. The author assumes no liability for generated content or API usage costs.
