# PubMed Pulse — Evidence Dashboard

A personal health-science dashboard that scans PubMed for recent research and lets you fact-check health claims with AI-powered summaries.

## Features

- **Weekly Digest**: Scans the last 7 days of PubMed across 7 health topics (nutrition, exercise, longevity, disease prevention, mental health, skin health, hormonal balance). Returns an AI briefing with evidence tiers, limitations, and practical takeaways.
- **Search & Fact-Check**: Search any molecule, ingredient, or health topic. Returns tiered results (Tier 1 → Tier 2 → Tier 3 fallback) with an AI summary that states what the evidence actually shows — and what it doesn't.

## Evidence Tiers

| Tier | Label | Includes |
|------|-------|----------|
| 1 | Gold Standard | Systematic Reviews, Meta-Analyses, RCTs |
| 2 | Strong Evidence | Clinical Trials, Observational Studies, Comparative Studies |
| 3 | Exploratory | In vitro, animal studies, case reports, narrative reviews |

Tier 1 and 2 are searched first. Tier 3 only appears if both are empty.

## Setup — GitHub Pages

### 1. Create a GitHub repository

1. Go to [github.com/new](https://github.com/new)
2. Name it something like `pubmed-pulse` (or anything you want)
3. Set it to **Public** (required for free GitHub Pages)
4. Click **Create repository**

### 2. Upload the files

**Option A — GitHub web interface (easiest)**:
1. On the repo page, click **Add file → Upload files**
2. Drag the entire contents of this `PUBMED` folder (both `index.html` and `README.md`)
3. Click **Commit changes**

**Option B — Git command line**:
```bash
cd ~/Desktop/PUBMED
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/pubmed-pulse.git
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages** (left sidebar)
2. Under **Source**, select **Deploy from a branch**
3. Select branch: **main**, folder: **/ (root)**
4. Click **Save**
5. Wait 1–2 minutes — your dashboard will be live at:
   `https://YOUR_USERNAME.github.io/pubmed-pulse/`

### 4. Add your API keys

1. Open the dashboard URL in your browser
2. Click the **⚙** (gear icon) in the top-right corner
3. Paste your **OpenAI API key** (required)
4. Paste your **NCBI API key** (optional but recommended)
5. Click **Save**

Keys are stored in your browser's localStorage — they never leave your machine except to call the respective APIs directly.

## Getting your API keys

### OpenAI
1. Go to [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
2. Click **Create new secret key**
3. Copy and paste into the dashboard settings

### NCBI (PubMed)
1. Go to [ncbi.nlm.nih.gov/account](https://www.ncbi.nlm.nih.gov/account/) and log in (or create an account)
2. Go to **Settings** → **API Key Management**
3. Click **Create an API key**
4. Copy and paste into the dashboard settings

The NCBI key raises the rate limit from 3 to 10 requests/second. Without it the dashboard still works, just slower on the weekly digest.

## Cost estimate

Using `gpt-4o-mini` (the default):
- Weekly digest: ~$0.01–0.03 per run
- Each search: ~$0.005–0.01

With `gpt-4o`: roughly 10× more. Stick with `gpt-4o-mini` for daily use.

## Privacy

- No backend, no server, no database
- API keys stored only in your browser's localStorage
- PubMed queries go directly to NCBI's public API
- AI summaries go directly to OpenAI's API
- GitHub Pages serves the static HTML file — it never sees your keys or queries
