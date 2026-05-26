---
name: industry-radar
description: >
  行业产品与竞争情报雷达——为户外/院落场景工具集成商（三大硬件平台 + GITRYIN）自动采集、分析、可视化行业动态。使用 web_search 对竞品、行业趋势、北美市场、相邻赛道、渠道政策、出海品牌等多个维度做情报收集，最终生成一份浅色、符合麦肯锡数据呈现标准的 HTML 卡片式情报看板（非书文档、非线性呈现），每条信号均链接到原文出处。Make sure to use this skill whenever 用户说"跑一下雷达""出一份行业情报报告""看看最近竞品有什么动作""市场上有什么新动向""搜一下行业最新进展""做一次情报收集""帮我看看行业动态"，或任何需要定期/即时对行业做情报扫描的场景——即使用户没有显式说"雷达"或"skill"这个词。
compatibility:
  tools:
    - web_search
    - create_file
    - present_files
---

# Industry Radar Skill
## 户外工具行业 · 产品与公司动态雷达

---

## 一、Skill 定位

本 Skill 是一个 **AI 驱动的行业情报扫描引擎**，服务于户外/院落场景工具集成商（以下简称"公司"）的战略与产品决策。

**公司背景锚点（执行时的情报过滤基准）：**
- 三大硬件平台：通水通电 / 通尘通电 / 大储能 56V+
- 独立品牌：GITRYIN（家居用电场景）
- 自有品牌观察对象：Giraffe Tools（通水 / 清洁 / 收纳相关产品与品牌声量）
- 孵化方向：Desktop AI / GiSpace / Toolmate
- 核心市场：北美（DIY 用户为主）+ 国内
- 传统竞品：DeWalt、Milwaukee、Makita、EGO、Greenworks、Ryobi、Husqvarna、Worx、Gardena
- 智能园艺 / 灌溉品牌：RainPoint、Rachio、Orbit B-hyve、Rain Bird、Hunter Hydrawise
- 出海同代竞品：Fanttik、Hoto、Litheli、MOVA、Aiper 等

---

## 二、雷达扫描维度（7 个频道）

每次运行时，按以下频道执行搜索，每频道 2-4 条 query。

### 频道 A · 竞品动态
```
- "DeWalt Milwaukee EGO outdoor power tools new product 2026"
- "Greenworks Ryobi Makita cordless garden tools launch"
- "outdoor tools brand acquisition partnership funding 2026"
```
重点：传统电动工具 / 户外工具品牌的新品发布、并购融资、价格策略、渠道变化

### 频道 B · 行业技术趋势
```
- "outdoor power tools AI smart automation 2026"
- "56V battery platform cordless tools trend"
- "robotic lawn mower garden automation technology"
- "smart irrigation soil sensor weather based watering AI 2026"
```
重点：电池平台演进、AI/自动化渗透、智能化路线图、智能灌溉闭环

### 频道 C · 北美市场动态
```
- "North America DIY outdoor tools market trends 2026"
- "Amazon outdoor garden tools best sellers category changes"
- "TikTok Shop outdoor garden tools trending"
- "smart irrigation garden watering Amazon Walmart Lowe's Home Depot 2026"
```
重点：市场规模、亚马逊类目变化、内容渠道、DIY 趋势

### 频道 D · 相邻赛道 · 智能家居 & Agent 硬件
```
- "smart home outdoor integration AI agent hardware 2026"
- "pool robot garden robot ecosystem CES"
- "home automation garden IoT sensor platform"
- "smart garden ecosystem robotic mower irrigation soil sensor app"
```
重点：相邻领域融合机会、竞争威胁、技术迁移路径

### 频道 E · 智能灌溉 / 水系统（重点频道）
```
- "Gardena smart SILENO smart system irrigation soil sensor news 2026"
- "RainPoint all-in-one smart irrigation system CES 2026"
- "Giraffe Tools retractable hose reel pressure washer news 2026"
- "Rachio Orbit B-hyve Rain Bird smart irrigation 2026"
```
重点：智能灌溉、通水通电、软管 / 卷管器、高压清洗、水泵、阀控、土壤传感器、天气数据、App 控制、零售渠道；需固定跟踪 Gardena、RainPoint、Giraffe Tools，并观察 Rachio、Orbit B-hyve、Rain Bird、Hunter Hydrawise 作为类目基准

### 频道 F · 宏观与政策信号
```
- "US tariff power tools lithium battery import China 2026"
- "US China trade policy hardware Section 301"
- "outdoor lifestyle consumer spending trend 2026"
```
重点：关税政策、贸易法律变化、消费趋势

### 频道 G · 跨境出海品牌观察（重点频道）
```
- "Fanttik Hoto cross-border brand tools new product 2026"
- "Chinese DTC tool brands TikTok Shop strategy 2026"
- "Litheli Aiper MOVA outdoor brand North America expansion"
```
重点：出海工具品牌的获客模型、渠道升级、品牌化路径、团队规模——
这一频道关注与公司"同代"的中国出海品牌，是判断竞争格局演变的核心窗口。
观察对象不限于 Fanttik / Hoto，应持续扩充（如 Anker 系、Baseus、Ecoflow 等
跨界进入工具/户外场景的品牌）。

---

## 三、执行流程

### Step 1 · 搜索执行
对 7 个频道逐一执行 web_search，每个频道至少 2 条 query。
- query 优先英文（针对北美市场）
- 优先最近 30-90 天结果
- 某频道结果弱时，替换关键词重搜一次
- **记录每条情报的原文 URL**（生成可点击链接必需）

### Step 2 · 情报提炼
每条情报记录格式：
```
{
  headline: "结论型行动标题（见第五节铁律）",
  channel: "A-G",
  signal_type: "新品发布 | 融资并购 | 技术趋势 | 政策风险 | 市场机会 | 渠道变化 | 竞争模型",
  urgency: "高 | 中 | 低",
  summary: "2-3 句核心摘要",
  implication: "对公司的战略含义（从公司视角，见第五节）",
  source_name: "来源名称",
  source_url: "原文完整 URL",
  date: "日期"
}
```
每频道提炼 2-4 条，全报告 17-24 条。

### Step 2.5 · 品牌声量对比分析
每次扫描必须生成一张品牌声量对比表，至少覆盖：
- Giraffe Tools（自有品牌）
- Gardena
- RainPoint
- Rachio
- Orbit B-hyve
- Rain Bird / Hunter Hydrawise（二选一或同时纳入）

品牌声量不使用单一搜索结果数作为结论，而采用 5 个可复核维度打分（1-5 分）：
- Owned：官网 / newsroom / product page 的更新活跃度
- Earned：媒体报道、测评、奖项、榜单、PR Newswire / GlobeNewswire 等外部曝光
- Retail：Amazon、Home Depot、Lowe's、Walmart、Costco、Tractor Supply 等渠道可见度
- Social / UGC：TikTok、YouTube、Reddit、论坛、达人内容与真实用户讨论
- Strategic Fit：与公司三大平台，尤其通水通电平台的战略相关度

输出字段：
```
{
  brand: "品牌",
  category: "品牌类型 / 核心品类",
  owned: 1-5,
  earned: 1-5,
  retail: 1-5,
  social_ugc: 1-5,
  strategic_fit: 1-5,
  total: "总分",
  readout: "一句话判断",
  evidence_urls: ["URL1", "URL2"]
}
```

### Step 3 · 生成 HTML 情报看板
调用 create_file 生成 HTML，严格按第四节规范。

### Step 4 · 输出文件
调用 present_files 呈现给用户。

### Step 5 · Obsidian 历史存储与去重
每次报告必须同步生成一份 Obsidian 友好的 Markdown 底稿，用于长期追溯、去重和复盘。

建议目录：
```
obsidian/Industry Radar/YYYY/YYYY-MM-DD - 户外工具行业雷达.md
obsidian/Industry Radar/index.md
```

Markdown 底稿必须包含：
- YAML frontmatter：`date`、`scan_window`、`channels`、`brands`、`source_count`、`html_report`
- 本次核心结论
- 情报信号表：每条包含 `signal_id`、频道、品牌、标题、摘要、战略含义、来源 URL、日期
- 品牌声量对比表
- 去重规则说明

去重规则：
- `signal_id = date + channel + brand + canonical_url_slug`
- 若同一 `canonical_url_slug` 在 90 天内重复出现，只更新旧信号的 `last_seen` 与新增备注，不新增卡片
- 同一新闻被多个转载站复制时，优先保留原始来源；若找不到原始来源，保留最早发布时间来源
- 对品牌声量表保留每次快照，不去重，用于看趋势

---

## 四、HTML 情报看板设计规范（浅色 · 麦肯锡标准）

### 4.1 整体风格
- **主题**：浅色商业报告风。白底卡片 + 浅灰页面背景，专业、克制、高信息密度
- **页面背景**：#f4f5f7　**卡片底**：#ffffff　**深色区块（页眉/页脚）**：海军蓝 #051c2c
- **字体**：标题用 'Newsreader'（衬线，编辑感）；正文与数据用 'IBM Plex Sans'；数据/来源用 'IBM Plex Mono'

### 4.2 麦肯锡数据呈现铁律（必须遵守）
1. **结论型标题**：每张卡片标题必须是带动词、有立场的完整结论句，不能是名词短语。
   - ❌「EGO 商用新品」　✅「EGO 用 Fleet App＋商用硬件抢先落地软硬一体，正面压迫公司 Agent 化路径」
2. **克制配色 / 数据墨水最大化**：灰度为基线，颜色只用于承载信息——
   海军蓝=强调、红 #c0392b=高优先级/警示、琥珀 #b07d1e=中优先级、绿 #2c7a52=机会。
   禁止 3D、阴影渐变、彩虹色、装饰性色块。
3. **图表必有比较**：顶部的频道分布图用横向条形图、按数值降序、数据标签内联、无多余坐标轴。
4. **三层金字塔结构**：顶部核心结论 + KPI → 中部分频道情报卡 → 底部方法说明。

### 4.3 页面结构
```
┌──────────────────────────────────────────────┐
│ MASTHEAD（海军蓝）：雷达标识 + 扫描日期 + 状态  │
├──────────────────────────────────────────────┤
│ EXEC SUMMARY：一句话核心结论 + 5 个 KPI 卡片    │
├──────────────────────────────────────────────┤
│ CHART：各频道情报分布横向条形图（麦肯锡式）      │
├──────────────────────────────────────────────┤
│ BRAND VOICE：品牌声量对比分析                  │
├──────────────────────────────────────────────┤
│ FILTER BAR：按频道 / 紧急度筛选（sticky 吸顶）  │
├──────────────────────────────────────────────┤
│ CARD GRID：情报卡片，3 列响应式                 │
├──────────────────────────────────────────────┤
│ FOOTER（海军蓝）：方法说明 + 下次扫描时间        │
└──────────────────────────────────────────────┘
```

### 4.4 卡片规范（关键）
每张情报卡片是一个 **可点击的 `<a>` 链接**，`href` 指向原文 URL，`target="_blank"`：
- 顶部彩条标识紧急度（红/琥珀/灰）
- 频道标签 + 信号类型 + 紧急度徽章
- 结论型标题（衬线字体）
- 核心摘要 2-3 句
- 「战略含义」区块（左边框高亮色，从公司视角写）
- 卡片页脚：来源名称 + 日期 + 「阅读原文 ↗」链接
- hover：轻微上浮 + 蓝色描边，「阅读原文」箭头位移——提示可点击

### 4.5 交互
- 频道筛选 + 紧急度筛选（纯 JS，切换 `.hidden`）
- 卡片加载渐入（staggered animation-delay）
- 不使用任何浏览器存储 API

---

## 五、情报解读原则（战略含义字段）

「战略含义」必须从公司视角写，落到具体平台/部门/动作，不能是泛泛的行业判断。

❌ 「这说明行业正在向智能化转型。」
✅ 「EGO 的 Fleet App＋硬件组合与公司『硬件×软件×Agent』路径高度重叠且已商业化，需跟踪其 App 功能边界是否会延伸到家用场景。」

❌ 「中国出海品牌做得不错。」
✅ 「Fanttik 用 30 人团队跑通『达人内容量产』获客模型，公司视觉团队（10 人）的内容打法需从精品自制转向达人共创＋模板化量产。」

---

## 六、输出文件命名

```
industry-radar-YYYY-MM-DD.html
```

---

## 七、运行频率建议

| 场景 | 频率 |
|------|------|
| 日常情报监控 | 每周一次 |
| 重大决策前（新品上市/战略调整） | 即时触发 |
| 竞品发布会 / 行业展会（CES、Equip Expo）前后 | 即时触发 |
| 季度战略复盘准备 | 月度一次 |

---

## 八、精简模式

用户说"快速扫描"或"简报模式"时：
- 每频道只执行 1 条 query
- 每频道只提炼 1-2 条情报
- HTML 报告仍生成，卡片压缩到 8-12 张
- 适合日常 5 分钟情报消费
