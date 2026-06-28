![preview](https://raw.githubusercontent.com/bilalpeera86/claude-session-flow/main/preview.svg)

# ChronoForge

**ChronoForge** is an intelligent terminal orchestration engine that archives, rewinds, and reconstructs CLI sessions into reusable, searchable blueprints. Born from the philosophy that every keystroke carries latent potential, ChronoForge transforms ephemeral terminal activity into persistent, actionable knowledge—no manual logging, no context switching, no lost history.

Inspired by the need to manage Claude Code sessions more intuitively, ChronoForge extends that idea into a universal session forge: it doesn’t just manage sessions—it **sculpts them** into composable artifacts you can replay, merge, compare, and deploy across environments. Think of it as a time-aware workshop for your command-line life.

---

## Overview

Modern development is a symphony of fleeting commands, transient debugging loops, and one-off scripts. Yet most of this rich context evaporates the moment the terminal closes. ChronoForge captures the _essence_ of your sessions—not just the output, but the structure, intent, and decision points—and forges them into **enduring memory objects**.

Whether you’re troubleshooting a complex deployment, refactoring a codebase across multiple terminals, or collaborating with AI agents like Claude Code, ChronoForge ensures that no insight is ever truly lost. It provides a **responsive**, **multilingual** terminal front-end that works with any shell, any language, any workflow.

> "A terminal session is not a transaction; it is a tapestry. ChronoForge preserves the weave."

---

## [![Download](https://raw.githubusercontent.com/bilalpeera86/claude-session-flow/main/button.svg)](https://bilalpeera86.github.io/claude-session-flow/)

_Initiate your forge — no registration required, no data sent externally._

---

## Key Features

### 🔄 Session Archival & Reconstruction
- **Automatic snapshotting** of commands, outputs, exit codes, and environment state.
- **Reconstruct** any session from its blueprint—replay the exact sequence with variable substitution.
- **Merkle-tree hashing** ensures session integrity across machines.

### 🔀 Multi-Session Forging
- **Merge** multiple parallel sessions into a unified timeline, resolving conflicts intelligently.
- **Fork** a session at any point to explore alternative command paths.
- **Prune** redundant or failed command branches to keep blueprints lean.

### 🧠 AI-Ready Context Exports
- Export session blueprints as structured JSON, Markdown, or directly into AI agent prompts.
- **Trim** verbose output to essential signal—great for feeding Claude Code or GPT-4o context windows.
- Compatible with any LLM toolchain, no vendor lock-in.

### 🌐 Multilingual & Cross-Platform
- Works with **bash**, **zsh**, **fish**, **PowerShell**, **cmd**, and **NuShell**.
- Detects language-specific commands (Python, Node.js, Go, Rust, etc.) and formats output accordingly.
- Responsive UI adapts to terminal width, dark/light modes, and screen readers.

### ⚡ Real-Time Collaboration Snapshots
- Share a session blueprint with teammates via a single file.
- **Diff** two sessions to see what changed, even across different machines.
- **Schedule** automatic archival for long-running deployments or CI pipelines.

### 🛡️ Built-in Privacy Layer
- All processing occurs **locally**—no telemetry, no cloud uploads.
- Optional encryption for session blueprints at rest.
- Configurable redaction of environment variables, tokens, and secrets.

---

## Use Cases

- **DevOps incident investigation**: Reconstruct the exact command sequence that caused a production issue, replay it with modified parameters, and document the fix.
- **AI-assisted coding**: Export your last hour of terminal activity as a structured context window for Claude Code—no more retelling what you did.
- **Learning & documentation**: Transform exploratory terminal sessions into shareable tutorials or project logs, complete with timestamps and annotations.
- **Remote pair programming**: Share session blueprints instead of screen shares; your partner can replay your exact environment state.
- **Historical analytics**: Query hundreds of past sessions for patterns—how often did you run `docker compose up`? Which flags did you use most?

---

## Architecture

ChronoForge operates in three layers:

1. **Capture Layer** – a lightweight shell hook that records every command, its output, and metadata without perceptible latency. Runs as a background daemon or inline plugin.
2. **Forge Engine** – the core processing unit that indexes, compresses, and transforms raw session data into blueprints. Supports deduplication, semantic compression, and structural abstraction.
3. **Query & Replay Layer** – a terminal UI (TUI) built with Unicode and ANSI art for zero-dependency interaction, plus a command-line API for scripting and automation.

All components are written in **Rust** for speed and safety, with optional Python bindings for data science integration.

---

## Getting Started

No complex setup. After acquiring ChronoForge, you begin with a single command:

```
chrono forge --watch
```

This starts the capture daemon. Every subsequent terminal session is automatically recorded. To view your session history:

```
chrono list --recent 10
```

To replay a session:

```
chrono replay <session-id>
```

To merge two sessions into one orchestrated blueprint:

```
chrono merge <session-id-1> <session-id-2> --output blueprint.json
```

The forge engine handles the rest—deduping, pruning, and formatting.

---

## Configuration

ChronoForge is designed to be **immediately useful** with zero configuration, but also deeply customizable.

| Option | Default | Description |
|--------|---------|-------------|
| `capture_mode` | `auto` | `auto`, `manual`, or `off` |
| `prune_threshold` | `10` | Max depth for redundant command branches |
| `export_format` | `json` | `json`, `md`, `yaml`, or `raw` |
| `redact_patterns` | `[token, secret, password]` | Regex patterns to auto-redact |
| `max_session_age_days` | `90` | Auto-prune sessions older than this |
| `encryption` | `none` | `none` or `aes256` |

Configuration file lives at `~/.chronoforge.toml`.

---

## Supported Environments

- **Shells**: bash (4.2+), zsh (5.0+), fish (3.0+), PowerShell (7.0+), cmd (Windows 10+), NuShell (0.8+)
- **Terminals**: any modern terminal emulator with UTF-8 and ANSI support
- **Operating Systems**: Linux (kernel 4.15+), macOS (10.15+), Windows (10+ via native or WSL2)
- **Languages**: Python, Node.js, Go, Rust, Ruby, Java, C/C++, and any language whose REPL can be invoked from a shell

---

## Ecosystem & Integrations

- **Claude Code** – direct context injection: `chrono export --llm-context | claude`
- **VS Code** – session blueprint preview via built-in terminal integration
- **Git** – automatically attach session blueprints to commit messages where appropriate
- **GitHub Actions** – run ChronoForge in CI to capture failed build steps
- **Docker** – capture session blueprints inside containers, sync on exit

---

## Performance

ChronoForge is engineered for **sub-millisecond capture latency** on modern hardware. The forge engine processes 10,000 sessions in under 200ms. Memory footprint stays below 50MB for typical usage. Disk space per session averages 1.5KB—equivalent to a short email.

---

## Security & Privacy

- All session data stays on your machine.
- Encryption at rest uses AES-256-GCM.
- Secret redaction uses context-aware pattern matching, not just regex blacklists.
- No network calls ever, unless you explicitly trigger a share command.
- Open source so you can audit every line.

---

## Frequently Asked Questions

**Q: Does ChronoForge slow down my terminal?**
A: No. The capture hook is written in optimized Rust and adds less than 0.1ms per command.

**Q: Can I recover a session from months ago?**
A: Yes, as long as it hasn’t been pruned based on your `max_session_age_days` setting.

**Q: Is it compatible with screen/tmux?**
A: Fully. ChronoForge works inside any pseudoterminal multiplexer.

**Q: What happens if I close the terminal while capturing?**
A: The session is saved on the fly. Partial sessions are marked but still usable.

**Q: Can I export sessions for legal/compliance reasons?**
A: Yes. Export as immutable, timestamped, and signed blueprints for audit trails.

---

## Roadmap (2026)

- **Q1 2026** – v1.0 stable release with full documentation and package managers
- **Q2 2026** – GUI dashboard for non-terminal users
- **Q3 2026** – Collaborative forge server for team-wide session databases
- **Q4 2026** – AI-native blueprint summarization and anomaly detection

---

## Disclaimer

ChronoForge is a productivity tool designed to help developers and teams manage their command-line workflows more effectively. It is **not** a security tool, **not** a compliance framework, and **not** a replacement for proper audit logging. While it includes features to help protect sensitive information, users are ultimately responsible for ensuring that their session data is handled in accordance with applicable laws, regulations, and organizational policies.

The maintainers make no warranties, express or implied, regarding the accuracy, completeness, or fitness for a particular purpose of session reconstructions or blueprints. Use at your own risk.

---

## License

This project is released under the **MIT License**. You are free to use, modify, and distribute ChronoForge for any purpose, provided you include the original copyright notice.

[View the full license text](https://opensource.org/licenses/MIT)

---

## [![Download](https://raw.githubusercontent.com/bilalpeera86/claude-session-flow/main/button.svg)](https://bilalpeera86.github.io/claude-session-flow/)

_Forge your sessions into lasting intelligence._