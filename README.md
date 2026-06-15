<div align="center">

# 🎯 ATS Resume Scorer

**AI-powered resume analyzer that tells you exactly how well your resume matches a job description — and how to fix it.**

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-Streamlit-FF4B4B?style=for-the-badge)](https://ats-score-resume.streamlit.app/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Frontend-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)

[🔗 Try it Live](https://ats-score-resume.streamlit.app/) ·
</div>

---

## 📖 About the Project

**ATS Resume Scorer** helps job seekers understand exactly how an Applicant Tracking System (ATS) — and a recruiter — would view their resume against a specific job description.

Upload your resume, paste a job description, and get back:

- ✅ An overall **ATS Score** with a category-wise breakdown
- ✅ **Matched vs. missing keywords** from the job description
- ✅ **Semantic similarity** between your resume and the JD (not just keyword matching)
- ✅ **Skill validation** — are the skills you've listed actually backed up by your project/experience descriptions?
- ✅ **AI-generated suggestions** (powered by Groq/Llama 3) on exactly what to improve
- ✅ A **history** of all your past analyses, saved to your account
- ✅ A downloadable **PDF report** of your analysis

---

## ✨ Features

| Category | What it checks |
|---|---|
| 📐 **Formatting** | ATS-friendly structure, section headers, layout issues |
| 🔑 **Keywords** | Keyword overlap between resume and job description |
| 📝 **Content** | Quality and relevance of bullet points, action verbs, quantification |
| 🧠 **Skill Validation** | Whether listed skills are supported by real project/work evidence |
| 🤖 **ATS Compatibility** | File format, parseability, and other ATS-specific checks |
| 💬 **AI Suggestions** | LLM-generated, actionable feedback for each issue found |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | [Streamlit](https://streamlit.io/) |
| **Backend** | [FastAPI](https://fastapi.tiangolo.com/) (Python) |
| **NLP** | [spaCy](https://spacy.io/) (`en_core_web_md`), [Sentence Transformers](https://www.sbert.net/) (`all-MiniLM-L6-v2`) |
| **LLM** | [Groq API](https://groq.com/) (Llama 3) |
| **Auth + Database** | [Supabase](https://supabase.com/) (email/password & Google OAuth) |
| **PDF Reports** | WeasyPrint + Jinja2 |

---

## 📂 Project Structure

```
ATS_Score_Checker/
├── backend/              # FastAPI app, NLP services, API routes
│   ├── api/              # Routes & auth
│   ├── core/             # Config
│   ├── database/         # Supabase DB layer
│   ├── models/           # Pydantic schemas
│   ├── services/         # Scoring, parsing, matching, PDF export, LLM
│   ├── templates/        # HTML templates for PDF reports
│   └── utils/            # Helper utilities
├── frontend/             # Streamlit app
│   ├── components/       # Reusable UI components
│   ├── services/         # API client & Supabase client
│   └── views/            # Page views (landing, scorer, history, resources)
├── jupyter notebooks/     # Research & dataset prep (not used at runtime)
├── requirements.txt       # Combined backend + frontend dependencies
└── .env.example           # Template for environment variables
```

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/Cherry-Syrina/ATS_Score_Checker.git
cd ATS_Score_Checker
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
python -m spacy download en_core_web_md
```

WeasyPrint needs system libraries on Linux:

```bash
# Debian / Ubuntu
sudo apt install -y libcairo2 libpango-1.0-0 libpangoft2-1.0-0 libffi-dev

# Fedora
sudo dnf install -y cairo pango gdk-pixbuf2 libffi
```

### 3. Configure environment variables

```bash
cp .env.example .env
```

You'll need:

- A **Supabase** project → `SUPABASE_URL`, `SUPABASE_KEY` (service role), `SUPABASE_ANON_KEY`, `SUPABASE_JWT_SECRET`
- A **Groq** API key from [console.groq.com](https://console.groq.com)
- *(Optional)* Google OAuth configured in the Supabase dashboard

The Streamlit frontend also needs `frontend/.streamlit/secrets.toml` — copy from `secrets.toml.example` and fill it in.

### 4. Run the backend

```bash
uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
```

API will be live at `http://localhost:8000` (docs at `/docs`).

### 5. Run the frontend

```bash
streamlit run frontend/streamlit_app.py
```

App will open at `http://localhost:8501`.

---

## 📸 Screenshots
<img width="1727" height="905" alt="image" src="https://github.com/user-attachments/assets/eda2a93a-0969-4453-99ed-b95290c09489" />


---

## 🗺️ Roadmap

- [ ] Resume builder / template suggestions
- [ ] Multi-language resume support
- [ ] Bulk resume comparison for recruiters
- [ ] Browser extension for one-click scoring

Got an idea? [Open an issue](https://github.com/Cherry-Syrina/ATS_Score_Checker/issues)!

---

## 🤝 Contributing

Contributions are welcome! Feel free to fork this repo, open issues, and submit pull requests.

```bash
# 1. Fork & clone the repo
# 2. Create a new branch
git checkout -b feature/your-feature-name

# 3. Commit your changes
git commit -m "Add: your feature description"

# 4. Push and open a PR
git push origin feature/your-feature-name
```

---

## ⚠️ Notes

- **Never commit `.env` or `secrets.toml`** — they contain API keys and are listed in `.gitignore`.
- The first run downloads the Sentence Transformer model (~80 MB), cached afterwards.
- Without a Groq API key, scoring still works — only the AI suggestions section will be empty.
- `jupyter notebooks/` is for experimentation and isn't required to run the app.

---

<div align="center">

### Made with ❤️ by Sushma Shukla

</div>
