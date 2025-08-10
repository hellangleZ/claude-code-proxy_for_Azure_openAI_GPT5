# Azure GPT-5 Compatibility Fix

This fork includes fixes for Azure OpenAI GPT-5 compatibility issues.

## Fixed Issues

### 1. Parameter Conversion
- **Problem**: Azure GPT-5 doesn't support `max_tokens` parameter
- **Solution**: Automatically convert `max_tokens` to `max_completion_tokens` for Azure models

### 2. Temperature Parameter
- **Problem**: Azure GPT-5 only supports default `temperature=1`
- **Solution**: Skip temperature parameter for Azure models to use default value

## Configuration

Set up your `.env` file:

```env
# Provider preference
PREFERRED_PROVIDER="azure"

# Model mapping
BIG_MODEL="gpt-5"
SMALL_MODEL="gpt-5"

# Azure configuration
AZURE_OPENAI_ENDPOINT="https://your-endpoint.openai.azure.com"
AZURE_OPENAI_API_KEY="your-api-key"
AZURE_API_VERSION="2025-01-01-preview"
AZURE_DEPLOYMENT_NAME="gpt-5"
```

## Usage

1. Start the proxy:
```bash
cd claude-code-proxy
uv run uvicorn server:app --host 0.0.0.0 --port 8082 --reload
```

2. Use with official Claude Code:
```bash
ANTHROPIC_API_KEY="sk-ant-dummy-key-for-proxy" ANTHROPIC_BASE_URL=http://localhost:8082 claude
```

## Verified Working

✅ Claude Code → Azure GPT-5 via proxy  
✅ Parameter conversion (max_tokens → max_completion_tokens)  
✅ Temperature handling (uses default value)  
✅ Chinese language support  
✅ Tool calling support  

## Original Project

Based on [claude-code-proxy](https://github.com/samuelint/claude-code-proxy) with Azure GPT-5 compatibility improvements.
