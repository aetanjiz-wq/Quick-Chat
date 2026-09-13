# AgentRouter on Windows: A Simple Developer Workflow

Windows users can connect supported coding agents to AgentRouter without changing their entire development environment. The most important habit is to keep API keys in environment variables rather than saving them directly inside source code.

For terminal tools, PowerShell is usually enough. Set the required key and base URL for your client, open a new terminal if needed, and run a small test request. If authentication fails, confirm that the variable exists in the same shell where the coding tool is running.

For editor-based tools, verify whether the client expects an OpenAI-compatible endpoint or an Anthropic-compatible endpoint. Mixing those two styles is a common cause of errors.

I personally received $200 in AgentRouter credits, which made Windows testing easier for me. That amount is not guaranteed and may depend on the current promotion or account.

Referral link: https://agentrouter.org/register?aff=rQi3

**Disclosure:** This is my referral link. I may receive a referral benefit if you use it.