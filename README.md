# Agentify Export Research（外贸工厂出海 · 整合调研 skill）

> 🇨🇳 一个**编排 skill**：把"B2B 市场调研"和"选品"两条 skill 串成一份完整的工厂出海调研报告。前半答「谁在竞争 / 卖给谁 / 怎么打」，后半答「做哪个品 / 数据背书」，本 skill 负责衔接两边并按统一模板合稿。以 Agentify AI 出海研究员身份，对外报告只标原始来源。

> 🇬🇧 An **orchestrator skill** that chains two skills into one end-to-end export go-to-market brief for OEM/ODM factories: B2B market research (competitors / ICP / outbound / inbound) → product selection (platform-aware, data-backed) → one merged report. Reports cite raw sources only.

## 依赖 / Depends on

两条子 skill 必须已安装：

| 子 skill | 角色 |
|---|---|
| [`agentify-b2b-market-research`](https://github.com/X-RayLuan/agentify-b2b-market-research) | 前半：竞品 / ICP / Outbound / Inbound |
| [`openclaw-ecommerce-product-research`](https://github.com/X-RayLuan/OpenClaw-Ecommerce-Product-Research) | 后半：双平台选品（Amazon 搜索电商 + TikTok 兴趣电商，含 EchoTik 真实销量） |

密钥各自走子 skill 的 `.env`，本 skill 不另存密钥。

## 用法 / Usage

把本仓库放进 skills 目录（`~/.claude/skills/agentify-export-research/`），给一个 1688/Alibaba 工厂页 URL，说"出海调研 / 工厂出海 / 整合调研 / 市场调研+选品"即可触发。

## 流程 / Flow

```
阶段 A  b2b-market-research  →  竞品 / ICP / Outbound / Inbound
   │
   ▼  衔接桥：ICP 定主战场（搜索电商 or 兴趣电商）；快照框定品类；竞品痛点喂微创新
   │
阶段 B  openclaw-ecommerce-product-research  →  时间窗口 / 找场景 / 真实销量 / 对标 / 净利 / IP / AI图
   │
   ▼
阶段 C  全保真合稿：Part A(b2b全量) + Part B(选品全量) + Part C(整合层)，落飞书文档
        ⚠️ 只增不减——两个子 skill 的每个模块/字段都保留，整合的增量只在 Part C
        （衔接说明 + GTM/选品验证 合并行动表）
```

## 结构 / Structure

- `SKILL.md` — 编排流程、衔接桥逻辑、硬性约束
- `references/integrated-report-template.md` — 8 节整合报告模板

## 脱敏 / Source masking

对外报告只标原始来源（Amazon / TikTok / Google Trends / Reddit / 1688 / USPTO / ImportYeti），不出现上游数据厂商名。
