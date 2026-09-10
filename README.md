# jd-resume-matcher

A portable Agent Skill for matching a target job description (JD) against a candidate's real resume evidence and producing truth-preserving resume revisions.

## Package structure

- `SKILL.md` — required skill metadata and core workflow
- `references/matching-rubric.md` — deterministic matching rubric
- `references/evidence-guidelines.md` — evidence extraction and truth-preserving rewrite rules
- `assets/output-template.md` — output structure
- `evals/evals.json` — regression test cases for iteration

## Install / use

### Any Agent Skills compatible client

Install or copy the whole `jd-resume-matcher/` directory into the skill location supported by that client. Keep the directory name exactly `jd-resume-matcher`, because the Agent Skills specification requires the parent directory name to match the `name` in `SKILL.md`.

### ChatGPT Skills

Where the Skills feature is available:
1. Open Plugins → Skills.
2. Create → Upload from your computer.
3. Upload the ZIP bundle or skill directory.
4. Review and install.

Availability depends on plan/workspace/product rollout.

### Gemini CLI

Place the directory under a supported skills directory such as:

`.agents/skills/jd-resume-matcher/`

Then start Gemini CLI and use `/skills` to confirm discovery.

### Claude / Claude Code

Claude supports Agent Skills. Upload/install the skill using the Skills UI where available, or place the directory in the skills location supported by your Claude Code setup.

### OpenAI API

The OpenAI Skills API accepts a directory upload or a single ZIP skill bundle. Create/upload the skill, then manage versions through the Skills API.

### Clients without native Agent Skills support

The skill can still be used manually:
1. Give the model `SKILL.md`.
2. Tell it to follow that file as the operating instructions for JD × resume matching.
3. Provide `references/matching-rubric.md`, `references/evidence-guidelines.md`, and `assets/output-template.md` when the task reaches those steps.
4. Provide the JD and resume.
5. Do not expect automatic trigger/discovery; the host has to load the files into context.

## Minimal manual invocation

> Read `SKILL.md` and use it as the operating procedure for this task. Load the referenced rubric, evidence guidelines, and output template when required. Then compare the attached JD and resume. Do not invent facts or metrics.

## Portability note

A raw foundation model does not install or discover a skill by itself. Skill discovery, loading, permissions, and tool access are responsibilities of the agent/client/runtime hosting that model.

## Versioning

Keep the skill name stable (`jd-resume-matcher`) and change version metadata or release tags instead of renaming the folder to `jd-resume-matcher-v2`, because the directory name must match the `name` field in `SKILL.md`.
