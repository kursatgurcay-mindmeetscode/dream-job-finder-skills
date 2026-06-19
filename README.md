# Dream Job Finder — Claude Skills

**Author:** Kursat GURCAY  
**Adapted from:** Austin Belcak's "Dream Job Finder" prompt system

A set of three Claude skills that work together to help you systematically find, evaluate, and shortlist companies that match your ideal job criteria.

---

## How It Works

```
Skill 1: Criteria Interview
        ↓
  dream-job-criteria.md
        ↓
Skill 2: Scoring Methodology
        ↓
  company-scoring-methodology.md
        ↓
Skill 3: Dream Job Finder (Claude Cowork)
        ↓
  Ranked shortlist of companies + open roles
```

---

## Skills

### Skill 1 — `dream-job-criteria`

An interactive career clarity interview. Claude plays the role of an executive career coach and asks 10–15 deep questions across categories like compensation, culture, management, flexibility, and growth.

It won't accept vague answers — if you say "I want a supportive manager," it will push back and ask you to define what that actually means to you, with real examples.

**Output:** A `dream-job-criteria.md` file with 15–20 specific, prioritized criteria.

---

### Skill 2 — `dream-job-scoring`

Takes your criteria and builds a weighted scoring rubric (0–100 scale) for evaluating any company.

**Output:** A `company-scoring-methodology.md` file that Claude can use autonomously to score companies.

---

### Skill 3 — `dream-job-finder`

A research agent (best run in Claude Cowork with web search) that:

1. Searches LinkedIn, Greenhouse, Lever, Ashby, Built In, Wellfound, and the open web for companies with matching open roles
2. Scores each company using your scoring methodology
3. Returns a ranked shortlist of 10–15 companies that scored 70+/100
4. Learns from your feedback via a persistent `decision-log.md`

---

## Installation

### Option A — Claude Cowork

1. Copy the three `.md` files from the `skills/` folder into your Claude Cowork folder
2. Run each skill in order by pasting the contents into a Claude.ai chat

### Option B — Claude Code

1. Copy the skill files to `~/.claude/skills/`
2. Invoke each skill with `/dream-job-criteria`, `/dream-job-scoring`, `/dream-job-finder`

---

## Workflow

**Step 1:** Run `dream-job-criteria` skill → save output as `dream-job-criteria.md`

**Step 2:** Run `dream-job-scoring` skill, paste your criteria → save output as `company-scoring-methodology.md`

**Step 3:** Create an empty `decision-log.md` file

**Step 4:** Run `dream-job-finder` skill in Claude Cowork (with web search enabled). Make sure all three files above are in your Cowork folder.

**Step 5:** After each run, give feedback. Claude will ask if you want to save it to `decision-log.md` — say yes, and future runs will get smarter.

---

## Requirements

- Claude.ai account (Pro recommended for Claude Cowork)
- Web search enabled in Claude Cowork (for Skill 3)

---

## License

MIT — free to use, adapt, and share.
