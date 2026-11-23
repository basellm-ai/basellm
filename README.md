# BaseLLM: self-hosted AI gateway

**BaseLLM** is a self-hosted AI gateway and control plane for enterprises, made by Base Interactive (Istanbul). All of an organization's LLM traffic goes through one OpenAI-compatible endpoint that runs on the organization's own infrastructure.

Website: https://llm.baseinteractive.com.tr
Docs: https://llm.baseinteractive.com.tr/en/docs/overview
30-day evaluation: https://llm.baseinteractive.com.tr/en/evaluation

> Name note: this BaseLLM is an enterprise AI gateway product. It is not the `BaseLLM` base class in LangChain or LlamaIndex.

## What it does

- **LLM Gateway:** one OpenAI-compatible endpoint (`POST /api/v1/chat/completions`) and an Anthropic Messages endpoint (`POST /api/v1/messages`) for every provider. Provider keys stay in BaseLLM, not in your apps.
- **Policy Engine:** project, API key, user and model limits, checked before the model is called. A rejected request costs nothing.
- **Budget and cost:** a monthly USD budget per project, with spend calculated on every request.
- **Sensitive data masking:** personal data and secrets are found and masked or blocked before the request leaves your network.
- **Prompt injection protection**, turned on per project.
- **Audit Log:** a tamper-evident record of who did what, and what the result was.
- **Agent control:** workflows, a tool registry with MCP servers, and human approval for risky steps.

## Connect your app

Change the base URL and the API key in your existing OpenAI SDK code:

```python
from openai import OpenAI

client = OpenAI(
    base_url="<basellm-endpoint>/api/v1",
    api_key="sk-ffm-...",  # project API key
)
resp = client.chat.completions.create(
    model="auto",
    messages=[{"role": "user", "content": "Hello"}],
    extra_headers={"X-FFM-User": "u-12345"},  # optional, for per-user limits
)
```

Claude Code and apps on the Anthropic SDK work the same way. See [Claude Code and the Anthropic SDK](https://llm.baseinteractive.com.tr/en/docs/claude-code).

## Installation

BaseLLM runs on Docker on a single server, or with a Helm chart on Kubernetes and OpenShift. See [Installation options](https://llm.baseinteractive.com.tr/en/docs/installation).

## Links

- Website: https://llm.baseinteractive.com.tr
- Product Hunt: https://www.producthunt.com/products/basellm
- SaaSHub: https://www.saashub.com/basellm
- Company: https://www.baseinteract.com
- Contact: info@baseinteract.com
