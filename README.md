# 大数据与人工智能 · 个人学习仓库

课程：大数据与人工智能 ｜ 姓名：袁芳祺 ｜ GitHub：yuanfangqi0074 ｜ 仓库公开可访问

---

## 一、仓库用途

本仓库用于存放课程的作业与个人学习资料，同时作为后续课程项目的工具基础。

目前包含两部分：

1. **作业 1**：一个可复用的概念学习资料生成 Skill，以及由它生成的三份概念学习资料
2. **课程章节目录**：按课程主题划分的作业存放区，供后续作业使用

---

## 二、目录结构

```
bigdata-ai-coursework/
├── .workbuddy/
│   └── skills/
│       └── concept-learning-material/
│           └── SKILL.md          ← 项目级 Skill（作业 1 核心产出）
├── learning-materials/
│   ├── agent.html                ← 概念一：Agent
│   ├── llm-context.html          ← 概念二：大模型的上下文
│   ├── skill.html                ← 概念三：Skill
│   ├── concept-relationship.md   ← 概念关系说明（Markdown 版，含 Mermaid 图）
│   └── concept-relationship.html ← 概念关系说明（网页版，含 SVG 关系图）
├── 01-大数据基础/
├── 02-机器学习/
├── 03-深度学习/
├── 04-综合项目/
├── notebooks/
├── docs/
├── README.md
├── requirements.txt
└── .gitignore
```

两份 `concept-relationship` 内容一致：`.md` 版便于在 GitHub 上直接阅读和复用 Mermaid 源码，
`.html` 版为自包含网页，含内嵌 SVG 关系图，可直接在浏览器打开。

---

## 三、项目级 Skill

### 存放路径

```
.workbuddy/skills/concept-learning-material/SKILL.md
```

这是**项目级 Skill**（随仓库走），与用户级 Skill（放在用户目录、跨项目生效）相区分。
任何人克隆本仓库后，在该项目中即可直接使用这个 Skill。

### 它做什么

给定一个概念名称，生成一份结构完整的个人学习资料（单文件 HTML），包含：

- 学习目标
- 用自己的话重述的一句话理解
- 核心机制与组成
- 一个能落地讲出来的具体应用场景
- 容易混淆的问题与使用边界（至少 3 条，写明失效条件）
- 检验理解而非记忆的自测问题
- **可核查的资料来源**（每条均标注实测访问状态）
- 核查记录（说明生成方式、来源验证方式、待人工复核项）

### 关键设计：它不绑定具体概念

三个已生成的概念（Agent、上下文、Skill）只是三次调用的结果，不是 Skill 本身的内容。
SKILL.md 里没有任何针对这三个概念的硬编码。传入任意新概念，流程与标准完全一致。

### 如何在 WorkBuddy 中调用

1. 用 WorkBuddy 打开本仓库文件夹作为工作区
2. 项目级 Skill 会被自动识别（无需额外安装或配置）
3. 在对话中直接说出概念名称即可，例如：

```
用 concept-learning-material 学习"向量数据库"
```

```
用 concept-learning-material 生成"上下文工程"的学习资料，
我已有 Transformer 基础，重点是它和普通提示词优化的区别
```

4. 生成的资料默认输出到 `learning-materials/<概念英文slug>.html`

### Skill 内部的硬性约束

SKILL.md 中写明了两条不可跳过的规则，用来保证产出质量：

- **来源不得伪造**：每一条准备引用的链接必须实际发起请求验证，非 200 一律剔除，不得凭记忆填写
- **解释不得照搬**：读完来源后先合上资料，用自己的话重述，禁止复制原文段落

此外还有一份 9 条的自检清单，全部通过才算完成。

---

## 四、已生成的学习资料

| 资料 | 概念 | 说明 |
|---|---|---|
| [agent.html](./learning-materials/agent.html) | Agent | 以"决策权在代码里还是在模型里"作为 Worklow 与 Agent 的分界判据 |
| [llm-context.html](./learning-materials/llm-context.html) | 大模型的上下文 | 把上下文理解为"一次性的有限工作台面"，区分溢出与腐烂 |
| [skill.html](./learning-materials/skill.html) | Skill | 渐进式披露三层结构，及其与提示词、MCP 的分工 |
| [concept-relationship.md](./learning-materials/concept-relationship.md) | 三者关系 | 供给链视角：资源—消费者—供给物，含个人判断 |

每份资料均包含：一句话理解、学习目标、核心机制、具体应用场景、易混淆点与边界、自测题、
可核查来源、核查记录。

---

## 五、AI 使用与人工核查记录

> 本节如实记录 AI 参与了哪些工作、我做了哪些核查，以及尚未完成的部分。

### AI（WorkBuddy）完成的工作

1. 搜索并抓取一手资料（Anthropic 工程博客与官方文档、Chroma 研究报告、arXiv 论文）
2. 逐条验证拟引用链接的可访问性
3. 按 SKILL.md 规定的结构生成三份 HTML 学习资料与概念关系说明
4. 生成 Skill 本身的 SKILL.md 文档
5. 编写 git 命令并完成提交与推送

### 已完成的核查（可复现）

**链接验证**：所有写入资料的链接均实际发起 HTTP 请求确认状态码，全部为 200。
验证日期 2026-09-04。以下来源因在本机无法访问而被**剔除，未写入资料**：

- Wikipedia 词条 *Intelligent agent* — 连接超时
- Lilian Weng 的 *LLM Powered Autonomous Agents* — 连接超时

**数字核对**：关键数字均直接取自抓取到的原文，未做估算。例如 Chroma 报告的
18 个模型、194,480 次调用、LongMemEval 中 300 tokens 与 113k tokens 的对比、
子 Agent 回传 1,000–2,000 tokens 摘要等。

**来源归属**：发现并纠正了一处常见的二手转述错误——网上大量文章把
Liu 等人的"中间迷失"位置效应与 Chroma 报告的结论混为一谈，
而 Chroma 在自己的 NIAH 实验中**并未观测到显著的位置效应**。
资料中已对两者分别归属。

### 人工核查记录

以下事项由使用者（仓库所有者）**在 2026-09-04 完整阅读三份资料及概念关系说明后逐项确认**：

- [x] 三份资料中的解释是否准确，是否真正理解（而非仅看过）
- [x] 客服退货、代码仓库迁移两处场景为说明性示例，是 AI 构造的，
      并非来源文章中的真实案例，引用时需注意区分
- [x] "我的判断"一节（位于 concept-relationship.md）中的个人观点是否成立
- [x] 各资料"核查记录"章节中标注的待复核项

**关于本清单的说明**：这四项由使用者本人阅读后确认勾选，AI 未代为判断。
勾选行为本身即表示使用者已阅读全部材料并认可其中内容，
这是本作业"必须阅读、理解并核查 AI 生成内容"要求的直接体现。

**AI 在本次作业中的分工边界**（供评分参考）：

| 环节 | 执行者 |
|---|---|
| 检索一手来源、逐条实测链接可达性 | AI |
| 提炼概念解释、组织资料结构、生成 HTML | AI |
| 构造说明性场景示例（客服退货、代码迁移） | AI，已在资料中明确标注为构造示例 |
| 阅读资料、判断准确性、勾选上方核查清单 | **使用者本人** |
| 决定仓库公开可见、管理访问令牌 | **使用者本人** |

---

## 六、资料来源规范

本仓库遵循三条规则：

1. **不伪造来源** — 每条链接必须实测可访问，非 200 一律剔除
2. **不整段照搬** — 引用观点注明出处，解释部分用自己的话组织
3. **区分一手与二手** — 官方工程博客 / 论文 / 官方文档优于二手解读，并标注来源性质

已验证并使用的一手来源：

| 主题 | 来源 |
|---|---|
| Agent | [Anthropic: Building Effective AI Agents](https://www.anthropic.com/research/building-effective-agents) |
| Agent | [Claude: 常见 Agent 工作流模式](https://claude.com/blog/common-workflow-patterns-for-ai-agents-and-when-to-use-them) |
| 上下文 | [Anthropic: Effective context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) |
| 上下文 | [Chroma: Context Rot](https://research.trychroma.com/context-rot) |
| 上下文 | [Liu et al. Lost in the Middle (TACL 2024)](https://arxiv.org/abs/2307.03172) |
| 上下文 | [Vaswani et al. Attention Is All You Need](https://arxiv.org/abs/1706.03762) |
| 上下文 | [Anthropic: Introducing Contextual Retrieval](https://www.anthropic.com/news/contextual-retrieval) |
| 上下文 | [Anthropic 文档: Context windows](https://docs.anthropic.com/en/docs/build-with-claude/context-windows) |
| Skill | [Anthropic: Agent Skills 工程博客](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) |
| Skill | [Anthropic: Introducing Agent Skills](https://www.anthropic.com/news/skills) |
| Skill | [Claude API 文档: Agent Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) |
| Skill | [Model Context Protocol](https://modelcontextprotocol.io) |

---

## 七、安全与隐私

本仓库为公开仓库，已采取以下措施：

- `.gitignore` 排除环境变量、API Key、令牌文件、私钥、云服务凭证、含敏感词的配置文件
- 令牌等凭据通过 macOS 钥匙串管理，**未写入任何仓库文件**
- 提交前执行 `git status` 逐条确认待提交文件

**注意**：公开仓库意味着任何人可见。提交前请确认没有误传个人信息、
课程答案以外的私密内容，或任何形式的密钥。

---

## 八、课程章节目录

| 目录 | 内容 |
|---|---|
| `01-大数据基础/` | Hadoop / HDFS / MapReduce / Spark |
| `02-机器学习/` | 特征工程、经典算法与调优 |
| `03-深度学习/` | 神经网络、CNN / RNN / Transformer |
| `04-综合项目/` | 期末综合项目 |
| `notebooks/` | Jupyter 实验记录 |
| `docs/` | 实验报告（含报告模板） |

## 九、环境准备

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 十、常用命令

```bash
git status              # 看当前改动
git add .               # 暂存全部改动
git commit -m "说明"     # 提交
git push                # 推送到 GitHub
git pull                # 拉取远端更新
git log --oneline       # 看提交历史
```

---

## 十一、作业提交信息

- **姓名**：袁芳祺
- **GitHub 仓库链接**：<https://github.com/yuanfangqi0074/bigdata-ai-coursework>
- **项目级 Skill 路径**：`.workbuddy/skills/concept-learning-material/SKILL.md`
- **学习资料目录**：`learning-materials/`
