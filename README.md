# Chat With Database

This project provides an **AI-powered workflow** that lets you ask natural language questions about your database and get meaningful answers in real-time.
It is powered by **n8n**, **OpenAI (or any LLM API)**, and supports multiple database types such as **Postgres, MySQL, and SQLite**.

📄 The full workflow description is available in [`Chat with Database.pdf`](./Chat%20with%20Database.pdf).

---

## 🚀 Features

* 🔎 Query databases using **natural language** (English → SQL → Answer).
* 🛠️ Supports **Postgres, MySQL, and SQLite**.
* 🤖 Uses **OpenAI API** (or any LLM provider you choose) to generate SQL queries.
* 📊 Returns structured query results in an easy-to-read format.
* ⚡ Built with **n8n** for flexible automation and customization.

---

## 📂 Project Structure

```
Chat-With-Database/
├── README.md
└── Chat with Database.pdf   # Workflow documentation
```

---

## 🧑‍💻 How It Works

1. **User Input**

   * You enter a question in plain English (e.g., *"What were the top 5 products sold last month?"*).

2. **AI SQL Conversion**

   * The workflow uses OpenAI (or another LLM) to convert the natural language into a valid SQL query.

3. **Database Execution**

   * n8n executes the generated SQL query on your configured database.

4. **Answer Formatting**

   * The query results are returned as a structured, human-readable response.

---

## 🛠️ Setup

### Prerequisites

* [n8n](https://n8n.io/) installed locally or hosted.
* Database (Postgres/MySQL/SQLite).
* API key for **OpenAI** (or alternative LLM).

### Steps

1. Clone this repository:

   ```bash
   git clone https://github.com/your-username/chat-with-database.git
   cd chat-with-database
   ```

2. Open the [`Chat with Database.pdf`](./Chat%20with%20Database.pdf) to review the workflow design.

3. Recreate or import the workflow in your n8n instance.

4. Configure environment variables in n8n:

   ```
   OPENAI_API_KEY=your_api_key_here
   DB_TYPE=postgres        # postgres | mysql | sqlite
   DB_HOST=localhost
   DB_PORT=5432
   DB_USER=your_username
   DB_PASSWORD=your_password
   DB_NAME=your_database
   ```

5. Execute the workflow.

---

## 📝 Example Usage

**Question:**

> "Show me the total sales by customer in the last 7 days."

**Generated SQL (Postgres):**

```sql
SELECT customer_name, SUM(amount) as total_sales
FROM orders
WHERE order_date >= NOW() - INTERVAL '7 days'
GROUP BY customer_name
ORDER BY total_sales DESC;
```

**Response:**

```
1. Alice - $12,340  
2. Bob   - $ 9,580  
3. John  - $ 7,220  
```

---

## 🔧 Customization

* Replace **OpenAI** with another LLM provider (Anthropic, Gemini, Mistral, etc.).
* Extend support for additional databases by updating the SQL execution node.
* Add authentication for secure query execution.

---

## 🛡️ Security Notes

* Always validate and sanitize SQL queries before execution.
* Use **read-only database users** where possible.
* Restrict workflow access to trusted users.

---

## 🤝 Contributing

Pull requests are welcome! If you’d like to improve database coverage, optimize prompt engineering, or add features, feel free to open an issue or PR.

---



⚡ Built with [n8n](https://n8n.io/) and [OpenAI](https://platform.openai.com/).

