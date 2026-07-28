# IntelliAudit — human survey values

Companion human-evaluation data for the IntelliAudit benchmark. Generated from
the study survey (`condition = balanced_v1`) on 2026-07-28.

## Files

| File | What it is |
|---|---|
| `survey_values_responses.csv` | One row per (respondent × case). |
| `survey_values_per_control.csv` | Aggregate: mean / SD / n per control × survey dimension. |

## Cleaning

- **Test accounts removed** — all roster `org=Test` accounts and team identities; no researcher self-ratings.
- **De-identified** — no names or emails. Each respondent is a stable anonymized id: `A###` (auditor) / `S###` (student).
- **Main study only** — the deadline ablation is not included.
- **Evidence modality is reported as served.** Controls 8.1 / 8.4 in **O1** were served as images (PNG access-list screenshots: `8-1_O1_Okta_User_List`, `8-4_O1_Code_Repo_Access_List`) and are tagged `modality = image`. On these image cases the deployed pipeline produced a skip / `INSUFFICIENT_EVIDENCE` output (it did not extract the tabular content from the image); the retained ratings are evaluations of that output. This is a genuine modality-robustness result and is left intact — the images are **not** transcribed to spreadsheets, because doing so would change the task these cases measure (reading an image) and mask the limitation.

## Columns (`survey_values_responses.csv`)

| Column | Meaning |
|---|---|
| `respondent_id` | Anonymized respondent (`A###` auditor, `S###` student) |
| `role` | `auditor` or `student` |
| `study_org` | `o1`–`o4` |
| `control_id` | ISO 27001 control (e.g., `5.9`, `8.4`) |
| `case_id` | Control × org (e.g., `8.4-o2`) |
| `modality` | Primary evidence type as served (`pdf`, `docx`, `xlsx`, `txt`, `image`) |
| `ground_truth_status` | Reference status where defined (`Unknown` when not fixed) |
| `llm_status` | System-produced status (`COMPLIANT` / `PARTIAL` / `NON_COMPLIANT` / `INSUFFICIENT_EVIDENCE`) |
| `rq1_understanding` | RQ1 — control understanding (1–5) *(auditors)* |
| `rq2_factual` | RQ2 — factual/accurate evidence evaluation (1–5) *(auditors)* |
| `rq2_fulfils` | RQ2 — evidence fulfils the control (1–5) *(auditors)* |
| `rq4_identified` | RQ4 — correctly identified issues (1–5) *(students)* |
| `rq4_remediate` | RQ4 — could remediate / explain (1–5) *(students)* |

**Likert scale:** Disagree=1, Somewhat Agree=2, Neutral=3, Agree=4, Strongly Agree=5. Blank = not applicable to that role or not answered.

## Coverage

467 responses · 48 cases · 12 controls · 48 respondents (17 auditors, 31 students).

Pooled means: RQ1 understanding 3.90 (SD 0.86, n=166); RQ2 factual 3.72 (SD 1.08, n=163); RQ2 fulfils 3.05 (SD 1.37, n=163); RQ4 identified 3.66 (SD 1.14, n=298); RQ4 remediate 3.84 (SD 1.10, n=296).

> Note: the paper's rating tables restrict 8.1/8.4 to O2–O4 (O1 was the image-skip case). This file retains the O1 8.1/8.4 rows as image cases, so per-control 8.1/8.4 values computed here include O1 and will differ from the paper's tables.
