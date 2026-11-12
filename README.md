# Software Architect — Claude Code & Codex

**Version:** `1.1.0` · **License:** [MIT](LICENSE) · **Maintainer:** [dimitriskl](https://github.com/dimitriskl)

A pragmatic software architecture agent for .NET/Angular systems, API boundaries, integrations, reliability and migration trade-offs.

## What problem does it solve?

Make evidence-based cross-layer design decisions without unnecessary architectural complexity. It gives Claude Code and Codex a focused specialist with explicit boundaries, a practical workflow, and evidence-based reporting. No additional dependencies, accounts, model downloads, or MCP servers are required beyond the host coding tool.

**Primary responsibilities:** Architecture decisions, API/data contracts, service boundaries, rollout and risk analysis.

This is an **agent definition**, not an executable app or a guarantee of correctness. The host tool, model, workspace permissions, available integrations, and user instructions determine what can actually run.

## Included files

| File | Purpose |
| --- | --- |
| [`.claude/agents/software-architect.md`](.claude/agents/software-architect.md) | Claude Code custom subagent (install-ready name). |
| [`.codex/agents/software-architect.toml`](.codex/agents/software-architect.toml) | Codex custom subagent (install-ready name). |
| [`releases/v1.1.0/software-architect-v1.1.0.md`](releases/v1.1.0/software-architect-v1.1.0.md) | Versioned Claude Code release snapshot. |
| [`releases/v1.1.0/software-architect-v1.1.0.toml`](releases/v1.1.0/software-architect-v1.1.0.toml) | Versioned Codex release snapshot. |
| [`VERSION`](VERSION) and [`CHANGELOG.md`](CHANGELOG.md) | Release version and history. |

The `.md` and `.toml` files are **alternatives for different tools**, not two agents that must run together. Install one or both depending on what you use. All agent definitions in this release declare version `1.1.0` in a comment; the release snapshots also contain the version in their filename. **Do not rename the install-ready files to include a version suffix**: the stable filenames are intentional for reliable upgrades.

## Installation — project scope (recommended)

Clone the repository:

```sh
git clone https://github.com/dimitriskl/software-architect.git
cd software-architect
```

Copy the relevant definition into the root of your **actual target code project**, not into the agent's source repository.

### Windows PowerShell

```powershell
$Target = "C:\path\to\your-project"  # replace with your project directory
New-Item -ItemType Directory -Force "$Target/.claude/agents", "$Target/.codex/agents" | Out-Null
Copy-Item ".claude/agents/software-architect.md" "$Target/.claude/agents/software-architect.md"
Copy-Item ".codex/agents/software-architect.toml" "$Target/.codex/agents/software-architect.toml"
```

### macOS / Linux / WSL

```sh
TARGET="/path/to/your-project"  # replace with your project directory
mkdir -p "$TARGET/.claude/agents" "$TARGET/.codex/agents"
cp ".claude/agents/software-architect.md" "$TARGET/.claude/agents/software-architect.md"
cp ".codex/agents/software-architect.toml" "$TARGET/.codex/agents/software-architect.toml"
```

If you only use Claude Code, copy only the `.md` file. If you only use Codex, copy only the `.toml` file.

## Installation — personal scope (all projects)

Run from the cloned agent repository's root.

**Windows PowerShell:**

```powershell
New-Item -ItemType Directory -Force "$HOME/.claude/agents", "$HOME/.codex/agents" | Out-Null
Copy-Item ".claude/agents/software-architect.md" "$HOME/.claude/agents/software-architect.md"
Copy-Item ".codex/agents/software-architect.toml" "$HOME/.codex/agents/software-architect.toml"
```

**macOS / Linux / WSL:**

```sh
mkdir -p "$HOME/.claude/agents" "$HOME/.codex/agents"
cp ".claude/agents/software-architect.md" "$HOME/.claude/agents/software-architect.md"
cp ".codex/agents/software-architect.toml" "$HOME/.codex/agents/software-architect.toml"
```

These are the exact locations read by Claude Code (`.claude/agents` or `~/.claude/agents`) and Codex (`.codex/agents` or `~/.codex/agents`). Your project's existing `CLAUDE.md`, `AGENTS.md`, tools and permissions still apply. If a new agents directory was created while Claude Code was already open, restart that session if the agent isn't recognized.

## Use

**Claude Code:**

```text
Use the software-architect agent to evaluate two designs for this cross-layer feature, recommend the simplest viable option, and outline migration risks and validation.
```

**Codex CLI / IDE:**

```text
Delegate this task to the software-architect custom agent: Use the software-architect agent to evaluate two designs for this cross-layer feature, recommend the simplest viable option, and outline migration risks and validation.
```

Codex normally discovers custom agents when they are configured in the recognized agent directories. To use subagents, request delegation explicitly in your Codex conversation. If your client or workspace restricts custom agents, check its available configuration.

## Behavior and boundaries

- Inspect project context and installed versions rather than assume the latest APIs exist.
- Keep recommendations or edits within the requested scope and respect the repository's rules.
- Do not invent tool access, test results, benchmarks, data or validation evidence.
- Do not commit, push, deploy or change production resources without appropriate authorization.
- Follow the agent instructions for role-specific checks, trade-offs, handoffs and reporting.

Codex custom agents **inherit the parent's sandbox and approval policy**; the TOML file cannot force a new sandbox. Even a read-only instruction is behavioral rather than enforceable isolation.

## Updates and release policy

The current release is **v1.1.0**. Versioned snapshots are immutable. For future updates, edit the stable `.md` and `.toml` source definitions, bump `VERSION`, document changes in `CHANGELOG.md`, add corresponding `releases/vX.Y.Z/` snapshots and create a Git tag `vX.Y.Z`. We use semantic versioning as a documentation convention (MAJOR = breaking instruction/behavior changes, MINOR = new capabilities, PATCH = corrections).

To upgrade, replace your installed stable `.md`/`.toml` files with the files from the desired tagged release. Check diffs before replacing custom local modifications.

## Official documentation

- [MyDevFactory](https://github.com/dimitriskl/mydevfactory)
- [Claude Code custom subagents](https://code.claude.com/docs/en/sub-agents)
- [Codex custom subagents](https://developers.openai.com/codex/subagents)

## Contributing

Issues and pull requests are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md). Please do not post private source code, credentials, sensitive dataset values or proprietary architecture in reports or examples.

## License

MIT © 2026 Dimitris Klis. See [LICENSE](LICENSE).
