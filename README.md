# Dave Video Workflow

从口播剪辑到字幕、封面和发布文案的完整制作流程。

把口播剪辑、可选 MG 动画、字幕、发布文案、封面和文件整理串成一套分阶段、可预览的制作流程。适合中文知识分享、软件教程和日常经验类口播，默认以小红书文案为例，也可按用户要求调整平台。

这是给 AI 助手使用的制作指引，不是独立的视频编辑软件。仓库只包含通用规则和虚构文字示例，不附带任何个人原片、成片、头像、账号资料或真实项目内容。

## 能做什么

- 清理重说、口头禅和无意义停顿，保留原意与自然节奏。
- 按需规划 MG 的位置、内容和时长，避免套用旧案例。
- 先校对和语义断句，再按真实口播时间生成字幕。
- 根据最终内容写标题、正文和标签，再制作封面。
- 保存各阶段结果，区分待确认、已确认、待导出和已交付。

默认流程：确认输入 → 口播剪辑 → 可选 MG 方案与制作 → 字幕 → 文案 → 封面 → 归档。每阶段展示并等待确认；用户可明确授权连续处理指定阶段。导出与发布默认由用户操作。

## 使用前需要什么

| 任务 | 所需能力 |
| --- | --- |
| 读取和执行 Skill | 支持 Agent Skills 的 AI 助手，例如 Codex、WorkBuddy |
| 实际剪辑、字幕和 MG 上时间线 | 已连接且具有相应权限的视频编辑工具；本工作流以 ChatCut 为主要使用场景 |
| 从音视频生成带时间的字幕 | 编辑工具的转写能力或用户提供的带时间字幕 |
| 生成封面图片 | 可用的图像生成或设计工具，或者用户提供的图片 |
| 导出和发布 | 用户使用自己的编辑器、存储位置与平台账号 |

Skill 不包含 ChatCut、工具插件、API 密钥、字体、模型额度或付费服务。部分工具功能可能收费，以使用者自己的服务页面为准。它不自动连接账号，也不自动上传原始素材。没有相应工具时，只能交付能完成的文字方案或文件，不能声称已剪辑、生成图片或完成导出。

无需安装额外的中文润色 Skill；自然表达要求已经写入参考文档。MG 部分提供制作原则，不包含动画模板源码、第三方样片或字体文件。

## 在 Codex 中使用

1. 下载本仓库，或使用 Git 克隆。
2. 将 `skills/dave-video-workflow/` 整个文件夹复制到你的视频工作区的 `.agents/skills/` 下。复制后应能找到 `.agents/skills/dave-video-workflow/SKILL.md`。
3. 在该工作区打开 Codex，确认技能已被识别；如未显示，重新打开工作区或会话，并参考当前官方文档。
4. 调用 `$dave-video-workflow`，提供本期项目位置与已导入素材的说明。

也可以向支持技能安装的助手提供这个仓库的实际 GitHub 地址，指定安装 `skills/dave-video-workflow`。不同助手的安装方式可能不同，不保证安装本仓库后即可直接调用其视频工具。

示例请求：

```text
用 $dave-video-workflow 处理本期口播。
项目保存在我指定的视频项目文件夹，原片已经由我导入 ChatCut。
画幅是 9:16，先做口播剪辑，不加 MG。每个阶段先让我确认。
```

如果只想生成文案：

```text
用 $dave-video-workflow，根据我提供的最终字幕生成小红书文案。
只做这一步，给我 10 个标题、1 版正文和 10 个相关标签，不制作封面。
```

## 在 WorkBuddy 中配合 ChatCut 使用

先 [下载 Skill 专用导入包](downloads/dave-video-workflow-skill.zip)，在 WorkBuddy 的 **专家·技能·连接器 → 技能 → 添加技能 → 上传技能** 中导入并启用。再连接自己的 ChatCut：本机项目使用 ChatCut Desktop 的 **Agents on this computer**；云端项目按 [ChatCut 的 WorkBuddy 专用指南](https://chatcut.io/workbuddy) 安装连接。导入 Skill 与连接视频工具是两件事。

详细步骤、连接检查和可复制的制作请求见 **[WorkBuddy + ChatCut 使用说明](docs/workbuddy-chatcut.md)**。该说明依据官方文档整理，导入包尚未在 WorkBuddy 客户端实测。[WorkBuddy 官方技能说明](https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)

## 仓库结构

```text
skills/dave-video-workflow/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── editing.md
    ├── motion-graphics.md
    ├── captions.md
    ├── copy-and-covers.md
    └── files-and-handoff.md
examples/
└── fictional-walkthrough.md
docs/
└── workbuddy-chatcut.md
downloads/
└── dave-video-workflow-skill.zip
```

参见 [技能入口](skills/dave-video-workflow/SKILL.md) 和 [虚构示例](examples/fictional-walkthrough.md)。示例仅用于解释工作方式，没有实际音视频，也没有经过完整媒体制作验证。

## 素材与隐私

使用者应把自己的项目和素材放在仓库外。仓库的 `.gitignore` 只放行约定目录中的 Markdown 文档、Skill 显示配置、从公开文件制作的专用导入包以及根目录说明和许可证，减少误提交素材的机会。新增脚本、图片或配置文件时，要先检查内容再有意修改放行规则。忽略规则不能清除已经提交的内容，也不能代替人工检查。

不要把密钥、登录状态、项目资产 ID、个人路径、客户资料、聊天记录或真实项目内容写入公开贡献。修改工作流时优先用虚构示例。

## 许可

本仓库原创说明与规则采用 [MIT License](LICENSE)，允许使用、修改和分发，也允许商用，需保留许可声明。使用者自己的视频、图片和文案不因使用本 Skill 自动适用此许可；另行引入的字体、音乐、模板与第三方素材应遵守各自许可。

## 参考

- [OpenAI：Skill 的组成与工具边界](https://developers.openai.com/plugins/concepts/skills)
- [OpenAI：构建 Skill](https://learn.chatgpt.com/docs/build-skills)
- [ChatCut：WorkBuddy 安装指南](https://chatcut.io/workbuddy)
- [WorkBuddy：技能管理](https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)
- [GitHub：忽略文件](https://docs.github.com/en/get-started/git-basics/ignoring-files)
