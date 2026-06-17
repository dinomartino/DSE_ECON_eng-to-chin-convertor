# Economics Prompt Builder · EN → 繁中

A fully static web page that turns English economics text into a **glossary-grounded
translation prompt** you can copy & paste into any chatbot (ChatGPT, Gemini, Claude, …).

Unlike the original Flask app, this version does **not** call an LLM itself — it has no
backend and no API keys. All glossary matching happens in the browser.

## How it works

1. You type English economics text.
2. The page scans it against the [HKSAR Economics Glossary](https://www.edb.gov.hk)
   (1,320 official EN → Traditional Chinese terms, stored in `glossary.json`) and shows
   every matching term, longest match first.
3. Click **Build Translation Prompt** to assemble a prompt that injects those terms as
   terminology guidance, followed by your text.
4. Copy the prompt into your chatbot of choice to get the translation.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The entire app (HTML + CSS + JS). |
| `glossary.json` | The 1,320-term glossary (`{ meta, entries }`). |
| `vercel.json` | Minimal Vercel config (`cleanUrls`). |

## Deploy to Vercel

This is a zero-config static site.

**Option A — Vercel dashboard**
1. Push this folder to a Git repo (or drag-and-drop the folder in the dashboard).
2. Import the project in Vercel. No framework, no build command, no output dir needed.
3. Deploy.

**Option B — Vercel CLI**
```bash
npm i -g vercel        # if not installed
cd vercel-app
vercel                 # follow prompts, accept defaults
vercel --prod          # promote to production
```

## Run locally

It must be served over HTTP (the page fetches `glossary.json`):
```bash
cd vercel-app
python3 -m http.server 8000
# open http://localhost:8000
```
