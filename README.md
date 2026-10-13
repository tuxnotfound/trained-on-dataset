# Trained On: the registry and the change record

Which AI tools train on your inputs, in the vendors' own words. One row per vendor plan with
the training clause quoted and dated, and every recorded change to those clauses since 2024,
classified and dated. This is the data behind [trainedon.me](https://trainedon.me).

This repository is a dated snapshot of the published record, taken 2026-10-13 (the
`generated_at` field inside the JSON files). The live files at
[trainedon.me/data](https://trainedon.me/data) update nightly, and the
[changes feed](https://trainedon.me/changes.atom) announces every new change. A Zenodo DOI for
this snapshot is pending.

## Which AI tools train on your prompts (October 2026)

| Tool | Plan | Trains on your inputs? | In their words since |
|---|---|---|---|
| ChatGPT | Free, Plus and Pro | Yes, by default. You can opt out. | 2025-07-31 |
| ChatGPT | Business, Enterprise, Edu and API | No, unless you opt in. | 2025-07-31 |
| Claude.ai | Free, Pro and Max | Yes, by default. You can opt out. | 2026-06-08 |
| Claude.ai | Commercial (Team, Enterprise, API) | No. | 2025-08-01 |
| Microsoft Copilot | Consumer Copilot | Yes, in certain markets. You can opt out. | 2025-10-11 |
| GitHub Copilot | Accounts under GitHub's Terms of Service | Yes, by default. You can opt out. | 2026-04-27 |
| Perplexity | API | No. | 2024-08-27 |
| Perplexity | Enterprise (data processing agreement) | No. | 2025-08-12 |
| Grok | Consumer (grok.com, X and apps) | You choose in settings. The terms do not say which way it starts. | 2025-08-01 |
| Grok | xAI API and enterprise | No. | 2026-05-18 |
| Cursor | All plans | No, unless you opt in. | 2025-06-14 |
| Windsurf (Codeium) | Free | Yes. No opt-out stated. | 2026-07-01 |
| Windsurf (Codeium) | Paid (Pro, Teams) | Yes, by default. You can opt out. | 2026-07-01 |
| DeepSeek | Consumer app and platform | Yes, by default. You can opt out. | 2025-02-23 |
| Jasper | All plans | Yes. Opt-out only in some regions. | 2025-09-11 |
| Le Chat | Free, Pro and Student | Yes, by default. You can opt out. | 2025-08-01 |
| Le Chat | Team and Enterprise | No, unless you opt in. | 2025-08-01 |

Each answer is a quote from the vendor's own terms, dated from the first archived capture of
the quoted words. The `quote` column carries the words; the `source_url` column links the
archived document history. The date is when the quoted words were first captured, which can lag
the vendor's stated effective date; capture gaps are recorded, not hidden.

## The change record

27 published changes across 11 vendors, from 2024-06-10 to 2026-07-01: 11 changes of position,
12 scope changes and 4 disclosures. Each change's page on the site shows the old and new
wording side by side with a link to the archived capture, for example
[Windsurf, 2026-07-01](https://trainedon.me/changes/2026-07-01-windsurf-terms-of-service),
where "we will never use your Autocomplete User Content to improve generative machine learning
models" was removed after the Cognition acquisition.

## Files

- `data/registry.csv` and `data/vendors.json`: one row per vendor plan.
- `data/changes.csv` and `data/changes.json`: one row per published change.

The JSON files carry the same rows plus `license`, `attribution` and (for vendors)
`generated_at` fields.

### registry columns

| Column | Meaning |
|---|---|
| `vendor` | Product name, for example ChatGPT. |
| `plan` | The plans the row covers. |
| `answer` | Machine-readable answer, one of: `trains_opt_out`, `trains_no_opt_out`, `trains_regional_opt_out`, `trains_in_some_markets`, `no_training`, `no_training_default`, `your_choice_default_unstated`. |
| `answer_text` | The answer in plain words. |
| `quote` | The training clause, verbatim from the tracked document. |
| `document` | Which document the quote is from. |
| `effective_on` | First archived capture of the quoted words. |
| `verified_on` | Last date the quote was checked against the latest capture. |
| `source_url` | The archived history of the document. |
| `opt_out` | How to opt out, where the terms state a way. |

### changes columns

| Column | Meaning |
|---|---|
| `date` | Date of the capture that carries the change. |
| `vendor`, `document` | Which product and which document changed. |
| `classification` | `position` (the training rule changed), `scope` (a plan, product or data source joined an existing rule), or `disclosure` (position unchanged, practice described). |
| `direction` | What the change did, one of: `now_trains`, `no_longer_trains`, `scope_widened`, `scope_narrowed`, `disclosure`. |
| `summary` | The change in at most 30 words, quoting the clause. |
| `decided_by` | `panel` (three readers agreed) or `human`. |
| `reverses` | The date of an earlier change this one undoes, when it does. |
| `previous_capture` | Date of the prior capture, so capture gaps are visible. |
| `url` | The change page, with old and new wording side by side. |
| `ota_commit` | The Open Terms Archive commit that recorded the new version. |

## How the record is made

The corpus is Open Terms Archive's
[genai-contrib collection](https://github.com/OpenTermsArchive/genai-contrib-versions), which
records every captured version of the tracked documents. The site normalises the captures
(tracking IDs, invisible characters, spacing), keeps the distinct states of each training
clause, and reads the transitions. Three models, one each from Anthropic, OpenAI and Google,
classify every candidate change from the old and new clause text alone. A change publishes only
when all three agree it is real, under the most cautious of their labels; everything else waits
for a person. Of the 27 published changes, 19 were decided by the panel and 8 by a person.
Method in full: [trainedon.me/methodology](https://trainedon.me/methodology).

## Licence

[ODC-By 1.0](https://opendatacommons.org/licenses/by/1-0/). Attribute
"Trained On, derived from Open Terms Archive contributors".

## Cite

> Trained On, "The registry and the change record" (dataset), https://trainedon.me/data.
> Derived from Open Terms Archive, ODC-By 1.0.

A single change has its own citation line on its page, under "Cite this change". Citation
metadata for this repository is in `CITATION.cff`. More on the
[press page](https://trainedon.me/press).
