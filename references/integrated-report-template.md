# 出海调研报告（整合版）模板 · by Agentify AI 出海研究员

> **全保真原则**：整合 = `agentify-b2b-market-research` 全量（Part A）+ `openclaw-ecommerce-product-research` 全量（Part B）+ 整合层（Part C）。**不缩减任何子 skill 的模块或字段，只增不减**。两个子模板的每一节、每一张表、每一个字段都要保留；整合的增量在 Part C（衔接 + 合并行动表），不是把前两部分压成摘要。
> 来源只标原始源（Amazon / TikTok / Google Trends / Reddit / 1688 / 阿里国际站 / USPTO / ImportYeti）。**不出现上游数据厂商名。** 缺数据写"待数据确认 / Not publicly verified"。
> 🖼 **每模块配可视化图（图随文走）**：A1–A5 / B1–B6 / C1–C2 每个模块标题下配一张**承载该模块真实数据/文案**的可视化图。
> - **数据型模块图 = 手写 SVG → 飞书画板**（`<whiteboard type="svg">…</whiteboard>` 经 `docs +update block_insert_after`）。文字精确（中文/数字清晰）、可编辑、**不需上传权限**。把该模块的真实内容（竞品名单、ICP三层、阈值数字、行动项…）画进图里，不要做"无字示意图"。
> - **gpt-image-2 只用于产品 hero 图**（如推荐主攻品实拍风），因为它**画不准文字**（中文/数字必糊），仅适合视觉氛围图；用 `KIE_API_KEY`（来自 openclaw skill `.env`，**密钥不入库**），配方见 `references/data-sources.md §5`，生成后肉眼校验文字。
> - 自检：SVG 插入前可用 browse 渲染 `file://…svg` 截图肉眼核对排版不溢出。

# 📋 {{工厂名}}出海市场调研报告（整合版）

> 顶部 callout：本报告把 B2B 出海调研（Part A）与选品（Part B）两条完整流程合为一份蓝图，Part C 做衔接与行动合并。对象 / 日期 / 来源声明 / 竞品已按全品类锚定真实店铺。

---

# PART A · B2B 出海市场调研（全量采用 agentify-b2b-market-research，所有模块保留）

## A1. 供应商快照
| 字段 | 内容 |
|---|---|
| Company / 公司 | |
| Input URL / 店铺 | |
| Core products / 核心产品（全品类）| |
| Business model | factory / trader / hybrid；MOQ 与定制姿态（如"一件起印"）|
| OEM/ODM posture | |
| Visible proof | 认证 / 案例 / 展会 / 目录 |
| Current export clues | 目标市场 / 语言线索 |
| Positioning summary | 一句话差异点 |
> 8–12 bullet 供应商画像：什么核心 vs 边缘、工厂/贸易/混合、质量/认证信号、项目制/渠道制/通货批发、隐含的海外用例。

## A2. Top 5 竞品（海外 + 中国国内，两套）+ 标杆品牌
**A2a · Top 5 海外竞品（目的地市场，按本厂全品类对标，非单一品类）**：
| 竞品 | 覆盖本厂哪些品类 | 类型 | 市场 | 内容/信任强项 | 威胁 | 来源 |
|---|---|---|---|---|---|---|

**A2b · Top 5 中国国内竞品（1688/阿里源头同行，优先同产业带集群 + 已出海者）**：
| 厂名 | 来源(1688/阿里) | 主营(与本厂重叠) | 起订量/价位 | 产能/牌级 | 是否已出海(阿里国际站/亚马逊?) | 威胁类型(直接/价格基准) | 相对本厂差异 |
|---|---|---|---|---|---|---|---|
> 每家国内同行必须分类：已出海=直接威胁 / 纯内贸=价格基准；并钉死本厂非价格差异点。

**A2c · 标杆/天花板（发现但归为非直接，研究不硬刚）**：
| 品牌 | 为何非直接 | 怎么用 |
|---|---|---|
> ⚠️ 别漏：① 高端/天花板（常不在 1688/Alibaba）② 平台型对手（POD 平台之于"一件起印"工厂）。
> 每个竞品打分（1–5）：product overlap / channel overlap / content strength / proof-trust strength / threat level。

## A3. ICP 客户画像（分层，每层全字段）
**Tier 1**：primary 细分 / buyer roles / trigger / pain points / proof required / objections / deal shape（样品-试点-批量-项目）
**Tier 2**：同上全字段
**Tier 3**：同上全字段
> 用 buying-committee + use-case 模型，不要停在宽泛行业标签；说明谁是 T1/T2/T3 及理由。

## A4. Outbound 获客方案（全字段）
**按 ICP 分层的打法**：
| ICP tier | target account types | target titles/roles | 渠道 | region priority | value prop | offer/CTA | 待补 proof |
|---|---|---|---|---|---|---|---|
渠道至少覆盖：email / LinkedIn / 分销-采购门户申请 / 展会-目录跟进。

**怎么找 ICP 联系人（公开源，禁造假；未确认标 Not publicly verified）**：
| 渠道 | 怎么用 | 适合 ICP |
|---|---|---|
| 海关/进口数据（Panjiva / ImportGenius / ImportYeti / 52WMB / Tradesns）| HS code + 品名 → 进口商名单 → LinkedIn 富化决策人 | 分销/进口商 |
| LinkedIn Sales Navigator | title（Procurement/FF&E/Purchasing）+ 行业筛 | 全层 |
| Vendor/Supplier 门户 | Become-a-Vendor / Supplier Registration 页 | 项目/酒店 |
| 展会 + 目录 | 参展+观众名单（广交会/Big5/KBIS/ISH）| T1/T2 |
| 公司站 + 工商登记 | Contact 页 + 企查查/天眼查/海外公开备案 | 全层 |
> **需求聚合方打法**：项目类 ICP 不逐个追终端买家，打 FF&E 采购公司 + fit-out 总包（各握几十个项目的 spec 决定权），进其 approved-vendor = 翻单。

**Starter 目标账户清单（需求聚合方优先）**：
| 账户 | Vendor entry URL | 公开 email/phone | 关键联系人 + LinkedIn（或 Not publicly verified）| 首触角度 |
|---|---|---|---|---|

**2 周触达节奏**：D1 首触 → D3 样品 → D6 案例 → D10 报价/MOQ → D14 邀约（每步写清动作与角度）。
**每个 ICP tier 额外说明**：在买什么 / 哪个 message angle 领头 / 哪个 proof asset 能拉回复率。

## A5. Inbound 方案（社媒 + 独立站 SEO/GEO，全字段）
### A5-1 社媒
- **Current gap**：
- **主阵地 + per-channel play（按本厂买家定，装饰/家居加 Pinterest）**：
| 渠道 | 定位 | 战术 | 优先级 |
|---|---|---|---|
- **3 content pillars**：
- **10 post angles**：
- **3 proof-first assets to create**：

### A5-2 独立站 SEO / GEO
- Positioning gap：
- Core keyword clusters：
- Comparison keywords（vs 平台型对手）：
- Buyer-intent 长尾问题：
- Must-build landing pages：
- Trust pages to add：
- GEO assets：llms.txt / FAQ blocks / 对比页 / 案例 / structured data
- 30-day content plan：

---

# PART B · 选品（全量采用 openclaw-ecommerce-product-research，所有步骤保留）

**平台与打法**：{{搜索电商 Amazon/独立站 ｜ 兴趣电商 TikTok}}（由 Part A 的 ICP 决定）　**主战场场景**：{{}}

## B1. 时间窗口（Google Trends, {{region}} 近 12 月）
| 关键词 | 峰值 | 达峰月 | 解读（上升/平稳/下降；是否更大搜索伞）|
|---|---|---|---|
> 🎯 结论：主词 + 早了/正好/晚了 + 按备货前置期倒推上架窗口。

## B2. 场景拆解（找场景不找产品）
| 细分场景 | 核心痛点 | 竞争(红/蓝海) | 客单价 | 毛利 | 平台契合度 | 优先级 |
|---|---|---|---|---|---|---|

## B3. 市场快照 + 机会窗口
- 搜：价格带/锚点/尺寸/竞争结构（评论数·头部品牌）·蓝海或红海
- 兴：起量信号(7天销量/总销量>40%) / 总销量<5000 / 售价$15-40 / 内容爆发力(总播放·带货视频数) / 转化效率(7天播放销量比<~50)；无实据标"待数据确认"

## B4. 社媒讨论：加分点 + 痛点（来源 Reddit / TikTok 评论 / Walmart 评论）
**👍 加分点**：满意 top3（各多少条）
**👎 雷区/痛点**：不满意 top3 + 有购买意愿未下单的原因（带原声引用，标注哪些可产品设计解决）

## B5. IP 风险（来源 USPTO 外观设计库）
高/中/低 + 依据；高风险须换次优对标重做该品。

## B6. 产品推荐（逐品，全字段）
### 产品 N ——【{{搜/兴}}｜{{场景}}】{{名}}
- 对标：{{ASIN 链接 / TikTok 视频·小店链接}}（价/星/评 或 7天增长·播放比）
- 主图/首帧视觉卖点元素逐条提取
- 微创新：功能微改 + 视觉强差异（回应趋势与痛点，能拍出"啪一下"记忆点）
- 净利测算：成本拆解 → 净利率 %（优秀>30/良好20-30/一般15-20/危险<15），盈亏平衡月销
- 定价：建议零售价 + 依据
- 运营：搜=上架窗/广告/冷启动/personalization ｜ 兴=钩子/达人/内容节奏/起量信号
- 文案：搜=Listing 标题/五点/后台词/A+ ｜ 兴=3 个前 3 秒钩子(≤15字)+15s 脚本
- 验证计划：首批 50-100 + $100-200 测，看 CTR/CVR/ROAS；3 天 ROAS>2 加投，7 天无单弃
- 生图 prompt：`{{可复用的 AI 生图 prompt}}`

## B7. 产品图（AI 生成，文字拼写已校验）
{{嵌入图}}

---

# PART C · 整合层（本 skill 的增量）

## C1. 衔接说明（A → B 单向）
- **ICP 定主战场**：Part A 的 Tier 1 ICP → Part B 的平台（B 端分销/项目→搜索电商；B2C 卖家/达人→兴趣电商）。
- **快照框定品类**：Part B 候选只落在 A1 的工厂真实产能内。
- **竞品痛点喂微创新**：A2 标杆痛点 + 工厂独特能力 → B6 微创新。
- ⚠️ 单向：B 不得反向给 A 的竞品范围缩圈（竞品锚 A1 全品类，非 B 的推品）。

## C2. 合并行动表（GTM + 选品验证，同一张 P1–P3）
| 优先级 | 动作（跨阶段合并）| Owner | 为何现在 |
|---|---|---|---|
| P1 | 选品卡位（B 的首批小批量验证）+ 同步 Outbound（ImportYeti 拉名单/卖家反查）| | |
| P1 | 建主阵地社媒，发 proof 内容（A5）| | |
| P2 | 独立站落地页 + vs 平台型对手对比页（A5-2）| | |
| P3 | 选品种草内容（达人联动，B 的运营）| | |
> 这张表是整合价值点：B 的验证动作与 A 的获客动作必须并列同一张表，不能各写各的。
