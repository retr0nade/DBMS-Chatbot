
# 💬 DBMS Chatbot

An intelligent chatbot that can understand, answer, and explain a wide range of topics in **Database Management Systems (DBMS)** — including SQL, MongoDB, PL/SQL, and more. Powered by modern large language models and hosted on an interactive notebook platform, this chatbot is your academic TA and coding partner — all in one.

## 📚 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Setup Instructions](#-setup-instructions)
- [Usage](#-usage)
- [Example Queries](#-example-queries)
- [Limitations](#-limitations)
- [To-Do](#-to-do)
- [License](#-license)



---

## 🌟 Features

- ✅ Ask DBMS theory questions (e.g., normalization, transaction ACID properties, ER models)
- ✅ Solve SQL and MongoDB queries with syntax explanations
- ✅ Support for:
  - `MySQL`, `PostgreSQL`, `PL/SQL`, `MongoDB`
- ✅ Handles complex queries and explains step-by-step
- ✅ Ideal for students, job prep, and college viva
- Note: Might hallucinate sometimes

---

## 🛠️ Tech Stack

| Layer          | Technology                             |
|----------------|----------------------------------------|
| Backend Logic  | Python (OpenAI/Gemma/Mistral model)    |
| Interface      | Jupyter Notebook / Kaggle / Colab      |
| NLP Model      | ChatGPT / Gemini / Llama / Mistral     |
| Database Logic | Prompt-engineered query parser         |
| Extensions     | Markdown rendering, Code formatting    |

---

## 🧑‍💻 Setup Instructions

1. **Clone the repo** or download the notebook:
   ```bash
   git clone https://github.com/your-username/dbms-chatbot.git
   cd dbms-chatbot
   ```

2. **Install required packages** (recommended inside a virtual environment):
   ```bash
   pip install -r requirements.txt
   ```

3. **API Setup**:
   - Get API key from OpenAI, Gemini, or your preferred provider.
   - Add to `.env` or directly in notebook:
     ```python
     import os
     os.environ["OPENAI_API_KEY"] = "your-key-here"
     ```

4. **Run the notebook**:
   - Open `dbms_chatbot.ipynb` in Jupyter, Colab, or Kaggle
   - Run all cells to start chatting!

---

## 💡 Usage

You can ask the chatbot:

> 🧠 *"Explain the difference between primary key and foreign key."*  
> 🧮 *"Write a SQL query to find all employees with a salary above average."*  
> 📦 *"How does MongoDB handle joins?"*  
> 📈 *"Can you convert this SQL query to MongoDB aggregation?"*

The chatbot responds with detailed explanations and formatted code blocks!

---

## 💬 Example Queries

```sql
-- SQL
SELECT name FROM Students WHERE marks > (SELECT AVG(marks) FROM Students);

-- MongoDB
db.students.aggregate([
  { $group: { _id: null, avgMarks: { $avg: "$marks" } } },
  { $lookup: {
      from: "students",
      pipeline: [
        { $match: { $expr: { $gt: ["$marks", "$$avgMarks"] } } }
      ],
      as: "aboveAverageStudents"
    }
  }
])
```

---

## ⚠️ Limitations

- Requires internet for API-based LLMs
- Not connected to a live database (currently text-based simulation)
- May hallucinate syntax/theory if asked something obscure or unsupported

---

## 🧠 To-Do

- [ ] Add support for live SQL execution using SQLite or Postgres
- [ ] GUI frontend using Streamlit or Flask
- [ ] Conversation memory for follow-up queries
- [ ] Upload schema or table for context-aware querying

---

## 📄 License

Feel free to use, improve, and share!

---
