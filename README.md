# AI Reviewer

一个面向 CV、NLP、多模态与机器学习论文的证据优先（evidence-first）审稿 skill。它的目标不是模仿官方 reviewer 或预测录用，而是帮助作者在投稿前发现高影响问题、把 review 转化为可执行修改计划，并在 rebuttal 后进行严格复审。

## 能做什么

- **Critical Review**：审查创新性、技术正确性、实验/基线、理论、效率、评测有效性、复现与伦理风险。
- **Pre-submission Hardening**：在投稿前对数学、符号、定理条件、表格口径、实验设置和 claim 边界作对抗式自检。
- **Revision Plan**：把 reviewer comments 转为“补什么证据、如何修改、如何回应”的优先级工作表。
- **Re-review**：将原始 concern 与 rebuttal/修订逐条对照，判断 resolved、partial 或 unresolved。
- **Review Challenge / AC Brief**：对有争议的低分 concern 建立可核验账本，生成克制、供 AC 快速判断的事实摘要。
- **Public Review Audit**：审计公开 OpenReview 讨论，提炼 reviewer 真正在意的 weakness 与有效回应；不从文风推断是否由 AI 撰写。

## 安装

### 方式一：从 GitHub 安装（推荐）

在 Codex 中输入：

```text
安装 https://github.com/civane/ai-reviewer 中的 ai-reviewer skill
```

也可以让 Codex 使用 Skill Installer：

```text
Install the skill from civane/ai-reviewer.
```

### 方式二：手动安装

```bash
git clone https://github.com/civane/ai-reviewer.git
mkdir -p ~/.codex/skills
cp -R ai-reviewer ~/.codex/skills/ai-reviewer
```

安装后新开一个 Codex 对话。可用 `$ai-reviewer` 显式调用，或直接提出与论文、review、rebuttal 相关的请求让它自动触发。

## 使用方式

推荐按下面的闭环使用，而不是等收到低分 review 才开始处理：

```text
Pre-submission Hardening
  → Critical Review
  → Revision Plan
  → Rebuttal
  → Re-review
  → Review Challenge / AC Brief（仅在确有争议时）
```

### 1. Pre-submission Hardening：投稿前专项加固

**输入：** 论文 PDF/LaTeX（最好包含补充材料、表格与代码说明）。

**产出：** hardening ledger，将问题标为“必须修复、必须澄清、补充证据、主动披露限制”。重点检查定义、符号、公式、定理假设、复杂度、表格、实验设置与 claim scope。

```text
用 ai-reviewer 做 Pre-submission Hardening。对定义、符号、公式、定理假设、
复杂度、表格、实验设置和 claim scope 建立 hardening ledger；
把问题分为必须修复、必须澄清、补充证据、主动披露限制。
```

### 2. Critical Review：模拟严格但公平的审稿

**输入：** 论文，以及目标会议/track（如 ICLR、CVPR、ACL）。

**产出：** claim–evidence map、major/minor concerns、复现与伦理检查、评分依据说明。每个重大 concern 必须包含证据位置、影响、修复动作和置信度。

```text
用 ai-reviewer 严格审这篇论文，按 ICLR 标准给出 Critical Review。
重点检查创新性、实验/基线、理论、复现性和可能被 reviewer 挑的问题。
```

### 3. Revision Plan：把 review 变成修改清单

**输入：** reviewer comments，最好同时提供论文与当前 rebuttal 草稿。

**产出：** 按决策影响排序的修改计划；区分补实验、澄清、收窄 claim 与不需要争辩的事项，并给出每条回应所需的最小证据。

```text
用 ai-reviewer 的 Revision Plan 模式分析以下 reviewer comments。
按“必须补实验 / 必须澄清 / 可以收窄 claim / 不值得争辩”排序，
并给每条写一个可执行 rebuttal。
```

### 4. Re-review：检查 rebuttal 是否真的解决问题

**输入：** 原始 review、作者 rebuttal、修订稿或新增实验。

**产出：** 每条 concern 的 `resolved / partial / unresolved` 判断、残余风险与更新后的评分依据。清晰表达不能替代缺失控制实验、无效指标或不适用的理论保证。

```text
用 ai-reviewer 的 Re-review 模式，对照原 review 和我的 rebuttal，
判断每个问题是 resolved、partial 还是 unresolved；
指出仍然可能阻碍升分的两件事。
```

### 5. Review Challenge / AC Brief：处理有争议的低分意见

**仅在同时具备论文、review 与 rebuttal/修订证据时使用。**

**产出：** concern ledger，将每条意见标为“有效、部分有效、证据不足、事实矛盾、超出 stated claim”；随后生成作者可直接使用的克制回应和一页中立 AC Brief。

```text
用 ai-reviewer 的 Review Challenge / AC Brief 模式，对照论文、review 和 rebuttal。
把每条 concern 标为有效、部分有效、证据不足、事实矛盾或超出 stated claim；
输出可核验的作者回应和一页中立的 AC brief。不要攻击 reviewer，也不要推断其是否使用 AI。
```

### 6. Public Review Audit：从公开讨论中学习

```text
用 ai-reviewer 审计这篇 OpenReview 讨论：总结 reviewer 真正在意的 weakness、
作者如何回应、哪些回应足以改变评价；不要判断 reviewer 是否使用 AI。
```

## 关键原则

- 每个 substantive concern 都必须给出证据位置、为什么重要、可执行修复和置信度。
- 不把“有趣但未做的实验”自动升级为 blocking issue。
- 数学纠错必须提供：原始假设/命题、正确推导或反例、与实际方法的关联、对结论的后果。
- 数字评分仅在用户提供目标会议 rubric 时给出；它是评分依据说明，不是录用预测。
- 不从写作风格判断 reviewer 或作者是否使用 AI。

## 目录

```text
ai-reviewer/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── cv-nlp-rubric.md
    └── rebuttal-playbook.md
```

## 使用边界

请将未公开投稿视作保密材料。该 skill 只提供审稿与修改建议，不能替代人工核验，也不应以生成文本冒充官方同行评审。
