# Chat with a Retail Database using AI

**Student:** Afreen Sorathiya  
**UNI:** as7852  
**Course:** AI in Business | Columbia University | Spring 2026

---

## Overview

An agentic AI workflow built in n8n that enables natural language querying of a 1 million+ row online retail dataset stored in a cloud PostgreSQL database (Neon). Users can ask plain English questions and the AI agent automatically generates and executes the correct SQL query, returning results in a readable format.

---

## Tech Stack

| Component | Tool Used |
|-----------|-----------|
| Workflow Automation | n8n Cloud |
| LLM | OpenAI gpt-4o-mini |
| Database | Neon PostgreSQL |
| Memory | n8n Simple Memory |
| Dataset | UCI Online Retail II (2009–2011) |

---

## Architecture

```
User Chat → AI Agent → Groq/OpenAI LLM
                     → Simple Memory (conversation history)
                     → Postgres Tool (dynamic SQL execution)
                     → Neon PostgreSQL Database
```

---

## Database

- **Database:** retaildb (hosted on Neon cloud PostgreSQL)
- **Table 1:** `year_2009_2010` — 525,461 rows
- **Table 2:** `year_2010_2011` — 541,910 rows
- **Total rows:** 1,067,371

**Columns:** Invoice, StockCode, Description, Quantity, InvoiceDate, Price, Customer ID, Country

---

## How It Works

1. User types a natural language question in the n8n chat interface
2. The AI Agent receives the question and uses the system prompt to understand the database schema
3. The LLM generates the appropriate SQL query
4. The Postgres tool executes the dynamic SQL query against the Neon database
5. Simple Memory retains conversation history for follow-up questions
6. Results are returned to the user in a readable format

---

## Sample Queries Demonstrated

**Q: Which tables are in the database?**
> The database contains: year_2009_2010 and year_2010_2011

**Q: What are the top 3 countries by total revenue in year_2009_2010?**
> 1. United Kingdom — £8,194,777.53
> 2. EIRE — £352,242.73
> 3. Netherlands — £263,863.41

**Q: Which country has the most orders in year_2010_2011?**
> 1. United Kingdom — 23,494 orders
> 2. Germany — 603
> 3. France — 461
> 4. EIRE — 360
> 5. Belgium — 119

**Q: How many unique customers are in year_2010_2011?**
> 4,372 unique customers

---

## Setup Instructions

1. Import `Chat_with_a_database_using_AI.json` into your n8n instance
2. Create a Neon PostgreSQL database and load the UCI Online Retail II dataset
3. Add your OpenAI API key as a credential in the OpenAI Chat Model node
4. Add your Neon connection details in the Postgres node
5. Activate the workflow and open the chat interface
6. Start querying in natural language!

---

## Dataset

UCI Online Retail II Dataset  
Source: https://archive.ics.uci.edu/dataset/502/online+retail+ii
