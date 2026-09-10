# Explore

Explore is a Codex skill for delegating broad codebase reconnaissance to explorer subagents before the main agent reads or edits many files.

It is useful when a coding task touches an unfamiliar repository, spans multiple areas, or likely requires reading many files. The skill asks subagents to return concise findings, a key-files table, and suggested next reads, so the main conversation stays focused on decisions and implementation.

## Install

Clone this repository into your Codex skills directory:

```bash
git clone https://github.com/oil-oil/codex-explore-skill.git ~/.codex/skills/explore
```

Then invoke it with:

```text
Use $explore to map this codebase before making changes.
```

## What It Enforces

- Delegate large read-only code exploration to explorer subagents first.
- Keep the main agent from reading the target codebase while subagents are exploring.
- Require a key-files table before broad local reads or edits.
- Ask explorers to distinguish primary, legacy, experimental, generated, unused, or unclear code paths when possible.
- Group likely changes by concern, such as UI, API, state, data model, permissions, i18n, tests, or configuration.

## License

MIT

## 配置、依赖与使用边界

优先使用宿主子 Agent 能力；仅在能力可用且当前规则允许时委托，否则按 Skill 的退化路径进行本地只读探索。无需为本 Skill 单独提供 API Key。

读取目标代码库，探索结论要有文件证据；不能把未读取的模块当成已验证，也不默认修改源码。

使用示例：

```text
用 explore 查清这个项目的登录请求如何到达数据库。
```

## GitHub 安装

把 [仓库地址](https://github.com/oil-oil/codex-explore-skill) 交给 Agent，要求按 README 安装；也可运行：

```bash
npx skills add oil-oil/codex-explore-skill
```

安装后由宿主重新加载 Skill。
