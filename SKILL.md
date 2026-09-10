---
name: jd-resume-matcher
description: Compare a target job description with a candidate's real resume and supporting experience materials; identify hard eligibility gates, atomic JD requirements, evidence strength, match status, evidence gaps, and truth-preserving resume revisions. Use when the user asks to match a JD to a resume, tailor a resume for a role, diagnose screening fit, or improve role-relevant resume evidence without fabricating experience.
compatibility: Agent Skills compatible clients; no external runtime dependencies required.
metadata:
  version: "2.0.0"
  language: "zh-CN/en"
---

# JD × Resume Matcher

## Purpose

Help a recruiter quickly see credible evidence that the candidate fits a target role.

Optimize for **evidence visibility and role relevance**, not keyword stuffing.

## Required inputs

For a full run:
1. Target JD
2. Candidate resume

Optional:
- internship/project source documents
- portfolio/work samples
- user-confirmed metrics or clarifications

If one required input is missing, identify only the missing input. Do not invent it.

## Source-of-truth policy

Use only user-provided materials and user-confirmed facts.

When multiple sources exist, use this hierarchy for confidence:
1. explicit user confirmation in the current task
2. detailed primary project/source document
3. current resume wording
4. cautious inference from adjacent evidence

If two sources conflict:
- do not silently choose one
- mark `【口径冲突待确认】`
- state the conflicting claims
- do not strengthen the resume claim until resolved

## Non-negotiable guardrails

1. Never fabricate experience, responsibility, project scope, tool use, metric, date, or outcome.
2. Never upgrade `参与` to `主导/独立负责` without direct evidence.
3. Never turn a team result into a personal result without evidence.
4. Never turn tool familiarity into proof of business application.
5. Never equate semantic similarity or keyword overlap with evidence.
6. Preserve the original meaning of the JD.
7. Unknown but potentially confirmable facts → `【待补充】`.
8. No supporting evidence → `【缺失】`.
9. Conflicting supplied facts → `【口径冲突待确认】`.
10. Diagnose first; rewrite second.
11. Never guarantee interview or hiring outcomes.

## Execution workflow

### Step 0 — Eligibility gate

Before semantic matching, identify hard requirements such as:
- graduation cohort/year
- degree level
- location/work authorization if explicitly stated
- mandatory certification
- other explicit must-have constraints

Classify each as:
- `满足`
- `不满足`
- `待确认`

Do not average a failed hard gate away with strong soft-skill evidence.

### Step 1 — Atomic JD decomposition

Split every compound JD sentence into independently assessable requirements.

For each atomic requirement extract:
- original JD text
- atomic requirement
- category
- JD requirement level: 高 / 中 / 低
- what observable evidence would prove it

Use `references/matching-rubric.md`.

### Step 2 — Evidence extraction and visibility

Extract supported evidence from two layers:

**Layer A — Screening-visible resume evidence**
Evidence already written in the current resume. This determines the *current screening match*.

**Layer B — Supplementary evidence reserve**
Confirmed evidence found only in project notes/source documents. This may be used for truthful revision, but must NOT be treated as already visible to a recruiter.

For each evidence object extract:
- Action
- Method / Tool
- Scope / Ownership
- Result
- Business/User context
- Evidence source
- Visibility: `简历已体现` / `仅补充材料体现`

Prefer behavior over self-description.

Use `references/evidence-guidelines.md`.

### Step 3 — Evidence selection

For each atomic JD requirement:
1. choose the strongest **resume-visible primary evidence**
2. separately identify the strongest **supplementary evidence reserve**
3. keep source locations visible
4. do not stitch unrelated fragments into an inflated claim
5. if strong supplementary evidence exists but the current resume omits it, classify the issue as an `表达缺口`

### Step 4 — Match evaluation

Evaluate **current screening fit** using only resume-visible evidence:
- JD requirement level
- Resume-visible evidence grade A–E

Then map them to a current match status using `references/matching-rubric.md`.

Separately, if supplementary evidence exists, state the **truthful improvement potential** after revision.

Allowed current match statuses:
- `优于需求`
- `强匹配`
- `部分匹配`
- `缺少证据`
- `明显缺口`
- `可忽略`

Do not assign a label without a one-sentence rationale.
Do not let hidden/source-document evidence inflate the current resume match.

### Step 5 — Gap typing

Classify the gap, because not all gaps should be "fixed" the same way:

- `表达缺口` — strong evidence exists but is buried/generic
- `证据缺口` — relevant experience exists but proof is incomplete
- `能力缺口` — no real experience currently supports the requirement
- `硬门槛缺口` — explicit eligibility condition is not met
- `无明显缺口`

This distinction is mandatory.

### Step 6 — Revision priority

High priority:
- high/medium JD requirement + expression gap with strong real evidence
- high requirement + evidence gap that may be resolved by a targeted clarification
- important evidence currently buried in a less relevant section

Medium priority:
- transferable evidence needs clearer framing
- ordering/emphasis is weak
- proof chain lacks one non-critical element

Low priority:
- low JD requirement
- minor wording polish
- keyword-only tuning with no additional evidence

Do **not** propose wording as the fix for a true capability gap.

### Step 7 — Truth-preserving rewrite

For each revised bullet:
- keep the user's factual boundary
- foreground role-relevant action
- add method/tool/result only when sourced
- preserve confirmed metrics exactly
- preserve the original resume's concise writing style where possible
- prefer `动作 + 方法/场景 + 结果`
- if a metric's unit/causal attribution is uncertain, flag it instead of strengthening it

### Step 8 — Quality assurance

Before finalizing, verify:
- hard gates are separated from semantic fit
- current match uses resume-visible evidence only
- supplementary evidence is clearly labeled as not yet visible to recruiters
- every strong match has traceable evidence
- evidence source and visibility are visible
- A–E grade follows the rubric
- match status follows the matrix
- no ownership inflation
- no invented metrics/tools
- no unresolved source conflict is presented as fact
- true capability gaps are not disguised by wording
- final bullets remain faithful to the source materials

## Output

Use `assets/output-template.md`.

## When NOT to use

Do not use for:
- fabricated-resume writing
- generic career advice without a JD-resume comparison
- interview scripting unless evidence matching is the core subtask
- pure ATS keyword stuffing
