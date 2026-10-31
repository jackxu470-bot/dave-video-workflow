# 在 WorkBuddy 中配合 ChatCut 使用

WorkBuddy（用户有时写作 WorkBody）负责理解需求和执行工作流；ChatCut 负责实际视频项目与时间线；Dave Video Workflow 提供分阶段制作规则。三者分别安装或连接，导入 Skill 不等于已经连接 ChatCut。

## 1. 导入这个 Skill

1. 下载 [Skill 专用导入包](../downloads/dave-video-workflow-skill.zip)。打开 GitHub 文件页后使用下载原始文件的入口，保存 ZIP，无需解压。不要把整个仓库的 Download ZIP 当作专用 Skill 包。
2. 在 WorkBuddy 左侧进入 **专家·技能·连接器 → 技能**，选择 **添加技能 → 上传技能**，选择刚下载的本地包。
3. 在 **已安装** 中确认 `dave-video-workflow` 已出现并启用，然后开启新对话。若界面名称不同，以当前版本的技能管理入口为准。

WorkBuddy 官方说明支持上传本地技能包；对话搜索安装针对技能市场中的技能。本项目尚未上架市场，采用本地导入方式。[WorkBuddy：技能管理](https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)

导入包内直接包含 `SKILL.md`、`references/`、`agents/` 和许可证，来自本仓库公开文件，不含素材或连接凭据。若当前版本拒绝导入，请保留具体报错并参考 [WorkBuddy：技能结构](https://open.workbuddy.cn/docs/skill)，不要把报错当作 ChatCut 未连接。此包已检查内容与结构，尚未在 WorkBuddy 中实际完成导入试验。

## 2. 连接 ChatCut：选择与你使用方式一致的一条

### A. 本机 ChatCut Desktop 项目

适合素材与剪辑工程主要在自己电脑上的使用者。

1. 在同一台电脑安装 WorkBuddy 和 ChatCut Desktop，并至少启动 ChatCut Desktop 一次。下载与安装方式见 [ChatCut Desktop 官方说明](https://chatcut.io/docs/desktop-app)。
2. 在 ChatCut Desktop 的侧边栏顶部打开 **Agents on this computer**，找到 WorkBuddy，按连接状态完成确认。WorkBuddy 显示 **Confirm** 时，需要到 WorkBuddy 中批准连接。
3. 退出并重新打开 WorkBuddy，开始新对话，让新会话加载 ChatCut 的本机工具。
4. 在 ChatCut Desktop 打开目标项目，或复制该连接面板中的 **Tell your agent** 项目提示，让 WorkBuddy 核对目标项目。

此方式通过本机连接操作 Desktop 工程。ChatCut Desktop 接入时会关闭 WorkBuddy 中的云端 Agent Plugin，避免把本机工程与云端工程混用；不要同时按下一节反复配置另一条连接。[ChatCut：外部助手连接 Desktop](https://chatcut.io/docs/desktop-app)

### B. ChatCut 云端项目

如果要让 WorkBuddy 连接云端 ChatCut，使用 [ChatCut 官方 WorkBuddy 安装指南](https://chatcut.io/workbuddy)，不要套用 Codex 或 Claude Code 的安装提示。[ChatCut：Agent Plugin 支持的应用](https://chatcut.io/docs/agent-plugin)

可以在 WorkBuddy 新对话中请它读取该官方指南并协助配置。按照指南完成本机环境检查、连接设置及浏览器授权，完成后再开新对话检查工具。密钥和令牌只放在本机配置中，不粘贴到聊天或公开仓库。授权失效时按官方指南恢复，不共享他人的登录信息。

官方云端指南提供的是 Bash 示例，需要相应命令环境；Windows 用户不能直接把 Bash 语法照搬到原生 PowerShell。让助手先核对当前系统，按官方指南完成适配。连接步骤会随产品更新，以该页面为准。[ChatCut：WorkBuddy 云端配置](https://chatcut.io/workbuddy)

## 3. 先验证连接，再开始剪辑

在 WorkBuddy 新对话中输入：

```text
请确认 Dave Video Workflow 技能已经启用，并检查 ChatCut 工具是否可用。
先读取或列出可用项目，告诉我当前连接的是本机 Desktop 还是云端项目。
先不要改动时间线、上传素材或创建生成任务。
```

能读到正确项目，才说明连接基本可用。只会解释流程、无法调用 ChatCut 工具时，先完成连接；不要把文字回复当作剪辑完成。

## 4. 开始制作本期视频

自己在 ChatCut 建立或打开本期项目并导入原片，核对名称、画幅和素材版本。随后在 WorkBuddy 中输入：

```text
请使用 Dave Video Workflow（dave-video-workflow）配合 ChatCut 制作本期口播。
原片已经由我导入，请先核对目标项目和素材版本。
本期为 9:16 竖屏，先做口播剪辑，不加 MG。
按照技能里的剪辑规则处理重说、无效语气词和明显长停顿，保留原意与自然节奏。
先保存并展示剪辑结果，等我确认后再进入字幕。
视频、字幕导出以及平台发布由我自己操作。
```

把画幅、是否需要 MG 和阶段要求换成自己的需求。上述项目和素材状态只有在实际完成后才能使用；尚未导入时先说明缺少什么，不让助手假定素材已经准备好。WorkBuddy 中按技能名调用即可，不要求照搬 Codex 的 `$` 调用语法。

剪辑确认后，可继续说“按同一工作流添加字幕”；字幕确认后再做文案与封面。希望连续处理时明确授权阶段范围。过程文件保存在自己的本期项目目录，不放回下载的公开仓库。

## 5. 常见问题

| 现象 | 检查方向 |
| --- | --- |
| 技能已导入，但不能剪视频 | Skill 与 ChatCut 连接分别检查，先验证实际工具可用 |
| 新装连接后，旧对话仍没有工具 | 重新打开 WorkBuddy 并开始新会话 |
| 找到项目，但不是自己要编辑的那一期 | 核对本机或云端连接与目标项目，确认后再修改 |
| 找不到这个技能 | 在已安装列表检查是否导入且开启；本项目不依赖技能市场搜索 |
| ZIP 无法导入 | 确认使用专用包，核对包内入口和当前客户端报错；尚未进行客户端导入实测 |
| 云端授权失效 | 返回官方 WorkBuddy 专用指南，按当前认证恢复方式处理 |

本说明依据上述官方文档整理，核对日期为 2026-10-31。未声称已在读者设备上安装、授权或完成制作，也未进行 WorkBuddy + ChatCut 的真实媒体全流程试跑。
