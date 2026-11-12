# 通用版 · 在 ChatGPT、WorkBuddy 等平台使用

这里是 AI 视频制作 SOP 的**通用版**，内容和 Claude Code 版完全一样，只是去掉了 Claude 专用的路径和工具名，并把人物三视图模板合并进来，变成**一个独立的 skill**，不依赖别的 skill。

它遵循 **Agent Skills 开放标准**（一个 `SKILL.md` + `references/` 文件夹），支持这个标准的平台都能直接装。

| 文件 | 给谁用 |
|---|---|
| `ai-video-sop.zip` | 支持 Skills 的平台：直接上传，或者发给平台的 AI 让它安装（ChatGPT Skills、WorkBuddy 等） |
| `ai-video-sop/` | 同上，解压后的文件夹，适合用命令行复制到平台的 skills 目录 |
| `gpt/` | 做 ChatGPT 自定义 GPT：`instructions.md` 粘贴到"指令"，`knowledge/` 里 11 个文件上传到"知识" |
| `single-file/ai-video-sop-完整版.md` | 其他平台（豆包、Kimi、Gemini Gems、各种"项目 / 知识库"功能）：整个文件上传为知识文件，或粘贴进系统提示词 |

---

## 三种安装方式，任选一种

| 方式 | 适合 | 怎么做 |
|---|---|---|
| **一、命令行** | 会用终端 | 复制下面的命令运行 |
| **二、让平台的 AI 帮你装** | 不想碰命令行 | 把下面的一段话发给平台里的 AI |
| **三、界面上传** | 平台有 Skills 页面 | 下载 `ai-video-sop.zip` 后在页面上传 |

仓库地址：`https://github.com/likunru-oss/ai-video-skills`，通用版 skill 在 `universal/ai-video-sop/`。

---

## WorkBuddy

**方式一：命令行**

macOS / Linux：

```bash
git clone https://github.com/likunru-oss/ai-video-skills.git
```

```bash
mkdir -p ~/.workbuddy/skills && cp -R ai-video-skills/universal/ai-video-sop ~/.workbuddy/skills/
```

Windows（PowerShell）：

```powershell
git clone https://github.com/likunru-oss/ai-video-skills.git
```

```powershell
New-Item -ItemType Directory -Force "$env:APPDATA\WorkBuddy\skills" | Out-Null; Copy-Item -Recurse ai-video-skills\universal\ai-video-sop "$env:APPDATA\WorkBuddy\skills\"
```

**方式二：让 WorkBuddy 帮你装**

在 WorkBuddy 的对话里发这段话：

> 帮我安装一个技能：从 https://github.com/likunru-oss/ai-video-skills 下载 `universal/ai-video-sop` 整个文件夹（包括 SKILL.md 和 references 文件夹里的全部文件），放到你的技能目录（macOS / Linux 是 `~/.workbuddy/skills/ai-video-sop/`，Windows 是 `%APPDATA%\WorkBuddy\skills\ai-video-sop\`）。装好后列出文件夹里的文件，确认 SKILL.md 在最外层。

**方式三：界面上传**
1. 下载本仓库里的 `universal/ai-video-sop.zip`。
2. 打开 WorkBuddy 的 Skills（技能）页面 → 添加技能 → 上传技能，选这个压缩包（或解压后的 `ai-video-sop` 文件夹）。
3. 上传前可以预览内容，确认后导入。

装完以后：旧对话不会加载新技能，新开一个对话（或者发 `/reload-skills`、重启 WorkBuddy）。技能列表里出现 `ai-video-sop` 就成功了；看不到时，检查文件夹路径，以及 `SKILL.md` 是否在 `ai-video-sop` 文件夹最外层。

> WorkBuddy 的菜单名称和目录可能随版本变化，以应用内界面和官方文档为准。

---

## ChatGPT

ChatGPT 网页版没有命令行，所以只有"让 AI 帮你装"和"界面上传"两种；需要你的套餐已开通 Skills 功能。想在终端里装，用下面的 Codex。

**方式二：让 ChatGPT 帮你装**
1. 下载 `universal/ai-video-sop.zip`。
2. 新开一个对话，把压缩包拖进去，发这段话：

> 用这个压缩包帮我创建并安装一个技能：保持 SKILL.md 和 references 文件夹里的所有内容原样，不要改写、删减或合并，技能名用 ai-video-sop。装好后告诉我怎么调用。

ChatGPT 会用它自带的建技能工具处理，按提示确认安装即可。

**方式三：界面上传**
1. 打开 chatgpt.com/skills → 创建 → 从电脑上传。
2. 选 `universal/ai-video-sop.zip`。
3. 上传后会做安全扫描，通过后就能在对话里用了。

**用自定义 GPT（所有付费套餐都能用，不需要 Skills 功能）**
1. ChatGPT → 探索 GPT → 创建 → 配置。
2. 名称：`AI 视频制作 SOP`；描述：`把任何故事变成 Seedance 2.5 + Nano Banana 可直接执行的制作包`。
3. 指令：把 `gpt/instructions.md` 的全部内容粘贴进去（约 2300 字，没超过 8000 字符的上限）。
4. 知识：上传 `gpt/knowledge/` 里的 11 个文件。
5. 功能：打开"网页搜索"（用来核实故事的真实依据）；需要导出文件时打开"代码解释器"。
6. 对话开场白（可选）：
   - 做一条 15 秒的竖版广告：一个外卖骑手雨夜送餐，导航带他绕开积水路段。
   - 做一条 30 秒的保温杯 TVC，产品照片我等下发你。
   - 帮我把这个故事做成 5 分钟短片：……
   - 把这段脚本改成 Seedance 2.5 全能参考的视频提示词。

> 自定义 GPT 只能在网页上手动建，ChatGPT 不能替你创建 GPT。

---

## Codex（OpenAI 的命令行 / IDE 工具）

**方式一：命令行**

```bash
git clone https://github.com/likunru-oss/ai-video-skills.git
```

```bash
mkdir -p ~/.codex/skills && cp -R ai-video-skills/universal/ai-video-sop ~/.codex/skills/
```

**方式二：让 Codex 帮你装**

在 Codex 里发：

> $skill-installer 从 https://github.com/likunru-oss/ai-video-skills/tree/main/universal/ai-video-sop 安装 ai-video-sop

装完新开一个会话；看不到时重启 Codex。

---

## 其他支持 Agent Skills 的工具

Cursor 等支持 Agent Skills 标准的工具，用同样的两种方法：
- **命令行：** 把 `universal/ai-video-sop` 文件夹复制到该工具的 skills 目录（看它的文档）。
- **让 AI 帮你装：** 发"从 https://github.com/likunru-oss/ai-video-skills 下载 `universal/ai-video-sop` 整个文件夹，安装到你的技能目录，装好后列出文件确认"。

## 不支持 Skills 的平台

把 `single-file/ai-video-sop-完整版.md` 作为知识文件上传到"项目 / 知识库 / 智能体"，再在说明里写一句：

> 按知识库里《AI 视频制作 SOP · 单文件完整版》的流程和规则工作，默认用中文回答。

---

## 和 Claude Code 版的区别

| | Claude Code 版（`skills/`） | 通用版（`universal/`） |
|---|---|---|
| 结构 | 两个 skill：`ai-video-sop` + `character-sheet` | 一个 skill，人物三视图模板在 `references/character-sheet.md` |
| 提问方式 | 用 Claude Code 的选项卡片提问 | 一次列出全部问题 |
| 文件交付 | 直接写到本地文件夹 | 能写文件就写，不能就把完整制作包分段输出在对话里 |
| 规则和样板 | 一样 | 一样 |
