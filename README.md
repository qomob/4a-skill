# 4A-Skill

4A广告 Campaign 全流程智能体工作流 —— **12 个专业 Agent** 协作完成从调度路由到提案交付及效果监测的完整广告 Campaign。

## 工作流架构

```
Traffic → Research → AE → Planner → Creative → AIGC → Content → GEO → Media → Producer → Proposal
                                                                              ↓
                                                                    Monitoring（并行）
Compliance（并行审查）
```

**核心链路**: 10 个串行 Agent + 2 个并行 Agent（合规审查 + 效果监测）

| 阶段 | Agent | 职责 |
|------|-------|------|
| 🔀 调度 | **Traffic Agent** | 意图识别、模式选择、路由调度 |
| 🔍 调研 | **Research Agent** | 联网搜索市场趋势、竞品分析、用户洞察 |
| 📋 需求 | **AE Agent** | 结构化 Brief，追问澄清 |
| 🧠 策略 | **Planner Agent** | Strategy Engine + 4A方法论引擎(BAV/FCB/HumanKind) |
| 🎨 创意 | **Creative Agent** | 四大创意流派(BigIdea/Disruption/ThinkSmall/Humankind) |
| 🤖 素材 | **AIGC Expert** | MJ/SD/DALL-E/即梦 图像Prompt + Runway/Kling 视频分镜 |
| ✍️ 内容 | **Content Agent** | Slogan + 视频脚本 + 多平台社媒内容 |
| 🔥 优化 | **GEO Expert** | AI可引用结构 + 语义增强 + 平台SEO适配 |
| 📢 投放 | **Media Agent** | 渠道组合 + 预算分配 + KPI设定 + A/B测试 |
| 🎬 统筹 | **Producer Agent** | 排期 + 资源盘点 + 风险管理 |
| 📄 提案 | **Proposal Agent** | 8章节专业方案（MD/HTML/PPT/Word/PDF）|
| ⚖️ 合规 | **Compliance Agent** | 法律/平台合规审查（并行）|
| 📊 监测 | **Monitoring Agent** | 五阶段监测闭环(P0-P3告警)（并行）|

## 使用模式

| 模式 | 触发词 | Agent数 | Checkpoint | 适用场景 |
|------|--------|---------|-----------|---------|
| **快速** | 快速/简单/新手/1 | 6个 | 4处暂停 | 首次使用、时间紧、只要方向 |
| **标准** | 完整/详细/2或默认 | 11个 | 每步暂停 | 正式项目、完整方案 |
| **自定义** | 只要.../指定Agent名 | 按需 | 仅指定+依赖暂停 | 特定环节迭代 |
| **预览** | 预览/快速看看 | 6个 | Proposal处暂停 | 快速看大致方向 |

**断点续跑**: 「从 {Agent名} 继续」— 复用已有输出，从指定点继续执行
**品牌档案**: 首次建立后自动引用，减少重复追问

## 项目结构

```
4ASkill/
├── SKILL.md                          # Skill 主入口（315行）
├── CHANGELOG.md                      # 版本变更记录
├── workflows/
│   └── campaign.yaml                 # DAG 工作流定义
├── agents/                           # 14 个文件（13个Agent + index.md）
│   ├── traffic-agent.md              #   调度路由
│   ├── research-agent.md             #   市场调研
│   ├── ae-agent.md                  #   客户总监
│   ├── planner-agent.md             #   策略引擎 + 方法论诊断
│   ├── creative-agent.md            #   创意总监 + 四大流派
│   ├── aigc-agent.md                #   AIGC制作专家（MJ/SD/即梦/Runway/Kling）
│   ├── content-agent.md             #   内容制作人
│   ├── geo-agent.md                 #   引擎优化专家
│   ├── media-agent.md               #   媒体策划
│   ├── producer-agent.md            #   执行统筹
│   ├── proposal-agent.md            #   提案总监
│   ├── compliance-agent.md          #   合规审查
│   ├── monitoring-agent.md          #   效果监测
│   └── index.md                     #   Agent 导航索引
├── scripts/                          # 辅助脚本
│   ├── budget_allocator.py           #   预算分配器（6渠道CPM/CPC + 3阶段）
│   └── kpi_simulator.py             #   KPI模拟器（8行业基准 × S-D级创意质量）
└── shared/
    ├── schemas/                      # 14 个 JSON Schema 数据契约
    │   └── (traffic/brief/strategy/creative/aigc/content/
    │       geo/media/production/proposal/research/compliance/campaign_output)
    └── references/                   # 37 个参考文档（渐进式加载）
        ├── rules.md                  #   通用规则集
        ├── output-templates*.md      #   输出模板库（1总 + 4拆分）
        ├── glossary*.md              #   术语词典 + 小白模式 + 可视化系统
        ├── methodology.md            #   方法论框架（OST/3C/AIDA等9类）
        ├── 4a-methodology-bible.md   #   4A方法论引擎（BAV/FCB/HumanKind/四大流派）
        ├── bible-strategic-methods.md # 战略方法圣经（含诊断输出JSON）
        ├── bible-creative-methods.md # 创意方法圣经（含360°品牌管家操作清单）
        ├── bible-media-methods.md   #   媒体方法圣经
        ├── kpi-benchmarks.md         #   KPI基准数据（8行业×4等级）
        ├── mermaid-templates.md      #   Mermaid图表模板（13类可视化）
        ├── industry-brief-templates.md # 行业Brief模板（12个行业预填值）
        ├── case-studies*.md          #   案例库（成功5 + 失败3）
        ├── creative-review.md        #   创意五维评审 + A/B Test框架
        ├── creative-toolkit.md       #   创意工具箱
        ├── creative-schools.md       #   创意四大流派详解
        ├── feedback-loop*.md         #   监测反馈闭环（P0-P3告警）
        ├── collaboration.md          #   多人协作(@批注/版本管理)
        ├── execution-resources.md    #   执行资源(AIGC工具/媒体平台/外包)
        ├── b2b-marketing-module.md   #   B2B营销模块(ABM/DMU)
        ├── brand-upgrade-mode.md     #   品牌升级模式(CBBE/JND)
        ├── multilingual-guide.md     #   多语言支持指南（7种语言）
        ├── jimeng-prompt-guide.md    #   即梦提示词规范
        ├── jimeng-guide-image.md     #   即梦图像指南
        ├── jimeng-guide-video.md     #   即梦视频指南
        ├── aigc-prompt-templates.md  #   AIGC Prompt模板库
        ├── aigc-tool-guide.md        #   AIGC工具指南
        ├── compliance-detailed-rules.md # 合规详细规则
        ├── monitoring-detailed-guide.md # 监测详细指南
        ├── planner-model-library.md  #   Planner模型库
        └── producer-vendor-price-guide.md # 外包供应商价格参考
```

## 核心能力

### Planner — Strategy Engine + 4A方法论引擎

1. **Model Library**: 10 个营销传播模型（AIDA / STP / 4P / 5A / JTBD / Hook / GoldenCircle / PAS / 3H / GrowthLoop）
2. **4A方法论诊断**: BAV品牌资产矩阵 / FCB网格 / HumanKind人性洞察 / Meaningfulness Gap
3. **Strategy Scoring**: 5维度量化评分（目标匹配/受众匹配/可执行性/创新性/转化潜力）
4. **创意流派推荐**: 基于诊断结果自动推荐 BigIdea / Disruption / ThinkSmall / Humankind

### Creative — 四大经典创意流派

| 流派 | 来源 | 核心理念 | 适用场景 |
|------|------|---------|---------|
| **BigIdea** | Ogilvy | 一个大创意贯穿所有触点 | 品牌建设/长期战役 |
| **Disruption** | TBWA | 打破品类常规 | 新品牌进入/颠覆者 |
| **ThinkSmall** | DDB | 小洞察大创意 | 社交传播/病毒内容 |
| **Humankind** | Leo Burnett | 人性洞察→社会价值 | 品牌升级/公益营销 |

### AIGC Expert — 全平台可执行 Prompt

每个素材输出 **4-6 套工具格式**的完整可复制 Prompt：

| 工具 | 图像 | 视频 | 特点 |
|------|------|------|------|
| **Midjourney v6** | `--ar --style --stylize --v` 完整参数 | — | 艺术感最强 |
| **Stable Diffusion** | Positive/Negative + Sampler/Steps/CFG | — | 可控性最强 |
| **DALL-E 3** | 自然语言格式 | — | 文字渲染准 |
| **即梦 Jimeng** | 中文原生 Prompt | Seedance 视频中文 | 抖音生态适配 |
| **Runway Gen-3** | — | Text-to-Video + Image-to-Video | 电影质感 |
| **Kling AI 可灵** | — | 文生视频 + 图生视频（最长2min）| 中国市场首选 |

### Media — 渠道策略与预算分配

- 6 大渠道默认配置（信息流/搜索/社媒KOL/户外/短视频/电商）
- 3 阶段投放节奏（蓄水15% / 爆发55% / 长尾30%）
- A/B 测试框架 + 动态预算调优规则
- 媒体平台一键映射（巨量引擎 / 腾讯广告 / 抖音聚光）

### 扩展模块（渐进式加载）

| 模块 | 触发词 | 能力 |
|------|--------|------|
| **📚 术语与小白模式** | `术语词典` `小白模式` `图表` | 100+术语词典 / 大白话输出 / 13类Mermaid图表 / 8行业KPI基准 |
| **📖 案例库** | `案例` `成功案例` | 5个成功案例(快消/SaaS/美妆/B2B/本地生活) + 3个翻车案例 |
| **🎨 创意评审** | `创意评审` `A/B Test` | 五维自评卡 / 四角人工评审 / A/B Test框架 |
| **📊 监测反馈闭环** | `监测报告` `效果怎么样` | 五阶段监测协议 / P0-P3异常告警 / 数据回传学习 |
| **👥 多人协作** | `协作模式` `邀请同事` | 角色权限矩阵 / @批注语法 / 版本管理(v{主}.{次}-阶段) |
| **🏭 行业模板** | `我是{行业}` `{行业}行业模板` | 12个行业Brief模板(含本地生活/餐饮/母婴/游戏) |
| **🔧 执行资源** | `执行` `怎么做素材` | AIGC工具(MJ/SD/即梦/Runway/Kling) / 媒体平台(巨量/聚光/腾讯) |
| **📐 4A方法论引擎** | `方法论` `诊断` | BAV/FCB/HumanKind诊断 + 四大创意流派推荐 |

### Scripts — 辅助计算工具

```bash
# 预算分配：50万预算，4渠道 + 3阶段
python3 scripts/budget_allocator.py '{"total_budget":500000,"channels":["info_stream","search","social_kol","short_video"],"phases":["warmup","burst","tail"]}'

# KPI模拟：美妆行业，50万预算，30天，A级创意质量
python3 scripts/kpi_simulator.py '{"industry":"beauty","budget":500000,"duration_days":30,"creative_quality":"A"}'
```

## 数据契约与质量保障

- **14 个 JSON Schema** 定义 Agent 间数据传递格式，校验失败触发自修复
- **三级上下文传递**: Required(必传) / Optional(按需) / Discardable(可裁剪)
- **双输出机制**: Markdown 摘要供用户确认 + JSON 供下游 Agent 引用
- **Checkpoint 系统**: 交互/自动/静默三种模式 + 5个关键必停节点 + 8条快捷命令
- **降级策略**: complete → limited → minimal 三级降级路径

## 使用示例

```
"客户X要推一款新茶饮，预算50万，目标人群Z世代，跑完整Campaign流程。"
"我们接到SaaS产品的品牌升级项目，需要Brief到执行排期全套方案。"
"帮我为一个汽车品牌的年度大促活动生成Campaign全案。"
"帮我快速看看这个美妆新品的大致方案。"                    ← 预览模式
"从Creative开始继续，前面Brief和Strategy已经确认了。"       ← 断点续跑
"只要创意方向和AIGC素材，不需要投放策略。"                   ← 自定义编排
"帮我跑一个Campaign，品牌是XX茶饮，记住这些信息。"           ← 品牌档案
```

## 集成方式

### Trae IDE

Skill 位于项目目录，Trae IDE 自动发现加载。直接描述广告需求即可触发：

```
"帮我跑一个新茶饮品牌的完整Campaign流程"
```

### 独立 Agent 系统

- **单 Agent**: 直接读取 `agents/{name}-agent.md` 作为 System Prompt
- **多 Agent 编排**: 参照 `workflows/campaign.yaml` 的 DAG 定义
- **数据校验**: 使用 `shared/schemas/*.schema.json` 对 Agent 间 JSON 做 Schema 校验
- **辅助计算**: 使用 `scripts/*.py` 进行预算分配和KPI模拟

### 自定义扩展

- **新增 Agent**: 在 `agents/` 下新建 `{name}-agent.md`，更新 `campaign.yaml` 的 DAG
- **新增平台**: 修改 `aigc-agent.md` / `execution-resources.md` 中的规格表
- **新增行业**: 在 `industry-brief-templates.md` 追加模板 + `kpi-benchmarks.md` 追加基准
- **新增语言**: 在 `multilingual-guide.md` 追加语言配置
- **新增脚本**: 在 `scripts/` 下新建 Python 脚本

## License

Apache License 2.0
