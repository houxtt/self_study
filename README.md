# Self-Study Skill · 自学助手

面向 Codex、中文优先的自学技能：**一次一个知识点，通过原生输入框逐题作答，检查掌握后再继续，并保存学习进度。**

仓库名是 `self-study-skill`，技能名是 `learn`，在 Codex 中通过 `$learn` 调用。

适合希望从零开始、需要小步讲解、容易被大量信息淹没的学习者。可学习编程、项目代码、文档或其他主题。

## 学习过程

1. 简短讲解一个知识点，给一个具体例子。
2. 弹出一道问题：选择题给选项；复述题和小练习允许自由输入。
3. 等待实际回答，根据复述、解释理由或练习结果判断理解。
4. 卡住时换例子、换讲法，或补必要的前置知识；当前点掌握后才推进。
5. 保存掌握证据、卡点和待答题，下次接着学。

“懂了”或猜对一个选项不直接算掌握。测验选项不会标注推荐答案；有必要时，会在下一轮请你说明理由。

## 安装到 Codex

下载本仓库并解压，或克隆后，进入 `self-study-skill` 目录。在 macOS / Linux 中运行以下命令，将技能复制到当前账号的全局技能目录：

```bash
mkdir -p "$HOME/.agents/skills"
cp -R -i skills/learn "$HOME/.agents/skills/"
```

如果已有同名技能，复制时会询问是否覆盖同名文件；更新前可先备份原目录。Windows 用户可将整个 `skills/learn` 文件夹复制到 `%USERPROFILE%/.agents/skills/learn`。

Codex 的用户技能目录是 `~/.agents/skills/`，也支持指向技能目录的符号链接。技能变更会自动检测；若列表没有更新，重启 Codex。详见 [OpenAI 官方技能说明](https://learn.chatgpt.com/docs/build-skills)。

这是一个提示词技能包，依赖 Codex 提供的工具；无需为它单独配置 API 密钥。

## 怎么使用

开始学习：

```text
$learn 从零教我三角函数
```

学习其他主题：

```text
$learn 教我 Python 函数，我是零基础
```

从指定材料学习：

```text
$learn 带我学习这个项目，先读取 README 和代码，从最基础的概念开始
```

继续、复习或暂停：

```text
$learn 继续学习 ai-isp，读取上次记录
$learn 复习 Python 函数，一次一题
今天先停，保存进度
```

默认使用中文。可以随时说明已有基础、改变语言或调整讲解方式；技能会结合实际回答调整难度。

## 输入框支持

优先使用当前环境可用的原生用户输入工具。选择题提供选项，复述和练习使用自由输入题，每次只问一道。

不同 Codex 客户端、版本和运行模式提供的工具可能不同。如果没有可用弹窗，或工具不支持自由输入题，技能会说明原因并在聊天中提同一道题。它不能凭提示词为客户端增加界面功能。

异步工具返回、预选项、关闭弹窗或超时均不算作答；没有实际回答，就不会评分或继续讲新知识。

## 学习记录

运行时在当前账号的主目录保存：

```text
~/.learn/
├── profile.md
└── topics/
    └── topic-slug/
        ├── knowledge-base.md
        └── concepts/
            └── area.md
```

包括学习偏好、当前知识点、最后一道待答题、掌握证据、未解决问题和复习日期。接续学习需要当前环境能访问这些文件；不同设备间不会自动同步。

### 复习安排

采用上游方案改写的、参考 FSRS 思路的简化启发式安排，根据回答表现调整间隔。它不是完整 FSRS 实现，也没有经过个人数据拟合；复习稳定度不代表已经理解，更不保证不会遗忘。

推进下一知识点的依据始终是实际复述或练习证据。技能只在学习会话中检查到期内容，不会自动发送复习提醒。

## 仓库结构

```text
self-study-skill/
├── README.md
├── LICENSE
├── PROVENANCE.md
└── skills/
    └── learn/
        ├── SKILL.md
        ├── LICENSE
        ├── agents/openai.yaml
        └── references/
            ├── teaching-loop.md
            ├── quiz-rules.md
            ├── fsrs.md
            └── templates.md
```

## 来源与许可证

本项目基于 [Bhala-Srinivash/agent-tutor-skill](https://github.com/Bhala-Srinivash/agent-tutor-skill) 修改，是其面向 Codex 的衍生版本。保留上游 MIT 许可证及版权声明；修改说明见 [PROVENANCE.md](PROVENANCE.md)。

沿用上游教学循环、概念记录和材料优先教学的思路；主要调整为中文小步学习、原生输入框逐题作答、掌握证据与复习状态分离，以及保存待答题的会话接续。

上游致谢的相关来源：

- [Mia Kiraki 的 AI tutor 文章](https://robotsatemyhomework.substack.com/p/the-ai-tutor-i-built-in-claude-that)：教学框架来源。
- [RoundTable02/tutor-skills](https://github.com/RoundTable02/tutor-skills)：概念记录及测验设计参考。
- [open-spaced-repetition](https://github.com/open-spaced-repetition)：FSRS 思路来源。
