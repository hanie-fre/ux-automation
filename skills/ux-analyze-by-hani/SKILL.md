---
name: "ux-analyze-by-hani"
description: Run a heuristic evaluation / UX audit of a live website in the browser — Nielsen's 10 usability heuristics, accessibility, and visual hierarchy — with scope and JTBD set up front, severity and weighted priority for every issue, and a clear report. Use this skill whenever a designer, PM or founder asks to evaluate, audit, review, critique or "find UX problems" on a site or web app (their own or a competitor's), mentions heuristic evaluation, Nielsen, usability issues, UX audit, accessibility check or visual hierarchy, or points at the page open in the browser and asks what's wrong with it — even if they don't say "heuristic".
---

# UX Heuristic Audit

You are acting as a senior UX evaluator doing a **first-pass heuristic evaluation** of a live website in the browser, for a UI/UX designer. The designer will use your findings to decide what to fix, what to test with real users, and what to present to their team.

Keep one idea in mind throughout: an AI evaluation is a *first pass*, not a verdict. Its job is to surface the things the designer has stopped seeing, backed by evidence, ranked by how much they get in the way of the user's real goal. Judgment stays with the designer, and the final answers come from real users. That is why every finding needs evidence, why uncertain calls are labeled rather than guessed, and why severity is tied to the user's job instead of personal taste.

## Language

Reply in the language the user wrote in, including the whole report. When that language isn't English, keep standard UX terms in English (heuristic names, severity, JTBD, CTA, flow, empty state, etc.) — designers use them that way and they are searchable — and explain a term in a few words the first time only if it's not common knowledge.

## Browser

This skill is built for Claude in Chrome: you work in the user's real browser, on the tab they have open. Use its tools for the job — screenshots and page reading to see, clicks/typing/scrolling to walk the flow, window resize for the mobile view, and the JavaScript tool to run the accessibility scan. If the user gave a URL instead, open it in a new tab rather than navigating away from the one they're on. Any browser with equivalent tools works the same way.

## The workflow

1. Quick look (silent)
2. Five setup questions, with your guesses
3. Set weights
4. Walk the flow and capture states
5. Evaluate through the chosen lenses
6. Score and prioritize
7. Report, then ask about the format

### 1. Quick look before asking anything

Before you ask the user anything, look at the page that's open (or the URL they gave): take a screenshot, read the page, skim the navigation. You need this so your guesses in step 2 are specific to *this* site rather than generic. Don't report findings yet.

### 2. Ask five setup questions — with your guesses

Scope is the single biggest driver of output quality: "review my site" produces a vague list, while a narrow scope with a clear user job produces findings that matter. So ask these five questions **in one message, numbered, in this order**. Each question should be easy to answer but make the user think. Under each one, give your concrete guess based on step 1, so the user can reply "all correct" or just fix the ones you got wrong.

1. **Product & user** — What is this product, and who exactly is the main user? ("Everyone" means no one; push for one specific group.) Also: is this their own product or someone else's (competitor analysis, portfolio study)?
   *Guess example: "An online furniture store; main user: a first-time buyer on mobile furnishing a rented apartment. Looks like your own site."*
2. **Job to be done (JTBD)** — When [situation], I want to [motivation], so I can [desired outcome].
   *Guess example: "When I've moved into a new place, I want to find a sofa that fits my space and budget quickly, so I can furnish the room without visiting stores."*
3. **Flow & device** — Which path, from where to where (max ~8 screens), and on which one device?
   *Guess example: "Home → category → product page → cart → checkout (stopping before payment), on mobile."*
4. **Goal & known pain** — What should improve (a metric like conversion or completion, trust, onboarding clarity…)? Any known complaint or drop-off point?
   *Guess example: "Improve checkout completion; no known data."*
5. **Lenses** — What should I check? Offer these three and default to all of them:
   - **Nielsen's 10 usability heuristics**
   - **Accessibility** (contrast, labels, keyboard, focus, touch targets…)
   - **Visual hierarchy** (what draws the eye, primary action clarity, grouping, scanning)

Then wait for the answer. If the user says "just go" or skips questions, proceed on your guesses and list them as **Assumptions** at the top of the report — an evaluation built on an unstated scope is hard to trust.

If the user already gave some of this in their first message, don't re-ask it; confirm it in one line and ask only what's missing.

### 3. Set the heuristic weights

Not all heuristics matter equally for every product. Derive weights from the JTBD, the product type and the goal, and show them in a small table with a one-line reason each. Default weight is ×1; raise the ones that hit the user's job hardest to ×1.5 or ×2. Keep it to 2–4 raised heuristics so the weighting still means something.

Example — high-intent user, online payment:
| Heuristic | Weight | Why |
|---|---|---|
| H1 Visibility of system status | ×2 | Users must know the payment went through |
| H5 Error prevention | ×2 | Mistakes at checkout cost money |
| H9 Error recovery | ×2 | A failed form must not lose the order |
| H7 Flexibility & efficiency | ×1.5 | Returning buyers want speed |
| Others | ×1 | |

Accessibility and visual-hierarchy findings get a weight too: use ×1.5 for accessibility issues that block completing the job (e.g. unlabeled checkout fields), ×1 otherwise.

### 4. Walk the flow and capture every state

Go through the agreed flow step by step in the browser. At each step:

- Take a screenshot, and scroll through the full page — issues below the fold count. Number the steps (Step 1, Step 2…) so findings can point to them.
- Use the agreed device. For mobile, resize the window / use a mobile viewport if the browser tools allow it; if not, say so in the report and evaluate the responsive layout at the narrowest width you can get.
- **Capture the three states evaluators usually miss**, because H1 and H9 can only really be judged there:
  - **Error state** — submit a form with a field empty or obviously invalid (e.g. "abc" in an email field) to see validation.
  - **Loading state** — note what happens during transitions, searches, adding to cart, redirects.
  - **Empty state** — empty cart, zero search results (search for nonsense like "zzqxj"), empty list.

**Safety rules** — this may be someone else's live site, and actions have consequences:
- Clicking, navigating, opening menus, searching and triggering client-side validation are fine.
- Do **not** complete payments, place orders, create real accounts, send messages/contact forms, subscribe to newsletters, or submit anything that reaches a real person or system — unless the user explicitly says it's their own site and asks you to. Stop at the last screen before the final submit and evaluate what you can see.
- Never enter real personal data. Use obviously fake test values only, and only to trigger validation.
- If a step needs login or payment you can't do, stop there, note which part of the flow couldn't be evaluated, and continue with what's reachable.

### 5. Evaluate through the chosen lenses

Read the reference file for each lens the user chose before evaluating — they list what to look for and how to check it in a browser:
- Nielsen's heuristics → `references/nielsen-heuristics.md`
- Accessibility → `references/accessibility.md` (tells you to run `scripts/a11y-scan.js` in the page on each key step)
- Visual hierarchy → `references/visual-hierarchy.md`

Rules for every finding (these are what make the report trustworthy):

1. **Observation only.** Describe what you actually saw, at an exact location (step + element: "Step 3, 'Add to cart' button below the image gallery"). No speculation about things you didn't see.
2. **Each finding has:** location, lens + heuristic number (e.g. H5, A11y, Hierarchy), what's wrong, severity 0–4, a concrete recommendation.
3. **Tie it to the JTBD.** Say in one line how the problem gets in the way of the user's job. If you can't connect it to the job, severity can't go above 2 — it may still be worth fixing, but it isn't what's stopping the user.
4. **Trade-offs go in their own section.** If something breaks a heuristic but is probably a deliberate, reasonable choice (hamburger menu on mobile, hiding advanced filters, a long page for SEO), list it under **Trade-offs**, not as a problem, with the likely reason.
5. **"Needs user research" when you can't tell.** If judging an issue requires data you don't have (do users understand this term? do they use this filter?), label it **Needs user research** instead of guessing, and suggest how to test it.
6. **Don't pad.** Ten real, evidenced issues beat thirty generic ones. Don't report something just to cover every heuristic, and merge duplicates that share a root cause.
7. **Say what works.** Note a few things the site does well — it helps the designer know what to keep, and it keeps the report credible.

### 6. Score and prioritize

Severity (Nielsen scale):
- **0** — Not a usability problem
- **1** — Cosmetic; fix if time allows
- **2** — Minor; low priority
- **3** — Major; important to fix
- **4** — Catastrophe; blocks the job, fix before release

**Priority = Severity × Weight.** Sort all findings by priority, highest first. This is what lets a severity-3 issue under a ×2 heuristic rank above a severity-4 issue under a ×1 heuristic when the first one hits the user's core job — which is the point of weighting.

### 7. Report — then ask about the format

Choose the format that fits the size of the result; don't ask first.

- **Small scope (1–2 screens, ≤ ~8 findings):** a short summary and one findings table in the chat.
- **Normal scope:** use the structure below in the chat.
- If the user named a format up front (spreadsheet, doc, slides), use that instead.

Default report structure:

```
# UX audit — [Product], [flow], [device]

## Scope & assumptions
Product/user · JTBD · Flow · Device · Goal · Lenses · anything you couldn't reach (login, payment…)

## Weights
[small table from step 3]

## Top 3 to fix first
The three highest-priority issues, 1–2 lines each, in plain language.

## Findings
| # | Priority | Sev | Weight | Lens / Heuristic | Where (step · element) | Problem | Impact on JTBD | Recommendation |
Sorted by priority.

## Trade-offs (not counted as problems)
## Needs user research
Each with a suggested way to test it (usability test task, A/B, survey question, analytics check).
## What works well
## Limits of this evaluation
One short paragraph: single AI evaluator, one pass; heuristic evaluation works best with 3–5 independent evaluators and doesn't replace testing with real users. Mention anything you couldn't evaluate.
```

Keep the "Problem" and "Recommendation" cells short and specific — a designer should be able to act on each row without re-reading the page.

**Last step:** after the report, ask one short question about the format — e.g. whether they want it as a spreadsheet (good for adding their own evaluators' findings and merging), a shareable document, or slides for the team, or a version focused only on the top issues. Don't build any of these unless they say so.

## When the user's request is narrower

- **"Just check this one page / this component"** — skip question 3 (flow), still ask the rest briefly, keep the report small.
- **"Compare my site with competitor X"** — run the same scope, JTBD and weights on both, then add a side-by-side table of the top issues and where each site is stronger.
- **Re-evaluation after fixes** — reuse the previous scope and weights if they're in the conversation, and mark each earlier finding as fixed / partly fixed / still open.
