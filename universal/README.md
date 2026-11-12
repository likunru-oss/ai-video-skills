# 通用版 · 在 ChatGPT、WorkBuddy 等平台使用

这里是 AI 视频制作 SOP 的**通用版**，内容和 Claude Code 版完全一样，只是去掉了 Claude 专用的路径和工具名，并把人物三视图模板合并进来，变成**一个独立的 skill**，不依赖别的 skill。

它遵循 **Agent Skills 开放标准**（一个 `SKILL.md` + `references/` 文件夹），支持这个标准的平台都能直接装。

| 文件 | 给谁用 |
|---|---|
| `ai-video-sop.zip` | 支持 Skills 的平台：直接上传这个压缩包（ChatGPT Skills、WorkBuddy 等） |
| `ai-video-sop/` | 同上，解压后的文件夹，适合手动放到平台的 skills 目录 |
| `gpt/` | 做 ChatGPT 自定义 GPT：`instructions.md` 粘贴到"指令"，`knowledge/` 里 11 个文件上传到"知识" |
| `single-file/ai-video-sop-完整版.md` | 其他平台（豆包、Kimi、Gemini Gems、各种"项目 / 知识库"功能）：整个文件上传为知识文件，或粘贴进系统提示词 |

---

## WorkBuddy

**方法一：在应用里上传**
1. 下载本仓库里的 `universal/ai-video-sop.zip`。
2. 打开 WorkBuddy 的 Skills（技能）页面 → 添加技能 → 上传技能，选这个压缩包（或解压后的 `ai-video-sop` 文件夹）。
3. 上传前可以预览内容，确认后导入。

**方法二：手动放文件**
把 `ai-video-sop` 文件夹整个复制到：
- macOS / Linux：`~/.workbuddy/skills/`
- Windows：`%APPDATA%\WorkBuddy\skills\`

重启 WorkBuddy，技能列表里出现 `ai-video-sop` 就成功了。看不到时，检查文件夹路径和 `SKILL.md` 是否在文件夹最外层。

> WorkBuddy 的菜单名称和路径可能随版本变化，以应用内界面和官方文档为准。

## ChatGPT

**方法一：Skills（需要你的 ChatGPT 套餐已开通 Skills 功能）**
1. 下载 `universal/ai-video-sop.zip`。
2. 在 ChatGPT 的 Skills 页面上传这个压缩包。
3. 之后在对话里说"做一条 AI 视频广告……"就会自动调用。

**方法二：自定义 GPT（所有付费套餐都能用）**
1. ChatGPT → 探索 GPT → 创建 → 配置。
2. 名称：`AI 视频制作 SOP`；描述：`把任何故事变成 Seedance 2.0 + Nano Banana 可直接执行的制作包`。
3. 指令：把 `gpt/instructions.md` 的全部内容粘贴进去（约 2300 字，没超过 8000 字符的上限）。
4. 知识：上传 `gpt/knowledge/` 里的 11 个文件。
5. 功能：打开"网页搜索"（用来核实故事的真实依据）；需要导出文件时打开"代码解释器"。
6. 对话开场白（可选）：
   - 做一条 15 秒的竖版广告：一个外卖骑手雨夜送餐，导航带他绕开积水路段。
   - 做一条 30 秒的保温杯 TVC，产品照片我等下发你。
   - 帮我把这个故事做成 5 分钟短片：……
   - 把这段脚本改成 Seedance 2.0 全能参考的视频提示词。

## 其他支持 Agent Skills 的工具

Codex、Cursor 等支持 Agent Skills 标准的工具：按各自文档把 `ai-video-sop` 文件夹放进它们的 skills 目录即可。

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
