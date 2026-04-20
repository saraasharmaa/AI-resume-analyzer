# Resume Analyzer

A browser-based resume evaluation tool that works for **any job role**. Paste a resume and job description — get a structured, signal-based candidate analysis in seconds. No backend, no API keys, no setup required.

---

## Live Demo

Deploy it yourself in under 2 minutes — see [Deployment](#deployment) below.

---

## What It Does

This tool evaluates how well a resume matches a specific job description — for any role: engineering, product, design, sales, marketing, operations, finance, or anything else.

It scores candidates across 5 dimensions:

| Dimension | What it measures |
|---|---|
| **JD Relevance** | How well the resume matches the specific job description |
| **Execution & Output** | Evidence of delivering real work — projects, products, initiatives |
| **Real-world Impact** | Quantified outcomes — metrics, percentages, revenue, scale |
| **Skills Coverage** | Breadth of technical or domain skills mentioned |
| **Clarity & Communication** | Structure, action verbs, stakeholder and collaboration signals |

### Output
- Overall match score (0–100)
- Verdict: `Strong Match` / `Good Match` / `Partial Match` / `Low Match`
- Interview fit: `High` / `Medium` / `Low`
- JD keyword match — which keywords are present and which are missing
- Strengths, weaknesses, and actionable improvement suggestions
- Signal breakdown (action verbs, metrics, skills, comms signals detected)

---

## How It Works

The scoring engine runs entirely in the browser — no server, no API calls.

**JD Relevance (30% weight)** — extracts the top keywords from the job description (filtering out stop words) and checks how many appear in the resume. This makes the tool role-agnostic — it adapts to whatever JD you paste in.

**Execution & Output (20% weight)** — detects action verbs (`built`, `led`, `delivered`, `managed`, `spearheaded`, etc.), speed signals (`MVP`, `sprint`, `deadline`, `independently`), and project volume references.

**Real-world Impact (25% weight)** — detects quantified metrics (`50%`, `3x`, `$2M`, `200 users`, `10ms`) and outcome-oriented language (`reduced`, `increased`, `exceeded`, `secured`, `closed`).

**Skills Coverage (15% weight)** — detects a broad set of technical and domain skills across engineering, data, design, business, and operations.

**Clarity & Communication (10% weight)** — detects stakeholder management, cross-functional collaboration, mentoring, presenting, and documentation signals.

Scores are combined with these weights:
```
overall = jd_relevance   × 0.30
        + execution      × 0.20
        + impact         × 0.25
        + skills         × 0.15
        + clarity        × 0.10
```

---

## Getting Started

### Option 1 — Run locally (zero setup)

1. Download `index.html`
2. Double-click it — opens in any browser
3. Paste resume + JD, click **Analyze Resume**

### Option 2 — Deploy to Netlify (30 seconds)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop `index.html`
3. Get a live public URL instantly — no signup needed

### Option 3 — Deploy to GitHub Pages

1. Create a new GitHub repository (must be **public**)
2. Upload `index.html` to the root of the repo — must be named exactly `index.html`
3. Go to **Settings → Pages**
4. Set source branch to `main`, folder to `/ (root)`
5. Click **Save** — live at `https://yourusername.github.io/repo-name` in ~2 minutes

### Option 4 — Deploy to Vercel

```bash
npx vercel
```
Or drag the file into [vercel.com/new](https://vercel.com/new).

---

## File Structure

```
index.html    ← entire app (HTML + CSS + JS, single file, no dependencies)
README.md     ← this file
```

No npm install. No build step. No external libraries.

---

## Verdict Thresholds

| Score | Verdict | Interview Fit |
|---|---|---|
| 78 – 100 | Strong Match  | High          |
| 62 – 77  | Good Match    | High / Medium |
| 45 – 61  | Partial Match | Medium        |
| 0 – 44   | Low Match     | Low           |

---

## Customization

All logic lives in the `analyze()` function inside `index.html`. Easy to modify:

- **Add domain-specific skills** to the `techSkills` pattern array (e.g. `\\bhubspot\\b` for sales roles)
- **Change score weights** in the `overall` calculation
- **Adjust verdict thresholds** in the `verdict` line
- **Add new dimensions** by extending the `dims` array

---

## Limitations

- This is a **heuristic engine** — it uses pattern matching, not semantic understanding
- Works best when resumes use specific keywords, tools, and concrete numbers
- Heavily formatted resumes exported from PDF (tables, columns) may score lower due to reduced text signal density
- Use it as a first-pass filter or self-assessment tool — not a final hiring decision

---

## Use Cases

- **Hiring managers** — quick first-pass screening before manual review
- **Recruiters** — check resume-JD fit before sending to the hiring team
- **Job seekers** — self-assess your resume against a target JD and find gaps
- **Career coaches** — show clients exactly what's missing and what to add

---

## Built With

- Vanilla HTML, CSS, JavaScript
- Zero external dependencies
- Runs 100% in the browser

---

## License

MIT — free to use, modify, and deploy.
