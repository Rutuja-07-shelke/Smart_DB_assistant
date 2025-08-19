# 🧠🔎 AI Database Search (Streamlit)

A simple Streamlit webapp that turns natural language prompts into **SQLite** queries and shows the results.
- If you provide an **OpenAI API Key**, it will use NL→SQL (model defaults to `gpt-4o-mini`).
- Without an API key, it falls back to a **naive keyword search** across text columns.

## Quickstart

```bash
pip install -r requirements.txt
# Optional: export your key for NL→SQL
export OPENAI_API_KEY=sk-...
streamlit run app.py
```

In the sidebar:
- Load the demo database (or upload your own `.sqlite` / `.db` file)
- Optionally set your OpenAI API key and model

Then type questions like:
- "List all orders with customer names and product names"
- "Total revenue by product category"
- "Top 3 products by quantity sold"
- "Customers from Pune who bought displays"
- "Orders placed after Aug 2, 2025"

## Safety
- The app **only executes SELECT (or CTE + SELECT)** queries and adds a LIMIT when missing.

## Notes
- This demo uses **SQLite** for simplicity. You can adapt `get_sqlite_connection` to other databases (Postgres/MySQL) with SQLAlchemy, and adjust the schema extractor.