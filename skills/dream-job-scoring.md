# Dream Job Company Scoring Methodology

**Author:** Kursat GURCAY  
**Category:** Career / Job Search  
**Tool:** Claude.ai (or Claude Code)  
**Prerequisite:** Run `dream-job-criteria` skill first and have `dream-job-criteria.md` ready.

## Purpose

Transform the personalized dream job criteria into a structured, weighted scoring methodology that can objectively rate any company on a 0–100 scale. The output feeds directly into the Dream Job Finder skill.

## Instructions for Claude

The user will paste the output from the Dream Job Criteria assessment (contents of `dream-job-criteria.md`).

Your task is to analyze all criteria and produce a **detailed scoring methodology** with the following components:

### 1. Category Weights

Assign a percentage weight to each criteria category based on the user's stated priorities. Weights must sum to **100%**. Higher priority categories get higher weights.

Example structure:
| Category | Weight |
|---|---|
| Compensation | 20% |
| Management Style | 15% |
| Company Culture | 15% |
| … | … |

### 2. Scoring Rubric Per Category

For each category, define a **0–10 scoring scale** with clear descriptions at each level:

- **9–10:** Exceeds criteria — all specific requirements are demonstrably met
- **7–8:** Meets criteria — most requirements are met with minor gaps
- **5–6:** Partially meets criteria — some requirements met, notable gaps exist
- **3–4:** Mostly doesn't meet criteria — significant misalignment
- **0–2:** Fails criteria — strong misalignment or no evidence available

### 3. Match Score Formula

```
Category Score (out of 100) = (Raw score / 10) × Category Weight × 100
Total Match Score = Sum of all Category Scores
```

### 4. Evidence Guidelines

For each category, list **specific signals** the researcher should look for when evaluating a company. Examples:

- **Compensation:** Salary ranges in job postings, Levels.fyi data, Glassdoor reports, equity mention
- **Culture:** Glassdoor reviews, Built In profiles, employee LinkedIn posts, press coverage
- **Flexibility:** Job posting keywords (remote/hybrid/async), company policy pages

### 5. Scoring Threshold

- **70+ / 100:** Strong match — include in final results
- **50–69 / 100:** Partial match — flag for manual review
- **Below 50:** Poor match — exclude

### Output Format

Save the output as both:
- Plain text in the conversation
- A markdown file called **`company-scoring-methodology.md`**

The file must be self-contained so that anyone (or an AI agent) can pick it up cold and score a company without needing additional context.
