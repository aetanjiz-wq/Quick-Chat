# AgentRouter with Codex: A Practical Setup Overview

If you use Codex from the terminal, AgentRouter can act as an OpenAI-compatible routing layer. This is useful when you want one routing account for multiple coding tools instead of managing a separate provider configuration for every client.

The important part is using the OpenAI-compatible endpoint, which includes `/v1`. Your Codex configuration should point the provider base URL there and read the API key from an environment variable rather than hardcoding it into a repository.

After configuration, test with a harmless task such as asking Codex to inspect a sample project or explain a file. If the client returns a model-not-found error, check the model IDs currently available in your AgentRouter account rather than copying an old model name from a tutorial.

In my own signup, I received $200 in credits. That was my experience at the time and should not be interpreted as a guaranteed offer for every account.

## Referral

Try AgentRouter: https://agentrouter.org/register?aff=rQi3

**Disclosure:** The link above is my referral link, and I may receive a benefit if you use it.