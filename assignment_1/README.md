# Problem Statement: Real-Time Market Sentiment Analyzer Using LangChain Chains

## Objective

Build a LangChain-powered pipeline (Chain) that:

1. Accepts a company name as input.
2. Extracts or generates its stock ticker symbol.
3. Fetches recent news related to the company from Yahoo Finance.
4. Extracts concise headlines or article summaries.
5. Analyzes sentiment using GPT-40 or GPT-40-mini.
6. Returns a structured JSON containing sentiment insights and relevant metadata.
7. Uses Langfuse for tracing, debugging, and monitoring.

---

## Tech Stack & Tools

- **Framework**: LangChain  
- **LLM**: GPT-40 or GPT-40-mini (via Azure OpenAI)  
- **Data Source**: Yahoo Finance (via LangChain tools)  
- **Prompt Management & Observability**: Langfuse  
- **Environment**: Python (v3.10+ recommended)  
- **Parsing Tools**: Structured OutputParser or Pydantic OutputParser from LangChain

---

## Task Breakdown

### Step 1: Accept Input

- Accept a company name as user input (e.g., `"Apple Inc"`).

---

### Step 2: Get Stock Code

- Extract or generate the stock ticker using:
  - A static lookup table, **or**
  - A dynamic tool like Yahoo Finance Symbol Suggest.
- This becomes the first component of the LangChain pipeline.

---

### Step 3: Fetch Company News

- Use LangChain’s Yahoo Finance integration to:
  - Retrieve the latest news articles for the identified stock ticker.
  - Extract a **concise list of headlines** or **article summaries**.

---

### Step 4: Analyze Sentiment with GPT-40 / GPT-40-mini

- Send the news summaries to GPT-40 or GPT-40-mini via LangChain.
- Prompt the LLM to:
  - **Classify overall sentiment** (Positive, Negative, Neutral).
  - **Extract named entities**:
    - People
    - Places
    - Other companies
    - Related industries
  - **Determine market implications** based on the sentiment.
- Use `Structured OutputParser` or `Pydantic OutputParser` to return the result in this structured JSON format:

```json
{
  "company_name": "",
  "stock_code": "",
  "newsdesc": "",
  "sentiment": "Positive/Negative/Neutral",
  "people_names": [],
  "places_names": [],
  "other_companies_referred": [],
  "related_industries": [],
  "market_implications": "",
  "confidence_score": 0.0
}
```

### Step 5: Integrate Langfuse

- Log prompts, outputs, and metadata using **Langfuse**.
- Add tracing spans for:
  - Stock code extraction
  - News fetching
  - Sentiment parsing