<div align="center">

<img src="docs/banner.png" width="820"/>

**Open-source Claude plugin for drafting Indian direct-tax appellate pleadings — Form 35 to Section 260A**

Visit the live site: [wolfgangrush.github.io](https://wolfgangrush.github.io)

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Claude Plugin](https://img.shields.io/badge/Claude-Plugin-purple)](https://claude.ai)
[![Made in India](https://img.shields.io/badge/Made%20in-India-orange)](#)

</div>


# indian-tax-drafting

> **Open-source Claude-compatible plugin for drafting Indian direct-tax appellate litigation pleadings and statutory registrations under the Income-tax Act 1961.**
>
> Six-agent drafting pipeline · ten case-type skills · case-config-aware · Income-tax Act 1961 + Income-tax Rules 1962 + Income-tax (Appellate Tribunal) Rules 1963 + Faceless Appeal Scheme 2021 + Faceless Assessment Scheme 2020 + Finance Act 2021 reassessment overhaul (Section 148A) + CBDT public-domain Circulars + Bharatiya Nagarik Suraksha Sanhita 2023 + Bharatiya Sakshya Adhiniyam 2023 discipline encoded.
>
> Released under MIT. Open infrastructure for the legal community. No commercial engagement offered through this repository — see Disclaimer below.

> ⚠️ **AI can make mistakes. Always verify the output.**
>
> This software generates assistive drafts and suggestions only. Every legal claim, citation, statute reference, procedural step, deadline calculation, and ground of relief must be independently verified by a qualified human practitioner before filing, advising a client, or relying on the output. The publisher accepts no liability for outputs used without verification.

> 🛡️ **Privacy primitive — Reader agent invokes the gateway:** This drafting plugin's **Reader agent** (the first agent in the 6-agent pipeline) calls [pseudonymisation-gateway](https://github.com/Wolfgangrush/pseudonymisation-gateway) (MIT · wolfgang_rush) on the user's case folder BEFORE any cloud-LLM call. Real client names · government IDs · case numbers · phone numbers · currency amounts are replaced with placeholders (`[PERSON_1]` · `[AADHAAR_1]` · `[CASE_NO_1]` · etc.) in a session-scoped in-memory token map that never touches disk. Downstream agents (Format · Drafter · Verifier · Refiner) work entirely on the sanitized text. The **Overseer agent** (the final agent) calls `desanitize()` to restore real values in the final pleading before it reaches the file system. Cloud LLM vendors never see your client's real PII.


## 🚀 Install — wolfgang_rush marketplace

This plugin is part of the [wolfgang_rush plugin family](https://github.com/Wolfgangrush/wolfgang-rush-marketplace) — 14 Indian-court drafting plugins distributed via one Claude Code marketplace.

**Via Claude Code (CLI) — recommended for the plugin family:**

```bash
/plugin marketplace add Wolfgangrush/wolfgang-rush-marketplace
/plugin install indian-tax-drafting@wolfgang-rush
```

**Via Claude Desktop:** see the [Installation](#installation) section below for the `.zip` upload flow.

---

---

## Table of contents

1. [What this plugin does](#what-this-plugin-does)
2. [Case-type skills (full inventory with statutory authority)](#case-type-skills-full-inventory-with-statutory-authority)
3. [The 6-agent drafting pipeline (what each agent does)](#the-6-agent-drafting-pipeline)
4. [Installation](#installation) — Claude Desktop application
5. [Your first pleading — step-by-step walkthrough](#your-first-pleading--step-by-step-walkthrough)
6. [The `case-config.md` file](#the-case-configmd-file)
7. [Built-in compliance disciplines](#built-in-compliance-disciplines)
8. [Privacy firewall — extra discipline for direct-tax content](#privacy-firewall--extra-discipline-for-direct-tax-content)
9. [Why MIT License](#why-mit-license)
10. [Sibling plugins](#sibling-plugins)
11. [Why this exists](#why-this-exists)
12. [Roadmap](#roadmap)
13. [Contributing](#contributing)
14. [Contact](#contact)
15. [Author and brand](#author-and-brand)
16. [Provenance and privilege statement](#provenance-and-privilege-statement)
17. [Disclaimer and Bar Council of India Rule 36 compliance](#disclaimer-and-bar-council-of-india-rule-36-compliance)
18. [License](#license)

---

## What this plugin does

This plugin lets an Indian advocate, sitting inside the Claude Desktop application, point at a case folder on disk and obtain a complete direct-tax appellate pleading or statutory registration application in `.docx` form — the statutory Form layout (Form 35 / Form 36 / Form 10A where applicable), the Particulars block, the Statement of Facts, the Grounds of Appeal, the Relief Claimed / Prayer, the Verification, the Signature block, the Procedural endnotes with filing-fee schedule and mandatory enclosures, and the accompanying applications (stay of demand under Section 220(6) / 220(3), condonation of delay under Section 249(3) or Section 253(5), additional evidence under Rule 46A of the Income-tax Rules 1962 or Rule 29 of the Income-tax (Appellate Tribunal) Rules 1963, early hearing application, exemption from personal appearance for faceless-assessment cross-objection) — formatted in the forum's idiom and the case-type-specific structure, sourced from a `case-config.md` file the user places in the case folder.

The pipeline is six agents running in sequence:

1. **Reader** — extracts direct-tax case-facts (assessee particulars, assessment year, financial year, AO designation, faceless centre, DIN of the order under appeal, date of order, date of service, additions or disallowances proposed or made, penalty proposed or imposed, demand under Section 156, TDS-default quantum, transfer-pricing adjustment quantum) from the case folder with a per-document audit log, and applies the **direct-tax privacy firewall** (every assessee name, every PAN, every Aadhaar reference, every TAN, every Assessing-Officer name, every DIN, every quantum figure substituted with structural placeholders before downstream AI processing; the placeholder → real-value mapping is stored locally on the user's machine only).
2. **Format** — loads the case-type skill template, reads the user's `case-config.md`, and pre-substitutes forum name / Form identifier / Rule reference / case-number prefix / filing-fee slab / statutory opening / limitation anchor into a `format-shell.md` ready for the Drafter.
3. **Drafter** — writes the actual pleading. The statutory Form layout in the correct order, the Particulars block, the Statement of Facts (where applicable), the Grounds of Appeal numbered consecutively with the statutory anchor for each ground, the Relief Claimed / Prayer, the Verification, the Signature block, the Procedural endnotes, and the accompanying applications.
4. **Verifier** — anti-hallucination firewall **plus** statutory-currency check (CrPC 1973 → BNSS 2023 transitions where Section 274 / 277 / 277A penal references arise; IEA 1872 → BSA 2023 transitions) **plus** Form-layout fidelity check (Form 35 follows Rule 45, Form 36 follows Rule 47, Form 10A follows Rule 17A) **plus** limitation computation (Section 249(2) for CIT(A) — 30 days; Section 253(3) for ITAT — 60 days; Section 260A(2) for High Court — 120 days; Section 144C(2) for DRP — 30 days from the date of receipt of draft assessment order) **plus** filing-fee scaling check against current notification **plus** Section 148A regime currency check (any Section 147 / 148 reference without the Section 148A flag is caught as legacy-pre-Finance-Act-2021) **plus** assessment-year vs financial-year discipline check **plus** PAN-format check **plus** DIN-presence check (every Income-tax order issued after 01-10-2019 carries a Document Identification Number under CBDT Circular No. 19/2019).
5. **Refiner** — applies Verifier flags, polishes language to formal Indian tribunal / court register, enforces internal numbering and exhibit-cross-reference consistency, strips AI-style markers, and re-substitutes real assessee names, real PAN / Aadhaar / TAN, real DIN, and real financial figures into the final `.docx` (strictly on the user's local machine — the underlying AI never holds real values).
6. **Overseer** — reads the polished draft with an opposing-counsel lens (Departmental Representative for an assessee appeal; assessee's counsel for a Department appeal; Senior Standing Counsel for a High Court Section 260A appeal). Flags weak grounds, missing statutory anchors, broken limitation, scope-creep in additional-evidence applications under Rule 46A, missing Section 270AA immunity election where the assessee is eligible, missing Section 144C(13) DRP-direction-binding argument, *Malabar Industrial* twin-condition deficiencies in a Section 263 reply, transitional-regime gaps in a Section 148A objection (*Ashish Agarwal* line), and Section 220(6) stay-pendente-lite gaps.

The output is what an advocate would put before the appellate authority or the Tribunal or the Court for filing — **not a template. Not a checklist. A pleading** — ready for the advocate's review, professional verification, signature, filing fee, and electronic filing on the Income-tax e-filing portal or physical filing as the forum requires.

---

## Case-type skills (full inventory with statutory authority)

The plugin ships with ten case-type skills, each covering a distinct direct-tax appellate or registration case-type:

### 1. `cit-appeals-form-35-draft`

**Statutory authority:** Income-tax Act 1961 — Section 246A (orders appealable before the Commissioner of Income-tax (Appeals)) + Section 249 (form of appeal, limitation, fee scaled by total assessed income) + Section 250 (procedure in appeal) + Section 251 (powers of CIT(A)); Income-tax Rules 1962 — Rule 45 (Form 35 layout); Faceless Appeal Scheme 2021; Faceless Assessment Scheme 2020 read with Section 144B. **Use case:** assessee aggrieved by an Assessing Officer's assessment order under Section 143(3) / Section 144 / reassessment order under Section 147 read with Section 148A / penalty order under Section 270A or Section 271 / TDS-default order under Section 201 / other appealable order listed in Section 246A. **Output:** complete Form 35 appeal with the Rule 45 layout, the Particulars block (Name / Address / PAN / Assessment Year / AO designation / DIN of order under appeal / date of order / date of service / nature of order / amount of income assessed / total tax including surcharge and cess / amount of demand / Section under which assessed), the Statement of Facts (clause 8 of the Form), the Grounds of Appeal numbered consecutively (clause 9), the Relief Claimed (clause 10), the Verification, the filing-fee tender per the slab in Section 249(1) (verify against current notification), and the accompanying applications (stay of demand under Section 220(6), condonation of delay under Section 249(3) where applicable, additional grounds under Rule 46A where applicable).

### 2. `itat-appeal-form-36-draft`

**Statutory authority:** Income-tax Act 1961 — Section 252 (constitution of the Appellate Tribunal) + Section 253 (appeals to the Appellate Tribunal — orders of CIT(A), DRP-binding orders, certain orders of Principal Commissioner / Commissioner) + Section 254 (procedure and powers of the Tribunal) + Section 255 (procedure of the Tribunal); Income-tax Rules 1962 — Rule 47(1) (Form 36 layout) + Form 36A for cross-objection; Income-tax (Appellate Tribunal) Rules 1963 — Rule 5A (additional-evidence discipline) and the related procedural rules. **Use case:** assessee or Department aggrieved by an order of CIT(A) under Section 250, or by certain orders of the Principal Commissioner / Commissioner under Section 263, or by DRP-direction-binding orders. **Output:** complete Form 36 appeal with the Rule 47 layout, the Particulars block (Name / Address / PAN / Assessment Year / Order of CIT(A) reference + date + DIN / Assessing Officer + ward / circle / range / faceless centre), the Grounds of Appeal numbered consecutively with statutory anchor for each ground, the Relief Claimed, the Verification, the filing-fee tender per the slab in Section 253(6) (verify against current notification), and the accompanying applications (stay of demand under Section 220(6), condonation of delay under Section 253(5) where applicable, additional evidence under Rule 29 of the ITAT Rules 1963, early hearing application). **Language option:** Hindi filing permitted under the ITAT Rules at notified-State benches — flagged in the base skill.

### 3. `high-court-appeal-section-260a-draft`

**Statutory authority:** Income-tax Act 1961 — Section 260A (appeal to the High Court on a substantial question of law from an order of the Appellate Tribunal) + Section 260B (case before High Court to be heard by not less than two judges) + Section 261 (appeal to the Supreme Court on a substantial question of law of general importance) read with the High Court Tax Bench Rules of the respective High Court (Bombay, Delhi, Gujarat, Karnataka, Madras, Calcutta, etc.). **Use case:** assessee or Department aggrieved by an order of the Income-tax Appellate Tribunal and able to formulate a substantial question of law within the *Sir Chunilal V. Mehta* (1962) framework adopted in *Santosh Hazari* (2001) 3 SCC 179 and *Hero Vinoth* (2006) 5 SCC 545. **Output:** complete High Court appeal memorandum, with the substantial questions of law set out at the threshold (forming the gateway), the chronology of orders below (AO → CIT(A) → ITAT), the facts essential to the questions of law, the Grounds of Appeal anchored to the framed questions, the Relief sought (re-framing of the question, remand to ITAT, or final disposal under Section 260A(7)), the Verification, the filing fee per the State High Court Rules, the certified copy of the ITAT order, and the accompanying applications (stay of demand pendente lite, condonation of delay under Section 260A(2A) where applicable). **Section 261 note:** Supreme Court appeal under Section 261 is rare and proceeds only on a substantial question of law of general importance; the present skill notes the route and the High Court certification framework but does not draft the SLP itself (the sibling plugin `supreme-court-drafting` covers SLPs).

### 4. `section-12a-registration-form-10a-draft`

**Statutory authority:** Income-tax Act 1961 — Section 12A (conditions for applicability of Section 11 and Section 12 to a charitable or religious trust / institution) + Section 12AB (post-Finance-Act-2020 procedure for registration of trusts and institutions, replacing the old Section 12AA regime — every existing registered trust required to re-apply within the prescribed window) + Section 13 (denial of exemption); Income-tax Rules 1962 — Rule 17A (Form 10A layout) + Rule 17AA (procedure for verification and grant of registration). **Use case:** charitable trust / religious trust / Section 8 company / society registered under the Societies Registration Act 1860 / public trust registered under the Maharashtra Public Trusts Act 1950 or other State Public Trust Act, seeking (a) provisional registration under Section 12AB for a newly formed entity, (b) regular registration on conversion of provisional registration, or (c) re-registration under the post-2020 regime for an existing Section 12A / 12AA registered trust. **Output:** complete Form 10A application with the Rule 17A layout, the Particulars block (Name of the applicant trust / institution / Date of creation / Address / PAN / Authorised signatory / Section under which application is made), the Statement of Objects (charitable purposes within Section 2(15)), the Statement of Activities, the Certificate from the auditor where applicable, the accompanying documents (Trust Deed / Memorandum of Association / Society Registration Certificate / Income-tax returns of last three years / annual accounts of last three years / list of trustees with PAN), the Verification, and the procedural endnotes (electronic filing on the Income-tax e-filing portal, digital signature).

### 5. `section-148a-reopening-objection-draft`

**Statutory authority:** Income-tax Act 1961 — Section 147 (income escaping assessment) + Section 148 (issue of notice for reassessment) + Section 148A (procedure before issue of notice — show-cause-and-hearing mandate introduced by the Finance Act 2021) + Section 149 (time limits for reassessment notice — three years and six years schemes) + Section 151 (sanction for issue of notice); read with the Supreme Court's direction in *Union of India v. Ashish Agarwal* (4 May 2022) on the transitional reassessment regime — pre-01-04-2021 reassessment notices issued under the unamended Section 148 were retrospectively converted to Section 148A(b) show-cause notices, with directions on the procedure to be followed thereafter; subsequent High Court litigation across Allahabad, Delhi, Bombay, Calcutta, Gujarat, Madras, and the Income-tax Appellate Tribunal lineage on the contours of *Ashish Agarwal*. **Use case:** assessee in receipt of a Section 148A(b) show-cause notice asking why a notice under Section 148 should not be issued — the assessee files a reply within the prescribed window (typically two weeks, extendable). **Output:** complete reply to the Section 148A(b) notice with the chronology of the original return, the original assessment (if any), the year-wise re-evaluation of "information suggesting income chargeable to tax has escaped assessment" within the meaning of Explanation 1 to Section 148, the response to each fact alleged by the Department, the legal grounds (no information that meets the Explanation-1 standard / change of opinion / barred by limitation / sanction-defect under Section 151 / *Ashish Agarwal* transitional-regime defect / reasons-recorded defect), the prayer that no notice under Section 148 be issued, the prayer for a personal hearing under Section 148A(b) proviso, and the Verification.

### 6. `section-271-270a-penalty-reply-draft`

**Statutory authority:** Income-tax Act 1961 — Section 270A (penalty for under-reporting and misreporting of income — applies to assessment years 2017-18 onwards) + Section 270AA (immunity from penalty on payment of tax and interest and on filing application within one month from end of the month in which order is received) + Section 271(1)(c) (legacy concealment / inaccurate particulars penalty — applies to assessment years up to and including 2016-17) + Section 274 (procedure — opportunity of hearing and confining the penalty proceeding) + Section 275 (bar of limitation for penalty); read with the Supreme Court framework in *CIT v. Reliance Petroproducts Pvt. Ltd.* (2010) 322 ITR 158 (incorrect claim does not amount to furnishing inaccurate particulars), *T. Ashok Pai v. CIT* (2007) 292 ITR 11 (the strict construction of penal provisions), and the Bombay High Court line in *CIT v. Samson Perinchery* (2017) on the requirement of specifying the limb under Section 271(1)(c) in the show-cause notice. **Use case:** assessee in receipt of a penalty show-cause notice under Section 270A read with Section 274 (for AY 2017-18 onwards) or Section 271(1)(c) read with Section 274 (for legacy years) — the assessee files a reply within the prescribed window. **Output:** complete reply to the penalty show-cause notice with the chronology of the assessment, the response to each ingredient of "under-reporting" within the meaning of Section 270A(2) and the corresponding response to "misreporting" within the meaning of Section 270A(9) (or for legacy notices, the response to concealment and to inaccurate particulars with a Samson Perinchery limb-specification challenge), the immunity election under Section 270AA where eligible, the legal grounds (debatable issue / two-views-possible doctrine / *Reliance Petroproducts* incorrect-claim doctrine / explanation-bona-fide-and-reasonable doctrine under Explanation 1(B) to Section 271(1)(c) or its counterpart in Section 270A(6)), the prayer that the penalty proceeding be dropped, and the Verification.

### 7. `section-263-revision-objection-draft`

**Statutory authority:** Income-tax Act 1961 — Section 263 (revision by Principal Commissioner / Commissioner of any order passed by an Assessing Officer that is erroneous in so far as it is prejudicial to the interests of revenue); read with the Supreme Court framework in *Malabar Industrial Co. Ltd. v. CIT* (2000) 243 ITR 83 (twin conditions — erroneous AND prejudicial to revenue — both must be satisfied), *CIT v. Max India Ltd.* (2007) 295 ITR 282 (one of two views permissible to AO is not erroneous), and *CIT v. Greenworld Corporation* (2009) 314 ITR 81 (revision cannot substitute the AO's view with the PCIT's). **Use case:** assessee in receipt of a Section 263 show-cause notice from the PCIT / CIT proposing to revise an order of the AO — the assessee files a reply within the prescribed window. **Output:** complete reply to the Section 263 show-cause notice with the chronology of the assessment, the response to the Department's case that the AO's order is "erroneous in so far as prejudicial to revenue" (the *Malabar Industrial* twin-condition response — both prongs must be defeated separately), the legal grounds (full enquiry conducted by the AO / one-of-two-views permissible / change-of-opinion bar / lack of jurisdiction under Section 263 / Explanation 2 to Section 263 inapplicable on facts), the prayer that the proposed revision be dropped, and the Verification.

### 8. `section-264-revision-application-draft`

**Statutory authority:** Income-tax Act 1961 — Section 264 (revision of any order by the Principal Commissioner / Commissioner on the application of the assessee, subject to limitation under Section 264(3) — one year from the date of the order — and to the bar in Section 264(4) where the order is the subject of an appeal). **Use case:** assessee aggrieved by an order of the AO and electing the Section 264 revisional remedy in lieu of the Section 246A appellate remedy (e.g. where the appellate remedy is barred by limitation or where the issue is purely on a question of law and the assessee prefers the lighter revisional remedy). **Output:** complete Section 264 application with the Particulars block, the chronology of the order under revision, the grounds for revision (mistake apparent from the record / order contrary to law / order based on wrong facts), the assessee's election under Section 264(4) that the order is not the subject of any appeal pending or disposed of, the prayer for revision, the Verification, the filing fee per the prescribed schedule, and the accompanying documents (copy of the order under revision, return and assessment particulars, evidence relied upon).

### 9. `section-201-tds-default-reply-draft`

**Statutory authority:** Income-tax Act 1961 — Section 200 (duty of deductor to deposit tax deducted at source) + Section 201 (deductor deemed assessee-in-default on failure to deduct or pay TDS) + Section 201(1A) (interest on TDS default — 1% per month for failure to deduct, 1.5% per month for failure to pay) + Section 194 family (Section 194A interest, 194C contractor, 194H commission, 194I rent, 194J professional fees, 194Q purchase of goods, etc.) + the proviso to Section 201(1) (no Section 201 default if the deductee has furnished a return under Section 139, taken the amount into total income, paid tax on it, and the deductor furnishes a certificate in the prescribed form) + Section 271C (penalty for failure to deduct TDS) read with Section 273B (no penalty on reasonable cause); CBDT public-domain Circulars on TDS reasonable cause. **Use case:** deductor in receipt of a Section 201 / 201(1A) show-cause notice from the AO (TDS) — the deductor files a reply within the prescribed window. **Output:** complete reply with the chronology of the TDS deposit, the response to each alleged default (deductee-side-paid-tax defence under the proviso to Section 201(1) with the Section 197 certificate exhibit / contractor-vs-employee re-characterisation defence / non-resident-TDS defence under Section 195 with the *GE India Technology* and *Vodafone* line / reasonable-cause defence under Section 273B), the prayer that the proposed Section 201 / 201(1A) demand be dropped, and the Verification.

### 10. `section-144c-drp-objection-draft`

**Statutory authority:** Income-tax Act 1961 — Section 144C (Dispute Resolution Panel — eligible assessee, draft assessment order, objections within 30 days, DRP direction binding on AO under Section 144C(13)) + Section 92CA (reference to Transfer Pricing Officer); Income-tax Rules 1962 — Rule 44CA (procedure of DRP); read with the Supreme Court / High Court line on DRP procedure including *Sony India* line at the High Court of Delhi and the Bombay High Court line on the binding character of DRP directions. **Use case:** eligible assessee (any person in whose case Transfer Pricing variation has been proposed, OR a non-resident not being a company / foreign company) in receipt of a draft assessment order under Section 144C(1) — files objection before the DRP within 30 days. **Output:** complete DRP objection with the Particulars block (Name / PAN / Assessment Year / AO designation / TPO designation / DIN of the draft assessment order), the Statement of Facts (the transfer-pricing reference and the TPO order under Section 92CA, the draft assessment order under Section 144C(1)), the Objections numbered consecutively with the corresponding ground of appeal, the international-tax / transfer-pricing arguments (selection of comparables / arm's-length-price methodology — TNMM / CUP / RPM / CPM / PSM under Section 92C / functions-assets-risks analysis), the Relief sought (variation rejected / DRP-direction to AO to drop the variation), the Verification, and the accompanying documents (Form 3CEB, the TP study report, the comparables data, the TPO order under Section 92CA, the draft assessment order under Section 144C(1)).

### Shared infrastructure skills

- **`_drafting_common`** — anti-pollution rules, direct-tax-specific privacy firewall, AI-style-marker blacklist, citation discipline, **statutory currency rules** (CrPC → BNSS / IEA → BSA where penal cross-cites arise; Section 147/148 → Section 148A regime conversion check; Section 12A → Section 12AB post-2020 conversion check; Section 271(1)(c) → Section 270A AY-2017-18-onwards conversion check), **Form-correspondence rules** (Form 35 / Rule 45, Form 36 / Rule 47, Form 10A / Rule 17A, Form 36A / cross-objection), **limitation map** (Section 249(2) CIT(A) 30 days, Section 253(3) ITAT 60 days, Section 260A(2) HC 120 days, Section 144C(2) DRP 30 days), **DIN-presence rule** (CBDT Circular No. 19/2019 — every order issued after 01-10-2019 carries a DIN), **PAN-format rule**, **assessment-year vs financial-year discipline**, **faceless-vs-physical jurisdiction discipline**.
- **`_tax_drafting_base`** — universal Indian direct-tax pleading skeleton built on the statutory Form layout discipline (Form identifier + Rule reference → Descriptive title → Particulars block → Statement of Facts where applicable → Grounds of Appeal → Relief Claimed → Verification → Signature block → Procedural endnotes).

---

## The 6-agent drafting pipeline

| Agent | What it reads | What it writes | Key direct-tax specialisation |
|---|---|---|---|
| **`reader`** | Every file in the case folder + the case-type skill's expected enclosure list | `case-facts.md` with per-document audit log + privacy-firewalled placeholder mapping in the header | Privacy firewall — substitutes assessee names + PAN + Aadhaar + TAN + AO names + DIN + financial figures + case-number references before downstream AI processing; mapping stored locally only |
| **`format`** | `case-facts.md` + `case-config.md` + case-type SKILL.md + `_tax_drafting_base` | `format-shell.md` with forum / Form identifier / Rule reference / case-number prefix / filing-fee slab / statutory opening / limitation anchor pre-substituted | Resolves CIT(A) vs ITAT vs High Court Tax Bench vs PCIT / CIT vs DRP forum nomenclature for the Cause Title; resolves Form 35 vs Form 36 vs Form 10A layout for the body |
| **`drafter`** | `case-facts.md` + `format-shell.md` + case-type SKILL.md + `_tax_drafting_base` + law PDFs | `draft-v1.md` + `draft-v1.docx` | Writes the statutory Form layout, Particulars block, Statement of Facts where applicable, Grounds of Appeal numbered consecutively with statutory anchor for each ground, Relief Claimed, Verification, Signature block, Procedural endnotes, and accompanying applications |
| **`verifier`** | `draft-v1.md` + `case-facts.md` + `case-config.md` + law PDFs | `verification-report.md` | Anti-hallucination + statutory-currency (Section 148A regime / Section 12AB regime / Section 270A regime / BNSS / BSA) + Form-layout fidelity (Form 35 / Rule 45, Form 36 / Rule 47, Form 10A / Rule 17A) + limitation map check + filing-fee scaling check + DIN-presence check + PAN-format check + assessment-year vs financial-year discipline check + faceless-vs-physical jurisdiction check |
| **`refiner`** | `draft-v1.md` + `verification-report.md` + `case-config.md` + `case-facts.md` | `draft-v2.md` + `draft-v2.docx` | Polish to Indian tribunal / court formal register + internal numbering / cross-reference consistency + privacy-firewall reversal (real values re-substituted from local mapping into final `.docx`) |
| **`overseer`** | `draft-v2.docx` + `case-facts.md` + `case-config.md` | `opposing-notes.md` + `final-draft.docx` | Opposing-counsel critique — weak grounds, missing statutory anchors, broken limitation, scope-creep under Rule 46A or Rule 29 ITAT Rules 1963, missing Section 270AA immunity election where eligible, missing Section 144C(13) binding-direction argument, *Malabar Industrial* twin-condition deficiencies in a Section 263 reply, *Ashish Agarwal* transitional-regime gaps in a Section 148A objection, Section 220(6) stay-pendente-lite gaps |

---

## Installation

This is a Claude-compatible plugin in the Anthropic plugin format, designed to run inside the **Claude Desktop application** (available at <https://claude.ai/download>). The plugin folder location depends on your OS:

| OS | Plugin folder path |
|---|---|
| **macOS** | `~/Library/Application Support/Claude/plugins/` |
| **Windows** | `%APPDATA%\Claude\plugins\` (typically `C:\Users\<you>\AppData\Roaming\Claude\plugins\`) |
| **Linux** | `~/.config/Claude/plugins/` |

Clone the plugin into that folder:

```bash
# macOS / Linux
mkdir -p ~/Library/Application\ Support/Claude/plugins   # adjust per OS table
cd ~/Library/Application\ Support/Claude/plugins
git clone https://github.com/Wolfgangrush/indian-tax-drafting.git indian-tax-drafting

# Windows (PowerShell)
mkdir -Force $env:APPDATA\Claude\plugins
cd $env:APPDATA\Claude\plugins
git clone https://github.com/Wolfgangrush/indian-tax-drafting.git indian-tax-drafting
```

Restart the Claude Desktop application. The plugin is auto-discovered on the next session start.

### Anthropic Plugin Marketplace (when available)

When the plugin lands on the Anthropic Plugin Marketplace, you will be able to install it from inside the application's plugin browser without `git`. Until then, the manual clone steps above are canonical.

### Verifying the install

In a Claude session, type:

- *"draft Form 35 CIT(A) appeal"* — triggers `cit-appeals-form-35-draft`
- *"draft Form 36 ITAT appeal"* — triggers `itat-appeal-form-36-draft`
- *"draft Section 260A High Court appeal"* — triggers `high-court-appeal-section-260a-draft`
- *"draft Form 10A 12A registration"* — triggers `section-12a-registration-form-10a-draft`
- *"draft Section 148A objection"* / *"draft reopening objection"* — triggers `section-148a-reopening-objection-draft`
- *"draft penalty reply Section 270A"* / *"draft Section 271(1)(c) reply"* — triggers `section-271-270a-penalty-reply-draft`
- *"draft Section 263 objection"* — triggers `section-263-revision-objection-draft`
- *"draft Section 264 revision"* — triggers `section-264-revision-application-draft`
- *"draft Section 201 TDS default reply"* — triggers `section-201-tds-default-reply-draft`
- *"draft DRP objection Section 144C"* — triggers `section-144c-drp-objection-draft`

---

## Your first pleading — step-by-step walkthrough

Suppose you wish to draft a **CIT(Appeals) Form 35 appeal** under Section 246A against an Assessing Officer's order under Section 143(3) for Assessment Year 2024-25, where the AO has made an addition to income on account of unexplained credits under Section 68.

### Step 1 — create a case folder

```
~/Desktop/cases/
└── cit-appeals-2026-AY-2024-25-section-68/
    ├── case-config.md         ← declares forum + AY + DIN + AO + order under appeal
    ├── inputs/
    │   ├── assessment-order-section-143-3.pdf
    │   ├── show-cause-notice-pre-assessment.pdf
    │   ├── reply-to-show-cause.pdf
    │   ├── return-of-income.pdf
    │   ├── computation-of-income.pdf
    │   ├── audit-report-form-3cd.pdf
    │   ├── ledger-extract-credits.pdf
    │   ├── confirmation-from-creditors.pdf
    │   ├── bank-statements.pdf
    │   ├── demand-notice-section-156.pdf
    │   └── form-26-authority-and-vakalatnama.pdf
    └── laws/
        ├── income-tax-act-1961.pdf
        ├── income-tax-rules-1962.pdf
        ├── faceless-appeal-scheme-2021.pdf
        └── cbdt-circular-19-2019-din.pdf
```

### Step 2 — write `case-config.md`

```yaml
forum: "Commissioner of Income-tax (Appeals), National Faceless Appeal Centre, Delhi"
case_type: "cit-appeals-form-35"
case_number_year: 2026
assessment_year: "2024-25"
financial_year: "2023-24"
order_under_appeal:
  section: "143(3)"
  date_of_order: "[Date-of-Order-Placeholder]"
  date_of_service: "[Date-of-Service-Placeholder]"
  din: "[DIN-Placeholder]"
  assessing_officer:
    designation: "Assessing Officer, National Faceless Assessment Centre"
    ward_or_circle_or_range: "[Faceless-Centre-Placeholder]"
total_income_assessed: "[Total-Income-Assessed-Placeholder]"
demand_under_section_156: "[Demand-Placeholder]"
filing_fee_slab: "verify-against-current-Section-249(1)-notification"
limitation_anchor:
  statute: "Section 249(2) of the Income-tax Act 1961"
  days: 30
  date_of_service_of_order: "[Date-of-Service-Placeholder]"
  date_of_filing: "[Date-of-Filing-Placeholder]"
condonation_of_delay_needed: false
assessee:
  name: "[Assessee-Name-Placeholder]"
  pan: "[PAN-Placeholder]"
  aadhaar_linked_pan: "linked"
  status: "Individual"           # or HUF / Firm / LLP / Company / AOP / Trust
  address: "[Address-Placeholder]"
  authorised_signatory: "[Authorised-Signatory-Placeholder]"
authorised_representative:
  name: "[AR-Name-Placeholder]"
  enrolment: "Advocate, Bar Council of [State]"
  vakalatnama_filed: true
faceless_or_physical: "faceless"
```

### Step 3 — invoke the plugin

Open Claude Desktop, navigate to the case folder, and type:

> *draft Form 35 CIT(A) appeal*

The pipeline runs:

1. **Reader** reads every PDF in `inputs/`, builds `case-facts.md` with privacy-firewalled placeholder mapping, validates that all required statutes are in `laws/`.
2. **Format** loads the `cit-appeals-form-35-draft` skill, reads `case-config.md`, builds `format-shell.md` with the Rule 45 / Form 35 layout pre-rendered.
3. **Drafter** writes `draft-v1.md` and `draft-v1.docx` — the Form 35, the Particulars block, the Statement of Facts on the Section 68 addition, the Grounds of Appeal numbered, the Relief Claimed, the Verification.
4. **Verifier** reads `draft-v1.md` against `case-facts.md`, checks limitation under Section 249(2), checks filing-fee scaling under Section 249(1), checks DIN-presence, checks PAN-format, writes `verification-report.md`.
5. **Refiner** applies the verification flags, polishes the prose, re-substitutes real values, writes `draft-v2.docx`.
6. **Overseer** reads `draft-v2.docx` with a Departmental-Representative lens, writes `opposing-notes.md` and `final-draft.docx`.

The advocate now reviews `final-draft.docx` against `opposing-notes.md`, makes professional adjustments, applies the filing fee, signs the verification, and electronically files via the Income-tax e-filing portal (where Faceless Appeal Scheme 2021 applies) or physically files where the appeal lies before a physical-bench CIT(A).

---

## The `case-config.md` file

This file declares all forum-level / case-type-level / matter-level constants that the plugin substitutes into the format shell. Keep it on the user's local machine — `.gitignore` excludes it from any git repo.

Minimum fields:

- `forum` — exact name of the appellate authority / tribunal / court (e.g. *"Commissioner of Income-tax (Appeals), National Faceless Appeal Centre, Delhi"* / *"Income-tax Appellate Tribunal, [Bench], [City]"* / *"High Courts of India"* / *"Principal Commissioner of Income-tax, [City]"* / *"Dispute Resolution Panel, [Seat]"*)
- `case_type` — one of the ten supported case types
- `case_number_year`
- `assessment_year` — in format YYYY-YY
- `financial_year` — in format YYYY-YY
- `order_under_appeal` — section + date of order + date of service + DIN + AO designation
- `total_income_assessed` — the figure (placeholder until Refiner re-substitution)
- `demand_under_section_156` — the figure (placeholder until Refiner re-substitution)
- `filing_fee_slab` — pointer to current notification
- `limitation_anchor` — statute + days + date of service + date of filing + condonation-needed flag
- `assessee` — name / PAN / Aadhaar-linked-PAN status / status (Individual / HUF / Firm / LLP / Company / AOP / Trust) / address / authorised signatory
- `authorised_representative` — name / enrolment / Vakalatnama-filed flag
- `faceless_or_physical` — *faceless* / *physical*

Case-type-specific fields (for the relevant skill) layer on top of the minimum schema — see each case-type SKILL.md.

---

## Built-in compliance disciplines

The Verifier enforces several disciplines mandatory in Indian direct-tax practice — see `skills/_drafting_common/SKILL.md` for the full discipline framework. Headline disciplines:

- **Form-correspondence discipline** — Form 35 strictly follows the Rule 45 layout, Form 36 strictly follows the Rule 47(1) layout, Form 10A strictly follows the Rule 17A layout; the Drafter does not deviate from the statutory Form, and the Verifier catches any deviation.
- **Section 148A regime currency discipline** — any reference to Section 147 / 148 without the Section 148A flag is caught as legacy-pre-Finance-Act-2021 and the Verifier flags for conversion to the post-Finance-Act-2021 regime.
- **Section 12AB regime currency discipline** — any reference to Section 12AA registration is caught as legacy-pre-Finance-Act-2020 and the Verifier flags for conversion to the Section 12AB regime.
- **Section 270A vs Section 271(1)(c) discipline** — assessment years up to 2016-17 fall under Section 271(1)(c); 2017-18 onwards fall under Section 270A; the Verifier catches mis-applied section reference.
- **Limitation map** — Section 249(2) CIT(A) 30 days, Section 253(3) ITAT 60 days, Section 260A(2) HC 120 days, Section 144C(2) DRP 30 days, Section 264(3) revision 1 year — Verifier checks limitation compliance and prompts for condonation-of-delay application where applicable.
- **Filing-fee scaling discipline** — Section 249(1) (CIT(A) scaled by total assessed income) and Section 253(6) (ITAT scaled by total assessed income) — Verifier flags any fee figure with "verify against current notification" since CBDT fee thresholds are periodically amended.
- **DIN-presence discipline** — CBDT Circular No. 19/2019 mandates a Document Identification Number on every Income-tax authority order issued on or after 01-10-2019; the Verifier checks that the DIN of the order under appeal is captured in the Particulars block.
- **PAN-format discipline** — PAN is a ten-character alphanumeric in the AAAAA9999A format; the Verifier checks PAN-format of every PAN in the Particulars block.
- **Assessment-year vs financial-year discipline** — Indian direct-tax pleadings frequently conflate the two; the Verifier catches AY / FY conflation and flags for correction.
- **Faceless-vs-physical jurisdiction discipline** — Faceless Appeal Scheme 2021 governs CIT(A) appeals in all cases except those expressly excluded; the Verifier flags any pleading that addresses a physical-bench CIT(A) where the matter properly lies before the National Faceless Appeal Centre, and vice versa.
- **Statutory-currency discipline (penal cross-cites)** — where Section 271AAA / 271AAB / 277 / 277A references arise alongside CrPC procedural cross-cites, CrPC 1973 references are converted to BNSS 2023 in any pleading filed post-BNSS-commencement; IEA 1872 references converted to BSA 2023.
- **Section 270AA immunity election discipline** — for any Section 270A penalty reply, the Verifier flags whether the assessee is eligible to elect immunity under Section 270AA (return-and-tax-paid + application within one month from end of the month of receipt of order + no appeal pending) and prompts for the immunity application as accompanying relief.

---

## Privacy firewall — extra discipline for direct-tax content

Direct-tax pleadings contain some of the most sensitive material an advocate handles — KYC of the assessee, PAN, Aadhaar-linked-PAN status, TAN, complete financial figures (total income / income from each head / additions and disallowances / penalty quantum / demand under Section 156), DIN of the order under appeal, AO identity and designation, faceless-centre designation, audit-report references, transfer-pricing data, deductee particulars. Section 138 of the Income-tax Act 1961 protects taxpayer-specific information at the Department's end; the plugin's discipline mirrors this:

1. **Reader** substitutes every assessee name, every PAN, every Aadhaar reference, every TAN, every Assessing-Officer name, every faceless-centre designation, every DIN, every quantum figure, and every authorised-signatory name with structural placeholders before downstream processing.
2. The placeholder → real-value mapping is stored in the header of `case-facts.md` on the user's local machine **only**.
3. **Format / Drafter / Verifier / Overseer** operate **only** on placeholder-substituted content. The underlying AI runtime never holds raw PANs or raw financial figures.
4. **Refiner** re-substitutes real values into the final `.docx`, strictly on the user's machine.
5. `.gitignore` excludes `case-facts.md` and `case-config.md` so they cannot be committed accidentally.

The user can verify the firewall by inspecting `case-facts.md` after the Reader runs — every assessee name appears as `[Assessee-A]`, every PAN as `[PAN-Placeholder]`, every DIN as `[DIN-Placeholder]`, every quantum figure as `[Quantum-Placeholder]`. The mapping is in the header of the same file.

---

## Why MIT License

The MIT licence is the most permissive widely-recognised open-source licence. Anyone may use, modify, distribute, sublicense, or sell the plugin or any derivative. The licence is short, well-understood, and compatible with every other open-source licence the legal community is likely to encounter. No proprietary gating, no field-of-use restriction, no contributor licence agreement (CLA) gymnastics. The accompanying `NOTICE.md` does not modify the licence — it documents the provenance and the privilege position so that any future audit can verify the plugin's clean origin.

---

## Sibling plugins

This plugin is one in the **wolfgang_rush** family of Indian legal-drafting plugins. All thirteen siblings ship under the same six-agent pipeline (Reader → Format → Drafter → Verifier → Refiner → Overseer) and the family-of-plugins doctrine — each plugin narrowly scoped to one practice area / forum:

| Plugin | GitHub repo | Scope |
|---|---|---|
| `supreme-court-drafting` | [supreme-court-drafting-litigation](https://github.com/Wolfgangrush/supreme-court-drafting-litigation) | SLPs · Writ Art 32 · Transfer · Review · Curative — Supreme Court of India |
| `indian-hc-drafting` | [indian-hc-drafting-litigation](https://github.com/Wolfgangrush/indian-hc-drafting-litigation) | Pleadings across all 25 Indian High Courts (bench-config-aware) |
| `district-court-drafting` | [district-court-drafting-litigation](https://github.com/Wolfgangrush/district-court-drafting-litigation) | Plaints · WS · CPC applications · BNSS complaints across 25+ States (state-config) |
| `indian-family-drafting` | [indian-family-drafting-litigation](https://github.com/Wolfgangrush/indian-family-drafting-litigation) | HMA · SMA · IDA · matrimonial · custody · DV Act · maintenance · adoption |
| `indian-contracts-drafting` | [indian-contracts-drafting-litigation](https://github.com/Wolfgangrush/indian-contracts-drafting-litigation) | MSA · NDA · employment · lease · sale · GPA · SHA · will · loan · arbitration |
| `indian-banking-drafting` | [indian-banking-drafting-litigation](https://github.com/Wolfgangrush/indian-banking-drafting-litigation) | DRT · SARFAESI · NI Act 138 · IBC §7 / §95 · DRAT |
| `indian-labour-drafting` | [indian-labour-drafting-litigation](https://github.com/Wolfgangrush/indian-labour-drafting-litigation) | ID Act · POSH · PG · EPF · ESI · MW · IESO + State exemplars |
| `indian-property-drafting` | [indian-property-drafting-litigation](https://github.com/Wolfgangrush/indian-property-drafting-litigation) | Gift · Exchange · Release · Trust · Wakf · Easement · Partition · Settlement · Mortgage · TIR |
| `indian-company-drafting` | [indian-company-drafting](https://github.com/Wolfgangrush/indian-company-drafting) | NCLT (241/242 · 245 · 230-232 · 66 · 252 · 213) · NCLAT (421 + 61) · IBC §9 / §10 |
| `indian-tax-drafting` (this) | [indian-tax-drafting](https://github.com/Wolfgangrush/indian-tax-drafting) | Form 35 CIT(A) · Form 36 ITAT · Form 10A · Sec 148A · 263/264 · 271/270A · 144C · 201 · 260A |
| `indian-consumer-drafting` | [indian-consumer-drafting](https://github.com/Wolfgangrush/indian-consumer-drafting) | District / State / NCDRC + medical-negligence + product liability |
| `indian-mact-drafting` | [indian-mact-drafting](https://github.com/Wolfgangrush/indian-mact-drafting) | MV Act 1988 (2019 amended) · Sarla Verma + Pranay Sethi · state-config |
| `indian-ip-drafting` | [indian-ip-drafting](https://github.com/Wolfgangrush/indian-ip-drafting) | Copyright · Trade Marks · Patents · Designs + HC IP Divisions (post-IPAB-abolition) + Anton Piller / John Doe |

Each plugin can be installed independently, each plugin's Rule 36 firewall is narrow and reviewable, each plugin's bench / forum discipline is depth-validated within its scope, and the user installs only what they need.

---

## Why this exists

Indian direct-tax appellate practice currently has no open-source pleading-drafting infrastructure. Practising advocates piece together pleadings from their own past drafts, from senior advocates' templates, from the various textbook precedent collections (Sampath Iyengar, Chaturvedi & Pithisaria, Kanga Palkhivala Vyas), and from such precedent volumes as the publishers issue from time to time. The result is uneven quality, uneven compliance with the latest statutory-currency rules (Section 148A reassessment regime, Section 12AB registration regime, Section 270A penalty regime, Faceless Appeal Scheme 2021), uneven discipline on the limitation map (30 / 60 / 120 days across forums) and on the filing-fee slabs (CBDT-amended periodically), and routine omissions that the Departmental Representative or Senior Standing Counsel exploits.

A plugin that codifies the procedural skeletons + the statutory-currency rules + the Verifier-side discipline + the privacy firewall is the first piece of infrastructure that the Indian direct-tax appellate practice has had — the second piece is community contribution from advocates who file regularly before specific ITAT benches and High Court Tax Benches and who deepen the bench-specific Practice Directions discipline.

Foreign legal-AI tools cannot fill this gap. The procedural conventions are jurisdiction-specific; the statutory framework is Income-tax Act 1961 + Income-tax Rules 1962 + ITAT Rules 1963 + Faceless Schemes which no foreign training data has indexed at depth; the filing requirements at the e-filing portal and at the ITAT Registry are matters of bench practice that no foreign tool has encountered.

This plugin opens that door.

---

## Roadmap

- [x] **v0.1.0-alpha (current)** — universal direct-tax pleading skeleton + 10 case-type skills + 6-agent pipeline + privacy firewall + Verifier disciplines + 0 bench-specific exemplars
- [ ] **v0.1.x** — bug fixes, quality-gate iteration, language-register polish, formatting refinements driven by user feedback
- [ ] **v0.x onward** — bench-specific Practice Direction calibration deepening per ITAT bench (Mumbai / Delhi / Chennai / Kolkata / Bangalore / Ahmedabad / Hyderabad / Pune / [bench city]) and per High Court Tax Bench, additional case-type skills (Section 154 rectification application / Section 220(6) stay application / Section 154 vs Section 263 election advisories / Section 273A waiver / Section 245C settlement application / Direct-Tax Vivad-se-Vishwas application where revived), and procedural-rule updates as CBDT notifications arrive
- [ ] **v1.0.0** — stable release after community-validated formatting and field-testing

Per-bench deep validation will arrive in the order advocates contribute. The plugin's case-config architecture means any advocate filing regularly before a given ITAT bench or High Court Tax Bench can deepen the calibration for that bench by opening an issue or pull request with their bench's idiom — no central roadmap is needed to enable that. The roadmap above is therefore intentionally open-ended.

---

## Contributing

Advocates with regular direct-tax appellate practice are invited to contribute bench-config calibration for the specific tribunal / court they practise before. Open a GitHub issue with:

- Your practice bench (e.g., *"ITAT Mumbai Bench A"* / *"ITAT Delhi Bench D"* / *"Bombay High Court Tax Bench"*)
- Your bench's Cause Title format
- Your bench's case-number convention
- Your bench's filing-counter conventions (paper-book pagination / annexure markers / Index format / verification format / language-option-Hindi where notified)
- Recent Practice Directions issued by the bench affecting pleading format

Pull requests are welcome with a one-paragraph explanation of the change and a reference to the bench rule or Practice Direction that justifies it.

This plugin is open source under MIT.

---

## Contact

Author and maintainer: **Rushikesh R. Mahajan**, Advocate, enrolled with the Bar Council of Maharashtra and Goa.

GitHub: <https://github.com/Wolfgangrush>

Issues raised with reproducible context are handled on a best-effort basis; this is an open-source contribution maintained outside the author's professional engagements and does not constitute a vehicle for legal services.

---

## Author and brand

The author is **Rushikesh R. Mahajan**, Advocate, practising before the High Courts of India. The plugin is published under the open-source brand **wolfgang_rush**, which is the author's publishing handle for legal-technology infrastructure. Personal accountability under the Advocates Act 1961 attaches to the author regardless of the use of a publishing handle.

---

## Provenance and privilege statement

See `NOTICE.md` for the full provenance + privilege + privacy + Rule 36 compliance statement. The short version:

- The plugin contains only universal procedural skeletons, formatting conventions, statutory references, and generic placeholders
- The plugin contains no specific assessee matter, no client communications, no client documents, no personal data of any data principal, and no tracking / telemetry / analytics
- The plugin is, in legal character, identical to a published direct-tax-law textbook — procedural knowledge in machine-readable form
- The author retains full enrolment, full responsibility, and full liability under the Advocates Act 1961 and the Bar Council of India Rules

---

## Compliance posture — Supreme Court e-Committee AI framework

This plugin is **assistive drafting infrastructure**, not autonomous decision-making software. Its operational posture is aligned with the Supreme Court of India e-Committee's stated position on AI in legal work.

> *"AI and digital tools must be used as supportive instruments and should not be allowed to override judicial reasoning."*
>
> — **Justice Rajesh Bindal**, Judge, Supreme Court of India
> [*Judicial Process Re-engineering and Digital Transformation*](https://www.sci.gov.in/press-release-dated-april-12-2026/) conference, 11–12 April 2026
> Organised by the Supreme Court e-Committee in collaboration with the Department of Justice, Government of India.
> ([Coverage — Law Trend](https://lawtrend.in/ai-must-not-replace-judicial-reasoning-warns-supreme-court-justice-rajesh-bindal/))

The same posture underpins the Supreme Court's own AI infrastructure for the judiciary:

- **[SUPACE](https://www.drishtiias.com/daily-news-analysis/ai-portal-supace)** — *Supreme Court Portal for Assistance in Court Efficiency.* AI-enabled assistive tool launched on 6 April 2021 by then-CJI S.A. Bobde. Provides legal research, fact extraction, document review, and drafting assistance to judges and legal researchers. **By design, SUPACE is not a decision-making system** — it processes facts and surfaces them to the human user. The Supreme Court has recommended adoption across all Indian High Courts.

- **[SUVAS](https://www.drishtijudiciary.com/current-affairs/supreme-court-vidhik-anuvaad-software-suvas)** — *Supreme Court Vidhik Anuvaad Software.* AI-powered translation tool launched in November 2019 by then-CJI S.A. Bobde. Translates judicial documents, orders, and judgments between English and ten Indian regional languages.

### What this plugin does — and does not — do under that framework

**Does:**

- Generate structural skeletons of pleadings, drawing on public statutes, schedule forms, and court rules.
- Run a six-agent assistive pipeline (Reader → Formatter → Drafter → Verifier → Refiner → Overseer) over the user's case facts.
- Surface citations, procedural anchors, and bench-specific conventions for advocate review.

**Does NOT:**

- Generate final filings autonomously.
- Substitute for advocate professional judgment.
- Replace human verification.
- Operate without an enrolled advocate retaining full professional responsibility.

**Every draft produced through this plugin must be advocate-owned and human-verified before filing.** The enrolled advocate using this plugin retains full professional responsibility under the Advocates Act 1961 and the Bar Council of India Rules, including verification of facts, accuracy of citations, correctness of legal grounds, propriety of the prayer, and signature on every pleading filed.

This is the same standard the Supreme Court itself applies to its own AI infrastructure (SUPACE / SUVAS): **AI as supportive instrument, never as decision-maker.**

---

## Disclaimer and Bar Council of India Rule 36 compliance

This repository is published as a personal open-source contribution to the legal-technology ecosystem. It is **not** an advertisement of professional services, **not** a solicitation of work, **not** an undertaking to act as counsel in any matter, and **not** a vehicle through which the author accepts professional engagement.

Bar Council of India Rule 36 of the Standards of Professional Conduct and Etiquette prohibits an advocate from soliciting work or advertising professional services through any medium. This repository complies with Rule 36 in both letter and spirit:

- No commercial offering is made through this repository
- No representation of professional results is made
- No invitation to engage the author professionally is made
- The README contains no contact details inviting professional retainer

The plugin is published in the same legal character as any practitioner's open-source library, public continuing-legal-education contribution, or published textbook chapter — the medium is software, the content is procedural knowledge, the practitioner retains full Bar discipline and accountability.

---

## License

MIT — see `LICENSE`.
