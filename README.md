# lyston-skills

个人 AI agent skills 集合，兼容 ZCode、Codex 和其他读取 Agent Skills 目录的工具。

## 目录结构

每个一级目录是一个独立 skill，入口文件为该目录下的 `SKILL.md`。部分 skill 还包含脚本、参考资料、模板、测试和示例资源。

## 安装到用户级目录

```bash
git clone git@github.com:lyston11/lyston-skills.git ~/.agents/skills
```

如果目录已经存在：

```bash
git -C ~/.agents/skills pull
```

也可以将仓库中的 skill 目录复制到 `~/.zcode/skills/` 或项目的 `.agents/skills/` / `.zcode/skills/` 中。

## 说明

- 凭据、API key、token 和其他秘密信息应通过环境变量或本机安全配置保存，不要提交到仓库。
- `nature-shared` 是供相关 Nature skills 复用的共享支持内容，不建议单独触发。
- 本仓库同步的是 skill 定义及其随附资源，不包含 ZCode/Codex 的全局配置、插件缓存或会话数据。
