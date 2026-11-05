# Yuki Skills 介绍

一共 5 个 skill，分两大类：网页制作 3 个，PPT 制作 2 个。
都是按真实汇报和制作场景沉淀下来的，不是通用模板。

| 大类 | Skill | 一句话 |
| --- | --- | --- |
| 网页制作 | engineering-machinery-blue-report-html | 给中国企业总裁看的工程机械汇报页 |
| 网页制作 | soft-frosted-html | 课题研究和产品说明的长篇可视化页 |
| 网页制作 | html-yuki-regular-work-style | 最常用的建站风格，做 AI 趋势、技术选型和产品 demo |
| PPT 制作 | strategic-planning-ppt | 季度、半年度战略规划汇报 |
| PPT 制作 | sany-fu-ppt | 每周、每月向 Fu 总裁汇报 |

## 网页制作

### 1. engineering-machinery-blue-report-html

**一句话：** 给中国企业 50 岁左右总裁汇报用的工程机械 HTML 报告。

**适合：** 工程机械、矿山、设备运营、工业 AI、数字化战略、试点和商业化汇报；
传统高层评审、产品战略页、经营报告、工业项目提案。

**风格：** 深蓝为主（McKinsey 蓝 + 支付宝蓝），暗红（深 SANY 红）只做重点强调；
克制、传统工业风；结论先行、连续滚动导航、证据标签、成本或 POC 表格；
响应式、Netlify 可直接部署。

**不适合：** 消费品营销站、柔雾玻璃风、暖色编辑风、PPT。

### 2. soft-frosted-html

**一句话：** 课题研究、产品说明、长篇可视化网页，内容先行的柔雾玻璃视觉。

**适合：** 课题研究页、产品说明页、长篇可视化研究页；需要先把内容逻辑讲清楚，
再用视觉承载的页面。

**风格：** 暗色 2.5D 柔雾玻璃，Yuki 研究页定稿样式；一眼能看出是讲 AI 相关的内容，
但做了设计调整，不走千篇一律的黑底蓝紫 AI 风；内容决定版式，表格做精确比较，
图做关系和流程。

**不适合：** 已经有其他明确设计系统时，不要用它去覆盖。

### 3. html-yuki-regular-work-style

**一句话：** 最常用的建站 skill，研报印刷品质感，避开千篇一律的黑底蓝紫 AI 风格。

**适合：** 研究 AI 趋势、某个技术选型和概念、产品场景痛点和 demo 演示；
没有指定其他设计系统时，生成任何 HTML 页面都可以默认用它。

**风格：** Modern Minimalism 基底，单色相 + 暖底色 + 字重对比 + 极致留白；
也叫 Sany WorkStyle / 研报红风格。

**说明：** 之前叫 html-sany-work-style，zip 里的文件夹名和 SKILL.md 内部名
都是 html-yuki-regular-work-style，以 zip 为准，是同一个 skill。

## PPT 制作

### 4. strategic-planning-ppt

**一句话：** 季度、半年度战略规划 PPT，蓝白配色，适合阿里体系领导。

**适合：** 季度或年度规划、新产品立项、商业化汇报。

**方法：** 市场洞察 → 客户洞察 → 扩客源增利润 → 模式验证，四步递进链；
一页呈现三层相扣的逻辑，要么逐渐递进，要么 3 个立论。

**风格：** 蓝白配色，干净、信息密度高但有层级。

### 5. sany-fu-ppt

**一句话：** 周会、月会向 SANY President Fu 汇报的 PPT，Fu 总专用。

**适合：** 每周、每月进展、产品计划、客户调研、客户价值、AI 或数字化、
风险、协同诉求等经营汇报；Fu 总下面层级的人汇报同样使用。

**风格：** 结论先行、信息密度高、蓝红黑的高层阅读风；强烈的 SANY 汇报风格。

**不适合：** 仅仅因为 PPT 里提到三一就用它；如果已经指定了其他视觉风格，
按指定的来。

## 怎么选

| 你的情况 | 用这个 |
| --- | --- |
| 给总裁汇报工程机械、工业项目 | engineering-machinery-blue-report-html |
| 写课题研究、产品说明，要长篇讲清楚 | soft-frosted-html |
| 做 AI 趋势、技术选型、产品痛点 demo，没指定风格 | html-yuki-regular-work-style |
| 做季度、年度战略规划 | strategic-planning-ppt |
| 每周、每月给 Fu 总汇报 | sany-fu-ppt |

## 文件位置

- 网页制作：`web/engineering-machinery-blue-report-html/`、
  `web/soft-frosted-html/`、`web/html-yuki-regular-work-style/`
- PPT 制作：`ppt/strategic-planning-ppt/`、`ppt/sany-fu-ppt/`
- 以后新增研究类 skill 放在 `research/` 下，新增 skill 先复制
  `_templates/new-skill/` 再改名。
