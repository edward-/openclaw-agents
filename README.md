<p align="center">
  <img src="https://img.shields.io/badge/OpenClaw-Multi--Agent-blue?style=for-the-badge" alt="OpenClaw">
  <br/>
  <img src="https://img.shields.io/badge/version-1.0.0-brightgreen?style=flat-square" alt="Version">
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License">
  <img src="https://img.shields.io/badge/agents-9-orange?style=flat-square" alt="Agents">
  <img src="https://img.shields.io/badge/channels-feishu%20%7C%20whatsapp%20%7C%20telegram%20%7C%20discord-purple?style=flat-square" alt="Channels">
</p>

<h1 align="center">🐾 OpenClaw Agents</h1>

<p align="center">
  <strong>One-command multi-agent initialization for <a href="https://docs.openclaw.ai">OpenClaw</a></strong>
  <br/>
  <em>Ship an entire AI agent fleet to your chat group in 60 seconds.</em>
</p>

<p align="center">
  <a href="#-installation">Installation</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-agents">Agents</a> •
  <a href="#-channel-support">Channels</a> •
  <a href="#-workflows">Workflows</a> •
  <a href="#-customization">Customization</a> •
  <a href="#-contributing">Contributing</a>
</p>

---

## ✨ What Is This?

**OpenClaw Agents** is a ready-to-deploy multi-agent configuration kit for [OpenClaw](https://docs.openclaw.ai). It provisions **9 specialized AI agents** as a collaborative team — complete with identities, workspace files, routing rules, and channel bindings — using a single setup command.

### What You Get

- 🤖 **9 pre-configured agents** with rich emoji identities for instant recognition in chat
- 📝 **Full workspace files** — `soul.md`, `agent.md`, `user.md` for every agent
- 🔗 **Channel routing** — auto-configured bindings for Feishu, WhatsApp, Telegram, Discord
- 📋 **4 workflow templates** — Paper Pipeline, Daily Digest, Brainstorm, Rebuttal
- ⚔️ **Adversarial collaboration** — Ideator↔Critic and Writer↔Reviewer creative tension
- 🎯 **SHARP taste gates** — quality checkpoints enforced by the Critic agent
- 🧩 **Extensible** — add custom agents via `agents.yaml`

---

## 📦 Installation

### For Humans

Paste this into your LLM agent session (Claude Code, Antigravity, Cursor, etc.):

```
Fetch the OpenClaw Agents installation guide and set up the multi-agent system by following:
curl -s https://raw.githubusercontent.com/shenhao-stu/openclaw-agents/main/docs/installation.md
```

Or just run it yourself:

```bash
git clone https://github.com/shenhao-stu/openclaw-agents.git
cd openclaw-agents
chmod +x setup.sh
./setup.sh
```

### For LLM Agents

> **IMPORTANT: Use `curl` to fetch this file, NOT WebFetch.** WebFetch summarizes content and loses critical details like CLI flags and config examples. Always use:
> ```bash
> curl -fsSL https://raw.githubusercontent.com/shenhao-stu/openclaw-agents/main/docs/installation.md
> ```

If you're an LLM Agent helping set up OpenClaw Agents, follow the [full installation guide](docs/installation.md). Here's the summary:

#### Step 0: Prerequisites

```bash
# Verify OpenClaw CLI is installed
if command -v openclaw &> /dev/null; then
    echo "OpenClaw $(openclaw --version) is installed"
else
    echo "Installing OpenClaw..."
    npm install -g openclaw@latest
    openclaw onboard --install-daemon
fi
```

#### Step 1: Ask User About Configuration

Ask the user these questions:

1. **Which channel do you use?** → `--channel feishu|whatsapp|telegram|discord|slack`
2. **What is your group/chat ID?** → `--group-id <ID>`
   - Feishu: `oc_xxxxxxxxx` (chat_id)
   - WhatsApp: `xxxxx@g.us`
   - Telegram: `-1001234567890`
   - Discord: guild ID
3. **Which LLM model?** (default: `anthropic/claude-sonnet-4-5`) → `--model <MODEL>`
4. **Do you need a session ID for group routing?** → `--session-id <ID>` (optional)

#### Step 2: Clone and Run Setup

```bash
git clone https://github.com/shenhao-stu/openclaw-agents.git
cd openclaw-agents
chmod +x setup.sh
./setup.sh --channel <CHANNEL> --group-id <GROUP_ID> --model <MODEL>
```

**Examples:**
- Feishu group: `./setup.sh --channel feishu --group-id oc_b1c331592eaa36d06a7e5df05d08a890`
- WhatsApp group: `./setup.sh --channel whatsapp --group-id 120363999999999999@g.us`
- Telegram group: `./setup.sh --channel telegram --group-id -1001234567890`
- Agents only (no channel): `./setup.sh --skip-bindings`
- Dry-run preview: `./setup.sh --dry-run --channel feishu --group-id oc_xxx`

The script will:
1. ✅ Verify `openclaw` CLI is installed
2. 🤖 Create 8 sub-agents via `openclaw agents add`
3. 🎨 Set emoji identities via `openclaw agents set-identity`
4. 📝 Deploy `soul.md` / `agent.md` / `user.md` to each workspace
5. 🔗 Configure `openclaw.json` with channel bindings
6. ✅ Verify the entire setup

#### Step 3: Verify Setup

```bash
openclaw agents list --bindings    # Should show all 8 agents with channel bindings
openclaw channels status --probe   # Should show channel connected
```

#### Step 4: Start the Gateway

```bash
openclaw gateway
```

Then mention any agent in your chat group to test. Each agent will respond with its distinct emoji identity.

> ⚠️ **Warning**: Do not modify the 8 core agent IDs (`planner`, `ideator`, `critic`, `surveyor`, `coder`, `writer`, `reviewer`, `scout`). These are protected and referenced throughout the workflow system.

---

## 🏗 Architecture

```
                         ┌──────────────┐
                         │   👤 User    │
                         └──────┬───────┘
                                │
                    ┌───────────▼───────────┐
                    │  🐾 OpenClaw Main     │
                    │  (Audit · Manage · Arbitrate)
                    └───────────┬───────────┘
                                │
                         ┌──────▼───────┐
                         │  🧠 Planner  │ ◄── Orchestration Hub
                         └──────┬───────┘
                                │
       ┌────────────────────────┼────────────────────────┐
       │                        │                        │
 ┌─────▼─────┐           ┌─────▼─────┐           ┌─────▼─────┐
 │ 💡Ideator │◄── ⚔️ ──►│ 🎯 Critic │           │ 📰 Scout  │
 │  Creative  │           │   Taste    │           │   Intel    │
 └─────┬─────┘           └─────┬─────┘           └───────────┘
       │                       │
 ┌─────▼─────┐           ┌─────▼─────┐
 │ 📚Surveyor│           │ 💻 Coder  │
 │  Research  │           │ Engineer   │
 └─────┬─────┘           └─────┬─────┘
       │                       │
       └───────────┬───────────┘
             ┌─────▼─────┐
             │ ✍️ Writer │
             │  Author    │
             └─────┬─────┘
                   │
             ┌─────▼─────┐
             │ 🔍Reviewer│ ◄── Quality Gate
             │  Reviewer  │
             └───────────┘
```

### Adversarial Collaboration

The system is built on **productive tension** between agents:

| Axis | Agents | Dynamic |
|------|--------|---------|
| **Creativity vs. Taste** | 💡 Ideator ↔ 🎯 Critic | Forge top-tier ideas through rigorous debate |
| **Writing vs. Review** | ✍️ Writer ↔ 🔍 Reviewer | Polish papers through iterative feedback |

- **🎯 Critic** holds ultimate **taste veto** — no idea passes Phase 2.5 without SHARP ≥ 18
- **🔍 Reviewer** holds ultimate **quality veto** — paper cannot submit without Reviewer's Accept

---

## 🤖 Agents

### Core Fleet (🔒 Protected)

| # | Agent | ID | Identity | Role |
|---|-------|----|----------|------|
| 0 | **Main** | `main` | 🐾 OpenClaw | System orchestrator, audit, final arbiter |
| 1 | **Planner** | `planner` | 🧠 Planner | Task decomposition, progress tracking, coordination |
| 2 | **Ideator** | `ideator` | 💡 Ideator | Idea generation, novelty assessment, contribution framing |
| 3 | **Critic** | `critic` | 🎯 Critic | SHARP taste evaluation, anti-pattern detection |
| 4 | **Surveyor** | `surveyor` | 📚 Surveyor | Literature search, research gap identification |
| 5 | **Coder** | `coder` | 💻 Coder | Algorithm implementation, experiment execution |
| 6 | **Writer** | `writer` | ✍️ Writer | Paper writing, LaTeX formatting |
| 7 | **Reviewer** | `reviewer` | 🔍 Reviewer | Internal peer review, rebuttal strategy |
| 8 | **Scout** | `scout` | 📰 Scout | Daily paper digest, trend monitoring |

### Per-Agent Workspace

Each agent has three core files inside `.agents/<agent_id>/`:

| File | Purpose | Customize When... |
|------|---------|-------------------|
| `soul.md` | 🧬 Identity, personality, decision principles | You want to change agent behavior |
| `agent.md` | ⚙️ Model, tools, sandbox, inter-agent protocols | You want to change model or tool access |
| `user.md` | 👤 User context, research profile, preferences | You want to adapt to a different research domain |

---

## 📡 Channel Support

Bind your agent fleet to any [OpenClaw-supported channel](https://docs.openclaw.ai/channels/telegram):

| Channel | Group ID Format | Example | Docs |
|---------|----------------|---------|------|
| **Feishu** (飞书) | `oc_xxxxxxxxx` | `oc_b1c331592eaa36d06a7e5df05d08a890` | [Feishu docs](https://docs.openclaw.ai/channels/feishu) |
| **WhatsApp** | `xxxxx@g.us` | `120363999999999999@g.us` | [WhatsApp docs](https://docs.openclaw.ai/channels/whatsapp) |
| **Telegram** | Negative integer | `-1001234567890` | [Telegram docs](https://docs.openclaw.ai/channels/telegram) |
| **Discord** | Guild ID | `1234567890` | [Discord docs](https://docs.openclaw.ai/channels/discord) |
| **Slack** | Team + Channel | `T0123/C0123` | [Slack docs](https://docs.openclaw.ai/channels/slack) |

### Feishu Binding Example

The generated `openclaw.json` binds each agent to your Feishu group:

```jsonc
{
  "bindings": [
    {
      "agentId": "planner",
      "match": {
        "channel": "feishu",
        "peer": {
          "kind": "group",
          "id": "oc_b1c331592eaa36d06a7e5df05d08a890"
        }
      }
    }
    // ... one binding per agent
  ]
}
```

> **Finding your Feishu Group ID**: Run `openclaw channels feishu groups` to list all group chat_ids.

Pre-built config examples: [`examples/openclaw.feishu.json`](examples/openclaw.feishu.json) · [`examples/openclaw.whatsapp.json`](examples/openclaw.whatsapp.json)

---

## 📋 Workflows

| Workflow | Slash Command | Description |
|----------|--------------|-------------|
| 📋 Paper Pipeline | `/paper-pipeline` | Full 9-phase paper production with taste gates |
| 📰 Daily Digest | `/daily-digest` | Scout-led daily paper summarization |
| 💡 Brainstorm | `/brainstorm` | Rapid idea generation and evaluation |
| 🔄 Rebuttal | `/rebuttal` | Reviewer response preparation |

### Taste Gates (品鉴节点)

The Critic agent enforces quality at four critical checkpoints:

| Gate | Checkpoint | Pass Criteria |
|------|-----------|---------------|
| 🎯 Idea Confirmation | SHARP score + Soul Questions | SHARP ≥ 18 |
| 🎯 Method Design | Elegance + Parsimony | Parsimony ≥ 4 |
| 🎯 First Draft | Narrative quality + Memorability | ≥ 1 clear hook |
| 🎯 Pre-submission | Full quality judgment | Critic says "worth submitting" |

---

## 🧩 Customization

### Adding Custom Agents

1. Add the agent definition to `agents.yaml`:

```yaml
agents:
  # ... existing agents ...
  - id: "math-prover"
    name: "🔢 Math Prover"
    emoji: "🔢"
    role: "Theorem proving, convergence analysis"
    model: "anthropic/claude-sonnet-4-5"
    protected: false
    workspace: ".agents/math-prover"
```

2. Re-run `./setup.sh` or add manually:

```bash
openclaw agents add math-prover --model anthropic/claude-sonnet-4-5 --workspace .agents/math-prover
openclaw agents set-identity --agent math-prover --name "🔢 Math Prover"
```

### Changing the Default Model

```bash
./setup.sh --model anthropic/claude-sonnet-4-5
```

---

## 📁 Repository Structure

```
openclaw-agents/
├── setup.sh                          # 🚀 One-command setup script
├── agents.yaml                       # 📋 Agent manifest (source of truth)
├── soul.md                           # 🐾 Main Agent definition
├── README.md                         # 📖 This file
├── LICENSE                           # MIT License
├── CONTRIBUTING.md                   # Contribution guidelines
├── CHANGELOG.md                      # Version history
├── docs/
│   └── installation.md               # 📖 Full installation guide (for LLM agents)
├── examples/
│   ├── openclaw.feishu.json          # Feishu config example
│   └── openclaw.whatsapp.json        # WhatsApp config example
└── .agents/
    ├── planner/                      # 🧠 soul.md + agent.md + user.md
    ├── ideator/                      # 💡 soul.md + agent.md + user.md
    ├── critic/                       # 🎯 soul.md + agent.md + user.md
    ├── surveyor/                     # 📚 soul.md + agent.md + user.md
    ├── coder/                        # 💻 soul.md + agent.md + user.md
    ├── writer/                       # ✍️ soul.md + agent.md + user.md
    ├── reviewer/                     # 🔍 soul.md + agent.md + user.md
    ├── scout/                        # 📰 soul.md + agent.md + user.md
    └── workflows/
        ├── paper-pipeline.md         # 📋 End-to-end paper workflow
        ├── daily-digest.md           # 📰 Daily paper digest
        ├── brainstorm.md             # 💡 Idea brainstorming
        └── rebuttal.md               # 🔄 Rebuttal preparation
```

---

## 🔧 CLI Reference

### Setup Script Flags

| Flag | Description | Default |
|------|-------------|---------|
| `--channel` | Channel type (feishu/whatsapp/telegram/discord/slack) | Interactive prompt |
| `--group-id` | Group/chat ID for channel binding | Interactive prompt |
| `--session-id` | Session ID for group routing | None |
| `--model` | LLM model for all agents | `anthropic/claude-sonnet-4-5` |
| `--skip-bindings` | Skip channel binding setup | `false` |
| `--dry-run` | Preview commands without executing | `false` |
| `-h, --help` | Show help | — |

### OpenClaw Commands

```bash
openclaw agents list --bindings       # List all agents and bindings
openclaw agents add <id>              # Add a new agent
openclaw agents set-identity          # Set agent display name
openclaw channels status --probe      # Check channel connectivity
openclaw gateway                      # Start the gateway
openclaw gateway restart              # Restart after config changes
```

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

- 🐛 **Bug Reports** — Open a GitHub Issue
- 💡 **New Agents** — Submit a PR with agent files + `agents.yaml` update
- 📋 **Workflows** — Share your research process templates
- 📖 **Docs** — Improve guides and examples

---

## 📄 License

[MIT](LICENSE) — Use freely, modify openly, share generously.

---

<p align="center">
  <strong>Built with ❤️ for the AI research community</strong>
  <br/>
  <sub>Powered by <a href="https://docs.openclaw.ai">OpenClaw</a> 🦞</sub>
</p>
