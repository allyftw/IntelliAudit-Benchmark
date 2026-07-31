# IntelliAudit; evidence corpus

The artifacts served to reviewers in the human study: 12 ISO/IEC 27001 controls
across 4 simulated organizations, 48 cases in total.

Real audit evidence is confidential, so the corpus is synthetic. It mixes
public standards and guidance, expert-crafted operational artifacts
(inventories, incident records, disciplinary letters), and generated policy
documents. Names, email addresses, and organization details are fabricated.

## Layout

One directory per control, under `by_control/`. File names encode the
organization, so `5-1_O2_GFP_Information_Security_Policy.docx` is control 5.1
for O2.

| Organization | Prefix |
|---|---|
| Global Enterprises Inc | `O1` |
| GlobalFinance Partners | `O2` |
| QuickServe Restaurants LLC | `O3` |
| TechInnovate Inc | `O4` |

Several cases carry more than one artifact. Control 6.4 bundles three
disciplinary letters and 5.2 pairs an executive-team document with an org
chart, which is why 48 cases map to 60 artifacts.

## Manifest

`evidence_labels.csv`, one row per artifact.

| Column | Meaning |
|---|---|
| `case_id` | Control and organization, for example `5.1-o2` |
| `control_id` | ISO control, `ISO-` prefixed |
| `org`, `org_name` | Which simulated organization |
| `file_type` | Extension on disk |
| `modality` | How the artifact is presented to reviewers |
| `compliance_label`, `compliance_status` | Always `UNKNOWN`, see below |
| `supported` | Whether the pipeline can read it without OCR or vision |
| `availability` | `included`, or `withheld_pending_review` |
| `file_path` | Path in this repo, blank when withheld |

`modality` can differ from `file_type`. Controls 5.2 and 7.14 are presented as
PDFs even where the stored file is `.docx`, matching what reviewers saw.

## There is no ground-truth answer key

`compliance_label` and `compliance_status` are `UNKNOWN` on every row, and that
is deliberate rather than a gap waiting to be filled.

The study collected reviewer ratings of the system's output. It did not collect
adjudicated per-(organization, control) ground truth. No such key exists for
this corpus, so any accuracy, precision, or recall figure computed against it
would rest on labels that were never established. The reviewer ratings are in
`../survey/`.

## Two artifacts are withheld

The O1 artifacts for controls 8.1 and 8.4 are screenshots of real systems and
show real people's names, account handles, and an administrator address. They
are not published here.

Their manifest rows are retained and marked `withheld_pending_review`, so the
corpus states plainly that two of the 48 cases are short an artifact rather
than appearing complete.

These two cases are also the only image-only evidence in the study. They are
marked `supported=No` because the pipeline cannot read them without OCR or a
vision model. That limitation is a reported finding, not a defect: transcribing
the screenshots into spreadsheets would change the task these cases measure and
mask the result.

## Control nomenclature

The study set is 12 controls. Controls 5.25 and 5.26 are consolidated into
**5.27**, whose scope covers assessment, response, and learning from incidents,
and which each organization evidences with a single incident report. Splitting
them asked reviewers to rate one artifact three times under three control
numbers. Nothing here refers to 5.25 or 5.26.
