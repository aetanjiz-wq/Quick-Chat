# AgentRouter Troubleshooting: 401, 404 and Model Errors

Most AgentRouter setup problems fall into a few categories: authentication, endpoint mismatch, or model selection.

A **401** usually means the API key is missing, invalid, expired, or not being read by the current shell or app. Re-check the environment variable and restart the terminal if necessary.

A **404** can happen when a client is pointed at the wrong compatibility endpoint. Anthropic-style and OpenAI-style clients do not always use the same base URL structure.

A **model not found** error usually means the configured model ID is outdated or unavailable for the account. Check the current dashboard rather than copying old examples blindly.

Also confirm that your account has usable balance and that the client supports the requested API format.

I personally received $200 in AgentRouter credits. That amount is not guaranteed for other users.

Referral: https://agentrouter.org/register?aff=rQi3

**Disclosure:** I may receive a benefit if you use this referral link.