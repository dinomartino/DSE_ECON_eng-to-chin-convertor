# DSE Prompt Builder · 英 ⇄ 繁中

A fully static web page that turns your text into a **glossary-grounded translation
prompt** you can copy & paste into any chatbot (ChatGPT, Gemini, Claude, …).

There is **no backend and no API key** — all glossary matching happens in the browser.

## Features

- **Five subjects** — pick from the toggle bar at the top:
  | Subject | Glossary | Terms |
  |---------|----------|-------|
  | 經濟 Economics | `glossaries/economics.json` | 1,320 |
  | 公經社 Citizenship, Economics & Society | `glossaries/ces.json` | 1,784 |
  | 地理 Geography | `glossaries/geography.json` | 4,351 |
  | 歷史 History | `glossaries/history.json` | 6,252 |
  | 旅遊與款待 Tourism & Hospitality | `glossaries/ths.json` | 2,505 |
- **Two directions** — toggle between **英文 → 繁體中文** (default) and **繁體中文 → 英文**.
- All glossaries are the official HKSAR (Education Bureau, CDI) English–Chinese
  glossaries. Geography includes the July 2025 amendments.

## How it works

1. Choose a **subject** and a **direction**.
2. Type your text. The page scans it against the selected glossary and shows every
   matching term, longest (most specific) match first.
   - **英 → 中** scans your English for glossary terms.
   - **中 → 英** scans your Chinese for glossary translations (each entry may list
     several synonyms separated by `/ ／ ； ；，` — any of them can match).
3. Click **建立翻譯 Prompt** to assemble a prompt that injects the matched terms as
   terminology guidance, followed by your text.
4. **複製提示** and paste it into your chatbot of choice.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The entire app (HTML + CSS + JS). |
| `glossaries/*.json` | One `{ meta, entries }` glossary per subject. |
| `glossary.json` | Legacy economics glossary (kept for backward compatibility). |
| `vercel.json` | Minimal Vercel config (`cleanUrls`). |

## Deploy to Vercel

Zero-config static site.

**Dashboard:** push this folder to a Git repo (or drag-and-drop in the dashboard),
import the project, no framework / build command / output dir needed, deploy.

**CLI:**
```bash
npm i -g vercel
cd "Eng to Chin_Vercel"
vercel          # accept defaults
vercel --prod
```

## Run locally

Must be served over HTTP (the page fetches the JSON glossaries):
```bash
cd "Eng to Chin_Vercel"
python3 -m http.server 8000
# open http://localhost:8000
```
