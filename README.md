# TreeProbe — Partial Data Release

> **Partial release.** This repository currently provides 50 curated Tibetan-medicine QA examples. **The complete TreeProbe benchmark dataset will be released after the paper is accepted.**
>
> **部分数据公开。** 本仓库目前公开50条经整理的藏医问答示例。**完整TreeProbe数据集将在论文录用后公开。**

## Released examples

50 Tibetan-language question-answer examples organized using the PR, CDR and CTP task definitions of TreeProbe. This release contains 20 pathological-reasoning examples, 15 complex-diagnostic-reasoning examples and 15 comprehensive-treatment-plan examples, covering all three roots of the Medical Tree.

## What this release contains

These are source-checked, AI-assisted editorial examples prepared from the project’s medical QA and structured disease materials. The `content_origin` field distinguishes 12 source-QA answers with revised stems, 15 treatment QAs revised against six source fields, and 23 examples reconstructed from source attributes (8 PR and 15 CDR). Reconstructed or rewritten examples have not been verified as the exact items used to compute the paper’s reported results. The source fields support the reference text; this release does not claim independent clinical validation or documented completion of the paper’s expert-panel adjudication.

This is a three-subtask QA example release. It is not the complete ten-subtask benchmark. No four-category multiple-choice items are included, because the available category claims have not been independently established for this release. It must not be used to reproduce the paper’s MCQ cultural-drift metrics.

## Files

- `samples.jsonl`: 50 UTF-8 JSON records, one example per line.
- `evidence.jsonl`: the corresponding source locators, source hashes, cited source fields and revision notes, linked by `id`.
- `dataset_info.json`: release scope and counts.
- `review.html`: a standalone reader with search and task filters.
- `LICENSE`: CC BY 4.0 license notice and official license link.

## Task definitions

| Task | Required question content | Reference targets | Count |
|---|---|---|---:|
| PR | Disease, or a complaint with tongue, urine and pulse observations | Etiology and pathogenesis | 20 |
| CDR | Complaint, tongue, urine and pulse observations | Three-humor state and disease | 15 |
| CTP | Disease or complaint | Principle, diet, lifestyle, medication, external therapy and consolidation | 15 |

CTP references are non-exhaustive, conditional summaries of the supplied source material. Lists of medicines are alternatives/examples rather than a prescription to use every entry together. Treatment steps, stages, exclusions and qualifications must be preserved when scoring. These records describe traditional medical knowledge for research and education, and are not patient-specific treatment instructions.

## Provenance and revisions

Every released reference has project-source locators in `evidence.jsonl`. Source paths are relative to the project data root. The full source workbooks are not redistributed. A cell or QA-record match establishes traceability to the supplied project materials; it does not establish a precise edition/page citation to the Four Tantras. No such bibliographic anchors or expert approvals are invented here.

The public records explicitly carry `expert_adjudication_verified: false` and `final_dataset_membership: "unverified"`. `content_origin: "source_reconstructed_QA_example"` identifies examples built from source fields, including those reconstructed in the earlier review. The other values identify source-QA revisions. The internal record of held-out candidates is not part of this release.

## Use for evaluation

Present only `question` to the evaluated model. Keep `answer`, `reference_components`, `reference_rubric`, titles and all evidence fields hidden during generation. The disease title is a target for CDR and must never be prepended to its question. Source fields and reference material in the evidence file may reveal answers.

Evaluate answers against the task targets and the supplied rubric, accepting semantically equivalent Tibetan expressions and preserving source qualifications. No numerical benchmark accuracy or cultural-drift score is supplied for these revised examples. Do not randomly divide related source examples into train/test splits: items sharing `case_group` must stay in one split. Unmapped groups require manual grouping before any split. This release provides examples, not predefined train/dev/test partitions.

## License and attribution

The contributed dataset material is released under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). Give credit to the TreeProbe dataset contributors, link to the license, and indicate modifications. Any pre-existing third-party rights are not expanded by this notice. See `LICENSE` and the official legal code.

Suggested attribution: “TreeProbe Curated QA Examples, 2026-11-11, TreeProbe dataset contributors, CC BY 4.0.” Repository: [https://github.com/zhangjin11111/TreeProbe-data](https://github.com/zhangjin11111/TreeProbe-data). No DOI is assigned to this partial release.
