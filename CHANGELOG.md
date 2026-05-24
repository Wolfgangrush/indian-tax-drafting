# Changelog

All notable changes to the `indian-tax-drafting` plugin are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/) and this project adheres to [Semantic Versioning](https://semver.org/).

---

## [0.2.3-alpha] — 2026-05-25

### Explicit per-agent invocation of `pair_md_to_docx.sh`

v0.2.2 documented the output-pairing rule in `_drafting_common/SKILL.md` and relied on every agent picking up the rule by reference. v0.2.3 makes the invocation EXPLICIT in each agent's prompt — Reader, Format, Drafter, Verifier, Refiner, Overseer — so the pairing happens deterministically rather than depending on inherited-rule compliance.

### Changed

- **Reader prompt** — after writing `case-facts.md`, explicit `pair_md_to_docx.sh case-facts.md` invocation appended.
- **Format prompt** — after writing `format-shell.md`, explicit invocation appended.
- **Drafter prompt** — explicit invocation appended (Drafter already had a pandoc command from v0.2.1; the helper invocation is now also documented as the canonical path).
- **Verifier prompt** — after writing `verification-report.md`, explicit invocation appended.
- **Refiner prompt** — after writing `draft-v2.md`, explicit invocation appended.
- **Overseer prompt** — after writing `opposing-notes.md` and `final-draft.md`, two explicit invocations appended.

### Why the change

User feedback 2026-05-25: relying on each agent to inherit the rule from `_drafting_common` is not robust enough. The Drafter has the pandoc command spelled out and it works; the other 5 agents had only the inherited rule. Explicit per-agent invocation makes the pairing deterministic. Once every agent reliably outputs both `.md` and `.docx`, a pipeline run on any forum becomes itself a calibration probe — the advocate visually inspects the rendered `.docx` from each stage and identifies any per-forum formatting gaps, without needing 14 separate gold-standard pleadings upfront.

---

## [0.2.2-alpha] — 2026-05-24

### Output-pairing discipline — every `.md` paired with `.docx`

Advocates do not natively read Markdown. Every pipeline output artifact (case-facts.md from Reader, format-shell.md from Format, draft-v1.md from Drafter, verification-report.md from Verifier, draft-v2.md from Refiner, opposing-notes.md + final-draft.md from Overseer) is now paired with a corresponding `.docx` rendered using the same locked Word styles in the shipped reference.docx.

### Added

- **`pair_md_to_docx.sh`** — helper script in `skills/<base>/` that every agent calls after writing a `.md` output. Wraps the two-step pandoc + fix_docx_tables.py pipeline so every agent produces a paired `.docx` without re-implementing the conversion logic.
- **OUTPUT-PAIRING DISCIPLINE** section in `_drafting_common/SKILL.md` documenting the per-agent output-pairing map (Reader → case-facts.{md,docx}; Format → format-shell.{md,docx}; Drafter → draft-v1.{md,docx}; Verifier → verification-report.{md,docx}; Refiner → draft-v2.{md,docx}; Overseer → opposing-notes.{md,docx} + final-draft.{md,docx}).

### Why the change

User feedback from the 2026-05-24 EPFO test demonstrated that the QC pipeline output (`verification-report.md`, `opposing-notes.md`) was not accessible to the advocate in their normal Word workflow. The advocate explicitly stated: "every note … needs to be docx too." v0.2.2 closes this gap.

### Clarification — per-court formatting

v0.2.1 propagated a single Bombay HC Nagpur pleading-style reference.docx across all 14 plugins. The structural styling (TNR 14pt 1.5 spacing 4cm-left margin Heading 1/2/3/4) is broadly defensible for pleading-style plugins (HC / SC / Tax / Rent / MACT / Banking / Company / Consumer / Labour / Family / IP / District Court) because the court-specific differences (cause-title text, annexure prefix, statutory opening, AOR Certificate language) live in the case-type SKILL.md (Drafter content) not the reference.docx (style template). For SC the universal style is correct as the SC Registry mandate matches the HC convention (A4 + TNR 14pt + 1.5 spacing + 4cm left margin). Court-specific content (P-1/P-2 annexure prefix instead of ANNEXURE-A; SYNOPSIS + LIST OF DATES instead of just INDEX; AOR Certificate verbatim) is rendered by the Drafter from the case-type skill. Per-bench fine-tuning (e.g., Delhi HC double-spacing under Original Side Rules 2018; Punjab & Haryana watermarked paper) is achieved by supplying a case-folder reference.docx override.

For the two TRANSACTIONAL plugins (indian-contracts-drafting-litigation + indian-property-drafting-litigation), v0.2.1 wrongly applied the pleading-style reference.docx. Those two plugins now ship a transactional-instrument variant (TNR 12pt single-spaced, no spaced section headers, no underline on headings) under their own v0.2.2 release.

---

## [0.2.1-alpha] — 2026-05-24

### Filing-grade format calibration

Inherits the v0.2.1 calibration from `indian-hc-drafting-litigation` (anchored to an actual filed Bombay HC Nagpur Second Appeal pleading) and applies it to the direct-tax pipeline.

### Added

- **`fix_docx_tables.py`** post-pandoc script at `skills/_tax_drafting_base/fix_docx_tables.py`. Forces column widths on every table in the rendered .docx — Particulars block tables, Enclosure list, Form 35 numeric clause tables. Profiles: 5-col 8/8/60/14/10; 4-col 10/10/65/15; 3-col 10/75/15; 2-col 18/82. Locks first-row bold + centered. Drafter runs this as the final post-pandoc step.
- **Heading 2 with UNDERLINE** in reference.docx for spaced section headers (`P A R T I C U L A R S`, `S T A T E M E N T   O F   F A C T S`, `G R O U N D S   O F   A P P E A L`, `R E L I E F   C L A I M E D`, etc.).
- **Heading 3 + Heading 4 styles** in reference.docx for unspaced bold-underlined section headers and left-anchored bold-underlined headings.

### Changed

- **Drafter pandoc command** is now TWO steps (pandoc → .docx, then `fix_docx_tables.py`). Step 2 is non-negotiable; skipping it produces stacking-column table defects.
- **reference.docx Heading 2 style** now includes UNDERLINE.

---

## [0.2.0-alpha] — 2026-05-24

### Critical render-defect repair + pipeline-optionality

This release inherits the v0.2.0-alpha fixes from `indian-hc-drafting-litigation` and adapts them to the direct-tax pipeline. The v0.1.0 render path produced filing-grade Markdown but the pandoc → `.docx` conversion failed CIT(A) / ITAT / High Court Tax Bench / DRP expectations on multiple counts (Form identifier not bold, section headers left-aligned, enclosure table column-headers wrapping vertically, ~6,200-word bloat).

### Added

- **Pre-customised direct-tax `reference.docx`** at `skills/_tax_drafting_base/reference.docx` with locked Word styles (TNR 14pt body, 1.5 line spacing, 4cm left / 2.5cm right-top-bottom margins, Heading 1 bold centered, Heading 2 bold centered with letter-spacing, Heading 3 bold left, fixed table layout).
- **`build_reference_docx.py`** — reproducible build script for the shipped reference.docx.
- **MARKDOWN HEADING DISCIPLINE** section in `_drafting_common/SKILL.md` and `agents/drafter/drafter.md` documenting the Markdown → Word-style mapping the Drafter must follow.
- **VERBOSITY DISCIPLINE** in `_drafting_common/SKILL.md` setting per-case-type word-count targets (Form 35 CIT(A) 2,500–4,500 / 6,000; Form 36 ITAT 3,000–5,000 / 7,000; Section 260A HC 4,000–6,000 / 8,500; Form 10A 1,500–2,500 / 3,500; Section 148A 2,000–3,500 / 4,500; Section 270A/271 2,000–3,500 / 4,500; Section 263 2,500–4,000 / 5,500; Section 264 2,500–4,000 / 5,500; Section 201 2,000–3,500 / 4,500; Section 144C DRP 4,000–6,500 / 9,000).
- **PIPELINE-OPTIONALITY** section in `_drafting_common/SKILL.md` — Verifier / Refiner / Overseer now OPTIONAL QC layers. Default exit point is after Stage 3 (Drafter); the advocate decides whether to invoke the QC stages.
- **COVER-PAGE DISCIPLINE** — LIST OF ENCLOSURES begins on `\newpage` and carries ONLY Form identifier + Descriptive title + assessee short name + section header + table + signature block.

### Changed

- **Drafter agent prompt** extended with the Markdown-heading discipline, verbosity ceilings, cover-page discipline, and pandoc invocation against the shipped reference.docx.
- **Pandoc invocation documented end-to-end.** The Drafter MUST use the shipped reference.docx; auto-generating one in the case folder is now banned.

### Cost / token-budget note

Running the full 6-agent pipeline burns approximately 600K tokens per draft, which can exhaust an advocate's Claude session limit. v0.2.0 makes Stages 4–6 OPTIONAL so a baseline Reader → Format → Drafter run (~280K tokens) is sufficient for routine pleadings (Form 10A registration applications, Section 201 TDS replies). The optional QC stages remain available for ITAT appeals with large quantum, Section 260A HC appeals, and Section 144C DRP objections in transfer-pricing matters.

---

## [0.1.0-alpha] — 2026-05-16 (initial release)

### Added

- **Plugin scaffolding** — `.claude-plugin/plugin.json` manifest · MIT `LICENSE` · `NOTICE.md` provenance and privilege statement · `.gitignore` · this `CHANGELOG.md` · comprehensive `README.md`.
- **Six-agent drafting pipeline** — Reader → Format → Drafter → Verifier → Refiner → Overseer. Each agent is a markdown file under `agents/<name>/<name>.md` with YAML frontmatter declaring `name`, `description`, and `allowed-tools`.
- **Shared infrastructure skills:**
  - `_drafting_common` — anti-pollution rules, encoding standards, language conventions, AI-style-marker blacklist, direct-tax privacy firewall (assessee name + PAN + Aadhaar + TAN + DIN + AO name + financial figures substituted with placeholders before downstream AI processing), citation discipline, and statutory currency rules (Income-tax Act 1961 current, Income-tax Rules 1962 current, Income-tax (Appellate Tribunal) Rules 1963 current, Finance Act 2021 reassessment overhaul Section 148A regime, Faceless Appeal Scheme 2021, Faceless Assessment Scheme 2020, BNSS 2023, BSA 2023).
  - `_tax_drafting_base` — universal Indian direct-tax pleading skeleton built on the statutory Form layout discipline (Form identifier + Rule reference → Descriptive title → Particulars block (Name / Address / PAN / Assessment Year / AO designation / DIN of order under appeal) → Statement of Facts (where applicable) → Grounds of Appeal → Relief Claimed / Prayer → Verification → Signature block → Procedural endnotes with filing-fee schedule and mandatory enclosures), plus the assessment-year vs financial-year discipline, the limitation-period discipline, and the Form-correspondence rules.
- **Ten case-type skill scaffolds:**
  - `cit-appeals-form-35-draft` — appeal before the Commissioner of Income-tax (Appeals) on Form 35 under Rule 45, Section 246A jurisdictional scheme + Section 249 procedure + Section 250 hearing discipline + Faceless Appeal Scheme 2021
  - `itat-appeal-form-36-draft` — appeal before the Income-tax Appellate Tribunal on Form 36 under Rule 47, Section 252 — 255 statutory framework + ITAT Rules 1963 (esp Rule 5A) procedural framework
  - `high-court-appeal-section-260a-draft` — appeal to the High Court on a substantial question of law under Section 260A
  - `section-12a-registration-form-10a-draft` — application for registration / re-registration of a charitable trust under Section 12A / 12AB on Form 10A under Rule 17A (post-Finance-Act-2020 regime — every existing registered trust required to re-apply)
  - `section-148a-reopening-objection-draft` — objection to a Section 148A(b) show-cause notice issued under the Finance Act 2021 reassessment regime, with *Ashish Agarwal* transitional discipline
  - `section-271-270a-penalty-reply-draft` — reply to a penalty show-cause notice under Section 271 (legacy concealment / inaccurate-particulars) and Section 270A (under-reporting / misreporting of income), with Section 270AA immunity application discipline
  - `section-263-revision-objection-draft` — objection to a notice of revision proposed by the Principal Commissioner / Commissioner of Income-tax under Section 263 (revenue-favoured revision against assessee), with the *Malabar Industrial* twin-condition discipline
  - `section-264-revision-application-draft` — taxpayer-initiated application for revision before the Principal Commissioner / Commissioner of Income-tax under Section 264
  - `section-201-tds-default-reply-draft` — reply to a Section 201 / 201(1A) TDS-default show-cause notice, with the Section 200 deduction discipline + Section 194 family discipline + the deductor-deemed-assessee-in-default framework
  - `section-144c-drp-objection-draft` — objection before the Dispute Resolution Panel under Section 144C against a draft assessment order in transfer-pricing / international-tax cases, structured under Rule 44CA
- **Forum-aware design** — the user supplies `case-config.md` declaring the chosen forum (CIT(A) — faceless or physical bench / ITAT bench / High Court Tax Bench / PCIT or CIT for revision or registration / DRP), assessment year, financial year, the assessment-order vintage (pre-Finance-Act-2021 reassessment regime vs Section 148A regime), faceless-vs-physical jurisdiction, demand-notice / penalty-notice trajectory, and the limitation-clock anchor.

### Notes on this release

This is a **v0.1.0-alpha scaffold release**. The structural skeletons, agent pipeline, base skills, and 10 case-type skill frames are in place. Deep per-skill encoding (full Grounds-of-Appeal exemplars for each case type, full *Malabar Industrial* / *Ashish Agarwal* / *Reliance Petroproducts* line of Supreme Court precedent encoded in the Verifier, and bench-specific Practice Directions for ITAT Mumbai / Delhi / Chennai / Kolkata / Bangalore / Ahmedabad / Hyderabad / Pune / Nagpur and the High Court Tax Benches) will land in v0.1.0 and onward.

### Released under

MIT License. Authored by Rushikesh R. Mahajan, Advocate, publishing under the Wolfgang Rush open-source brand for legal-technology infrastructure.
