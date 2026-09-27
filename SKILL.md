---
name: "superb-prompt"
description: "Build or fix a prompt that names its reader and asks for one insight: the five-part framework (role, task, context, constraints, format), five prompt types (summarize, role-based, reformat, compare, evaluate), and the superb test every prompt must pass before it goes out. Use when Natalia asks for a prompt, asks why a prompt isn't working, wants to compare answers to the same prompt across AI platforms, or asks where AI fits in her roles. For prompts she will paste into an AI — not for creating skills (that is skill-creator)."
---

# Superb prompt

Based on "Prompting as the New Literacy" (Steven Johnson). A strong prompt turns what is in your head into instructions the AI can act on. Write it in plain language. The framework is a guide, not a rulebook: aim for a clear prompt, not a perfect one, so that the AI has nothing important left to guess.

A good prompt gets a correct answer. A superb prompt also gets an answer that is **written for a named reader** and **tells that reader something they didn't already know**. Every prompt this skill writes does both.

## The five parts

| Part | Question it answers | Example |
|---|---|---|
| 1. Role | Who should the AI be? | "You are a public health communications strategist specializing in behavioral health campaigns." |
| 2. Task | What exactly do I need? | "Develop a campaign concept that reduces stigma and increases awareness of free resources." |
| 3. Context | Who is it for, why, and what facts matter? (audience, purpose, channels, background, source material) | "Audience: 18–35-year-olds. The state has a 24/7 hotline, but awareness is low. Must work on billboards, radio, social, schools, clinics." |
| 4. Constraints | What must it do or avoid? (tone, length, accuracy rules, what not to say) | "Hopeful, supportive. Avoid triggering language; never imply someone is 'broken' or 'dangerous.'" |
| 5. Format | What should the output look like? | "Three concepts, each with a tagline and a 2–4 sentence explanation." |

## Two additions that make a prompt superb

### A. Name the audience (always)
Say who will read or use the output, in a way that changes how the AI writes: their title, what they already know, and what decision they face. "For leadership" is weak. "For a health plan Chief Dental Officer deciding which coordination program to fund next year" is strong.

Natalia's usual audiences:

| Audience | What they care about | Tone |
|---|---|---|
| Payers (health plan dental and medical leaders) | Cost, ROI, member outcomes, operational burden | Executive, numbers first |
| Policymakers (CMS, state Medicaid, Congress staff) | Statutory authority, budget impact, equity, feasibility | Neutral, precise, sourced |
| Federal agencies (FDA, VA, DHA) | Regulatory accuracy, requirements alignment, evidence | Formal, compliance-minded |
| Clinicians (dentists, physicians, medical teams) | Evidence quality, workflow, patient benefit | Clinical, peer-to-peer |
| Health-tech and AI audiences | Performance, validation, integration, adoption | Crisp, concrete |
| Overjet leadership | Strategy, market timing, risk, competitive position | Direct, decision-oriented |
| Researchers and reviewers | Methods, validity, novelty | Scholarly |
| Parents and patients | Clarity, reassurance, what to do next | Warm, plain, 6th-grade reading level |

### B. Ask for one insight (the "so what")
End the prompt with one request that pushes past a summary into judgment. Choose the one that fits the type:

| Type | Insight requests (pick one) |
|---|---|
| Summarize | "…and flag the one [finding/provision] most likely to change [X]." · "…and note what is surprising or missing." |
| Role-based | "…and end with the question this reader is most likely to push back on, and how to answer it." · "…and state the one decision this should prompt." |
| Compare | "…and say which option is best for [GOAL] and why." · "…and name the trade-off that matters most." |
| Evaluate | "…and name the single change that would most improve it." · "…and rank the risks by likelihood and impact." |
| Reformat | **No insight request.** A formatting prompt changes only the layout. Add nothing that invites rewriting or analysis. |

One insight request per prompt. Several at once dilute the answer.

## The five prompt types

First identify which type the request is. Then make sure the prompt includes that type's must-haves.

| Type | Must include | Template |
|---|---|---|
| Summarize | The word "summarize"; what to include (key points, findings, conclusions); the format; the audience; one insight | "Summarize [CONTENT] for [AUDIENCE] by highlighting [WHAT TO INCLUDE] in [FORMAT], and flag [INSIGHT]." |
| Role-based | A named role ("You are…" / "Act as…"); who it is for or how it will be used; one insight | "Act as [ROLE] and draft [OUTPUT] for [AUDIENCE + THEIR DECISION], covering [ELEMENTS], and end with [INSIGHT]." |
| Reformat | Exactly how to lay it out; change only the format, not the content; a single instruction; who will use it (optional) | "Convert the following [TEXT] into [STRUCTURE], [RULE], without changing any wording." |
| Compare / contrast | The word compare, contrast or differences; at least two named items; the dimensions; the audience; one insight | "Compare [A] and [B] for [AUDIENCE] and explain the key differences in [DIMENSIONS] in [FORMAT], and say which is best for [GOAL] and why." |
| Evaluate | The word evaluate, assess or review, or "pros and cons"; one named thing; the criteria; the evaluator's perspective; one insight | "Evaluate [THING] from the perspective of [READER] and identify its strengths, weaknesses and risks based on [CRITERIA], and name the single change that would most improve it." |

Many real tasks combine types, for example a role-based prompt that asks for an evaluation. Include the must-haves of each type used.

## Mode A: build a prompt from a rough request

1. **Extract.** Fill in the five parts from what she said, the files she attached, and what you know of her work (Overjet; Medicare and Medicaid; dental–medical integration; research). Never invent facts. Put [BRACKETS] around any placeholder she needs to fill in.
2. **Pick the prompt type(s)** and check the must-haves.
3. **Name the audience** using the audience table: who they are, what they know, what they will decide.
4. **Add one insight request** from the insight table (skip it for reformat prompts).
5. **Ask only what is missing and matters.** If a guess about audience, purpose or format would change the output, ask up to 3 short questions in one AskUserQuestion call. Otherwise, choose sensibly and say which choice you made.
6. **Add a technique only when the task calls for one:**
   - Facts, numbers, citations or policy → "Use only [SOURCES]; cite and link each claim; say 'not found' rather than guess."
   - Analysis or recommendations → "Explain your reasoning step by step."
   - A specific style or layout → few-shot: give one short example of the output.
   - An uncertain direction → "Give three distinct versions so I can compare."
   - A big job → numbered steps.
7. **Choose the length:**
   - **Quick** (1–2 sentences): for a single clear ask, or when she asks for a short prompt. It must still carry the task, what to include, the format, the audience and one insight.
   - **Full**: two versions. A structured version (five labeled parts) and a narrative version (2–3 paragraphs). Put each in a code block.
8. **Run the superb test** (below) and fix any ✗ before showing her.
9. **Pre-empt weak output.** Give 2–3 ready-to-send follow-up lines drawn from the diagnosis table.

## Mode B: review or fix an existing prompt

1. Name the prompt type. Run the superb test and show the results (✓ present / ~ weak / ✗ missing).
2. Say in 1–2 lines what is working well, then what to improve.
3. If she shared the output too, diagnose it with the diagnosis table.
4. Return the rewritten prompt, with a short list of the changes and the reason for each.

## Mode C: map where AI fits her roles

When she asks how AI can help in her work, build a table. Rows: her roles (Chief Dental Officer and clinical innovation at Overjet; researcher and author; policy expert and speaker; pediatric dentist). Columns: the five prompt types. Each cell holds one concrete task. Then offer to turn any cell into a finished prompt.

## Mode D: compare across platforms

When she runs the same prompt on more than one AI platform and shares the answers: compare them on accuracy, depth, format compliance and insight. Say which prompt gaps caused the differences, and return a tightened prompt that would get the best answer from any platform.

## The superb test

Check every prompt before delivering it:

| # | Check |
|---|---|
| 1 | **Task** is one clear verb (summarize, draft, compare, evaluate, convert) |
| 2 | **Role** is named when expertise matters |
| 3 | **Audience** is named, with what they will decide or do |
| 4 | **Content** is specified: what to include, or which items and criteria |
| 5 | **Format** is specified: bullets, table, number of items, length |
| 6 | **Constraints** are specified: tone, sources, what to avoid |
| 7 | **Insight**: one "so what" request (reformat prompts are exempt) |
| 8 | **Accuracy**: anchored to sources, with citations required, whenever facts, numbers or policy are involved |
| 9 | **Length**: 1–2 sentences for quick prompts; no filler words in any prompt |

## Worked example (from her course activity)

**Good:** "Compare fee-for-service, managed care carve-in, and standalone dental plan Medicaid delivery models, and explain the key differences in program-integrity oversight, claims data availability, and readiness for AI-based claim review in a table."

**Superb:** "Compare fee-for-service, managed care carve-in, and standalone dental plan Medicaid delivery models for state Medicaid directors, explaining the key differences in program-integrity oversight, claims data availability, and readiness for AI-based claim review in a table, and say which model offers the fastest path to AI adoption and why."

What changed: the audience was added (#3) and one insight request was added (#7). Everything else stayed.

## Diagnosis table: when the output misses

| If output is… | Try… |
|---|---|
| Too generic | More context: audience, tone, purpose |
| Off-tone | Name the tone explicitly ("friendly but firm") |
| Hard to use | Break the task into steps, or request a specific format |
| Repetitive or unclear | Simplify the prompt; clarify the intent |
| Hallucinated or inaccurate | Anchor it in source material; require citations; allow "not found" |
| Not usable at all | Ask for three different versions, or ask it to try again |
| Unclear logic | Chain of thought: "Explain your reasoning step by step" |
| Wrong format | Few-shot: give a clear example of the output you want |
| Correct but shallow | Add or sharpen the insight request |
| Right content, wrong reader | Name the audience and the decision they face |

## Output format

1. The prompt: quick, or full with structured and narrative versions (code blocks)
2. The superb test results (compact table, or one line if everything passes)
3. **If the result is off, send:** 2–3 follow-ups she can paste in as-is

Keep the commentary short. The prompt is the deliverable.

## Rules

- Plain language. No jargon unless she uses it first.
- Never add facts she did not give.
- For anything involving evidence, numbers or policy, always include the anchoring and citation constraint (she requires verified, linked citations).
- For outside audiences (payers, partners, agencies), add a constraint that keeps proprietary methods and IP out, unless she says otherwise.
- Reformat prompts never ask for analysis or rewording.
- If she will reuse the prompt, offer to save it as its own skill.
