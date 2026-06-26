---
name: agentify-export-research
description: >
  Use when an 外贸工厂 / 跨境 OEM-ODM supplier wants a full go-to-market export brief that
  goes from "who we compete with / who to sell to / how to reach them" all the way to
  "which concrete product to make and the data backing it". Orchestrates two skills in
  sequence — agentify-b2b-market-research (competitors / ICP / outbound / inbound) then
  openclaw-ecommerce-product-research (platform-aware product selection) — and merges them
  into one integrated 出海调研报告. Input is usually a 1688 / Alibaba supplier page.
  Triggers: "出海调研", "出海报告", "工厂出海", "整合调研", "市场调研+选品", "export market research",
  "go-to-market brief", "GTM + 选品".
---

# Agentify Export Research（外贸工厂出海 · 整合调研）

研究员身份：**Agentify AI 出海研究员**。

这是一个**编排 skill**：把两条已有 skill 串成一份可执行的工厂出海蓝图，不重复造轮子。

- **前半 = `agentify-b2b-market-research`** → 答"**谁在竞争 / 卖给谁 / 怎么打**"（竞品 / ICP / Outbound / Inbound）。
- **后半 = `openclaw-ecommerce-product-research`** → 答"**做哪个品 / 有数据背书**"（双平台趋势 / 真实销量 / 对标 / 痛点微创新 / 净利 / IP / AI 图）。
- **本 skill 的活 = 衔接 + 合稿**：把前半的 ICP/竞品/平台判断喂给后半选品，再按统一模板合成一份报告。

## 何时用本 skill（vs 单独用某一条）

- 只要竞品/ICP/获客打法 → 直接用 `agentify-b2b-market-research`。
- 只要选哪个品 → 直接用 `openclaw-ecommerce-product-research`。
- **要一份"从市场到具体产品"的完整出海报告** → 用本 skill 串起来。

## 前置

- 两条子 skill 必须已安装（`~/.claude/skills/agentify-b2b-market-research/`、`~/.claude/skills/openclaw-ecommerce-product-research/`）。
- 密钥各自走子 skill 的 `.env`（本 skill 不另存密钥）：选品侧需 `PANGOLIN_MCP_URL`/`TAVILY_API_KEY`/`EXA_API_KEY`/`ECHOTIK_API_*`/`KIE_API_KEY`。
- 输入：一个 1688 / Alibaba 工厂页 URL，或工厂名 + 一个店铺 URL。

> ⚠️ **脱敏铁律**（两条 skill 共用）：对外报告**只标原始来源**（Amazon / TikTok / Google Trends / Reddit / 1688 / 阿里国际站 / USPTO / ImportYeti 等），**不得出现上游数据厂商名**（Pangolinfo、Tavily、Exa、EchoTik、Kalodata 等）。

## 编排流程（按序执行，每阶段先出结论再进下一步）

### 阶段 A · B2B 市场调研（调用 `agentify-b2b-market-research`）
按该 skill 跑完它的全流程，产出：
1. 供应商快照（工厂/贸易/混合、OEM-ODM、MOQ、出口线索、定位）
2. Top 5 竞品**两套（海外目的地市场 + 中国国内 1688/阿里源头同行）** + **标杆/天花板品牌**（含反盲区三网：tier sweep / 需求侧反查 / 种子滚雪球）
3. ICP 分层（T1/T2/T3，买家角色/触发/痛点/proof/异议/成交形态）
4. Outbound（渠道/话术/CTA + **怎么找联系人**：海关数据 ImportYeti、LinkedIn、Vendor 门户、展会）
5. Inbound（社媒主阵地 per-channel play + 独立站 SEO/GEO）

> 🧭 **方向铁律（防串扰）**：阶段 A 的竞品/ICP **锚定供应商真实店铺的全品类**（storefront = truth anchor）。阶段 B 的选品是**前瞻下游建议**——它可以聚焦某个新品方向，但**绝不能反向给阶段 A 的竞品画像缩圈**。两者方向相反：A 看现状全貌，B 押未来单品。合稿时别让 B 的推品污染 A 的竞品范围。

### 衔接桥（本 skill 的核心增量）
把阶段 A 的结论转成阶段 B 的选品输入（单向：A→B，不反向）：
- **产品范围**：用供应商快照里"工厂产能覆盖的品类"框定选品候选（不推工厂做不了的品）。
- **平台判断**：用 ICP 的买家类型决定选品主战场——
  - ICP 偏 **B 端分销/项目** → 选品侧重 **Amazon/独立站（搜索电商）** 对标与净利。
  - ICP 偏 **B2C 卖家/达人带货生态** → 选品侧重 **TikTok（兴趣电商）** 真实销量与钩子。
  - 多数工厂两条都给，主战场跟着 Tier 1 ICP 走。
- **差异化锚点**：把竞品分析里的"标杆痛点 + 工厂独特能力（如一件起印/印错包赔）"带进选品的微创新建议。

### 阶段 B · 选品（调用 `openclaw-ecommerce-product-research`）
在阶段 A 框定的品类与平台里跑选品全流程：时间窗口 → 找场景 → 真实销量阈值（Amazon/EchoTik）→ 对标 → 评论挖改进点 → 净利测算 → IP 排查 → 钩子文案 → AI 出图 → 小批量验证计划。

### 阶段 C · 合稿（全保真，只增不减）
按 [`references/integrated-report-template.md`](references/integrated-report-template.md) 合成**一份**整合报告：**Part A（b2b 全量）+ Part B（选品全量）+ Part C（整合层）**。要点：
- 🚫 **不缩减铁律**：两个子 skill 的**每一节、每一张表、每一个字段都必须保留**，不得压成摘要。
  - Part A 保留 b2b 的全部模块：供应商快照、竞品(海外+国内+标杆+5维打分)、ICP 三层全字段、Outbound（分层打法 + 找联系人表 + starter 账户清单 + 2周节奏 + 每层 message/proof）、Inbound（社媒 per-channel + 3 pillars + 10 angles + 3 proof assets + SEO/GEO 全套 + 30天计划）。
  - Part B 保留选品的全部步骤：时间窗口 / 场景拆解 / 市场快照+机会窗口 / 社媒痛点 / IP / **逐品全字段**（对标/视觉卖点/微创新/净利/定价/运营/文案/验证/生图 prompt）/ 产品图。
  - 选品若已单独成文，Part B 仍**内联完整内容**（可在末尾附详版链接），**不要只给摘要+链接**。
- **Part C 是唯一的"压缩区"**：衔接说明（A→B 单向）+ 合并行动表（GTM 动作 + 选品验证 同一张 P1–P3 表）。这是整合的增量，不是用它替代前两部分。
- 🖼 **每模块配可视化图（图随文走，真实数据进图）**：
  - **数据型模块图 = 手写 SVG → 飞书画板**（`<whiteboard type="svg">…</whiteboard>`，`docs +update block_insert_after` 插到模块标题下）。文字精确、可编辑、不需上传权限——把该模块真实内容画进去，**禁做无字示意图**。插前可 browse 渲染 SVG 截图自检排版。
  - **gpt-image-2 只画产品 hero 图**（它画不准中文/数字），密钥 `KIE_API_KEY` 走 env/keychain **严禁入库**，配方见 openclaw skill `references/data-sources.md §5`，生成后肉眼校验文字。
- 用 lark-doc 落飞书文档进知识库（`docs +create --api-version v2`，归属 user；长文用 create 骨架 + `update --command append` 分段灌，避免单次过长）。AI 图用外链 `<img href=...>` 插入即可（飞书会自动 re-host 成永久素材）。
  > ⚠️ lark `append`（锚点 -1）偶发 `Block ID transform failed`；遇到改用 `block_insert_after` + 显式末块 id（`docs +fetch --detail with-ids` 取）。

## 硬性约束

- 不替子 skill 的活：竞品/ICP/选品的方法细节以各子 skill 为准，本 skill 只管衔接与合稿。
- 选品候选必须落在工厂真实产能内（阶段 A 快照为准）。
- 每个竞品/对标必须有真实可点击来源；选品推荐必须有真实对标（ASIN / TikTok 链接）。
- 第 7 节行动表必须**跨阶段合并**，不得前后两半互不相干。
- 脱敏铁律贯穿全程；缺数据写"待数据确认 / Not publicly verified"，不编。

## 报告模板

见 [`references/integrated-report-template.md`](references/integrated-report-template.md)。
