# AgentRouter Guide 2026: One API for Claude Code, Codex, OpenCode, Cursor & More

AgentRouter is a unified AI routing service that exposes **Anthropic-compatible** and **OpenAI-compatible** API endpoints so you can connect multiple coding agents and AI clients to one account and API key.

This guide shows the practical setup patterns, the tools currently documented by AgentRouter, and a few things to check before relying on any third-party routing service in production.

> **Referral disclosure:** The signup link in this guide is my referral link. If you register through it, I may receive a referral benefit. Referral bonuses, trial credits, pricing, and model availability can change, so check the AgentRouter website for the current offer before signing up.

## Quick signup

**Referral link:** https://agentrouter.org/register?aff=rQi3

## What AgentRouter does

AgentRouter provides a single routing layer for multiple AI models and coding tools. According to its current documentation, the same AgentRouter API key can be used across supported clients, while usage is measured through the same account.

The important detail is that there are **two connection styles**:

- **Anthropic-compatible** endpoint for Claude-family integrations
- **OpenAI-compatible** endpoint for GPT and other compatible integrations

Current documented base URLs:

```text
Anthropic-compatible:
https://co.agentrouter.org

OpenAI-compatible:
https://co.agentrouter.org/v1
```

Do not mix them. Claude/Anthropic integrations generally use the URL **without `/v1`**, while OpenAI-compatible integrations use the URL **with `/v1`**.

## Tools currently documented by AgentRouter

AgentRouter's current integration guide lists support for tools including:

### VS Code extensions

- Claude Code for VS Code
- Cline
- Roo Code
- Kilo Code
- GitHub Copilot custom endpoints

### CLI / terminal tools

- Claude Code CLI
- Codex
- OpenCode
- Qwen Code
- Crush
- Hermes Agent

### Desktop / IDE clients

- Claude Desktop
- Trae
- Cursor
- Craft Agents

Model availability can depend on your account or resource pool, so always check the model list in your own AgentRouter dashboard rather than assuming a specific model will always be available.

## Claude Code CLI setup

AgentRouter documents Claude Code through its Anthropic-compatible endpoint.

Install Claude Code:

```bash
npm install -g @anthropic-ai/claude-code@latest
```

### macOS / Linux

```bash
export ANTHROPIC_AUTH_TOKEN="<YOUR_AGENTROUTER_API_KEY>"
export ANTHROPIC_BASE_URL="https://co.agentrouter.org"
export ANTHROPIC_MODEL="<MODEL_ID_FROM_YOUR_DASHBOARD>"

claude
```

### Windows PowerShell

```powershell
$env:ANTHROPIC_AUTH_TOKEN="<YOUR_AGENTROUTER_API_KEY>"
$env:ANTHROPIC_BASE_URL="https://co.agentrouter.org"
$env:ANTHROPIC_MODEL="<MODEL_ID_FROM_YOUR_DASHBOARD>"

claude
```

Use a model ID that is actually available to your AgentRouter account.

## Codex setup

Codex uses the OpenAI-compatible endpoint.

Create or edit:

```text
~/.codex/config.toml
```

Example:

```toml
model = "<MODEL_ID_FROM_YOUR_DASHBOARD>"
model_provider = "agentrouter"

[model_providers.agentrouter]
name = "AgentRouter"
base_url = "https://co.agentrouter.org/v1"
env_key = "AGENTROUTER_API_KEY"
wire_api = "chat"
```

Then set the API key.

### macOS / Linux

```bash
export AGENTROUTER_API_KEY="<YOUR_AGENTROUTER_API_KEY>"
```

### Windows PowerShell

```powershell
$env:AGENTROUTER_API_KEY="<YOUR_AGENTROUTER_API_KEY>"
```

Then test Codex with a simple prompt.

## OpenCode setup

AgentRouter documents OpenCode through an OpenAI-compatible custom provider.

Example `opencode.json`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "agentrouter": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "AgentRouter",
      "options": {
        "baseURL": "https://co.agentrouter.org/v1"
      },
      "models": {
        "YOUR_MODEL_ID": {
          "name": "AgentRouter Model"
        }
      }
    }
  },
  "model": "agentrouter/YOUR_MODEL_ID"
}
```

Then authenticate the provider and launch OpenCode:

```bash
opencode providers login --provider agentrouter
opencode
```

## Cursor setup

AgentRouter's guide currently documents Cursor through its OpenAI-compatible custom base URL.

In Cursor:

1. Open **Settings**.
2. Go to **Models**.
3. Add your AgentRouter API key in the OpenAI API key field.
4. Enable the custom/override OpenAI base URL.
5. Set the base URL to:

```text
https://co.agentrouter.org/v1
```

AgentRouter notes that Cursor's own plan or UI limitations may affect custom-model selection, especially on free plans.

## Cline / Roo Code / Kilo Code

The same pattern applies:

- Choose **Anthropic** when connecting a Claude-compatible model.
- Use `https://co.agentrouter.org`
- Or choose **OpenAI Compatible** for compatible models.
- Use `https://co.agentrouter.org/v1`

Do not use the `/v1` suffix for Anthropic Messages-style endpoints.

## Why this can be useful

A routing layer can be convenient if you regularly switch between coding agents or model families because you do not need to maintain a completely different API setup for every tool.

Potential advantages include:

- one API account for multiple coding tools
- OpenAI-compatible and Anthropic-compatible endpoints
- easier model switching
- a common usage/credit pool across supported agents
- less configuration duplication across Claude Code, Codex, OpenCode and other tools

AgentRouter also advertises enterprise features such as centralized management, usage controls, audit logs and routing/failover capabilities.

## Important things to check before using it

A third-party model router sits between your coding tool and the underlying model provider. That means you should evaluate it like any other infrastructure provider.

Before sending sensitive code or business data, check:

- current terms of service
- privacy/data-handling policy
- whether prompts or responses are retained
- which underlying providers may receive your data
- current pricing and credit rules
- rate limits
- available model IDs
- support and outage procedures

For production or confidential workloads, do not choose a service only because it is cheaper. Reliability, data handling and support matter just as much.

## Troubleshooting

### 401 / authentication error

Check:

- your API key is correct
- the environment variable name matches your client configuration
- your account has available balance/credit

### 404 when using Claude

A common configuration error is adding `/v1` to the Anthropic-compatible endpoint.

Use:

```text
https://co.agentrouter.org
```

not:

```text
https://co.agentrouter.org/v1
```

for Anthropic-style Claude integrations.

### Model not found

Do not assume a model ID from an old tutorial is still available. Check the current model list in AgentRouter and update your configuration.

### OpenAI-compatible client fails

Make sure you are using:

```text
https://co.agentrouter.org/v1
```

and that the selected model supports the API format your client expects.

## Who is AgentRouter most useful for?

It is potentially useful for developers who:

- use several AI coding agents
- switch between Claude-compatible and OpenAI-compatible clients
- want one account for multiple tools
- experiment with different models frequently
- want to avoid maintaining many separate configurations

If you only use one model/provider and already have a stable direct API setup, adding another routing layer may not provide much benefit.

## Signup

If you want to try AgentRouter, you can register here:

### https://agentrouter.org/register?aff=rQi3

**Disclosure:** This is a referral link. I may receive a benefit if you sign up through it. Check AgentRouter directly for the latest pricing, trial-credit and referral terms.

## Official resources

- AgentRouter: https://agentrouter.org/
- Integration guide: https://co.agentrouter.org/portal/guide
- Pricing information: https://co.agentrouter.org/portal/pricing
- Terms of service: https://co.agentrouter.org/portal/terms

---

_Last reviewed: September 2026. Tool compatibility, model names, pricing and referral offers can change._
