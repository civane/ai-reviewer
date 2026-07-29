# AI Reviewer

一个面向 CV、NLP、多模态与机器学习论文的证据优先（evidence-first）审稿 skill。它的目标不是模仿官方 reviewer 或预测录用，而是帮助作者在投稿前发现高影响问题、把 review 转化为可执行修改计划，并在 rebuttal 后进行严格复审。

## 能做什么

- **Critical Review**：审查创新性、技术正确性、实验/基线、理论、效率、评测有效性、复现与伦理风险。
- **Revision Plan**：把 reviewer comments 转为“补什么证据、如何修改、如何回应”的优先级工作表。
- **Re-review**：将原始 concern 与 rebuttal/修订逐条对照，判断 resolved、partial 或 unresolved。
- **Public Review Audit**：审计公开 OpenReview 讨论，提炼 reviewer 真正在意的 weakness 与有效回应；不从文风推断是否由 AI 撰写。

## 安装

### 方式一：从 GitHub 安装（推荐）

在 Codex 中输入：

```text
安装 https://github.com/<你的用户名>/ai-reviewer 中的 ai-reviewer skill
```

也可以让 Codex 使用 Skill Installer：

```text
Install the skill from <你的用户名>/ai-reviewer.
```

### 方式二：手动安装

```bash
git clone https://github.com/<你的用户名>/ai-reviewer.git
mkdir -p ~/.codex/skills
cp -R ai-reviewer ~/.codex/skills/ai-reviewer
```

安装后新开一个 Codex 对话。可用 `$ai-reviewer` 显式调用，或直接提出与论文、review、rebuttal 相关的请求让它自动触发。

## 使用方式

### 1. 投稿前严格审稿

```text
用 ai-reviewer 严格审这篇论文，按 ICLR 标准给出 Critical Review。
重点检查创新性、实验/基线、理论、复现性和可能被 reviewer 挑的问题。
```

### 2. 将 reviewer comments 转为修改计划

```text
用 ai-reviewer 的 Revision Plan 模式分析以下 reviewer comments。
按“必须补实验 / 必须澄清 / 可以收窄 claim / 不值得争辩”排序，
并给每条写一个可执行 rebuttal。
```

### 3. Rebuttal 后复审

```text
用 ai-reviewer 的 Re-review 模式，对照原 review 和我的 rebuttal，
判断每个问题是 resolved、partial 还是 unresolved；
指出仍然可能阻碍升分的两件事。
```

### 4. 分析公开评审

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
