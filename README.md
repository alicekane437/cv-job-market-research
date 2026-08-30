# CV Job Market Research (Claude Skill)

Turn a CV into a structured, multi-region, bilingual-ready Excel research file of companies worth applying to — with real web research behind every row, not guesses.

Upload a CV (or just describe your target role), and this skill builds a professional spreadsheet covering:
- Companies you already have in mind (if you give it a list)
- An expanding search radius: your city → your country → remote-worldwide → your nearest relocation hub → further abroad
- A **fit score tied to your actual skills and projects**, not generic "do they hire fresh grads"
- Per-company salary estimates
- A ready-to-use shortlist with a concrete next action for each top match
- Full Arabic and/or English output, built correctly from the start

---

## Why this exists

Generic "find me companies to apply to" prompts tend to produce shallow, unstructured lists — a handful of company names with no verification, no way to compare them, and no sense of which ones are actually worth your time. This skill turns that into a repeatable, structured process: real per-company research, a consistent scoring method, and a spreadsheet you can filter, sort, and actually work from.

It was built and refined from real, repeated use — not written speculatively — including a full pass that added a fit-to-CV scoring column, restructured sheets after real feedback, and a deep-verification step after the first-pass research turned out to contain outdated or unconfirmed company details.

## What it produces

A workbook (or two, if you request both languages) with three sheets:

| Sheet | Purpose |
|---|---|
| **Quick Summary** | One row per company — name, source, region, fit, salary, primary contact. Built for fast filtering. |
| **Shortlist / Best Matches** | Only the strongest matches, ranked, each with a concrete next step ("apply via X," "follow on LinkedIn, don't apply yet — here's why"). |
| **All Companies** | The full dataset: website, address, LinkedIn, social media, services, tech focus, AI/specialty flag, fit reasoning, every email found (HR, main, manager, owner where available), current openings, internship requirements, salary range, and notes. |

Every sheet ships with a bold frozen header, autofilter, zebra striping, color-coding by region, sensible column widths, and correct right-to-left/left-to-right formatting for Arabic vs. English — no blank spacer rows, no half-finished formatting.

## How it works

1. **Intake** — asks (once, up front, and skips anything you've already answered):
   - Do you have a CV to upload, or should we work from a description instead?
   - Do you have specific companies/emails to check, or should everything come from search?
   - What role, field, or path are you targeting? (Traditional jobs and non-traditional paths — like continuing into a research/academic track — are both supported.)
   - Arabic, English, or both?
2. **CV extraction** (if provided) — pulls specialization, specific tools/frameworks, standout projects with their exact technical stack, education, and location. Confirms the detected location with you instead of assuming.
3. **Named-company research** (if you gave a list) — resolves each domain/email with real web search. Never invents an email, address, or contact name; explicitly marks anything that couldn't be verified.
4. **Tiered expansion search** — radiates outward: local city → rest of country → remote/worldwide → nearest relocation region → further abroad. Stops at any tier you say you're not interested in (e.g., skip relocation entirely).
5. **Fit scoring** — every company is scored against your *specific* skills and projects, not against how junior-friendly its hiring generally is. Each score comes with a one-line reason tied to something concrete in your background.
6. **Salary estimation** — a per-company range (not one blanket market number), adjusted for company size, funding, and local pay levels — clearly flagged as an estimate for negotiation purposes, not a quoted figure.
7. **Deep verification** — before final delivery, re-checks anything flagged as uncertain or estimated in the first pass. You're told plainly what was independently verified vs. what wasn't.
8. **Delivery** — saves the finished workbook(s) and hands them over with an honest summary of confidence levels.

## Requirements

- Runs inside Claude with file creation and web search enabled (Claude.ai, Claude Code, or the API with the equivalent tools).
- No external accounts or API keys needed — everything runs through Claude's built-in tools.

## Installation

1. Download `cv-job-market-research.skill` (or clone this repo).
2. Add it to your skills directory:
   - **Claude.ai**: upload via Settings → Skills.
   - **Claude Code**: place the unpacked folder in `~/.claude/skills/` (personal) or `.claude/skills/` (project-level).
3. Upload a CV (or describe your target role) and ask Claude to research companies for you — the skill activates automatically when it's relevant.

## ⚠️ Limitations & things to know before you rely on this

- **Salary figures are estimates, not quotes.** They're derived from company size, funding stage, and general market rates — useful for a negotiation starting point, not a guarantee. Never make a decision (like turning down an offer) based solely on a number in this sheet.
- **Not every company detail is independently verified.** The deep-verification step targets whatever was flagged as uncertain in the first research pass — for large company lists, re-checking every single row isn't practical. Treat unverified rows as a starting point for your own confirmation, not a final answer.
- **It can surface personal emails, not just HR inboxes.** When a company's only public contact is a named individual (e.g., a CTO's personal address), the skill will say so — but you're responsible for using that contact respectfully and appropriately.
- **Tested on a limited number of profiles so far.** It's been run end-to-end on a handful of real CVs across different fields and locations, with fixes applied based on that feedback. If you hit a rough edge on a profile type it hasn't seen yet (a very different field, a very different geography), please open an issue.
- **Web search quality varies by region and industry.** Less-documented companies (small local firms, personal-Gmail "companies") will inevitably have thinner, less certain data than well-known ones — the output says this explicitly rather than papering over the gaps.

## Contributing

Issues and pull requests are welcome — especially reports from profiles/fields/geographies this hasn't been tested against yet. If something produces a wrong or misleading result, please include the CV type (no need for the actual CV) and target region so the failure mode can be reproduced.

## License

MIT — use it, fork it, adapt it.
