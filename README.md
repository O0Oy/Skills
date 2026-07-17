# Agent Skills Workspace

基于 [mattpocock/skills](https://github.com/mattpocock/skills) 搭建的 AI 编码代理技能库，包含一个**元技能导航器**，让 41 个 skills 触手可及。

## 快速上手

```bash
# 已安装完成，直接在 Cursor / Claude Code 中使用
# 不知道用哪个 skill？让 Agent 自动路由：
/use-mattpocock-skills

# 或者直接使用最常用的流程：
/grill-with-docs    # 深度访谈，对齐需求
/to-spec            # 整理成 Spec
/to-tickets         # 拆成工单
/implement          # 逐个实现
```

## 核心流程

```
想法 ──→ /grill-with-docs ──→ /to-spec ──→ /to-tickets ──→ /implement ──→ 上线
             │                                                  │
             │ 需要原型？                              每个工单用：
             ├─ /handoff → /prototype → /handoff 回来    ├─ /tdd
             │                                           └─ /code-review
             │ 超大项目？
             └─ /wayfinder → 决策地图 → /to-spec
```

## 场景速查

| 你想做什么 | 用哪个 Skill |
|-----------|-------------|
| 开发新功能 | `/grill-with-docs` → `/to-spec` → `/to-tickets` → `/implement` |
| 修简单 Bug | `/tdd` |
| 修难 Bug | `/diagnosing-bugs` |
| 改善架构 | `/improve-codebase-architecture` |
| 审查代码 | `/code-review` |
| 处理 Issue | `/triage` |
| 做原型 | `/prototype` |
| 做调研 | `/research` |
| 学新东西 | `/teach` |
| 换 Session | `/handoff` |
| 不知道用啥 | `/ask-matt` 或 `/use-mattpocock-skills` |

## 文件结构

```
├── .agents/skills/              # 41 个 mattpocock skills
├── .cursor/skills/
│   └── use-mattpocock-skills/   # 元技能导航器
│       ├── SKILL.md             # 决策树 + 分类速查
│       └── WORKFLOWS.md         # 12 个工作流菜谱
├── AGENTS.md                    # Agent 配置入口
├── docs/agents/                 # Issue 追踪器 + 标签 + 领域文档配置
├── Skills使用方法论.md           # 中文完整方法论
└── README.md                    # 本文件
```

## 致谢

- [Matt Pocock](https://github.com/mattpocock) — 原始 skills 作者
- [skills.sh](https://skills.sh) — Skills 安装器

## License

Skills 内容遵循 [MIT License](https://github.com/mattpocock/skills/blob/main/LICENSE)。
