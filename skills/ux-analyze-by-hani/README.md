# ux-analyze-by-hani

Run a heuristic evaluation / UX audit of a live website in the browser — Nielsen's 10 usability heuristics, accessibility, and visual hierarchy — with scope and JTBD set up front, severity and weighted priority for every issue, and a clear report.

Use this skill whenever a designer, PM or founder asks to evaluate, audit, review, critique or "find UX problems" on a site or web app (their own or a competitor's), mentions heuristic evaluation, Nielsen, usability issues, UX audit, accessibility check or visual hierarchy, or points at the page open in the browser and asks what's wrong with it — even if they don't say "heuristic".

## What it does

1. Takes a quick silent look at the page/URL before asking anything.
2. Asks five setup questions (product & user, JTBD, flow & device, goal & known pain, lenses) — each with a guess the user can just confirm.
3. Sets weights per heuristic based on the job to be done.
4. Walks the flow in the browser, capturing error / loading / empty states.
5. Evaluates through the chosen lenses (Nielsen heuristics, accessibility, visual hierarchy).
6. Scores and prioritizes findings by `Severity × Weight`.
7. Produces a structured report, then asks about export format (spreadsheet, doc, slides).

## Requirements

- A browser tool with screenshot, click/type/scroll, resize, and JavaScript-execution capabilities (e.g. Claude in Chrome).

## Known gap

This skill references three supporting files that are **not yet included** in this folder:

- `references/nielsen-heuristics.md`
- `references/accessibility.md`
- `references/visual-hierarchy.md`
- `scripts/a11y-scan.js`

The exported `.skill` package only contained `SKILL.md`. Add these files under `references/` and `scripts/` here once available, or the skill will fall back to the model's own knowledge for those lenses instead of the intended reference material.

## Install

See the [root README](../../README.md) for install instructions (GitHub and skills.sh).
