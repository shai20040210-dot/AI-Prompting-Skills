# AI-Prompting-Skills

> **AI 提问模板**：把模糊想法、零散要求和粗略问题，整理成可直接复制给 AI 的高质量提示词。

`craft-ai-prompts` 会根据任务类型自动选择提问结构，补全目标、背景、约束、输出格式和验收标准，同时避免编造用户没有提供的信息。

**Skill 名称：** `craft-ai-prompts` · **显示名称：** `AI 提问模板` · **许可证：** `Apache-2.0`

## 导航

- [快速开始](#快速开始)
- [它能做什么](#它能做什么)
- [安装与部署](#安装与部署)
- [如何使用](#如何使用)
- [典型示例](#典型示例)
- [输出模式](#输出模式)
- [项目结构](#项目结构)
- [使用原则](#使用原则)

## 快速开始

### 1. 安装

如果你使用 Codex，可直接输入：

```text
$skill-installer 请从 https://github.com/shai20040210-dot/AI-Prompting-Skills 安装这个 Skill
```

使用其他智能体时，请前往[安装与部署](#安装与部署)查看对应流程。支持 Claude Code、Cursor、Gemini CLI、GitHub Copilot、OpenCode、Cline、Windsurf / Devin Desktop、WorkBuddy 和 TRAE。

### 2. 调用

| 使用环境 | 调用方式 |
| --- | --- |
| ChatGPT | 输入 `@` 并选择 **AI 提问模板** |
| Codex | 输入 `$craft-ai-prompts`，或在 `/skills` 中选择 |
| 其他智能体 | 使用平台对应命令，或直接用自然语言指定 `craft-ai-prompts` |

### 3. 直接试用

```text
帮我把下面这个想法整理成一条完整、可直接复制的 AI 提示词：
我要比较三款 AI 视频工具，重点看画质、价格和短剧制作效率。
```

## 它能做什么

- 把一句话需求扩展为结构清晰、可直接使用的专业提示词
- 保留中文表达、行业术语和用户原意
- 信息不足时使用明确占位符，只在关键条件缺失时提问
- 根据任务复杂度提供 Quick、Standard 和 Professional 三种输出模式
- 为研究、方案、对比、编程、学习、图片、视频和文案任务自动选择结构
- 支持 ChatGPT、Codex 及多种主流 Agent Skills 平台的显式调用和自动触发

### 常见场景

| 场景 | 可以这样说 |
| --- | --- |
| 资料研究 | 帮我整理一条研究 2026 年 AI 视频行业趋势的专业提问词 |
| 执行方案 | 把“做一个短剧 AI 工作流”整理成可执行方案提示词 |
| 对比决策 | 帮我生成即梦、Runway、可灵的专业对比提问模板 |
| 编程调试 | 把报错、环境和目标整理成完整的代码排错提示词 |
| 学习辅导 | 帮我生成一套零基础学习 PyTorch 的提问词 |
| 图片生成 | 根据人物、场景、机位和画风生成专业图片提示词 |
| 视频与分镜 | 把剧情整理成可生成九宫格分镜的提示词 |
| 文案优化 | 把原始文案整理成高级、简洁的改写提示词 |

## 安装与部署

> [!NOTE]
> 以下流程依据各平台截至 **2026-08-24** 发布的 Agent Skills 文档整理。无论使用哪种方式，都请保留仓库完整目录，并确保安装后的文件夹名为 `craft-ai-prompts`。

### 平台速查

| 智能体 | 推荐安装位置或方式 | 显式调用 |
| --- | --- | --- |
| OpenAI Codex | Skill Installer，或 `.agents/skills/craft-ai-prompts` | `$craft-ai-prompts` |
| Claude Code | `~/.claude/skills/craft-ai-prompts` | `/craft-ai-prompts` |
| Cursor | GitHub Remote Rule，或 `~/.cursor/skills/craft-ai-prompts` | `/craft-ai-prompts` |
| Gemini CLI | `gemini skills install <仓库地址>` | 描述任务，由 Gemini 激活 Skill |
| GitHub Copilot | `gh skill install`，或 `~/.copilot/skills/craft-ai-prompts` | 在提示中使用 `/craft-ai-prompts` |
| OpenCode | `~/.config/opencode/skills/craft-ai-prompts` | 描述任务，由 Agent 的 `skill` 工具加载 |
| Cline | `~/.cline/skills/craft-ai-prompts` | `/craft-ai-prompts` |
| Windsurf / Devin Desktop | `~/.codeium/windsurf/skills/craft-ai-prompts` | `@craft-ai-prompts` |
| WorkBuddy（腾讯） | **技能 → 添加技能 → 上传技能** | 自然语言指定 `craft-ai-prompts` |
| TRAE（TraeCode / TraeWork） | `.trae/skills`、`.trae-cn/skills` 或上传 ZIP | `/craft-ai-prompts` 或自然语言指定 |

### 推荐：跨平台共享安装

Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf / Devin Desktop 均可识别通用的 `.agents/skills/` 目录。一份安装即可被这些智能体共同发现。

**macOS / Linux / WSL**

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git ~/.agents/skills/craft-ai-prompts
```

**Windows PowerShell**

```powershell
New-Item -ItemType Directory -Force "$HOME\.agents\skills" | Out-Null
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git "$HOME\.agents\skills\craft-ai-prompts"
```

目录已存在时，可更新到最新版本：

```bash
git -C ~/.agents/skills/craft-ai-prompts pull
```

> [!IMPORTANT]
> WorkBuddy 主要通过客户端上传 ZIP；TRAE 的不同产品使用不同目录。请查看下面对应的平台说明，不要直接套用通用路径。

### 分平台安装说明

点击平台名称展开完整步骤。

<details open>
<summary><strong>OpenAI Codex</strong> · Skill Installer 或手动安装</summary>

#### 使用 Skill Installer

在 Codex 中输入：

```text
$skill-installer 请从 https://github.com/shai20040210-dot/AI-Prompting-Skills 安装这个 Skill
```

#### 手动安装

下载或克隆本仓库，并将完整目录放到以下任一位置：

- 个人范围：`$HOME/.agents/skills/craft-ai-prompts`
- 当前项目：`<项目目录>/.agents/skills/craft-ai-prompts`

请保持 `SKILL.md`、`references/`、`agents/` 和 `assets/` 的相对位置不变。

官方文档：[OpenAI · Build skills](https://learn.chatgpt.com/docs/build-skills)

</details>

<details>
<summary><strong>Claude Code</strong> · <code>/craft-ai-prompts</code></summary>

个人全局安装：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git ~/.claude/skills/craft-ai-prompts
```

仅在当前项目使用时，安装到：

```text
<项目目录>/.claude/skills/craft-ai-prompts
```

安装后输入 `/craft-ai-prompts` 显式调用，也可以直接描述需求让 Claude 自动匹配。如果是在 Claude Code 已运行后第一次创建顶层 `skills` 目录，请重新启动当前会话。

官方文档：[Claude Code Skills](https://code.claude.com/docs/en/skills)

</details>

<details>
<summary><strong>Cursor</strong> · GitHub Remote Rule 或手动安装</summary>

推荐使用 Cursor 内置的 GitHub 导入流程：

1. 打开侧边栏 **Customize**。
2. 进入 **Rules**，点击 **Add Rule**。
3. 选择 **Remote Rule (Github)**。
4. 输入 `https://github.com/shai20040210-dot/AI-Prompting-Skills`。
5. 在 **Customize → Skills** 中确认已发现 `craft-ai-prompts`。

也可以手动放到项目目录 `.cursor/skills/craft-ai-prompts`，或个人目录 `~/.cursor/skills/craft-ai-prompts`。输入 `/craft-ai-prompts` 即可显式调用。

官方文档：[Cursor Agent Skills](https://cursor.com/docs/skills)

</details>

<details>
<summary><strong>Gemini CLI</strong> · 使用 <code>gemini skills install</code></summary>

安装到个人范围：

```bash
gemini skills install https://github.com/shai20040210-dot/AI-Prompting-Skills
```

仅安装到当前工作区：

```bash
gemini skills install https://github.com/shai20040210-dot/AI-Prompting-Skills --scope workspace
```

验证安装：

```bash
gemini skills list --all
```

在 Gemini CLI 会话内，可使用 `/skills list` 查看，使用 `/skills reload` 重新扫描。安装远程 Skill 时会要求确认来源，Skill 被激活时也可能再次请求授权。

官方文档：[Gemini CLI Agent Skills](https://geminicli.com/docs/cli/skills/)

</details>

<details>
<summary><strong>GitHub Copilot</strong> · GitHub CLI 或手动安装</summary>

使用 GitHub CLI 2.90.0 或更高版本时，可先预览再安装：

```bash
gh skill preview shai20040210-dot/AI-Prompting-Skills craft-ai-prompts
gh skill install shai20040210-dot/AI-Prompting-Skills craft-ai-prompts --scope user
```

手动安装位置：

- 项目范围：`.github/skills/craft-ai-prompts`
- 个人范围：`~/.copilot/skills/craft-ai-prompts`

在 Copilot CLI 中执行 `/skills reload` 后，用 `/skills info craft-ai-prompts` 验证。调用示例：

```text
Use the /craft-ai-prompts skill to turn my rough idea into a professional AI prompt.
```

官方文档：[GitHub Copilot Agent Skills](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills)

</details>

<details>
<summary><strong>OpenCode</strong> · 由原生 <code>skill</code> 工具加载</summary>

个人全局安装：

```bash
mkdir -p ~/.config/opencode/skills
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git ~/.config/opencode/skills/craft-ai-prompts
```

当前项目安装位置为 `.opencode/skills/craft-ai-prompts`。OpenCode 会把 Skill 加入原生 `skill` 工具的可用列表；直接描述“把这个需求整理成专业 AI 提示词”，Agent 会在相关时自动加载。

官方文档：[OpenCode Agent Skills](https://opencode.ai/docs/skills/)

</details>

<details>
<summary><strong>Cline</strong> · <code>/craft-ai-prompts</code></summary>

将仓库安装到以下任一位置：

- 项目范围：`.cline/skills/craft-ai-prompts`
- macOS / Linux 全局：`~/.cline/skills/craft-ai-prompts`
- Windows 全局：`C:\Users\<用户名>\.cline\skills\craft-ai-prompts`

安装后打开 Cline 面板底部的 **Skills** 菜单，确认该 Skill 已启用。输入 `/craft-ai-prompts` 可强制调用，也可以直接描述任务让 Cline 自动匹配。

官方文档：[Cline Skills](https://docs.cline.bot/customization/skills)

</details>

<details>
<summary><strong>Windsurf / Devin Desktop</strong> · <code>@craft-ai-prompts</code></summary>

将仓库安装到：

- 当前工作区：`.windsurf/skills/craft-ai-prompts`
- 个人全局：`~/.codeium/windsurf/skills/craft-ai-prompts`

也可以打开 Cascade 面板右上角菜单，进入 **Customizations → Skills** 查看和管理。输入 `@craft-ai-prompts` 显式调用，或直接描述任务自动触发。

Devin Desktop 还会识别通用的 `.agents/skills/` 与 `~/.agents/skills/` 目录，因此可直接使用前面的跨平台共享安装方案。

官方文档：[Windsurf / Devin Desktop Skills](https://docs.devin.ai/desktop/cascade/skills)

</details>

<details>
<summary><strong>WorkBuddy（腾讯）</strong> · 上传 ZIP 安装</summary>

WorkBuddy 主要通过客户端界面导入本地技能包，不建议直接套用 `.agents/skills/` 路径。

先将仓库打包为 ZIP，并确保 ZIP 根目录直接包含 `SKILL.md`。

**macOS / Linux / WSL**

```bash
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git craft-ai-prompts
cd craft-ai-prompts
zip -r ../craft-ai-prompts.zip SKILL.md agents assets references README.md LICENSE
```

**Windows PowerShell**

```powershell
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git craft-ai-prompts
Compress-Archive -Path ".\craft-ai-prompts\*" -DestinationPath ".\craft-ai-prompts.zip" -Force
```

在 WorkBuddy 中安装：

1. 打开客户端的 **技能** 页面。
2. 点击 **添加技能**。
3. 选择 **上传技能**，上传 `craft-ai-prompts.zip`。
4. 安装完成后进入 **已安装**，确认 `craft-ai-prompts` 已启用。
5. 在任意任务中直接用自然语言触发。

测试示例：

```text
使用 craft-ai-prompts，把下面这个模糊需求整理成一条可直接复制的专业 AI 提问词：
我想做一个面向短剧制作的 AI 视频工作流。
```

WorkBuddy 也支持在对话中描述能力需求，让智能体查找或创建 Skill；从本仓库安装时，上传经过检查的本地 ZIP 更便于确认实际内容。

官方文档：[WorkBuddy 技能](https://www.workbuddy.ai/docs/zh/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market) · [创建自己的 Skills](https://www.workbuddy.ai/docs/zh/workbuddy/From-Beginner-to-Expert-Guide/Practice-Cases/Create-Skills)

</details>

<details>
<summary><strong>TRAE（TraeCode / TraeWork）</strong> · 本地目录或上传 ZIP</summary>

TRAE 原生支持包含 `SKILL.md` 的 Agent Skill，但 TraeCode / IDE 与 TraeWork 国内版的全局目录不同。

#### TraeCode / TRAE IDE

项目范围：

```text
<项目目录>/.trae/skills/craft-ai-prompts
```

macOS / Linux 全局安装：

```bash
mkdir -p ~/.trae/skills
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git ~/.trae/skills/craft-ai-prompts
```

Windows PowerShell 全局安装：

```powershell
New-Item -ItemType Directory -Force "$HOME\.trae\skills" | Out-Null
git clone https://github.com/shai20040210-dot/AI-Prompting-Skills.git "$HOME\.trae\skills\craft-ai-prompts"
```

#### TraeWork 国内版

- 项目范围：`<项目目录>/.trae/skills/craft-ai-prompts`
- macOS / Linux 全局：`~/.trae-cn/skills/craft-ai-prompts`
- Windows 全局：`%USERPROFILE%\.trae-cn\skills\craft-ai-prompts`

也可以使用前面生成的 `craft-ai-prompts.zip` 通过界面安装：

1. 打开左侧 **插件市场**。
2. 进入 **技能** 页签。
3. 点击右上角 **上传技能**。
4. 上传 ZIP 文件并确认。
5. 在 **已安装** 页签确认 Skill 已启用。

#### 在 TRAE 中调用

- 在对话框输入 `/`，从列表选择 `craft-ai-prompts`。
- 直接输入“使用 craft-ai-prompts 把下面需求整理成专业提问词”。
- 也可以直接描述需求，由 TRAE 根据 `description` 自动调用。

官方文档：[TRAE IDE Skills](https://docs.trae.ai/ide/skills?_lang=zh) · [TraeWork 技能](https://docs.trae.cn/work_skills)

</details>

### 兼容说明

- 核心能力位于 `SKILL.md` 和 `references/prompt-patterns.md`，符合通用 Agent Skills 目录结构。
- `agents/openai.yaml` 主要用于 OpenAI 产品的界面显示；其他智能体即使忽略它，也不影响 Skill 的核心能力。
- 当前版本不包含可执行脚本，安装内容只有说明、模板、配置和图标。
- 如果目标智能体只支持 Rules、Commands 或 `AGENTS.md`，但不支持 Agent Skills，则不能仅靠复制本仓库完成原生安装，需要先转换格式。

## 如何使用

### ChatGPT

在输入框键入 `@`，选择 **AI 提问模板**，然后描述原始需求：

```text
@AI 提问模板
我想用 AI 帮我设计一套短剧分镜，但不知道应该怎么问。请整理成专业提示词。
```

### Codex

输入 `$craft-ai-prompts` 显式调用：

```text
$craft-ai-prompts 把下面的需求整理成一条可直接复制的专业提问词：
我想用 PyTorch 做一个 Windows 摄像头图像识别项目。
```

也可以输入 `/skills` 后选择该 Skill。

### 自动触发

安装后也可以直接用自然语言提出需求：

```text
帮我把这个想法整理成一条完整的 AI 提问词：
我要比较三款 AI 视频工具，重点看画质、价格和短剧制作效率。
```

## 典型示例

<details>
<summary><strong>示例 1：通用需求</strong> · 新媒体账号运营方案</summary>

**输入**

```text
帮我写一个问 AI 的模板，我要制定新媒体账号运营方案。
```

Skill 会补全目标、账号背景、目标用户、平台、周期、预算、交付物和验收标准，输出一条可以直接复制的完整提示词。

</details>

<details>
<summary><strong>示例 2：图片生成</strong> · 16:9 UE5 动漫场景</summary>

**输入**

```text
$craft-ai-prompts 帮我生成一个 16:9、UE5 3D 动漫风、卧室场景的图片提示词，人物和空间位置必须保持一致。
```

Skill 会组织人物、场景、机位、构图、灯光、风格、连续性和负面提示词等关键字段。

</details>

<details>
<summary><strong>示例 3：代码排错</strong> · OpenCV 摄像头错误</summary>

**输入**

```text
$craft-ai-prompts 把我的 OpenCV 摄像头报错整理成一个能让 AI 精准排查的问题模板。
```

Skill 会要求补充操作系统、Python 与依赖版本、硬件、完整报错、最小复现代码、预期行为和验证步骤。

</details>

## 输出模式

| 模式 | 适合情况 | 输出内容 |
| --- | --- | --- |
| Quick | 目标明确、只想快速使用 | 一条精炼、可直接复制的提示词 |
| Standard | 大多数日常任务 | 完整提示词，加必要占位符或假设；默认模式 |
| Professional | 复杂项目或专业交付 | 完整版、精简备选版，以及确有价值时的模型使用建议 |

## 项目结构

```text
AI-Prompting-Skills/
├── SKILL.md                    # Skill 的核心工作流程与规则
├── agents/
│   └── openai.yaml             # 显示名称、简介和默认调用提示
├── references/
│   └── prompt-patterns.md      # 不同任务类型的提问模板库
├── assets/
│   └── icon.svg                # Skill 图标
├── README.md                   # 使用说明
└── LICENSE                     # Apache-2.0 许可证
```

## 使用原则

- 默认只生成提示词，不直接执行提示词中的任务；除非你明确要求“提示词和结果都要”。
- 不会虚构个人信息、资料来源、工具能力或未提供的要求。
- 对时效性研究任务，会要求目标 AI 使用最新权威来源、标注日期并提供链接。
- 对创意任务，会锁定必须保持的角色、服装、道具、空间关系、画幅和输出数量。

## 相关资源

- [Skill 核心说明](./SKILL.md)
- [完整提问模板库](./references/prompt-patterns.md)

<details>
<summary><strong>展开查看各平台官方文档</strong></summary>

- [OpenAI：Build skills](https://learn.chatgpt.com/docs/build-skills)
- [Claude Code：Skills](https://code.claude.com/docs/en/skills)
- [Cursor：Agent Skills](https://cursor.com/docs/skills)
- [Gemini CLI：Agent Skills](https://geminicli.com/docs/cli/skills/)
- [GitHub Copilot：Agent Skills](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills)
- [OpenCode：Agent Skills](https://opencode.ai/docs/skills/)
- [Cline：Skills](https://docs.cline.bot/customization/skills)
- [Windsurf / Devin Desktop：Skills](https://docs.devin.ai/desktop/cascade/skills)
- [WorkBuddy：技能](https://www.workbuddy.ai/docs/zh/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)
- [TRAE IDE：Skills](https://docs.trae.ai/ide/skills?_lang=zh)
- [TraeWork：技能](https://docs.trae.cn/work_skills)

</details>

## License

本项目使用 [Apache License 2.0](./LICENSE) 开源许可证。
