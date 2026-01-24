# CLAUDE.md - Project Guide for Claude Code

## Project Overview

**awesome-llm-apps** is a curated collection of LLM-powered applications demonstrating various AI patterns including RAG (Retrieval Augmented Generation), AI Agents, Multi-agent Teams, MCP (Model Context Protocol), Voice Agents, and more. The repository serves as an educational resource and reference implementation for building LLM applications.

## Repository Structure

```
awesome-llm-apps/
├── starter_ai_agents/          # Beginner-friendly AI agent examples
├── advanced_ai_agents/         # Complex agent implementations
│   ├── single_agent_apps/      # Single agent applications
│   ├── multi_agent_apps/       # Multi-agent systems
│   │   └── agent_teams/        # Coordinated agent teams
│   └── autonomous_game_playing_agent_apps/  # Game-playing agents
├── voice_ai_agents/            # Voice-enabled AI agents
├── mcp_ai_agents/              # Model Context Protocol agents
├── rag_tutorials/              # RAG pattern implementations
├── advanced_llm_apps/          # Advanced LLM applications
│   ├── chat_with_X_tutorials/  # Chat with various data sources
│   ├── llm_apps_with_memory_tutorials/  # Memory-enabled LLM apps
│   ├── llm_finetuning_tutorials/  # Fine-tuning guides
│   └── llm_optimization_tools/    # Optimization utilities
├── ai_agent_framework_crash_course/  # Framework tutorials
│   ├── google_adk_crash_course/      # Google ADK examples
│   └── openai_sdk_crash_course/      # OpenAI Agents SDK examples
└── docs/                       # Documentation assets
```

## Technology Stack

### Primary Languages
- **Python** - All applications are written in Python

### Common Frameworks & Libraries
- **Streamlit** - Primary UI framework for most applications
- **agno** - AI agent framework (formerly phidata)
- **LangChain** - LLM orchestration framework
- **CrewAI** - Multi-agent framework
- **OpenAI SDK** - OpenAI API and Agents SDK
- **Google ADK** - Google's Agent Development Kit

### LLM Providers Supported
- OpenAI (GPT-4o, GPT-4)
- Anthropic (Claude)
- Google (Gemini)
- xAI (Grok)
- Meta (Llama - via Ollama for local)
- Alibaba (Qwen - via Ollama for local)
- DeepSeek (via Ollama for local)

### Vector Databases & Storage
- Qdrant
- Pinecone
- ChromaDB
- PostgreSQL with pgvector

## Project Conventions

### Directory Structure (per project)
Each project typically contains:
- `README.md` or `README.MD` - Project documentation with setup instructions
- `requirements.txt` - Python dependencies
- Main application file (commonly named after the feature, e.g., `travel_agent.py`)
- Optional: Local version using Ollama (e.g., `local_travel_agent.py`)

### Naming Conventions
- Directories use `snake_case` (e.g., `ai_travel_agent`, `chat_with_pdf`)
- Python files use `snake_case` (e.g., `travel_agent.py`)
- Agent teams typically have `_team` suffix
- Local/Ollama variants prefixed with `local_`

### Environment Variables
Most projects require API keys configured via environment variables or Streamlit sidebar input:
- `OPENAI_API_KEY` - OpenAI API access
- `ANTHROPIC_API_KEY` - Anthropic Claude access
- `GOOGLE_API_KEY` / `GEMINI_API_KEY` - Google Gemini access
- `XAI_API_KEY` - xAI Grok access
- `SERPAPI_API_KEY` - Web search functionality
- `QDRANT_API_KEY` / `PINECONE_API_KEY` - Vector database access

## Common Commands

### Running a Streamlit Application
```bash
cd <project_directory>
pip install -r requirements.txt
streamlit run <main_file>.py
```

### Running with Ollama (Local LLMs)
```bash
# Ensure Ollama is installed and running
ollama pull llama3.1  # or other model
streamlit run local_<app_name>.py
```

## Development Guidelines

### Adding a New Project
1. Create a directory under the appropriate category
2. Include a `README.md` with:
   - Project description
   - Features list
   - Setup instructions (clone, install, API keys, run)
   - How it works explanation
3. Include a `requirements.txt` with pinned major versions where important
4. Add the project to the main `README.md` under the appropriate section

### Code Style
- Use clear, descriptive variable names
- Include docstrings for functions and classes
- Handle API errors gracefully
- Support both cloud and local LLM options where practical

### Dependencies
- Prefer `agno` framework for new agent implementations
- Use Streamlit for interactive UIs
- Pin critical dependency versions in requirements.txt

## Key Patterns

### Agent Pattern (using agno)
```python
from agno.agent import Agent
from agno.models.openai import OpenAIChat

agent = Agent(
    model=OpenAIChat(id="gpt-4o"),
    tools=[...],
    instructions=[...],
)
```

### RAG Pattern
1. Load documents
2. Split into chunks
3. Create embeddings
4. Store in vector database
5. Query with semantic search
6. Augment LLM prompt with retrieved context

### Multi-Agent Pattern
- Define specialized agents with specific roles
- Coordinate via agent teams or orchestration
- Use handoffs for task delegation

## Testing

Projects in this repository are primarily demonstrations and tutorials. When modifying:
- Verify the application runs without errors
- Test core functionality manually via the Streamlit UI
- Ensure API integrations work with valid keys

## Notes for Claude Code

- Each subdirectory is a standalone project with its own dependencies
- When working on a specific project, install requirements from that project's `requirements.txt`
- Many projects offer both cloud (OpenAI) and local (Ollama) variants
- The main README.md serves as the index for all projects
- Look for existing patterns in similar projects before creating new implementations
