# 📄 ATS Resume Checker

A Streamlit app that scores a resume for ATS (Applicant Tracking System) compatibility and gives specific, prioritized improvements, powered by Google's Gemini Flash model.

## Features

- Upload a resume as **PDF** or **DOCX**
- Optional **job description** for targeted keyword matching
- Overall **ATS score (0-100)** with section-by-section scores
- Keywords found vs. missing
- Formatting issues, strengths and prioritized improvements
- Download the full report as JSON

## Project structure

```
.
├── app.py             # Streamlit app
├── requirements.txt   # Python dependencies
└── README.md
```

## Run locally

1. Get a free Gemini API key at https://aistudio.google.com/apikey
2. Install and run:

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
export GEMINI_API_KEY="your-key" # Windows PowerShell: $env:GEMINI_API_KEY="your-key"
streamlit run app.py
```

You can also skip the environment variable and paste the key into the sidebar.

## Configuration

| Setting | How | Default |
|---|---|---|
| `GEMINI_API_KEY` | environment variable or Streamlit secret | none (sidebar input if missing) |
| `GEMINI_MODEL` | environment variable, or the sidebar field | `gemini-flash-latest` |

For local secrets, create `.streamlit/secrets.toml` (never commit it):

```toml
GEMINI_API_KEY = "your-key"
```

## Deploy on Streamlit Community Cloud

1. Push this repo to GitHub.
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, choose your repo, branch `main` and main file `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your-key"
   ```
5. Click **Deploy**.

## Notes and limitations

- Scanned (image-only) PDFs cannot be read. That is also true for most real ATS systems, so use a text-based PDF or DOCX.
- The score is an AI estimate, not the output of any specific ATS product. Treat it as guidance.
- Your resume text is sent to the Gemini API. Do not upload documents you are not comfortable sharing with Google.
