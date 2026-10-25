# ResearchMind: Multi-Agent Research Assistant

A multi-agent AI system that researches any topic on the web and writes a structured report, then has a critic review it.

## How it works

```
Topic → Search Agent → Reader Agent → Writer Chain → Critic Chain
```

1. **Search Agent**: uses the Tavily API to find recent, relevant web sources.
2. **Reader Agent**: picks the most relevant URL and scrapes its content with BeautifulSoup.
3. **Writer Chain**: turns the research into a report (Introduction, Key Findings, Conclusion, Sources).
4. **Critic Chain**: reviews the report and gives a score, strengths, areas to improve and a verdict.

The search and reader steps are LangChain tool-calling agents. The writer and critic are prompt chains. All four run on OpenAI `gpt-4o-mini`.

## Tech stack

LangChain · OpenAI GPT-4o-mini · Tavily · BeautifulSoup · Streamlit

## Setup

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt streamlit
```

Create a `.env` file in the project folder:

```
OPENAI_API_KEY=your_openai_key
TAVILY_API_KEY=your_tavily_key
```

## Run

Web app:

```bash
streamlit run app.py
```

Command line:

```bash
python pipeline.py
```

## Project structure

| File | Purpose |
|---|---|
| `tools.py` | `web_search` (Tavily) and `scrape_url` (BeautifulSoup) tools |
| `agents.py` | LLM setup, search/reader agents, writer and critic chains |
| `pipeline.py` | Runs the full pipeline from the command line |
| `app.py` | Streamlit web interface |

## Credits

Based on the original project by [Akarsh Vyas](https://github.com/AkarshVyas/Multi-agent-research-system).
