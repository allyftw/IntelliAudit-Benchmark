# IntelliAudit — human survey data (de-identified)

Response-level human-evaluation data for the IntelliAudit benchmark, from the
finalized survey export (frozen 2026-07-29), de-identified for release.

## File

`survey_case_responses_deidentified.csv` — one row per (respondent × case).

## Cleaning

- **Test accounts removed** — roster `org=Test` accounts, team identities, and team members who used personal/roster accounts (including a team test account whose roster org was a real institution).
- **De-identified** — dropped `participant_name`, `participant_email`, self-reported employer org, and the raw `background_json` / `answers_json` blobs. Each respondent is a stable anonymized id (`A###` auditor / `S###` student). Verified: 0 emails, 0 participant names in the released file.
- **Main study only** — condition `balanced_v1`; the deadline ablation is not included.
- **Free-text comments retained** (`rq*_what_was_missed`, `rq4_remediation_blocker`, `judge_followup_turns`) — these are participant audit reasoning; scanned and contain no direct identifiers (names/emails).

## Columns

`respondent_id`, `study_org` (o1–o4, from `case_id`), `participant_role`, `participant_group`, `case_id`, `control_id`, `condition`, `modality`, `evidence_name`, `ground_truth_label`, `ground_truth_status`, `llm_status`, `rq1_understands_control`, `rq1_what_was_missed`, `rq2_factual_evaluation`, `rq2_what_was_missed`, `rq2_evidence_fulfils`, `rq4_correctly_identified`, `rq4_could_remediate`, `rq4_remediation_blocker`, `judge_followup_turns`, `judge_changed_status`, `judge_updated_status`, `created_at`, `updated_at`, `participant_completed_at`.

**Likert values:** Disagree, Somewhat Agree, Neutral, Agree, Strongly Agree (map to 1–5). Blank = not applicable to that role / not answered.

## Coverage

479 responses · 49 respondents (18 auditors, 31 students).
