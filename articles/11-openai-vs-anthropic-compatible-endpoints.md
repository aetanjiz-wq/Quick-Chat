# OpenAI-Compatible vs Anthropic-Compatible Endpoints in AgentRouter

One of the easiest mistakes to make with an AI router is using the wrong API style for the client. AgentRouter supports both OpenAI-compatible and Anthropic-compatible connections, but they are not interchangeable.

OpenAI-compatible clients usually expect an endpoint shaped like an OpenAI API and often use a base URL ending in `/v1`. Anthropic-style clients such as Claude-oriented tools typically use the Anthropic-compatible base URL without that same suffix.

If authentication succeeds but requests still fail, check the API style before changing everything else. Also verify that the model ID is actually available in your account.

This distinction matters when switching between tools such as Claude Code, Codex, OpenCode, Cursor, Cline, Roo Code and Kilo Code.

I received $200 in credits when I joined AgentRouter, but that is my personal experience and not a guaranteed signup amount.

Referral link: https://agentrouter.org/register?aff=rQi3

**Disclosure:** This is my referral link and I may receive a benefit if you use it.