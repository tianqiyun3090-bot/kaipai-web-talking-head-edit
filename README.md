# 开拍网页口播剪辑 Codex Skill

将本地口播视频上传到[开拍网感剪辑](https://www.kaipai.com/ai-edit)，通读文字快剪页已展示的全部字幕，按用户范围清理无效停顿、重复起句、重录废句、口误和多余口头禅，检查声音与画面的切口，再校对字幕、应用网感模板，并按交付要求导出或下载。

快剪默认以自然流畅为目标，保留有效内容、自然换气和强调停顿；只有用户要求精简时才进一步压缩内容。剪除内容必须同时处理对应声音和画面，网页无法完成的精确剪切会单独报告。

## 在 Codex 中安装

在 Codex 中发送：

> 使用 `$skill-installer` 从 GitHub 仓库 `tianqiyun3090-bot/kaipai-web-talking-head-edit` 的根目录（路径 `.`）安装技能，安装名为 `kaipai-web-talking-head-edit`。

仓库根目录就是技能目录，因此需要指定路径 `.` 和安装名。已用 Codex 自带的 skill-installer 验证这一安装方式。安装完成后的下次对话即可调用 `$kaipai-web-talking-head-edit`。

## 首次使用的浏览器准备

技能安装本身不需要 Node.js。如果 Codex 当前的浏览器工具无法上传本地视频，则需要 Node.js 20+、npm 和电脑上已有的 Chrome 或 Edge。Codex 可按 `SKILL.md` 的说明安装 `agent-browser` CLI；Windows 上使用的命令是：

```powershell
npm install --prefix "$env:LOCALAPPDATA\Codex\agent-browser" agent-browser@0.38.1 --registry https://registry.npmjs.org/
```

`0.38.1` 是本技能验证过的 CLI 版本。命令会下载 `agent-browser` 包及其本机可执行文件；不会运行下载 Chrome 的 `agent-browser install`。CLI 通常会发现系统 Chrome，必要时可指定现有浏览器的路径。无需修改 shell 配置或安装全局 npm 包。

## 使用

向 Codex 指定源视频和操作范围，例如：

> 使用 `$kaipai-web-talking-head-edit`，把我指定的口播视频上传到开拍，删除长停顿和重复起句，校对字幕，选第一个网感模板并导出。先不要下载。

首次使用时在可见浏览器中自行登录开拍账号。技能不会要求提供账号密钥。模板处理可能使用网站免费次数；如出现付费选项，应由用户决定。请勿将登录状态、视频素材、下载成片或浏览器缓存提交到 GitHub。

技能入口是 `SKILL.md`；本 README 用于 GitHub 安装说明。
