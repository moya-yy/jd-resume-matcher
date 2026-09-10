# Evidence Guidelines V2

## 1. Evidence object

Extract each useful resume fact as:

- Source: company/project + bullet/section
- Action
- Method/Tool
- Scope/Ownership
- Context
- Result
- Confidence: confirmed / pending / conflicting

## 2. Strong evidence principles

Behavioral evidence > self-description.

Example:
- weak: `数据敏感度强`
- stronger: `基于 SQL/Hive 对圈选 Case 做后验分析并据此调整分层策略`

## 3. Ownership vocabulary

Treat these as materially different:
- 参与
- 协助
- 负责某一模块
- 独立负责
- 主导

Never upgrade the level without explicit source support.

## 4. Metrics

For every important metric, check:
- unit
- baseline
- final value
- relative change vs percentage-point change
- whether the result belongs to the individual, project, or team
- whether causality is supported

If uncertain, mark `【待补充】` or `【口径冲突待确认】`.

## 5. Rewriteable vs non-rewriteable

Rewriteable:
- evidence is real but buried
- verb is vague
- result is present elsewhere in the same supported experience
- JD-relevant method is omitted from the resume but confirmed in source material

Not rewriteable by wording alone:
- candidate never used required tool
- candidate never owned required scope
- candidate lacks required qualification
- result/metric does not exist

## 6. Truth-preserving rewrite

Allowed:
- reorder clauses
- foreground relevant evidence
- translate internal jargon into external language
- shorten generic wording
- add confirmed method/result from source docs

Forbidden:
- add unsupported JD keywords
- invent causality
- invent ownership
- invent metrics
- disguise governance work as growth work if facts do not support that framing


## 7. Screening visibility

Always distinguish:

### 简历已体现
The recruiter can currently see this evidence in the submitted resume.

### 仅补充材料体现
The candidate has real supporting evidence, but it is absent from the current resume.

Important:
- current match grade must use `简历已体现`
- `仅补充材料体现` can justify a rewrite recommendation
- strong hidden evidence usually indicates `表达缺口`, not `能力缺口`
- never describe hidden evidence as if it were already present in the resume
