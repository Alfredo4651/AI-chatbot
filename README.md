
# AI Crypto Trading Chatbot (MCP + Wellat Integration)

A conversational AI agent that lets users query their crypto portfolio, trading history, and performance metrics in natural language — powered by **Claude AI**, **Model Context Protocol (MCP)**, and **n8n** workflow orchestration.

---

## Overview

This project implements an AI-powered chatbot that acts as a personal trading assistant. Instead of navigating dashboards manually, users ask questions like *"What's my best-performing asset this week?"* or *"Show me my last 5 trades"* — and the agent retrieves the relevant data and responds conversationally.

The system integrates with **Wellat** (a financial data platform) via MCP tool-calling, enabling the agent to pull live portfolio snapshots and trading records dynamically per query.

Built on dummy data for portfolio demonstration purposes.

---

## Architecture

```
User Input (chat interface)
    │
    ▼
n8n Webhook Trigger
    │
    ▼
AI Agent Node (Claude via Anthropic API)
    │
    ├── MCP Tool: get_portfolio()       → Wellat portfolio snapshot
    ├── MCP Tool: get_trading_records() → Recent trade history
    └── MCP Tool: get_performance()     → P&L, win rate, asset breakdown
    │
    ▼
Natural Language Response → Returned to user
```

---

## Features

- **Natural language querying** — ask questions about your portfolio in plain English
- **MCP tool-calling** — structured, schema-validated calls to Wellat data endpoints
- **Portfolio snapshot** — current holdings, asset allocation, total value
- **Trading records** — paginated trade history with filters (asset, date range, type)
- **Performance analytics** — P&L summary, win rate, top/worst performers
- **n8n orchestration** — handles routing, tool execution, and response formatting
- **Stateless design** — each query is self-contained; no user data persisted

---

## Tech Stack

| Layer | Tool |
|---|---|
| AI model | Claude (Anthropic API) |
| Tool protocol | Model Context Protocol (MCP) |
| Workflow orchestration | n8n |
| Data source | Wellat (financial platform) |
| Language | Python / JavaScript (n8n expressions) |
| Data | Dummy / simulated trading data |

---

## What is MCP?

**Model Context Protocol** is an open standard that allows AI models to call external tools in a structured, schema-validated way. Rather than parsing unstructured text, the AI sends typed function calls (e.g. `get_portfolio(user_id=123, currency="USD")`) and receives structured JSON back — making integrations reliable and auditable.

This project uses MCP to connect the AI agent to Wellat's data layer cleanly, without hardcoding API logic into the prompt.

---

## Example Queries

> *"What's my current portfolio value?"*  
> *"Show me my last 10 trades for Bitcoin"*  
> *"Which asset has the highest return this month?"*  
> *"What's my overall win rate?"*

---

## Note on Data & Credentials

This project runs on **dummy/simulated trading data**. All API credentials and sensitive configuration have been removed from shared assets. Screenshots of the workflow are included in this repository in place of raw JSON exports.

---

## Screenshots

Workflow canvas and chatbot interaction screenshots are included in this repository.

---

## Author

**Alfred Michael** — AI Automation Specialist & Data Scientist  
[Portfolio](https://alfredo4651.github.io) · [GitHub](https://github.com/Alfredo4651) · [LinkedIn](https://linkedin.com/in/alfredmichael01)
