# Claude Code Proxy for Azure OpenAI 🚀

**Use Claude Code with Azure OpenAI GPT-5, O3, and Latest Models** ✨

A proxy server that enables seamless integration between Claude Code and Azure OpenAI's latest models (GPT-5, O3, etc.), with automatic parameter conversion and full compatibility.

## 🎯 Key Features

- ✅ **Azure OpenAI GPT-5 & O3 Support** - Full compatibility with latest models
- ✅ **Automatic Parameter Conversion** - `max_tokens` → `max_completion_tokens`  
- ✅ **Temperature Handling** - Proper Azure model parameter support
- ✅ **Chinese Language Support** - Perfect multilingual support
- ✅ **Tool Calling Support** - All Claude Code features work seamlessly
- ✅ **Production Ready** - Stable and tested

## ⚡ Quick Start

### Prerequisites
- Azure OpenAI API key and endpoint 🔑
- [uv](https://github.com/astral-sh/uv) installed

### 1. Clone & Setup
```bash
git clone https://github.com/hellangleZ/claude-code-proxy_for_Azure_openAI_GPT5.git
cd claude-code-proxy_for_Azure_openAI_GPT5
```

### 2. Configure Environment
Copy and edit the environment file:
```bash
cp .env.example .env
```

Edit `.env` for Azure OpenAI:
```env
# Provider preference
PREFERRED_PROVIDER="azure"

# Model mapping to Azure deployments
BIG_MODEL="gpt-5"     # or "o3", "gpt-4o", etc.
SMALL_MODEL="gpt-5"   # or your preferred model

# Azure OpenAI Configuration
AZURE_OPENAI_ENDPOINT="https://your-endpoint.openai.azure.com"
AZURE_OPENAI_API_KEY="your-azure-api-key"
AZURE_API_VERSION="2025-01-01-preview"
AZURE_DEPLOYMENT_NAME="gpt-5"
```

### 3. Start the Proxy
```bash
uv run uvicorn server:app --host 0.0.0.0 --port 8082 --reload
```

### 4. Use with Claude Code
```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Connect to proxy
ANTHROPIC_BASE_URL=http://localhost:8082 claude
```

## 🔧 Supported Azure Models

### Latest Azure OpenAI Models
- **GPT-5** - Latest reasoning model
- **O3** - Advanced reasoning capabilities  
- **GPT-4O** - Multimodal model
- **GPT-4O-mini** - Fast and efficient
- And more Azure deployments...

### Model Mapping
| Claude Model | Maps to Azure Model |
|--------------|-------------------|
| `claude-3-5-haiku` | `azure/{SMALL_MODEL}` |
| `claude-3-5-sonnet` | `azure/{BIG_MODEL}` |

## 🛠️ How It Works

1. **Receives** Claude API requests 📥
2. **Converts** parameters for Azure compatibility 🔄
   - `max_tokens` → `max_completion_tokens`
   - Handles temperature restrictions
3. **Routes** to Azure OpenAI 📤
4. **Returns** Claude-formatted responses ✅

## ✨ What's Fixed

This fork specifically addresses Azure OpenAI compatibility issues:

- **Parameter Conversion**: Automatic `max_tokens` → `max_completion_tokens` for Azure models
- **Temperature Handling**: Respects Azure model parameter constraints
- **Error Handling**: Proper Azure API error responses
- **Authentication**: Seamless Azure API key handling

## 🤝 Contributing

Contributions welcome! This project focuses on Azure OpenAI compatibility improvements.

---

**Based on [claude-code-proxy](https://github.com/samuelint/claude-code-proxy) with Azure OpenAI enhancements.**
