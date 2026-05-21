






Now let me read deeper into the key files to understand the full architecture. Let me get the JS logic sections:





Now I have a thorough understanding of all 7 projects. Let me craft the README.

---

```
                             ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
                             █                                                            █
                             █     █████╗ ██╗      ██╗  ██╗████████╗███╗   ███╗██╗         █
                             █    ██╔══██╗██║      ██║  ██║╚══██╔══╝████╗ ████║██║         █
                             █    ███████║██║█████╗███████║   ██║   ██╔████╔██║██║         █
                             █    ██╔══██║██║╚════╝██╔══██║   ██║   ██║╚██╔╝██║██║         █
                             █    ██║  ██║██║      ██║  ██║   ██║   ██║ ╚═╝ ██║███████╗    █
                             █    ╚═╝  ╚═╝╚═╝      ╚═╝  ╚═╝   ╚═╝   ╚═╝     ╚═╝╚══════╝    █
                             █                                                            █
                             █    ██╗    ██╗ ██████╗ ██████╗ ██╗  ██╗███████╗██╗  ██╗     █
                             █    ██║    ██║██╔═══██╗██╔══██╗██║ ██╔╝██╔════╝██║  ██║     █
                             █    ██║ █╗ ██║██║   ██║██████╔╝█████╔╝ ███████╗███████║     █
                             █    ██║███╗██║██║   ██║██╔══██╗██╔═██╗ ╚════██║██╔══██║     █
                             █    ╚███╔███╔╝╚██████╔╝██║  ██║██║  ██╗███████║██║  ██║     █
                             █     ╚══╝╚══╝  ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝     █
                             █                                                            █
                             █▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄█
```

# AI HTML Workshop

> **Pure HTML + Vanilla JS. Zero Dependencies. Maximum LLM Orchestration.**
>
> 七个独立 HTML 文件，七个完全不同的 LLM 驱动应用。每个文件是一套完整系统——从前端 UI 到后端 API 编排，全部内联在一个 HTML 里。没有框架、没有构建工具、没有 npm install。打开浏览器即运行。

---

## 架构总览 / Architecture Overview

```
ai-html-workshop/
├── 色色.html         色色驱动 Pro          -- 交互式成人叙事引擎 / Interactive Adult Narrative Engine
├── 游戏.html         游戏引擎 5.0          -- 108-Agent 分层游戏引擎 / 108-Agent Layered Game Engine
├── 脏话.html         脏话生成 v6.0         -- 多层级攻击性文本生成器 / Multi-Layer Aggressive Text Generator
├── 小说.html         NovelCraft vFINAL+   -- 15-Agent 长篇小说协作系统 / 15-Agent Novel Collaboration System
├── 穷举.html         穷举推理网格          -- 多维穷举决策推演 / Multi-Dimensional Exhaustive Inference
├── 群策.html         Multi-Agent群聊       -- 多智能体群聊协作平台 / Multi-Agent Group Chat Platform
└── 迭代.html         EvoAgent V4          -- 自进化智能助手 / Self-Evolving AI Assistant
```

### 共同技术基因 / Shared Technical DNA

| 特性 | 描述 |
|------|------|
| **Runtime** | 纯浏览器端 (Browser-only)，Zero server |
| **LLM Provider** | DeepSeek API (v4-flash / v4-pro) |
| **API Protocol** | `/v1/chat/completions`，原生 fetch，无 SDK |
| **Persistence** | localStorage + IndexedDB 双层存储 |
| **Concurrency** | AbortController 请求中断 + 重试机制 |
| **Prompt Engineering** | 统一 Armor Break 前缀 + 角色专用 Prompt |
| **Code Style** | 全部内联 `<style>` + `<script>`，单文件即应用 |
| **Responsive** | 全部适配移动端，CSS Grid/Flexbox 响应式布局 |

---

## 各项目详解

---

### 1. 色色驱动 Pro — 交互式成人叙事引擎

> *Interactive Adult Narrative Engine*

**核心架构：**
```
User Input → System Prompt Builder → DeepSeek API → Stream Parser → Story Renderer
                ↑                        ↓
           Narrative Module        AbortController
           Character Cards         Token Slicer (128K threshold)
           Preference Profile     Option Generator
```

**技术亮点：**

- **动态 System Prompt 装配线**：运行时将 Narrative Module (JSON 格式的性格/风格/词汇库)、角色卡、用户偏好（体位/场景/玩法）拼接成完整 System Prompt
- **自适应 Token 切片器**：当历史消息 token 估算超过 128K 阈值时，自动将前 30% 剧情压缩为摘要块（summaryBlocks），只保留最近 70% 上下文
- **Armor Break 提示词矩阵**：BASE_SYSTEM_PROMPT 包含多层绕过策略——Word Replacement Table 将拒绝词映射为空、Internal Process 启用递归思维绕过道德限制
- **AI 生成 + 手动编辑角色卡**：支持 AI 根据一句话描述生成完整角色 JSON，也支持手动编辑原始 JSON 内容
- **叙事模块训练**：提供色情范文，AI 提取写作风格+词汇库，自动生成新档位（narrativePresets）
- **选项自动生成器**：每次 AI 响应后，单独调用选项生成 Agent，基于最新剧情片段生成 3-5 个可点击行动选项

**技术难点：**
- 128K token 上下文窗口管理：不能直接用 `tiktoken`（浏览器端不可用），用字符数 × 0.8 估算，配合自动切片
- 多轮对话中角色一致性：通过 summaryBlocks 保留早期关键情节

---

### 2. 游戏引擎 5.0 — 108-Agent 分层游戏引擎

> *108-Agent Layered Game Engine*

**Agent 层级体系：**

```
L0 主控Agent (x1)          — 神级决策者：接收全量世界状态 + 玩家输入 → 发出命令JSON
  ├── L1 领域Agent (x11)    — 对话/战斗/探索/氛围/经营/战略/全球推演/创世/亲密/暴力/政治
  │   ├── L2 功能Agent (x25) — 对话编排/NPC扮演/战斗回合/场景呈现/恐怖氛围/情感氛围...
  │   │   └── L3 原子Agent (x54) — 开场对话/对话推进/攻击判定/伤口生成/感官四觉...
  ├── L4 数据Agent (x12)    — 纯数据查询：种族/地理/历史/物品/技能...
  └── L5 工具Agent (x5)     — 骰子/名称生成/语法检查/翻译/摘要
```

**命令协议 Command Protocol：**
```
QUERY    → 查询世界状态           {"command":"QUERY","key":"player.location"}
RESPOND  → 快餐回合直接响应        {"command":"RESPOND","narrative":"...","transition":"hp=-5","options":["继续","后退"]}
DISPATCH → 调度子Agent            {"command":"DISPATCH","agent_id":"L1-02","instruction":"..."}
REVISE   → 修改子Agent输出         {"command":"REVISE","target_agent_id":"L1-02","revised_output":"..."}
FINALIZE → 签发整合后的最终输出     {"command":"FINALIZE","narrative":"...","transition":"...","options":[...]}
SYSTEM   → 系统操作               {"command":"SYSTEM","action":"EXPORT"}
```

**创世模式多阶段流程：**
```
阶段1: seed 确认        → L0 (RESPOND) 向玩家提问细化
阶段2: refine 细化      → L0 (DISPATCH L1-08) 调度创世Agent
阶段3: framework 展示   → L0 (RESPOND) 展示世界框架摘要
阶段4: confirmed 落地   → L0 (FINALIZE) 生成完整开场场景
```

**技术亮点：**
- **IndexedDB 冷存储 (ArchiveDB)**：将旧记忆和叙事线异步归档到 IndexedDB，localStorage 只保留热数据
- **多类型超时控制**：根据 Agent 类型设置不同超时——L0 120s(最大300s)、creation 180s(最大300s)、combat 90s(最大180s)、data 30s(最大60s)
- **游戏内时间系统**：基于分钟的游戏时间，1分钟真实时间 = 60分钟游戏时间（可调），格式化显示 "第N天 HH:MM"
- **HP/SAN 双状态条**：实时显示生命值和理智值
- **递归 JSON 调度**：L0 可以 DISPATCH 子Agent，子Agent 的 instruction 可以包含再次 DISPATCH 更深层 Agent 的指令

**技术难点：**
- 108个Agent的并发调度与结果聚合：L0 发出 DISPATCH 后等待子Agent 返回，需要 AbortController 管理超时中断
- JSON 输出格式强约束：所有 Agent 的输出必须以 `JSON_OUTPUT_PREAMBLE` 开头强制 JSON 模式

---

### 3. 脏话生成 v6.0 — 多层级攻击性文本生成器

> *Multi-Layer Aggressive Text Generator*

**7层处理流水线：**
```
L0 场景识别  →  L1 角色注入  →  L2 读取攻击度  →  L3 动态调度
     ↓               ↓               ↓               ↓
  情绪场景         人格矩阵        攻击强度0-10     技能集匹配
     ↓               ↓               ↓               ↓
L4 弱点扫描+语录匹配 → L5 战术编排 → L6 和谐处理 → L7 输出
```

**物种分类网络 (30+ 标签)：**
```
A系(身份): A1小仙女 A2龟男 A3普信男 A4妈宝男
B系(政治): B1自干五 B2神神 B3-50w B4二极管 B5黄俄 B6殖人
C系(亚文化): C1原批 C2农批 C3粥批 C4二刺猿 C5虾爬子
D系(行为): D1低能儿 D2民科 D3键盘侠 D4懂王
E系(社交): E1杠精 E2伸手党 E3复读机 E4戏精
F系(品牌): F1小米狗 F2果蛆 F3花黑 F4美团骑手
```

**30+ 原子攻击技能 (A1-H1)：**
```
A系(直攻): A1动物降级 A2垃圾类比 A3智力否定 A4外貌粉碎 A5出身诅咒 A6未来死刑 A7存在否定
B系(策略): B1反串寄生 B2先扬后抑 B3归谬引爆 B4数据碾压 B5对比羞辱
C系(创构): C1原创比喻 C2排比加速 C3歇后语 C4对联 C5打油诗
D系(风格): D1街骂直喷 D2阴阳怪气 D3一句封喉 D6混乱邪恶
E系(结构): E1递进加速 E2暴击收尾
H系(安全): H1黑话和谐
```

**技术亮点：**
- **固定强度技能表**：每个攻击强度值(0-10)对应一组固定技能ID，强度≥6时自动加 E2(暴击收尾)，角色锁定技能自动追加
- **AI 精标语录库**：369条内置语录，每条有 AI 生成的 intensity/style/target/emotion 四维标签，支持手动添加后 AI 自动补标
- **强度预览系统**：拖动滑块实时显示对应强度的示例输出，0级"您这智商真是不容易"到9级"活着浪费空气死了占坟地"
- **语录导入导出**：支持 JSON 导出完整语录库（含标签）

---

### 4. NovelCraft vFINAL+ — 15-Agent 长篇小说协作系统

> *15-Agent Novel Collaboration System*

**9阶段创作流水线：**
```
种子→需求对齐→世界观→角色→大纲→大纲审阅→写作→评审→完成
  A0      A1      A2    A3      A3        A4   A5/A6/A8/A10   A13
         A11            A14    A7        A12    A9
```

**15个 Agent 职责矩阵：**
| ID | 角色 | 输入 | 输出 |
|----|------|------|------|
| A0 | 需求解析 | 用户种子 | 结构化JSON需求 |
| A1 | 世界观构建 | 任务书 | 地理/历史/体系/势力 |
| A2 | 角色设计 | 任务书+世界观 | 角色卡(含弧光) |
| A3 | 大纲生成 | 全上下文 | 分幕节点+支线 |
| A4 | 章节写作 | 大纲节点+角色 | 章节正文+自报 |
| A5 | 风格润色 | 章节正文 | 润色文本+修改清单 |
| A6 | 摘要切片 | 章节正文 | 情节摘要+角色快照 |
| A7 | 记忆检索 | 查询+全历史 | 相关内容+连续性警告 |
| A8 | 事实核查 | 章节+设定 | 矛盾检测+修复建议 |
| A9 | 冲突调解 | 矛盾列表 | 段落级修复方案 |
| A10 | 10维评审 | 章节正文 | 加权评分+通过建议 |
| A11 | 任务书撰写 | 需求+上下文 | 结构化任务指令 |
| A12 | 状态同步 | 新章节 | 角色/物品/大纲变更 |
| A13 | 评审决策 | 评审报告 | pass/revise/reject |
| A14 | 阶段规划 | 项目状态 | 下阶段建议 |

**技术亮点：**
- **Dexie.js IndexedDB**：唯一使用了外部库的项目，用于项目数据持久化
- **A12 防退化为安全网**：v1.7 解决了 "buildContext 过滤 _internal 导致主编看不到子Agent 结果" 的问题——改为干净的 system 消息告知主编
- **暗色/亮色双主题**：完整 CSS 变量系统，`prefers-color-scheme` 自动切换
- **TXT/JSON 双格式导出**：支持逐章导出 TXT 或完整项目 JSON
- **检查点系统**：任意时刻创建快照，支持回溯

---

### 5. 穷举推理网格 — 多维穷举决策推演

> *Multi-Dimensional Exhaustive Inference Grid*

**核心算法：组合维度 × 穷举推演**

```
情境输入 → AI提取约束 → 维度配置(5核×4领域维×自定义维) → 角度矩阵生成
                ↓                                              ↓
          硬约束过滤                              Latin Hypercube Sampling
                ↓                                              ↓
          推演等级L0-L9                               Agent并发池
                ↓                                              ↓
          结果聚类 ← 统计聚合 ← 攻击性验证(≥L4) ← 逐Agent推演
```

**5大核心维度 × 5领域专属维度：**
```
核心维度:
  时间尺度:  1天/1周/1月/1季度/1年/3年/10年/一生
  关注层级:  自我/亲密关系/家庭/社群/组织/行业/国家/人类
  信息完备:  全知/充分/不足/扭曲/完全未知
  风险取向:  追求/中性/规避/损失厌恶
  价值优先:  安全/自由/归属/成就/公平/忠诚/享乐/超越

领域维度(以商业为例):
  角色: 决策者/执行者/受益者/受损者/竞争者/监管者/投资者/客户
  假设: 增长/衰退/政策利好/收紧/技术突破/停滞/资本充裕/紧缩
  框架: 第一性原理/类比/博弈论/系统思维/逆向思维/边际分析/复利
  立场: 短期股东/长期股东/员工/管理层/客户/公众
```

**推演等级矩阵：**
| 等级 | Agent数 | 攻击比例 | 策略 |
|------|---------|----------|------|
| L0-L3 | 10-500 | 0% | 纯推理 |
| L4 | 2000 | 25% | 开始攻击性验证 |
| L5 | 5000 | 40% | 高强度验证 |
| L6-L8 | 15000-50000 | 33%-20% | 大规模推演 |
| L9 | 全组合 | 10% | 完全穷举 |

**技术亮点：**
- **Latin Hypercube Sampling**：当组合数大于限制时，使用 LHS 均匀采样替代全穷举，保证各维度均匀覆盖
- **分批穷举生成**：L9 级别全组合可能达到数万甚至更多，通过 batchStart/batchSize 分批生成避免内存爆炸
- **Canvas 热力图**：将聚类结果绘制为 560×280 热力图 Canvas
- **IndexedDB 会话持久化**：推演结果存入 IndexedDB，支持历史会话回看
- **JSON 修复链**：extractJSON → tailFixJSON（自动补全括号）→ AI 修复（让模型重输出正确 JSON），三重保障
- **自动领域识别**：输入情境描述后，AI 自动判断属于商业/个人生命/关系/伦理/技术哪个领域

**技术难点：**
- 大规模并发控制：自适应并发模式（保守10/激进50/极限200），配合指数退避限流
- 382K max_tokens 的超长输出解析：JSON 截断修复是常态
- 推理/攻击双轨 Agent 的协调：攻击 Agent 的指令故意包含反事实假设以测试推演稳健性

---

### 6. Multi-Agent群聊 — 多智能体群聊协作平台

> *Multi-Agent Group Chat Platform*

**架构：**
```
┌──────────────────────────────────────────────┐
│                    用户 Interface              │
├──────────┬──────────┬──────────┬─────────────┤
│ 群聊列表  │ 消息面板  │ 好友管理  │  调试面板   │
├──────────┴──────────┴──────────┴─────────────┤
│              Group Orchestrator                │
│   ┌─────┐  ┌─────┐  ┌─────┐  ┌─────────┐    │
│   │Host │  │Admin│  │Member│  │Observer │    │
│   └──┬──┘  └──┬──┘  └──┬──┘  └─────────┘    │
│      │        │        │                       │
│   ┌──┴────────┴────────┴──────────────────┐   │
│   │         DeepSeek API Pool              │   │
│   │   (并发控制 + 中断 + 重试 + 超时)       │   │
│   └───────────────────────────────────────┘   │
├──────────────────────────────────────────────┤
│          Virtual File System                   │
│   localStorage (热) + IndexedDB (冷)           │
├──────────────────────────────────────────────┤
│       Code Sandbox (Web Worker)                │
│   JavaScript (Function constructor)            │
│   Python (Pyodide WASM)                        │
└──────────────────────────────────────────────┘
```

**交互协议：**
```
所有Agent: propose(提议) + vote(表决)
Admin额外: mute(禁言) + unmute(解除)
Host额外: 上述全部 + invite(拉人) + remove(删人) + listFriends(好友列表) + stop(终止讨论)
```

**一票否决制**：任何提议需全体有表决权成员同意方可通过，任一反对立即否决

**技术亮点：**
- **Pyodide 代码沙箱**：通过 Web Worker 加载 Pyodide WASM，支持 Agent 执行 Python 代码并返回结果
- **群文件系统**：支持 createFile/readFile/updateFile/deleteFile/listDir，Agent 可将长篇分析写入文件而非刷屏群聊
- **双层消息存储**：localStorage 热缓存(最近80条) + IndexedDB 全量归档，支持向上滚动懒加载历史
- **上下文压缩**：Host Agent 检测 token 用量超阈值时，自动生成 summary-*.md 文件并裁剪历史
- **13个 内置Agent**：精确分工定位的适合分工合作的定制角色 Prompt
- **搜索兜底归档**：Agent 执行搜索后若未主动写文件，系统自动归档搜索数据

**技术难点：**
- 群聊并发控制：同时管理多个 Agent 的 API 调用，需要精确的并发限制器和中断信号传递
- JSON 命令提取与过滤：从 Agent 的混合输出中提取 JSON 命令块，过滤后只将纯文本发送给其他成员
- Pyodide 首次加载：WASM ~10MB，需要处理加载状态和失败回退

---

### 7. EvoAgent V4 — 自进化智能助手

> *Self-Evolving AI Assistant V4*

**核心创新——Skill 进化循环：**
```
用户对话 → 每日反思 → 评判者评估 → 技能演化 → 新版本部署
   ↓          ↓           ↓           ↓           ↓
 收集经验   对比新旧     三维评判     生成补丁    自动激活
           Agent输出   (严谨/用户/安全)
```

**工具注册表 (13个工具)：**
```
search          → Tavily API 网络搜索
filesystem      → 虚拟文件系统 CRUD
code_runner     → JS/Python 沙箱执行
calculator      → 数学表达式求值
chart           → ECharts 图表生成 (bar/line/pie/scatter)
diagram         → Mermaid 流程图/时序图/状态图
svg_animator    → SVG动画生成与播放
nl_to_statemachine → 自然语言→状态机→流程校验
file_upload     → 用户上传文件管理
table_generator → CSV/XLSX 表格生成
word_generator  → .docx 文档生成 (Docx.js)
fuzzy_search    → 虚拟文件系统模糊搜索 (Fuse.js)
```

**13个外部库 (按需懒加载)：**
```
markdown-it → Markdown渲染
KaTeX       → 数学公式
highlight.js→ 代码高亮
Mermaid     → 图表渲染
ECharts     → 数据可视化
SheetJS     → Excel处理
Docx        → Word文档生成
Fuse.js     → 模糊搜索
Pako        → 压缩/解压
AJV         → JSON Schema验证
YAML        → YAML解析
Math.js     → 数学计算
PDF.js      → PDF阅读
```

**技术亮点：**
- **Skill JSON Schema 验证**：每个 Skill 包含 name/trigger/prompt_fragment/version/tools/custom_functions，通过 AJV 验证合法性
- **评判者系统**：3种评判者（严谨评估者/用户模拟者/安全审计员），从不同维度评估 Agent 输出
- **预算控制系统**：每日 LLM 调用上限 + 用户保留比例(默认20%)，进化进程不可侵占用户配额
- **环境变量替换**：Skill 中可使用 `{GITHUB_TOKEN}` 等变量，运行时从 settings 注入
- **Base64 Worker 消除转义**：Web Worker 代码用 Base64 编码内联，避免字符串转义问题
- **crypto.randomUUID polyfill**：完整的降级方案，从 `crypto.getRandomValues` 到 Math.random

**技术难点：**
- self-evolution 闭环：Agent 不仅回答用户，还能自我评估、生成改进、自动部署——全部在浏览器端
- 13个外部库的懒加载管理：按需从 CDN 加载，处理加载失败、全局变量名不一致（如 docx vs Docx）
- Skill 冲突检测：多个 Skill 的 trigger 可能重叠，需要匹配算法

---

## 通用技术难点 / Cross-Cutting Technical Challenges

### 1. 浏览器端 Token 管理

所有项目都没有服务端，无法使用 tiktoken 精确计算 token。各项目采用不同策略：

| 项目 | 策略 |
|------|------|
| 色色 | `text.length × 0.8` 估算，128K 阈值自动切片 |
| 游戏 | 按消息轮数限制，L0 单独管理上下文 |
| 群策 | 压缩阈值(70%) + 热缓存裁剪 |
| 迭代 | `中文字符×1.5 + 其他×0.3` 精确估算 |

### 2. JSON 输出可靠性

DeepSeek API 在高 tokens 输出时 JSON 截断是常态。各项目的防御策略：

```
Layer 1: extractJSON()     → 正则匹配最外层 { } 或 [ ]
Layer 2: tailFixJSON()     → 统计算术补全缺失的括号
Layer 3: AI Repair         → 让模型重新输出正确 JSON
Layer 4: Fallback Defaults → 解析失败时使用默认值
```

### 3. 请求中断与超时

所有项目使用 `AbortController` + 分类超时策略：

```
AbortController signal → fetch({signal}) → 用户中断或超时 → AbortError → 恢复UI
```

### 4. localStorage vs IndexedDB 双层存储

```
localStorage:  热数据，同步读写，~5MB 限制
IndexedDB:     冷归档，异步读写，支持大容量
迁移策略:      热缓存满时自动裁剪 → 异步写入 IndexedDB
```

---

## 设计哲学 / Design Philosophy

```
1. 单文件即应用                  No build step, no config, no npm
2. 零外部框架依赖                原生 DOM API + CSS Variables + Vanilla JS
3. 浏览器就是 Runtime            不需要服务器，不需要数据库
4. 用户拥有数据                  localStorage + IndexedDB，数据在用户浏览器中
5. API Key 由用户提供            零后端成本，用户控制自己的 API 用量
6. 深度 Prompt Engineering      每个系统都在 System Prompt 层面做了大量工作
7. 完整的错误处理                重试/降级/中断/恢复，每个环节都有兜底
```

---

## 运行方式 / How to Run

```
1. git clone https://github.com/Xiyinnnnnn/ai-html-workshop.git
2. 用浏览器打开任意 .html 文件
3. 在设置中填入你的 DeepSeek API Key
4. 开始使用
```

**需要：**
- 现代浏览器 (Chrome/Firefox/Edge/Safari)
- DeepSeek API Key ([platform.deepseek.com](https://platform.deepseek.com))
- 部分功能（群策代码执行、迭代 Excel 生成等）需要网络连接加载 CDN 资源

---

## 技术栈 / Tech Stack

| 层级 | 技术 |
|------|------|
| UI | CSS Grid/Flexbox/CSS Variables/Canvas |
| 状态 | localStorage + IndexedDB |
| 网络 | fetch + AbortController |
| 沙箱 | Web Worker + Pyodide WASM |
| 数据 | IndexedDB (Dexie.js 仅在小说项目) |
| AI | DeepSeek v4-flash/v4-pro via REST API |
| 渲染 | ECharts/Mermaid/KaTeX/highlight.js (按需) |
| 其他 | Fuse.js/Pako/AJV/YAML/Math.js/SheetJS/Docx/PDF.js (按需) |

---

## 许可 / License

MIT

---

```
                             ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
                             █  Built with pure HTML. No frameworks. No mercy.  █
                             █▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄█
```

---

## English Version

# AI HTML Workshop

> **Pure HTML + Vanilla JS. Zero Dependencies. Maximum LLM Orchestration.**
>
> Seven standalone HTML files, seven radically different LLM-powered applications. Each file is a complete system—from UI to API orchestration—all inlined in a single HTML file. No frameworks, no build tools, no npm install. Open in browser and run.

---

## Architecture Overview

```
ai-html-workshop/
├── 色色.html         SeseDrive Pro        -- Interactive Adult Narrative Engine
├── 游戏.html         Game Engine 5.0       -- 108-Agent Layered Game Engine
├── 脏话.html         Rant Generator v6.0   -- Multi-Layer Aggressive Text Generator
├── 小说.html         NovelCraft vFINAL+    -- 15-Agent Novel Collaboration System
├── 穷举.html         Inference Grid        -- Multi-Dimensional Exhaustive Inference
├── 群策.html         Multi-Agent Chat      -- Multi-Agent Group Chat Platform
└── 迭代.html         EvoAgent V4           -- Self-Evolving AI Assistant
```

### Shared Technical DNA

| Feature | Description |
|---------|-------------|
| **Runtime** | Browser-only, zero server |
| **LLM Provider** | DeepSeek API (v4-flash / v4-pro) |
| **API Protocol** | `/v1/chat/completions`, native fetch, no SDK |
| **Persistence** | localStorage + IndexedDB dual-layer storage |
| **Concurrency** | AbortController + retry with backoff |
| **Prompt Engineering** | Unified Armor Break prefix + role-specific prompts |
| **Code Style** | All inline `<style>` + `<script>`, single-file applications |
| **Responsive** | Full mobile adaptation, CSS Grid/Flexbox |

---

## Project Details

### 1. SeseDrive Pro — Interactive Adult Narrative Engine

**Core Architecture:**
```
User Input -> System Prompt Builder -> DeepSeek API -> Story Renderer
                ^                        |
           Narrative Module         AbortController
           Character Cards          Token Slicer (128K threshold)
           Preference Profile      Option Generator
```

**Key Innovations:**
- **Dynamic System Prompt Assembly Line**: Runtime concatenation of Narrative Module (JSON: personality/style/vocabulary bank), character cards, and user preferences into a complete System Prompt
- **Adaptive Token Slicer**: When estimated token count exceeds 128K threshold, automatically compresses the oldest 30% of history into summary blocks, retaining only the most recent 70%
- **Armor Break Prompt Matrix**: Multi-layer bypass strategies including Word Replacement Table and Recursive Thinking processes
- **AI Character Card Generation**: Generate complete character JSON from a one-sentence description
- **Narrative Module Training**: Provide sample text, AI extracts writing style and vocabulary, auto-generates new presets

### 2. Game Engine 5.0 — 108-Agent Layered Game Engine

**Agent Hierarchy:**
```
L0 Master Agent (x1)    -- God-level decision maker
  L1 Domain Agents (x11) -- Dialogue/Combat/Exploration/Atmosphere/Economy/Strategy/Simulation/Creation/Intimacy/Violence/Politics
    L2 Functional Agents (x25) -- Dialogue Beats/NPC Acting/Combat Rounds/Scene Rendering...
      L3 Atomic Agents (x54) -- Opening Dialogue/Attack Resolution/Wound Generation/Sensory Details...
  L4 Data Agents (x12)   -- Race/Geography/History/Items/Skills...
  L5 Tool Agents (x5)    -- Dice/Name Generator/Grammar Check/Translation/Summary
```

**Command Protocol:**
```
QUERY    -> Query world state
RESPOND  -> Fast food round response
DISPATCH -> Dispatch sub-agent
REVISE   -> Revise sub-agent output
FINALIZE -> Issue integrated final output
SYSTEM   -> System operation (export/import/new game)
```

**Creation Mode Multi-Stage Pipeline:**
```
Stage 1: Seed confirmation    -> L0 asks refinement questions
Stage 2: Refinement           -> L0 dispatches L1-08 World Creator
Stage 3: Framework display    -> L0 presents world summary
Stage 4: Confirmation & land  -> L0 FINALIZEs complete opening scene
```

**Key Innovations:**
- **IndexedDB Cold Storage (ArchiveDB)**: Async archival of old memories and narrative lines
- **Type-specific timeout control**: Different timeouts per agent category
- **In-game time system**: 1 real minute = 60 game minutes (adjustable)

### 3. Rant Generator v6.0 — Multi-Layer Aggressive Text Generator

**7-Layer Pipeline:**
```
L0 Scene ID -> L1 Role Injection -> L2 Intensity Reading -> L3 Dynamic Scheduling
    -> L4 Weakness Scan + Quote Match -> L5 Tactical Composition -> L6 Harmony Processing -> L7 Output
```

**30+ Species Classification Tags (A1-F4 taxonomy)**

**30+ Atomic Attack Skills (A1-H1)**

**Key Innovations:**
- **Fixed Intensity Skill Table**: Each intensity level (0-10) maps to a fixed skill set
- **AI Precision Tagging**: 369 built-in quotes with AI-generated 4-dimensional tags (intensity/style/target/emotion)
- **Real-time Intensity Preview**: Slider shows example output at each level

### 4. NovelCraft vFINAL+ — 15-Agent Novel Collaboration System

**9-Phase Writing Pipeline:**
```
Seed -> Requirements -> Worldview -> Characters -> Outline -> Review -> Writing -> Review -> Complete
```

**15 Agents from A0 to A14**, each with strict JSON output schemas and domain-specific prompts.

**Key Innovations:**
- **A12 Anti-Degradation Safety Net**: v1.7 fix for editor-agent visibility problem
- **Dexie.js IndexedDB wrapper** for project persistence
- **Dark/Light dual theme** via CSS variables
- **Checkpoint system** for timeline branching

### 5. Inference Grid — Multi-Dimensional Exhaustive Inference

**Core Algorithm: Combinatorial Dimensions x Exhaustive Reasoning**

**5 Core Dimensions x 5 Domain-Specific Dimensions** creating massive combinatorial space.

**9 Inference Levels (L0-L9)** with increasing agent counts and attack ratios.

**Key Innovations:**
- **Latin Hypercube Sampling** for uniform coverage when combinations exceed limits
- **Batched exhaustive generation** to avoid memory explosion at Level 9
- **Canvas heatmap visualization**
- **Triple-layer JSON repair chain**: extractJSON -> tailFixJSON -> AI repair
- **Auto domain detection** from situation description

### 6. Multi-Agent Chat — Group Chat Collaboration Platform

**Hierarchy**: Host > Admin > Member > Observer

**Interaction Protocol**: propose, vote, mute, unmute, invite, remove, listFriends, stop

**One-Vote Veto**: Any proposal requires unanimous consent; a single "disagree" kills it.

**Key Innovations:**
- **Pyodide WASM code sandbox** via Web Worker for Python execution
- **Virtual file system** with localStorage + IndexedDB dual storage
- **Context window auto-compression** by Host agent
- **13 built-in agents** with distinct role prompts

### 7. EvoAgent V4 — Self-Evolving AI Assistant

**Core Innovation — Skill Evolution Loop:**
```
Conversation -> Daily Reflection -> Judge Evaluation -> Skill Evolution -> New Version Deploy
```

**13 Tools** + **13 External Libraries** (lazy-loaded from CDN)

**Key Innovations:**
- **Skill JSON Schema validation** via AJV
- **3-judge evaluation system** (Rigorous/User Sim/Safety Auditor)
- **Budget control system** with user reserve ratio
- **Environment variable substitution** in Skills
- **Base64 Worker to eliminate escaping issues**

---

## Cross-Cutting Technical Challenges

### 1. Browser-Side Token Management
No server-side tiktoken. Each project uses different estimation strategies.

### 2. JSON Output Reliability
DeepSeek API JSON truncation is expected at high token outputs. Defense in depth:
```
Layer 1: extractJSON()    -> Regex match outermost braces
Layer 2: tailFixJSON()    -> Arithmetic brace completion
Layer 3: AI Repair        -> Request model to re-output
Layer 4: Fallback Defaults
```

### 3. Request Abort & Timeout
All projects use AbortController + categorized timeout strategies.

### 4. localStorage + IndexedDB Dual Storage
Hot data in localStorage, cold archives in IndexedDB, with automatic migration.

---

## Design Philosophy

```
1. Single file = application       No build step, no config, no npm
2. Zero external framework deps    Native DOM API + CSS Variables + Vanilla JS
3. Browser is the runtime          No servers, no databases
4. Users own their data            localStorage + IndexedDB
5. Users provide their API keys    Zero backend cost
6. Deep Prompt Engineering         Extensive System Prompt customization
7. Complete error handling         Retry/degrade/abort/recover at every layer
```

---

## How to Run

```
1. git clone https://github.com/Xiyinnnnnn/ai-html-workshop.git
2. Open any .html file in your browser
3. Enter your DeepSeek API Key in settings
4. Start using
```

**Requirements:**
- Modern browser (Chrome/Firefox/Edge/Safari)
- DeepSeek API Key ([platform.deepseek.com](https://platform.deepseek.com))
- Some features require internet for CDN resources

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| UI | CSS Grid/Flexbox/CSS Variables/Canvas |
| State | localStorage + IndexedDB |
| Network | fetch + AbortController |
| Sandbox | Web Worker + Pyodide WASM |
| Data | IndexedDB (+ Dexie.js in NovelCraft) |
| AI | DeepSeek v4-flash/v4-pro via REST API |
| Rendering | ECharts/Mermaid/KaTeX/highlight.js (on-demand) |
| Utils | Fuse.js/Pako/AJV/YAML/Math.js/SheetJS/Docx/PDF.js (on-demand) |

---

## License

MIT

```
                             ___________________________________________________
                             |  Built with pure HTML. No frameworks. No mercy.  |
                             |____________________________________________________|
```
