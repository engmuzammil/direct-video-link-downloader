# Direct Video Link Downloader (Blogger + FastAPI Backend)

Works only for **direct video file links**: `.mp4 .webm .mov .mkv`
Not for YouTube/TikTok/Instagram/Facebook links.

## Repo folders
- `backend/` FastAPI API (deploy on HuggingFace Spaces Docker)
- `frontend/` Simple static website (optional, can host anywhere)
- `blogger/` Paste-ready embed snippet for Blogger

---

## Backend Deploy (FREE) on HuggingFace Spaces (Docker)

### 1) Create Space
- New Space
- SDK: Docker

### 2) Important
HuggingFace Docker Space expects `Dockerfile` at the repository root **of the Space**.

Recommended: create a separate HF Space repo that contains only backend files:
- `main.py`
- `requirements.txt`
- `Dockerfile`
- `.dockerignore`

So when you deploy to HF, copy contents of `backend/` into the Space repository root.

### 3) Space Settings → Variables and secrets
Set:
- `CORS_ORIGINS` = `https://webstore381.blogspot.com`
- `APP_SECRET` = random strong string

### 4) Test
Open:
- `https://<username>-<space>.hf.space/docs`

---

## Blogger Embed
Use `blogger/blogger-embed.html` and set:
`API_BASE = "https://<username>-<space>.hf.space"`

Paste into:
- Blogger → Pages → New Page → HTML view
OR
- Blogger → Layout → HTML/JavaScript gadget

---

## Local Backend Run (optional)
```bash
cd backend
python -m venv .venv
# activate venv
pip install -r requirements.txt
uvicorn main:app --reload --port 8000