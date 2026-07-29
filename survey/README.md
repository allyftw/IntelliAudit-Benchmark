# IntelliAudit; human survey data

Response-level human-evaluation data for the IntelliAudit benchmark, from the
finalized survey export de-identified for release.


## Columns

`respondent_id`, `study_org` (o1–o4, from `case_id`), `participant_role`, `participant_group`, `case_id`, `control_id`, `condition`, `modality`, `evidence_name`, `ground_truth_label`, `ground_truth_status`, `llm_status`, `rq1_understands_control`, `rq1_what_was_missed`, `rq2_factual_evaluation`, `rq2_what_was_missed`, `rq2_evidence_fulfils`, `rq4_correctly_identified`, `rq4_could_remediate`, `rq4_remediation_blocker`, `judge_followup_turns`, `judge_changed_status`, `judge_updated_status`, `created_at`, `updated_at`, `participant_completed_at`.

**Likert values:** Disagree, Somewhat Agree, Neutral, Agree, Strongly Agree (map to 1–5). Blank = not applicable to that role / not answered.

## Coverage

479 responses · 49 respondents (18 auditors, 31 students).
