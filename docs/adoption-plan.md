# Skills 渐进式采用计划

> 不要一次学完 41 个 skills。分阶段采用，每个阶段只加 2-3 个，用熟了再加下一批。

## Phase 1: 对齐意图（第 1 周）

**目标**：让 Agent 在动手前先理解你要什么。

| 要学的 Skill | 怎么用 | 什么时候用 |
|-------------|--------|-----------|
| `/grill-with-docs` | 每次开始新功能前，先跑一轮深度访谈 | 任何新功能 / 新需求 |
| `/grill-me` | 不在代码库里也能用的快速访谈 | 技术方案讨论、架构决策 |

**练习**：挑一个你正在做的功能，用 `/grill-with-docs` 跑一遍，感受"先对齐再动手"的区别。

**Loop 检查点**：一周后用 `/skills-review` 记录体验。

---

## Phase 2: 建立工作流（第 2-3 周）

**目标**：有清晰的流程可循，不再临时想怎么用。

| 要学的 Skill | 怎么用 |
|-------------|--------|
| `/to-spec` | 访谈结束后，把对话整理成 Spec |
| `/to-tickets` | 把 Spec 拆成可执行的工单 |
| `/implement` | 按工单逐个实现 |

**主流程**：`/grill-with-docs` → `/to-spec` → `/to-tickets` → `/implement`

**练习**：用完整主流程做一个真实功能。

---

## Phase 3: 质量反馈循环（第 4-5 周）

**目标**：代码写完就有信心，不再靠手动验证。

| 要学的 Skill | 怎么用 |
|-------------|--------|
| `/tdd` | 红-绿-重构：先写失败测试，再写代码让它通过 |
| `/code-review` | 完成后做双轴审查（标准 + Spec） |
| `/diagnosing-bugs` | 遇到难 bug 时用诊断循环 |

**练习**：用 `/tdd` 修一个真实 bug。

---

## Phase 4: 上下文管理（第 6-7 周）

**目标**：复杂任务不再崩溃。

| 要学的 Skill | 怎么用 |
|-------------|--------|
| `/handoff` | Session 之间的交接 |
| `/wayfinder` | 超大任务的决策地图 |
| `上下文规则` | grill → spec → tickets 保持同一窗口；implement 每次新窗口 |

**练习**：用 `/wayfinder` 规划一个大项目。

---

## Phase 5: 架构与持续改进（第 8 周+）

**目标**：代码库越用越好，不是越用越烂。

| 要学的 Skill | 怎么用 |
|-------------|--------|
| `/improve-codebase-architecture` | 每周跑一次，扫描架构摩擦点 |
| `/domain-modeling` | 维护共享语言，让 Agent 越来越懂你的项目 |
| `/skills-review` | 每个阶段结束后回顾 skills 使用体验 |

---

## 每个项目的快速启动清单

在新项目中启用 skills：

```bash
# 1. 安装 skills
npx skills@latest add mattpocock/skills

# 2. 配置仓库（跑一次）
# 在 Agent 中说：请按照 /setup-matt-pocock-skills 配置这个仓库

# 3. 开始使用
# 新功能：/grill-with-docs → /to-spec → /to-tickets → /implement
# 修 bug：/diagnosing-bugs 或 /tdd
# 不确定用啥：/use-mattpocock-skills
```

## 闭环机制

```
每周：
  1. 使用 skills 完成日常工作
  2. 遇到摩擦 → 记录到 docs/skills-changelog.md
  3. 每周五用 /skills-review 回顾本周
  4. 小改进 → 直接编辑 .agents/skills/<name>/SKILL.md
  5. 大改进 → 用 /writing-great-skills 重新设计
  6. 下周继续，循环往复
```
