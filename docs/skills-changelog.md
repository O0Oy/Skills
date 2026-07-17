# Skills Changelog — 使用反馈记录

## 2026-07-17 — /grill-me (首次试用)

**Context**: 通过 /grill-me 的访谈流程了解自身使用场景，设计 skills 推广策略
**Worked**: 访谈流程清晰，一个问题一个问题问，不会被淹没
**Friction**: 在 Cursor 中没有 `/grill-me` 的原生触发方式，需要手动说"按照 grilling skill 来访谈我"
**Action**: 已创建元技能 use-mattpocock-skills 作为路由器；后续考虑为高频 skills 创建 Cursor 快捷触发方式

---

## 用户画像（从首次 grilling 中提取）

- **场景**: 全栈开发 + 多种混合场景
- **项目数**: 5+ 个同时维护
- **痛点** (全部命中):
  1. Agent 不理解意图 → `/grill-with-docs`
  2. 代码质量差 → `/tdd` + `/code-review` + `/codebase-design`
  3. 上下文窗口不够 → `/handoff` + `/to-tickets` 拆分 + 上下文管理规则
  4. 没有工作流 → 主流程 + 元技能路由
  5. 测试不足 → `/tdd` 红-绿-重构循环
