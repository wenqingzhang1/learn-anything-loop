<div align="right">
  <a href="./README.md"><img alt="中文 README" src="https://img.shields.io/badge/README-%E4%B8%AD%E6%96%87-dc2626?style=for-the-badge"></a>
  <a href="./README_EN.md"><img alt="Switch to English" src="https://img.shields.io/badge/Language-English-2563eb?style=for-the-badge"></a>
</div>

# AI 学习闭环 · learn-anything-loop

一个面向 Codex 的持久化学习系统 Skill。它把“想学一个主题”转化为可执行、可测量、可断点继续的学习闭环：

> 目标诊断 → 学习阶梯 → 核心 20% → 限时训练 → AI 考官 → 费曼复述 → 一页速查表 → 持续复习

## 它能做什么

- **搭建学习阶梯**：默认生成 5 个等级，并按主题复杂度调整为 4–7 级。每级都有必会知识、实践产物、常见错误和升级门槛。
- **处理两种学习入口**：上传资料时以资料为主、只补明显缺口；自选主题时实时筛选 5 个免费且高价值的资源。
- **找出核心 20%**：按目标价值、前置依赖、使用频率和错误成本筛选最值得先学的内容。
- **制定限时计划**：默认生成 7 天计划，单次 45–120 分钟，每天最多 2 次，并确保总时数精确匹配。
- **担任 AI 考官**：一次只问一个重要问题，从简单到困难评分，只重新解释没有掌握的部分。
- **运行费曼复述**：先用 12 岁孩子能理解的话解释，再让学习者讲回来；最多进行两次复述。
- **生成一页速查表**：压缩定义、核心概念、真实例子、常见错误、检查清单和 5 道自测题。
- **跨对话继续学习**：将每个主题的计划、得分、薄弱点和下一步动作保存为本地 Markdown 档案。

## 安装

### 方式一：使用 Git 克隆

在 PowerShell 中运行：

```powershell
git clone https://github.com/wenqingzhang1/learn-anything-loop.git "$env:USERPROFILE\.codex\skills\learn-anything-loop"
```

### 方式二：手动安装

1. 下载本仓库。
2. 将整个文件夹放到：

```text
C:\Users\<你的用户名>\.codex\skills\learn-anything-loop
```

3. 重新打开 Codex 任务，然后调用 `$learn-anything-loop`。

## 快速开始

从一个新主题开始：

```text
$learn-anything-loop 我是完全新手，想用 10 小时学会使用 Python 分析 CSV 并制作图表。
```

从上传资料开始：

```text
$learn-anything-loop 根据我上传的资料搭建学习阶梯，并制定 7 天计划。
```

进入专项模式：

```text
继续上次的 SQL 学习
考考我，直到我答不上来
用费曼法检查我对闭包的理解
生成这个阶段的一页速查表
```

Skill 只会询问尚未提供的关键信息：学习主题、目标项目、当前水平和总学习时数。

## 学习档案

本仓库的默认配置面向 Windows。第一次确认某个学习主题后，Skill 会创建：

```text
E:\<topic-name>-LearningDocs\
├── learning-record.md
└── cheatsheet.md
```

例如：

```text
E:\Python-LearningDocs\
E:\线性代数-LearningDocs\
```

关键规则：

- Skill 本体保留在 C 盘，学习档案单独保存在 E 盘。
- 已有但不含管理标记的同名目录不会被覆盖；新目录会自动使用 `-2`、`-3` 等后缀。
- 上传资料默认只记录原始路径，不复制、移动或改写源文件。
- E 盘不可用时会停止创建并询问其他位置，不会静默改存到 C 盘。
- 若要修改默认存储位置，请编辑 [`references/learning-record.md`](./references/learning-record.md) 中的存储约定。

## 7 天计划约束

| 规则 | 默认值 |
| --- | --- |
| 单次训练 | 45–120 分钟 |
| 每天训练次数 | 最多 2 次 |
| 七天总容量 | 最多 28 小时 |
| 小于 45 分钟 | 要求提高预算 |
| 超过 28 小时 | 延长周期或缩小第一阶段目标 |

每次正式训练都必须包含目标、资源切片、主动回忆、实践任务、可验证产出和复盘问题。单纯观看或阅读不算完整训练。

## 项目结构

```text
learn-anything-loop/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── learning-record.md
│   └── protocols.md
├── README.md
└── README_EN.md
```

- [`SKILL.md`](./SKILL.md)：自动路由和核心学习流程。
- [`references/protocols.md`](./references/protocols.md)：阶梯、资源筛选、时间计划、考官、费曼法和速查表协议。
- [`references/learning-record.md`](./references/learning-record.md)：E 盘档案结构、冲突保护和断点恢复规则。
- [`agents/openai.yaml`](./agents/openai.yaml)：Skill 的 Codex 界面元数据。

## 使用说明

- 自选主题的资源推荐需要联网检索，以避免使用过期内容或失效链接。
- “完成课程”不等于掌握；升级必须同时通过测评和实践产物验证。
- 学习档案保存在本机，不会因为本仓库公开而上传到 GitHub。

## 验证状态

本 Skill 已通过官方 `quick_validate.py` 校验，并测试了：

- 6、10、20 小时的七天时间分配；
- 超过 28 小时的边界处理；
- AI 考官一次一题；
- E 盘目录冲突保护；
- 中英文 README 相互跳转。
