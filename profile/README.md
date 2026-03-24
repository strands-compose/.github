<div align="center">
  <img src="https://raw.githubusercontent.com/strands-compose/.github/main/img/strands-compose.png" width="500" alt="strands-compose">

  --- 
  **Declarative multi-agent orchestration for [strands-agents](https://github.com/strands-agents/sdk-python) — wire entire agent systems with YAML**

  <p>
    <a href="https://www.python.org/"><img src="https://img.shields.io/badge/python-3.11+-blue.svg" alt="Python 3.11+"></a>
    <a href="https://pypi.org/project/strands-compose/"><img src="https://img.shields.io/pypi/v/strands-compose.svg" alt="PyPI version"></a>
    <a href="https://github.com/strands-agents/sdk-python"><img src="https://img.shields.io/badge/strands--agents-1.32.0-green.svg" alt="Strands Agents"></a>
    <a href="https://github.com/strands-compose/sdk-python/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License"></a>
  </p>
</div>

> [!IMPORTANT]
> Community project — not affiliated with AWS or the strands-agents team.

## What is this?

> **Think Docker Compose, but for AI agents**

[Strands](https://github.com/strands-agents/sdk-python) is a powerful agent SDK. Building multi-agent systems with it means writing the same wiring code over and over — models, MCP servers, hooks, orchestration topology. **Strands-compose kills that boilerplate**: describe your entire agent system in YAML, call `load()`, and get back plain, fully-wired strands objects. No wrappers. No magic. The real deal.

```yaml
models:
  default:
    provider: bedrock
    model_id: us.anthropic.claude-sonnet-4-6-v1:0

agents:
  researcher:
    model: default
    system_prompt: "You research topics."
  writer:
    model: default
    system_prompt: "You write reports."
  coordinator:
    model: default
    system_prompt: "Coordinate the team."

orchestrations:
  team:
    mode: delegate
    entry_name: coordinator
    connections:
      - agent: researcher
        description: "Research a topic."
      - agent: writer
        description: "Write the report."

entry: team
```

## Repositories

### [`sdk-python`](https://github.com/strands-compose/sdk-python) · [PyPI](https://pypi.org/project/strands-compose/) · [Examples](https://github.com/strands-compose/sdk-python/tree/main/examples)

The heart of the organization. Everything else builds on top of it.


---

## Coming Soon

### 🚀 `bedrock-agentcore`

Your `config.yaml` goes straight to production — no refactoring, no new abstractions. Dseploy your entire agent system to **AWS Bedrock AgentCore** with fully managed infrastructure, auto-scaling, and zero ops.

<div align="center">
  <img src="https://raw.githubusercontent.com/strands-compose/.github/main/img/bedrock-agentcore.png" width="500" alt="bedrock-agentcore preview">
</div>

---

### 💬 `chat-ui`

A ready-to-use chat frontend that connects to a **strands-compose server**. Point it at your server URL, and get a streaming chat panel with a live **Agent Flow graph** — watch every reasoning step, delegation, and agent completion render in real time as your system runs.

<div align="center">
  <img src="https://raw.githubusercontent.com/strands-compose/.github/main/img/chat-ui.png" width="500" alt="chat-ui preview">
</div>

---

## 🤝 Get Involved

**This project is built in the open — everyone is welcome.**

Whether you're fixing a bug, adding a new provider, improving docs, or just kicking the tyres — contributions of any size are appreciated. Come join the effort.

- ⭐ **Star [sdk-python](https://github.com/strands-compose/sdk-python)** to show support and help others discover the project
- 🐛 **Open an issue** if something doesn't work or you have a feature idea
- 🔀 **Submit a PR** — from a typo fix to a full new feature, all contributions are welcome
- 👀 **Watch this org** to follow new repos and releases as they land
