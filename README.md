# 🤖 AI Research Chatbot using LangGraph, Tavily, Wikipedia, and Arxiv APIs

### 🚀 Project Overview

The **AI Research Chatbot** is a LangGraph-powered intelligent assistant capable of retrieving and synthesizing information from multiple trusted sources — **Arxiv**, **Wikipedia**, and **Tavily Search API** — all integrated with the **Groq LLM** for high-speed, context-aware reasoning.

This chatbot acts as a **research companion**, capable of fetching recent research papers, verified news, and encyclopedia-level summaries — all within a single conversation flow.

---

## 🧠 Key Features

- 🔗 **Multi-Source Integration:** Fetches research data from **Arxiv**, general knowledge from **Wikipedia**, and the latest verified updates from **Tavily Search**.
- 🧩 **LangGraph Workflow:** Uses a **graph-based architecture** with tool nodes and conditional routing to control tool invocation intelligently.
- ⚙️ **ReAct Agent Loop:** Implements **Reasoning + Acting (ReAct)** loop for iterative reasoning — the LLM decides when to call a tool and when to respond directly.
- 💬 **Context Retention:** Maintains message states using `TypedDict` schema with message reducers for seamless multi-turn conversations.
- ⚡ **Groq LLM Integration:** Powered by **Llama 3.1 8B Instant model** through Groq API for fast inference and low latency.
- 🧰 **Modular Design:** Clean separation of nodes, tools, and graph compilation for easy debugging and extensibility.

---

## 🏗️ Architecture Overview

### 🔹 Tools Integrated
1. **ArxivQueryRun** — Fetches research papers and abstracts using `ArxivAPIWrapper`.
2. **WikipediaQueryRun** — Retrieves concise factual data from Wikipedia using `WikipediaAPIWrapper`.
3. **TavilySearchResults** — Searches the web for latest verified AI-related news and updates.

### 🔹 Workflow

```mermaid
graph TD;
    START --> LLM_Node["tool_calling_llm"]
    LLM_Node -->|Tool call detected| ToolNode["ToolNode (Arxiv / Wiki / Tavily)"]
    ToolNode --> LLM_Node
    LLM_Node -->|No tool call| END
