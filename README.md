# Agentify Export Research · 外贸工厂出海整合调研

> **EN** — An orchestrator skill that chains two skills into one end-to-end export go-to-market brief for OEM/ODM factories, then merges them with full fidelity and a per-module data visualization.
> **中文** — 一个**编排 skill**：把"B2B 市场调研"和"选品"两条 skill 串成一份完整的工厂出海调研报告，全保真合稿，并给每个模块配一张承载真实数据的可视化图。

As an **Agentify AI export analyst** / 以 **Agentify AI 出海研究员**身份产出，对外报告只标原始来源。

---

## What it does · 它做什么

**EN** — One run takes a `1688` / `Alibaba` supplier page and produces a single integrated report:

- **Part A — B2B market research** (delegated to `agentify-b2b-market-research`): supplier snapshot, **Top 5 overseas + Top 5 China-domestic competitors** + benchmark brands, tiered ICP, full outbound plan (incl. customs-data contact sourcing), full inbound plan (social + SEO/GEO).
- **Part B — Product selection** (delegated to `openclaw-ecommerce-product-research`): timing window, scenario decomposition, **real sales thresholds** (Amazon + TikTok via EchoTik), benchmark listings, review-mined micro-innovation, net-margin math, IP screening, hooks, AI product hero image.
- **Part C — Integration layer** (this skill's value-add): the A→B bridge + a **merged P1–P3 action table** combining GTM moves and selection-validation steps.

**中文** — 一次跑通：输入一个 1688/Alibaba 工厂页 → 输出一份整合报告：

- **Part A · B2B 调研**（调用 `agentify-b2b-market-research`）：供应商快照、**Top5 海外 + Top5 中国国内竞品** + 标杆品牌、分层 ICP、完整 Outbound（含海关数据找联系人）、完整 Inbound（社媒 + SEO/GEO）。
- **Part B · 选品**（调用 `openclaw-ecommerce-product-research`）：时间窗口、找场景、**真实销量阈值**（Amazon + TikTok/EchoTik）、对标、评论挖微创新、净利测算、IP 排查、钩子文案、AI 产品图。
- **Part C · 整合层**（本 skill 的增量）：A→B 衔接桥 + **合并的 P1–P3 行动表**（GTM 动作与选品验证拧成一张）。

---

## Design principles · 设计铁律

| Principle | EN | 中文 |
|---|---|---|
| **Full fidelity** | Part A & B keep **every** sub-skill module/field — never summarized. Only Part C is the "compression". | Part A/B 保留子 skill 的每节每字段，**只增不减**；唯一压缩区是 Part C。 |
| **Two competitor sets** | Map **overseas (destination-market)** AND **China-domestic (1688/Alibaba source peers)**; classify each domestic peer as already-exporting (direct threat) vs domestic-only (price benchmark). | 竞品同时映射**海外目的地**与**中国国内源头同行**；国内同行分"已出海=直接威胁"vs"纯内贸=价格基准"。 |
| **Storefront-anchored** | Competitor discovery anchors on the supplier's **real full product line**; the downstream selection pick must NOT narrow the competitor map. Direction is one-way A→B. | 竞品锚定供应商**真实店铺全品类**；下游选品**不得反向缩圈**竞品。方向单向 A→B。 |
| **Right tool per visual** | **Data-bearing module visuals = hand-authored SVG → Feishu whiteboard** (crisp text, editable, no upload scope). **gpt-image-2 only for product hero shots** (it cannot render accurate text/Chinese). | **数据型模块图 = 手写 SVG → 飞书画板**（文字精确、可编辑、不需上传权限）；**gpt-image-2 只画产品 hero**（画不准中文/数字）。 |
| **Source masking** | Cite raw sources only (Amazon / TikTok / Google Trends / Reddit / 1688 / USPTO / ImportYeti); never expose upstream data vendors. | 只标原始来源，不出现上游数据厂商名。 |

---

## Dependencies · 依赖

| Sub-skill | Role · 角色 | Repo |
|---|---|---|
| `agentify-b2b-market-research` | Part A — competitors / ICP / outbound / inbound | https://github.com/X-RayLuan/agentify-b2b-market-research |
| `openclaw-ecommerce-product-research` | Part B — platform-aware selection (Amazon search-commerce + TikTok interest-commerce via EchoTik) | https://github.com/X-RayLuan/OpenClaw-Ecommerce-Product-Research |

Secrets live in each sub-skill's own `.env` (this skill stores none). Selection side needs `PANGOLIN_MCP_URL` / `TAVILY_API_KEY` / `EXA_API_KEY` / `ECHOTIK_API_USERNAME`+`ECHOTIK_API_PASSWORD` / `KIE_API_KEY`. · 密钥各自走子 skill 的 `.env`，本 skill 不另存密钥。

---

## Flow · 流程

```
Stage A  agentify-b2b-market-research   →  competitors(海外+国内) / ICP / Outbound / Inbound
   │  Bridge: ICP picks the channel (search vs interest commerce); snapshot scopes the
   │          category; competitor pain → micro-innovation.  ONE-WAY A→B.
Stage B  openclaw-ecommerce-product-research  →  timing / scenario / real sales / benchmark / margin / IP / hooks / image
   │
Stage C  Full-fidelity merge: Part A + Part B + Part C(bridge + merged P1–P3 action table)
         + per-module SVG-whiteboard visualization, written to a Feishu doc.
```

## Usage · 用法

Drop into your skills dir (`~/.claude/skills/agentify-export-research/`), give a 1688/Alibaba supplier URL, and say "出海调研 / 工厂出海 / 整合调研 / export market research". · 放进 skills 目录，给工厂页 URL 并说触发词即可。

## Structure · 结构

- `SKILL.md` — orchestration flow, A→B bridge, full-fidelity & visualization rules · 编排流程、衔接桥、全保真与可视化规则
- `references/integrated-report-template.md` — the full 3-part (A/B/C) report template · 三部分整合报告模板

---

## Changelog · 更新记录

### 2026-06-26
- **EN** Initial release: orchestrates b2b-market-research + ecommerce-product-research into one export brief with an A→B bridge and a merged action table.
  **中文** 首发：把两条 skill 编排成一份出海报告，含 A→B 衔接桥与合并行动表。
- **EN** Competitors split into **Top 5 overseas + Top 5 China-domestic** (source peers); domestic peers classified exporting-vs-domestic-only with a named non-price differentiator.
  **中文** 竞品拆成 **Top5 海外 + Top5 中国国内**；国内同行分"已出海/纯内贸"并钉死非价格差异点。
- **EN** **Storefront-anchor rule** + one-way A→B: selection output must not narrow the competitor map; competitors map the supplier's full product line.
  **中文** 新增**锚定真实店铺**铁律 + 单向 A→B：选品不得反向缩圈竞品；竞品覆盖全品类。
- **EN** **Full-fidelity merge**: Part A/B keep every sub-skill module/field; only Part C compresses.
  **中文** **全保真合稿**：Part A/B 保留子 skill 每个模块/字段，只 Part C 压缩。
- **EN** **Per-module visualization**: data modules use hand-authored **SVG → Feishu whiteboard** (crisp text); gpt-image-2 reserved for product hero shots only.
  **中文** **每模块可视化**：数据图用手写 **SVG → 飞书画板**（文字精确）；gpt-image-2 仅用于产品 hero。
- **EN** Ops note baked in: lark `append`(-1) can hit a block-anchor bug → use `block_insert_after` with an explicit last-block id.
  **中文** 固化运维坑：lark `append`(-1) 偶发锚点 bug → 改用显式末块 id 的 `block_insert_after`。
