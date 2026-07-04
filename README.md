# Agentic AI Learning

A hands-on learning repository for building agentic AI applications with [LangChain v1](https://python.langchain.com/). The notebooks walk through core concepts—models, messages, tools, agents, and middleware—using Jupyter so you can experiment interactively.

## What You'll Learn

- **LangChain v1 basics** — version check, environment setup, and the new `create_agent` API
- **Model integration** — unified chat model initialization with OpenAI, Groq, and Google Gemini via `init_chat_model`
- **Messages** — structured conversation with `SystemMessage`, `HumanMessage`, and `AIMessage`
- **Tools** — defining tools with the `@tool` decorator, binding them to models, and inspecting tool calls
- **Agents** — building agents that invoke tools to answer questions
- **Middleware** — conversation summarization with `SummarizationMiddleware` for long-running, multi-turn dialogues

## Project Structure

```
agentic_ai_learning/
├── updatedLangchain/
│   ├── 1-langchainintro.ipynb    # LangChain v1 intro & create_agent
│   ├── 2-modelintegration.ipynb  # Multi-provider model setup
│   ├── 3-tools.ipynb             # Tool definition & binding
│   └── 4-middleware.ipynb        # SummarizationMiddleware
├── 4-messages.ipynb              # Message types & chat invocation
├── main.py                       # Placeholder entry point
├── pyproject.toml                # Project metadata & dependencies
├── uv.lock                       # Locked dependency versions (uv)
├── .python-version               # Python version pin (3.13)
└── .env                          # API keys (create locally, do not commit)
```

## Prerequisites

- [uv](https://docs.astral.sh/uv/) package manager
- Python 3.13+ (uv will install the pinned version from `.python-version` if needed)
- API keys for at least one provider:
  - [OpenAI](https://platform.openai.com/)
  - [Groq](https://console.groq.com/) (optional)
  - [Google AI Studio](https://aistudio.google.com/) (optional)

## Setup

1. **Install uv** (if you don't have it yet)

   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

   See the [uv installation docs](https://docs.astral.sh/uv/getting-started/installation/) for other platforms.

2. **Clone the repository**

   ```bash
   git clone <repo-url>
   cd agentic_ai_learning
   ```

3. **Install dependencies**

   This creates a `.venv` virtual environment and installs all packages from `uv.lock`:

   ```bash
   uv sync
   ```

4. **Configure environment variables**

   Create a `.env` file in the project root:

   ```env
   OPEN_AI_API_KEY=your-openai-key
   GROQ_API_KEY=your-groq-key
   GOOGLE_API_KEY=your-google-key
   ```

   Notebooks load these via `python-dotenv` and map them to the provider-specific env vars LangChain expects (e.g. `OPEN_AI_API_KEY` → `OPENAI_API_KEY`).

5. **Launch Jupyter and open a notebook**

   ```bash
   uv run jupyter notebook
   ```

   Alternatively, activate the virtual environment first:

   ```bash
   source .venv/bin/activate   # macOS/Linux
   jupyter notebook
   ```

## Notebooks

| Notebook | Topics |
|----------|--------|
| `updatedLangchain/1-langchainintro.ipynb` | LangChain v1 overview, `create_agent`, custom tool functions, agent invocation |
| `updatedLangchain/2-modelintegration.ipynb` | `init_chat_model` with Google Gemini (`google_genai:gemini-2.5-flash-lite`) |
| `updatedLangchain/3-tools.ipynb` | `@tool` decorator, `model.bind_tools()`, parsing tool calls |
| `updatedLangchain/4-middleware.ipynb` | `SummarizationMiddleware`, `InMemorySaver` checkpointer, threaded conversations |
| `4-messages.ipynb` | `SystemMessage`, `HumanMessage`, `AIMessage`, multi-turn chat |

Run the notebooks in order within `updatedLangchain/` for a progressive walkthrough, then explore `4-messages.ipynb` for the message abstraction layer.

## Dependencies

| Package | Purpose |
|---------|---------|
| `langchain` | Core framework (v1.x) |
| `langchain-openai` | OpenAI model integration |
| `langchain-groq` | Groq model integration |
| `langchain-google-genai` | Google Gemini integration |
| `langchain-community` | Community integrations |
| `python-dotenv` | Load API keys from `.env` |
| `ipykernel` | Jupyter kernel support |

See `pyproject.toml` and `uv.lock` for version details.

### Adding a new dependency

```bash
uv add <package-name>
```

This updates `pyproject.toml` and `uv.lock`.

## Running main.py

```bash
uv run python main.py
```

This is a minimal placeholder; the primary learning material lives in the notebooks.
