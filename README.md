# academic-writing-polishing

`academic-writing-polishing` 是一个面向 Codex 类代理的学术写作润色 skill，用于在不改变科学事实和证据边界的前提下，润色、重写或起草学术论文段落、投稿信和审稿回复。

这个 skill 的目标不是“把文字改得更像 AI”，而是让输出在学术语境下更清楚、更简洁、更符合 section 角色与期刊语境，同时严格保留原有的 claim strength、numbers、citations、equations、variables 和其他 protected tokens。

## 适用场景

- 润色或重写论文段落
- 调整 Introduction / Methods / Results / Discussion / Abstract 的 section fit
- 起草或润色 cover letter
- 起草或润色 reviewer response
- 处理学术写作里常见的啰嗦、动词无力、段落逻辑松散、句式单调、hedging 失衡、数字表达不清等问题

## 设计原则

- 只做解决问题所需的最轻量改写，不做无意义的 cosmetic churn
- 默认保留原始科学含义，不擅自强化或弱化结论
- 只在必要时读取最相关的参考片段，避免把整个参考库一次性塞进上下文
- 如果涉及期刊规则，只依赖用户提供的要求或期刊官方页面
- 对 cover letter、reviewer response、section rewrite 等任务分别使用不同的工作流

## 仓库结构

```text
academic-writing-polishing/
├─ SKILL.md
├─ agents/
│  └─ openai.yaml
└─ references/
   ├─ academic-revision-examples.md
   ├─ core-editing.md
   ├─ manuscript-sections.md
   └─ publishing-and-review.md
```

- `SKILL.md`：skill 的主入口，定义适用范围、路由优先级、模式切换、约束和输出契约
- `agents/openai.yaml`：界面展示名称、简短说明和默认提示词
- `references/core-editing.md`：句级与段级润色规则，包括 cut clutter、verbs、paragraph logic、hedging、numbers 等
- `references/manuscript-sections.md`：按论文 section 组织的写作要求，包括 Results、Introduction、Discussion、Abstract 和 cover letter
- `references/publishing-and-review.md`：投稿、revision、peer review 与 reviewer response 的写作约束
- `references/academic-revision-examples.md`：按问题类型整理的 before/after 示例库

## 参考来源

这个 skill 的写作原则和知识结构，主要参考了 [quanghuy0497/Writing-in-the-Sciences](https://github.com/quanghuy0497/Writing-in-the-Sciences)。该仓库整理自 Stanford / Coursera 的 *Writing in the Sciences* 课程材料，重点覆盖：

- clear and concise writing
- verbs and sentence structure
- paragraph organization
- writing process and revision
- manuscript sections
- scientific publishing and peer review
- broader scientific communication

本项目不是对原仓库的直接搬运，而是把其中与“学术写作润色”最相关的内容重新组织成适合代理执行的 skill 结构：

- 将通用写作原则收束到 `core-editing.md`
- 将论文 section 角色要求收束到 `manuscript-sections.md`
- 将投稿与审稿往返信息收束到 `publishing-and-review.md`
- 将例句和 before/after 模式单独整理到 `academic-revision-examples.md`

换句话说，这个仓库更像是“面向 agent 的可执行版写作规则整理”，而不是课程资料镜像。

## 如何使用

1. 将 `academic-writing-polishing/` 放到你的 `$CODEX_HOME/skills/` 目录下。
2. 在对话中调用 `$academic-writing-polishing`。
3. 提供与你任务匹配的最小输入，例如：

- 润色已有文本：给出原文，必要时说明目标 section
- 起草 section：给出 section 类型、研究问题和必须保留的事实
- cover letter：给出稿件标题、核心发现、目标期刊和已确认的声明信息
- reviewer response：给出 reviewer comment、你准备采取的回应立场，以及已确认的修改内容

示例提示：

```text
Use $academic-writing-polishing to rewrite this Discussion paragraph for clarity and tighter claim calibration without changing the underlying science.
```

```text
Use $academic-writing-polishing to draft a journal cover letter for this manuscript. Keep it specific, professional, and aligned with the journal's readership.
```

## 说明

- 这个仓库聚焦于 skill 本身
- 如果你要公开分发或二次改写相关参考材料，请自行确认原始课程材料及其衍生整理内容的版权与许可边界
- 如果你的任务核心是翻译、文献检索、统计审稿或基金申请写作，这个 skill 不是最合适的入口
