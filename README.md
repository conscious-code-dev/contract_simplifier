# 📜 Contract Simplifier API

A **production-ready LangChain v0.3 + FastAPI** project that simplifies legal contracts into plain English.
Built with **modern Python tooling (Poetry, Pydantic v2, src layout)**, tested with `pytest`, and deployed on [Render](https://render.com).

---

## 🚀 Features

* **LangChain v0.3** with LCEL composability (`prompt | llm`)
* **FastAPI** REST endpoints:

  * `GET /health` → Service status check
  * `POST /simplify` → Simplifies legal contract text
* **Poetry** project management with modern `pyproject.toml` (PEP 621)
* **Pydantic v2** request validation (rejects empty/bad input)
* **pytest** automated tests for endpoint verification
* Cloud-ready with **render.yaml** (no Docker required)
* Secure configuration via `.env` + `python-dotenv`

---

## 📂 Project Structure

```plaintext
contract_simplifier/
├── pyproject.toml
├── README.md
├── .gitignore
├── .env                # not committed, contains secrets
├── render.yaml         # deployment config for Render
├── src/
│   └── contract_simplifier/
│       ├── api/
│       │   └── main.py
│       └── chains/
│           └── simplify_contract.py
└── tests/
    └── test_contract_api.py
```

---

## 🛠️ Local Setup

### 1️⃣ Clone & Install

```bash
git clone https://github.com/<your-username>/contract-simplifier.git
cd contract-simplifier
poetry install
```

### 2️⃣ Configure Environment

Create a `.env` file in the root:

```env
OPENAI_API_KEY=sk-your-key-here
```

### 3️⃣ Run Tests

```bash
poetry run pytest -v
```

### 4️⃣ Start the API Locally

```bash
poetry run uvicorn src.contract_simplifier.api.main:app --reload
```

Visit Swagger UI: [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 🌐 Deployment

This project is ready for **Render** deployment.

1. Push your repo to GitHub
2. Create a new **Web Service** on Render
3. Use:

   * **Build Command**: `poetry install --no-root`
   * **Start Command**:
     `poetry run uvicorn src.contract_simplifier.api.main:app --host 0.0.0.0 --port 10000`
4. Add environment variables (like `OPENAI_API_KEY`) in Render's dashboard

See [`render.yaml`](render.yaml) for full config.

---

## 🧪 Example Request

```bash
curl -X POST http://localhost:8000/simplify \
-H "Content-Type: application/json" \
-d '{"contract_text": "The lessee shall indemnify the lessor from all claims..."}'
```

**Response:**

```json
{
  "simplified_text": "The renter will protect the owner from any claims..."
}
```

---

## 🎯 Use Cases

* **Legal tech startups** needing contract simplification APIs
* **AI-powered document assistants**
* **Educational demos** of LangChain v0.3 + FastAPI best practices

---

## 📜 License

MIT License — free to use and modify.

---

## 🤝 Contributing

Pull requests welcome! If you find bugs or want features, open an issue.

---

## ⭐ Acknowledgements

* [LangChain](https://www.langchain.com/) — composable AI chains
* [FastAPI](https://fastapi.tiangolo.com/) — blazing fast Python APIs
* [Render](https://render.com/) — easy cloud deployment

---


