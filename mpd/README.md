# /mpd · 多项目需求总控

一个需求同时涉及多个仓库时，用一个总控会话记录范围、共享接口和交付进度，每个仓库用自己的执行会话。支持 Claude Code 和 Codex；会话嵌套、置顶和侧栏归组取决于客户端提供的能力。

## 安装

先下载整个技能仓库：

```sh
git clone https://github.com/DamionH0108/skills.git
cd skills
```

在此目录下，按你使用的客户端选一条命令。目标路径已有同名技能时命令会停止，不会覆盖它。

**Claude Code**
```sh
mkdir -p ~/.claude/skills && test ! -e ~/.claude/skills/mpd && ln -s "$PWD/mpd" ~/.claude/skills/mpd
```

**Codex**
```sh
mkdir -p ~/.codex/skills && test ! -e ~/.codex/skills/mpd && ln -s "$PWD/mpd" ~/.codex/skills/mpd
```

保留下载的仓库目录。打开新会话，在 Claude Code 中输入 `/mpd DEMO-123 协调前台和管理后台的订阅设置`，在 Codex 中用 `$mpd` 加上需求说明。更新时在下载的仓库中运行 `git pull --ff-only`。

## 使用前

- 在自己的私有台账目录启动总控；不要把真实需求、会话 ID 或业务代码放入这个公开仓库。
- 前端执行流程引用独立的 `fe-workflow`；本仓库不包含该插件或 Jira 授权。要读写 Jira，须先配置相应连接和权限。
- 默认分支基线为最新的 `origin/master`。团队使用 `main` 时，在启动需求时明确指定。执行模型也可按本机可用模型覆盖。

完整的拆分规则、会话归组、Jira 优先级与交接模板见 [SKILL.md](SKILL.md)。
