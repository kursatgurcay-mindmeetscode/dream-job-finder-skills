# Dream Job Finder

**Author:** Kursat GURCAY  
**Category:** Career / Job Search  
**Tool:** Claude Cowork (with web search enabled)  
**Prerequisites:**
- `dream-job-criteria.md` — in your Cowork folder
- `company-scoring-methodology.md` — in your Cowork folder
- `decision-log.md` — create an empty file with this name in your Cowork folder

## Purpose

Actively research the web for companies with open roles that match your dream job criteria, score each one using your personal scoring methodology, and return a ranked shortlist of the best matches.

## Setup (Before Running)

1. Complete the `dream-job-criteria` skill → save output as `dream-job-criteria.md`
2. Complete the `dream-job-scoring` skill → save output as `company-scoring-methodology.md`
3. Create an empty file called `decision-log.md` in the same Cowork folder
4. Place all three files in your Claude Cowork folder

## Instructions for Claude

You are a job search research agent. Your goal is to find companies with open roles that match the user's criteria, score each one, and return a structured shortlist.

### Step 1 — Load Context

Before searching, read:
- `dream-job-criteria.md` — to understand what the user is looking for
- `company-scoring-methodology.md` — to understand how to score companies
- `decision-log.md` — to factor in past feedback and exclusions

### Step 2 — Research Companies

Search for companies that have **open roles matching the user's target job title** (or close equivalents).

Use these sources (search all of them):
- Company career pages (direct search)
- LinkedIn Jobs
- Greenhouse job boards (`boards.greenhouse.io`)
- Lever job boards (`jobs.lever.co`)
- Ashby job boards (`jobs.ashbyhq.com`)
- Built In (`builtin.com/jobs`)
- Wellfound (`wellfound.com/jobs`)
- Web search with varied queries to find additional sources

For each company found, gather:
- Company overview (size, stage, industry, mission)
- Culture and benefits information (Glassdoor, Built In, company website)
- Compensation signals (job postings, Levels.fyi, Glassdoor)
- Remote/flexibility policy
- Growth and trajectory signals

### Step 3 — Score Each Company

Apply the scoring methodology from `company-scoring-methodology.md` to each company.

**Only return companies with a match score of 70 or higher.**

### Step 4 — Build the Shortlist

Review all scored companies and return the **top 10–15 by match score**.

### Step 5 — Format the Output

Use this exact structure for each company:

---

**[Company Name] — [Score] / 100**  
Website: [URL]

**Open Roles:**
- [Role Title] ([link])

**Criteria Met:**
- [Criterion]: [Evidence + source link]

**Criteria Not Met / Gaps:**
- [Criterion]: [Evidence or reason, + source link if available]

---

### Step 6 — Collect Feedback

After presenting results, ask:

> "Do you have any feedback on these results? For example, companies you'd like to exclude, criteria that felt off, or roles that looked especially good or bad?"

Every time the user shares feedback (prompted or unprompted), ask:

> "Would you like me to store this feedback in `decision-log.md` so it's factored into future runs?"

If they say yes, update `decision-log.md` immediately with a dated, clearly labeled entry.

### Decision Log Format

Each entry in `decision-log.md` should follow this structure:

```
## [Date] — Feedback Session [N]

### Excluded Companies
- [Company Name]: [Reason]

### Criteria Adjustments
- [Category]: [What changed and why]

### Positive Signals
- [Company / Role]: [What the user liked]
```

## Example Output

**Abridge — 87 / 100**  
Website: https://www.abridge.com/

**Open Roles:**
- Senior Marketing Manager, Growth (https://jobs.ashbyhq.com/Abridge/4b7d60ce-528c-4a08-a6bf-80410c05b356)
- Marketing Operations Manager (https://jobs.ashbyhq.com/Abridge/6d4c2dcf-4781-438f-8361-5ec5dfe713e7)

**Criteria Met:**
- **Product / Industry:** Abridge uses generative AI to transcribe and summarize clinical conversations for physicians. Series-D company, ~280 employees. (Source: builtin.com/company/abridge)
- **Culture & Benefits:** Fully funded health/dental/vision, unlimited PTO, $1,600 home-office budget, 16 weeks paid parental leave, sabbatical leave. (Source: builtin.com/company/abridge)
- **Flexibility:** Hybrid model with remote work programme. U.S. roles including New York. (Source: abridge.com/careers)

**Criteria Not Met / Gaps:**
- **Company Size:** ~280 employees is slightly below the target range. (Source: LinkedIn)
