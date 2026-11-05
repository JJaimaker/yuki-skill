# Yuki Skills

个人 skill 库：把本地 Mac 上的制作 skill 集中到 GitHub，减轻本地存储压力，
同时让 Muse、Codex 等工具都能按文件夹调用同一个 skill。

目标账号：JJaimaker。GitHub 仓库是唯一正本，本地只是它的副本。

## 分类（增删改查就按这个结构来）

| 大类 | 文件夹 | 说明 |
| --- | --- | --- |
| 网页制作 | `web/` | 做网页、长篇可视化页面的 skill |
| PPT 制作 | `ppt/` | 做汇报 PPT 的 skill |
| 研究类（预留） | `research/` | 以后新增的研究类 skill 直接放在这里，不用改整体结构 |
| 模板 | `_templates/new-skill/` | 新增 skill 时复制这个文件夹改名 |

每个 skill 都是一个文件夹，里面必须有 `SKILL.md`（正文）和 `skill.yaml`
（名字 + 一句话说明）。工具认的是文件夹，不是单个文件。
Mac 的 `.DS_Store` 和 `__MACOSX` 不是 skill 内容，部署时已排除，不要再加回来。

## 索引

### 网页制作 `web/`

| Skill | 适合场合 | 文件夹 |
| --- | --- | --- |
| engineering-machinery-blue-report-html | 向中国企业 50 岁左右总裁汇报；深蓝 + 暗红，传统工业风格 | `web/engineering-machinery-blue-report-html/` |
| soft-frosted-html | 课题研究、产品说明、长篇可视化网页；内容先行的柔雾玻璃视觉（暗色 Yuki 研究页版） | `web/soft-frosted-html/` |
| html-yuki-regular-work-style | 最常用的建站 skill；避开千篇一律的黑底蓝紫 AI 风格；AI 趋势、技术选型和概念、产品场景痛点和 demo 演示。注：之前叫 html-sany-work-style，zip 里的文件夹名和 SKILL.md 内部名都是 html-yuki-regular-work-style，以 zip 为准 | `web/html-yuki-regular-work-style/` |

### PPT 制作 `ppt/`

| Skill | 适合场合 | 文件夹 |
| --- | --- | --- |
| strategic-planning-ppt | 半年度、季度战略规划；蓝白配色；适合阿里体系领导；一页 3 个逻辑，要么逐渐递进，要么 3 个立论。注：zip 里文件夹名带空格（strategic-planning-ppt skill），部署时只去掉空格改成 strategic-planning-ppt，内容未改 | `ppt/strategic-planning-ppt/` |
| sany-fu-ppt | 周会、月会向主管总裁汇报；SANY President Fu 专用汇报 skill，他下面层级的人同样使用；强烈的 SANY 汇报风格 | `ppt/sany-fu-ppt/` |

## 增删改查（小白版）

- **增（新增一个 skill）：** 复制 `_templates/new-skill/`，改成新 skill 的名字，
  放到对应的大类文件夹下（网页放 `web/`，PPT 放 `ppt/`，研究类放 `research/`），
  写好 `SKILL.md` 和 `skill.yaml`，最后在上面索引表里加一行。
- **增（新增一个大类）：** 新建一个文件夹（例如 `research/` 已经预留好了），
  在上面分类表里加一行，以后这个大类下的 skill 都放这个文件夹。
- **删：** 删掉那个 skill 文件夹，并在索引表里删掉对应的一行。不要只删索引表、
  也不要只删文件夹，两边要一致。
- **改：** 直接改那个 skill 文件夹里的 `SKILL.md`；只改一句话说明时改 `skill.yaml`。
- **查：** 先看上面索引表找“适合场合”，再进对应文件夹看 `SKILL.md`。

## 后续调用

原则只有一条：**把仓库 clone 下来，把要用的 skill 文件夹原样复制到
你所用工具的 skills 目录里，文件夹名就是 skill 名。**

```bash
git clone https://github.com/JJaimaker/yuki-skill.git
```

### Muse

Muse 的自定义 skill 放在工作区的 `custom-skills/` 下，例如：

```bash
cp -r yuki-skill/web/soft-frosted-html ~/workspace/custom-skills/
cp -r yuki-skill/ppt/strategic-planning-ppt ~/workspace/custom-skills/
```

复制后在对话里按 skill 名或按它的适用场合提要求即可，例如
“用 soft-frosted-html 做这个研究页”。

### Codex

Codex 个人 skill 放在 `~/.agents/skills/`（较旧版本也读 `~/.codex/skills/`），
例如：

```bash
cp -r yuki-skill/web/soft-frosted-html ~/.agents/skills/
cp -r yuki-skill/ppt/strategic-planning-ppt ~/.agents/skills/
```

复制后在 Codex 里打开 `/skills` 看到它就说明已识别；看不到就重启一次 Codex
再看。用的时候输入 `$` + skill 名，或在 `/skills` 里选它。

### 更新 skill

仓库里改了 skill 后，本地再拉一次并重新复制覆盖即可：

```bash
cd yuki-skill && git pull
cp -r web/soft-frosted-html ~/.agents/skills/
```

注意：不要在两个地方各改一份，GitHub 仓库是唯一正本，本地只是它的副本。
