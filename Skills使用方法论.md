# Matt Pocock Skills 使用方法论

> 这套 skills 来自 [mattpocock/skills](https://github.com/mattpocock/skills)（174k stars），核心理念：**用工程纪律驾驭 AI 编码代理，而不是盲目 vibe coding。**

## 一、安装状态

- **41 个 skills** 已安装到 `.agents/skills/` 目录
- **Cursor 元技能** 已创建于 `.cursor/skills/use-mattpocock-skills/`
- 支持 Cursor、Claude Code、Codex、Amp 等多个 Agent

## 二、核心哲学：四个痛点 → 四个解法

| # | 痛点 | 根因 | 解法 Skills |
|---|------|------|-------------|
| 1 | Agent 没做我想要的 | 沟通鸿沟，需求不对齐 | `/grill-with-docs` `/grill-me` |
| 2 | Agent 太啰嗦 | 没有共享语言 | `/domain-modeling` + `CONTEXT.md` |
| 3 | 代码不能用 | 缺乏反馈循环 | `/tdd` `/diagnosing-bugs` |
| 4 | 代码变泥球 | 软件熵加速 | `/codebase-design` `/improve-codebase-architecture` |

## 三、Skills 全景图

### 3.1 工程类（日常编码）

#### 用户调用（你主动输入名字触发）

| Skill | 一句话说明 | 使用时机 |
|-------|-----------|---------|
| `/ask-matt` | 路由器：不知道用哪个 skill 就问它 | 迷茫时 |
| `/grill-with-docs` | 深度访谈 + 自动维护 CONTEXT.md 和 ADR | 每次开始新功能前 |
| `/to-spec` | 把对话整理成 PRD/Spec | 访谈结束后 |
| `/to-tickets` | 把 Spec 拆成纵切的 tracer-bullet 工单 | 多 session 的任务 |
| `/implement` | 按 spec/工单构建，内部驱动 /tdd 和 /code-review | 实际编码时 |
| `/wayfinder` | 规划超大任务的决策地图 | 迷雾重重的大项目 |
| `/triage` | Issue 分诊：分类 → 验证 → 写 Agent Brief | 处理积压 issue |
| `/improve-codebase-architecture` | 扫描架构摩擦点，生成 HTML 报告 | 每隔几天跑一次 |
| `/setup-matt-pocock-skills` | 首次配置：issue 追踪器 + 标签 + 文档布局 | 每个仓库跑一次 |

#### 模型调用（Agent 也会自动触发）

| Skill | 一句话说明 |
|-------|-----------|
| `/prototype` | 一次性原型：回答设计问题 |
| `/diagnosing-bugs` | 硬 bug 诊断循环 |
| `/research` | 后台代理查阅一手资料 |
| `/tdd` | 红-绿-重构循环 |
| `/domain-modeling` | 构建/打磨领域模型 |
| `/codebase-design` | 深模块设计词汇表 |
| `/code-review` | 双轴代码审查 |
| `/resolving-merge-conflicts` | 逐 hunk 解决合并冲突 |

### 3.2 生产力类（通用工作流）

| Skill | 一句话说明 |
|-------|-----------|
| `/grill-me` | 无状态深度访谈（无需代码库） |
| `/handoff` | 压缩对话为交接文档 |
| `/teach` | 多 session 教学工作空间 |
| `/writing-great-skills` | 写好 skill 的参考手册 |
| `/grilling` | 访谈原语（被其他 skill 调用） |

## 四、主流程：从想法到上线

```
想法 ──→ /grill-with-docs ──→ /to-spec ──→ /to-tickets ──→ /implement ──→ 上线
             │                                                  │
             │ 需要原型？                              每个工单使用：
             ├─→ /handoff → /prototype → /handoff 回来    ├─ /tdd
             │                                            └─ /code-review
             │ 超大项目？
             └─→ /wayfinder → 解决决策工单 → /to-spec
```

### 入口匝道

- **积压 Bug/请求** → `/triage` → 产出 agent-ready 工单 → `/implement`
- **紧急 Bug** → `/diagnosing-bugs` → 修复 → 可能触发 `/improve-codebase-architecture`
- **大而模糊的项目** → `/wayfinder` → 决策地图 → 路径清晰后 → `/to-spec`

## 五、上下文管理规则

1. **保持连续**：`/grill-with-docs` → `/to-spec` → `/to-tickets` 在**同一个上下文窗口**完成，不要中途 compact
2. **隔离实现**：每个 `/implement` 在**新的上下文**中启动，只带工单信息
3. **Smart Zone**：接近 ~120k tokens 时，用 `/handoff` 保存 → 新 session 继续
4. **Wayfinder**：每个 session 最多解决一个决策工单（research 工单除外）

## 六、快速入门指南

### 第一次使用（仅需一次）

```bash
# 1. 已完成安装（41 skills 在 .agents/skills/ 中）

# 2. 在 Agent 中运行 setup（配置 issue 追踪器等）
/setup-matt-pocock-skills
```

### 日常使用决策树

```
你想做什么？
├── 开发新功能 → /grill-with-docs → /to-spec → /to-tickets → /implement
├── 修复 Bug
│   ├── 简单 Bug → /tdd
│   └── 难 Bug → /diagnosing-bugs
├── 改善架构 → /improve-codebase-architecture
├── 审查代码 → /code-review
├── 处理 Issue → /triage
├── 做原型 → /prototype
├── 做调研 → /research
├── 学习新技术 → /teach
├── 换 Session → /handoff
└── 不知道用啥 → /ask-matt 或 /use-mattpocock-skills
```

## 七、元技能：`/use-mattpocock-skills`

为了简化海量 skills 的使用，我创建了一个 Cursor 元技能：

- 位置：`.cursor/skills/use-mattpocock-skills/SKILL.md`
- 功能：
  - **决策树**：根据你想做什么，推荐正确的 skill
  - **快速参考表**：所有 skill 分类一目了然
  - **工作流菜谱**：12 个常见场景的步骤指南（见 `WORKFLOWS.md`）
  - **上下文管理规则**：何时保持/切换/交接上下文

Agent 会自动识别并使用这个元技能（`disable-model-invocation` 未设置），所以当你不确定用哪个 skill 时，Agent 自己也能找到正确答案。

## 八、文件结构总览

```
Skills/
├── .agents/skills/              ← 41 个 mattpocock skills（标准格式）
│   ├── ask-matt/SKILL.md
│   ├── grill-with-docs/SKILL.md
│   ├── tdd/SKILL.md
│   ├── implement/SKILL.md
│   ├── ...
│   └── (共 41 个)
├── .cursor/skills/              ← Cursor 专用技能
│   └── use-mattpocock-skills/   ← 元技能（导航器）
│       ├── SKILL.md             ← 主文件：决策树 + 分类表
│       └── WORKFLOWS.md         ← 12 个工作流菜谱
└── Skills使用方法论.md           ← 本文档
```
