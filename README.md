# Lulu Agent Skill

让你常用的 Agent 调用本机 Lulu，处理文稿、转录、配音与素材任务。技能按需安装，也可单独卸载；无需重新下载 Lulu。

## 可以做什么

| 功能 | 用途 |
| --- | --- |
| 文稿 | 查找、读取、创建、改稿，查询和恢复历史版本 |
| AI 对话 | 使用 Lulu 中配置的模型处理内容，查看或取消任务 |
| 本地转录 | 音频和视频转文字，查询模型与完整结果 |
| 本地配音 | 使用已安装模型和保存的音色生成音频 |
| 链接素材 | 下载视频、音频、封面与公开作品资料 |
| 任务与技能 | 查询任务进度和回执，管理 Lulu 内部技能 |

**可用范围以本机 Lulu 返回的功能清单为准。** Skill 可以比 App 更新；旧版 Lulu 未接通的功能不能通过下载 Skill 获得。模型需要在 Lulu 中准备，Skill 不附带模型。

当前支持 macOS、`/Applications/Lulu.app` 中的 Lulu generation 9 安装，以及 CLI 1.x 中已验证的 1.0.0 协议。需要 Python 3 标准库运行只读安装检查。首次使用须在 Lulu 中完成正常安装与授权。此仓库不包含 Lulu 主程序或模型，也不提供绕过授权的入口。

## 安装

把下面这段话发给你使用的 Agent：

> 请访问 https://github.com/AidenXu-1/lulu-agent ，阅读 README，下载完整的 lulu-agent 文件夹，安装到你当前使用的技能目录。先检查脚本和兼容性，不覆盖已有同名内容。保留所有 scripts 和 references 文件。不要改动 Lulu 管理的 ~/.agents/skills/lulu-agent，也不要安装或删除 Lulu 后台组件。安装后按 SKILL.md 验证本机 Lulu，再查询实际可用功能。本次仅安装与检查连接，不下载模型，不修改文稿，不开始转录、配音或云端调用。

也可以克隆本仓库后，使用系统已有的 Python 3 安装。例如，为使用 `~/.codex/skills` 的 Agent 安装：

```sh
git clone https://github.com/AidenXu-1/lulu-agent.git
cd lulu-agent
python3 -B manage.py install --skills-dir "$HOME/.codex/skills"
```

其他 Agent 请把 `--skills-dir` 换成它实际使用的技能目录。脚本不会猜测目录，不改动已有同名文件，不写入 App 或后台组件。

如果 Agent 只识别 `~/.agents/skills`，请先检查是否已有 Lulu 管理的旧版副本：已有时按其随包说明使用，不能用本仓库覆盖。没有旧副本时，可使用该 Agent 支持的项目级技能目录，或采用它官方支持的其他安装位置。本安装器始终保护 Lulu 旧版受管路径。

## 使用

安装后可直接告诉 Agent：

- “在 Lulu 里找一下上周的访谈文稿。”
- “用 Lulu 把这段录音转成文字。”
- “用我保存的音色朗读这篇文稿。”

Agent 先验证 Lulu，再查询功能和模型。文稿修改、联网下载、云端调用等实际操作仍以你的请求和 Lulu 返回的要求为准。只安装技能不会自动执行这些任务。

## 更新与卸载

更新前在克隆目录执行 `git pull --ff-only`，再卸载旧副本、安装新副本。卸载不会删除 App、文稿、模型、音色或任务记录：

```sh
python3 -B manage.py uninstall --skills-dir "$HOME/.codex/skills"
python3 -B manage.py install --skills-dir "$HOME/.codex/skills"
```

仅卸载时只运行第一行。脚本只删除本安装器记录的 `lulu-agent` 副本；如果内容被你修改过，保留文件并停止。手动安装的副本请使用 Agent 自己的技能管理功能卸载。不要手动删除 Lulu 管理的 `~/.agents/skills/lulu-agent` 或 `~/.local/bin/lulu`。

删除本仓库的下载副本可以进一步释放下载占用，不影响安装在 Agent 目录中的技能。

## 安装检查的范围

独立 Skill 验证 App 和产品安装记录，直接调用固定的 App 内命令。Skill 自身可以独立更新和卸载，不依赖可选的命令行快捷方式。完整性验证可发现损坏和混用版本，不代表 Apple 公证，也不能防御已经控制同一 macOS 账户的软件。
