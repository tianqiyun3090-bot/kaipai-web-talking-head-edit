# 开拍网页口播剪辑 Codex Skill

将本地口播视频上传到[开拍网感剪辑](https://www.kaipai.com/ai-edit)，按用户要求删除长停顿和重复起句、校对字幕、选择网感模板，并在获得相应请求后导出或下载。

## 安装

需要 Node.js 20 或更新版本、npm，以及电脑上已有的 Chrome 或 Edge。将本技能目录复制到 `$HOME/.codex/skills/kaipai-web-talking-head-edit`。在 Windows PowerShell 中，如果仓库根目录包含 `kaipai-web-talking-head-edit` 文件夹，可以运行：

```powershell
$skillDir = Join-Path $HOME '.codex\skills'
New-Item -ItemType Directory -Path $skillDir -Force | Out-Null
Copy-Item -LiteralPath '.\kaipai-web-talking-head-edit' -Destination $skillDir -Recurse
```

如果仓库根目录本身就是技能目录，则将该目录整体复制到上述目标路径，不要只复制 `SKILL.md`。

需要 `agent-browser` 时，检查 Node.js 版本并安装 CLI：

```powershell
node --version
npm --version
npm install --prefix "$env:LOCALAPPDATA\Codex\agent-browser" agent-browser@0.38.1 --registry https://registry.npmjs.org/
```

`0.38.1` 是本技能验证过的 CLI 版本。安装会下载 `agent-browser` 包及其本机可执行文件；不运行 `agent-browser install`，因此不会下载 Chrome 或其他浏览器。CLI 通常会发现系统 Chrome；必要时用 `--executable-path` 指定现有 Chrome/Edge。不会修改 shell 配置，也不会安装全局 npm 包。其他系统可直接复制技能目录到 `~/.codex/skills/`，再按 [agent-browser 官方说明](https://github.com/vercel-labs/agent-browser)只安装 CLI。下次 Codex 对话即可调用 `$kaipai-web-talking-head-edit`。

## 使用

向 Codex 指定源视频和操作范围，例如：

> 使用 `$kaipai-web-talking-head-edit`，把我指定的口播视频上传到开拍，删除长停顿和重复起句，校对字幕，选第一个网感模板并导出。先不要下载。

首次使用时在可见浏览器中自行登录开拍账号。技能不会要求提供账号密钥。模板处理可能使用网站免费次数；如出现付费选项，应由用户决定。请勿将登录状态、视频素材、下载成片或浏览器缓存提交到 GitHub。

技能入口是 `SKILL.md`；本 README 用于 GitHub 安装说明。
