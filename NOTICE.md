# NOTICE — Provenance and Privilege Statement

This document is part of the public release of the `indian-tax-drafting` plugin (v0.1.0-alpha and onwards). It declares the provenance of the plugin's content, in order to address any question about advocate-client privilege, client confidentiality, professional ethics, personal-data protection, taxpayer confidentiality under Section 138 of the Income-tax Act 1961, and commercial confidentiality that may be raised by any reader, complainant, regulator, or Bar Council disciplinary authority.

The plugin is **case-config-aware**: the universal structural skeleton of any Indian direct-tax appellate pleading is uniform, and the parties' chosen forum (Commissioner of Income-tax (Appeals), Income-tax Appellate Tribunal, High Court Tax Bench, Principal Commissioner / Commissioner of Income-tax for revision and registration, Dispute Resolution Panel), assessment year, the assessment-order vintage (pre-Finance-Act-2021 reassessment regime vs Section 148A regime), faceless-vs-physical jurisdiction, and the demand-notice / penalty-notice trajectory are supplied by the user via a `case-config.md` file in the case folder.

This NOTICE is published in plain language so that any reader — practising advocate, Chartered Accountant, judge or Member of the Appellate Tribunal, Bar Council officer, regulator, member of the public, fellow developer — can understand the position without ambiguity.

---

## 1. What this plugin contains

This plugin contains the following categories of content, and **only** the following categories of content:

(a) **Universal direct-tax-pleading skeleton** — the structural shape of any Indian direct-tax appellate pleading or statutory registration application (Form identifier and rule reference, Descriptive title, Particulars block with Name / Address / PAN / Assessment Year / Assessing Officer reference, Statement of Facts where applicable, Grounds of Appeal, Relief Claimed / Prayer, Verification, Signature block, Procedural endnotes, and the case-type-specific structural skeleton).

(b) **Formatting conventions** — text-formatting conventions for pleadings before the Commissioner of Income-tax (Appeals), the Income-tax Appellate Tribunal, the High Court Tax Bench, the Dispute Resolution Panel, and the Principal Commissioner / Commissioner of Income-tax exercising revisional or registration jurisdiction.

(c) **Statutory references** — citations to public statutes (Income-tax Act 1961, Income-tax Rules 1962, Income-tax (Appellate Tribunal) Rules 1963, Finance Acts including Finance Act 2021 reassessment overhaul, Direct Tax Vivad se Vishwas Act 2020 references where transitional, Bharatiya Nagarik Suraksha Sanhita 2023, Bharatiya Sakshya Adhiniyam 2023, Limitation Act 1963 only where cross-cited).

(d) **Procedural rule references** — citations to public rules and schemes (Income-tax Rules 1962 — Rule 45 / Rule 47 / Rule 17A / Rule 44CA, Income-tax (Appellate Tribunal) Rules 1963 — Rule 5A and the related ITAT procedural rules, Faceless Appeal Scheme 2021, Faceless Assessment Scheme 2020, Faceless Penalty Scheme 2021, and public-domain CBDT Circulars and Instructions regarding limitation, fee thresholds, and procedural directions to Assessing Officers).

(e) **Generic placeholders** — every variable in every template is a placeholder (`[Assessee Name]`, `[PAN]`, `[Aadhaar-Linked-PAN-Status]`, `[TAN]`, `[Assessment Year]`, `[Financial Year]`, `[Assessing Officer Designation]`, `[Faceless Centre — National / Regional / Local]`, `[DIN — Document Identification Number]`, `[Date of Order under Appeal]`, `[Date of Service]`, `[Total Income Assessed]`, `[Demand under Section 156]`, `[Penalty Quantum]`, `[TDS Default Quantum]`). No placeholder is filled with any specific assessee, assessment year, PAN, AO, financial figure, or any other identifying information.

(f) **Anti-hallucination and privacy-firewall workflow** — six agents (Reader, Format, Drafter, Verifier, Refiner, Overseer) that operate on a case folder supplied by the user. The plugin itself contains no case folder. The Reader substitutes every assessee name, PAN, Aadhaar, TAN, Assessing Officer name, DIN, financial figure, and case-number reference with structural placeholders before downstream AI processing.

---

## 2. What this plugin does NOT contain

This plugin does **not** contain any of the following, and has never contained any of the following at any point in any committed version:

(a) **No specific assessee, no specific tax matter.** No client of the author, and no specific assessment, reassessment, penalty, revision, or appellate proceeding handled by the author or any client, appears in the plugin — by name, by PAN, by Aadhaar reference, by TAN, by DIN, by AO designation, by assessment-year reference, by quantum of addition, by penalty quantum, by demand reference, by case-number reference, or by any other identifying signature.

(b) **No client communications.** No oral or written communication made to the author by or on behalf of any assessee (whether an individual, a Hindu Undivided Family, a firm, a Limited Liability Partnership, a company, a charitable trust, an Association of Persons, or any other entity) appears in the plugin in any form.

(c) **No client documents.** No document or instrument with which the author has become acquainted in the course of professional employment as an advocate appears in the plugin, in original, in redacted, in summary, in extract, or in pattern. This includes — but is not limited to — assessment orders, reassessment notices, penalty orders, show-cause notices under Section 148A(b), demand notices under Section 156, revision orders, CIT(A) orders, ITAT orders, Audit Reports in Form 3CD, Tax Audit Reports, Transfer Pricing study reports, Form 3CEB filings, financial statements, ledgers, vouchers, bank statements, valuation reports, or any document filed before any Income-tax authority.

(d) **No personal data of any data principal.** The plugin processes no personal data, collects no personal data, stores no personal data. No PAN, no Aadhaar, no Aadhaar-linked-PAN status, no taxpayer identification of any kind appears in the plugin.

(e) **No specific board resolution, no specific power-of-attorney, no specific Vakalatnama** of any specific assessee handled by the author or any other advocate.

(f) **No client list, no panel-counsel list of any tax department, no chamber list, no associate list, no opposing-counsel list, no Assessing-Officer-specific intelligence, no CIT(A)-specific intelligence, no ITAT-Member-specific intelligence.**

(g) **No tracking, no telemetry, no analytics, no opt-in error reporting, no login, no account, no cloud sync.** The plugin runs entirely on the user's machine. The author receives no information about who installs the plugin, who uses it, on what cases, with what consideration, with what outcomes.

(h) **No Section 138 of the Income-tax Act 1961 breach.** Section 138 of the Income-tax Act 1961 protects the confidentiality of taxpayer-specific information held by Income-tax authorities. Nothing in this plugin draws on any such confidential record. The plugin's content is procedural skeleton and public statutory reference only.

---

## 3. The legal distinction

Indian law has long recognised a clear distinction between two categories:

(i) **Specific client communications and documents** — protected under Section 132 of the Bharatiya Sakshya Adhiniyam 2023 (formerly Section 126 of the Indian Evidence Act 1872) and under Rule 17 of the Bar Council of India Standards of Professional Conduct and Etiquette. This category is privileged and confidential. Taxpayer-specific information additionally enjoys protection under Section 138 of the Income-tax Act 1961 at the Department's end.

(ii) **General professional knowledge of direct-tax law, appellate procedure, and pleading craft** — an advocate's accumulated knowledge of how a Form 35 CIT(A) appeal is structured under Rule 45 of the Income-tax Rules 1962, how a Form 36 ITAT appeal is structured under Rule 47 of the Income-tax Rules 1962, how a Form 10A application for charitable-trust registration under the post-2020 Section 12AB regime is structured under Rule 17A, what the Finance Act 2021 reassessment overhaul (Section 148A) requires of a show-cause-objection reply, what *Ashish Agarwal* (the Supreme Court's direction on the transitional reassessment regime, May 2022) holds about pre-Finance-Act-2021 reassessment notices retrospectively converted to Section 148A notices, what *Malabar Industrial Co. Ltd. v. CIT* (2000) 243 ITR 83 (SC) holds about the dual conditions of Section 263, what *CIT v. Reliance Petroproducts Pvt. Ltd.* (2010) 322 ITR 158 (SC) holds about Section 271(1)(c) concealment penalty, what Section 270A immunity under Section 270AA permits, how a Section 144C objection before the Dispute Resolution Panel is structured under Rule 44CA, how a Section 201 / 201(1A) TDS-default reply is structured. This category is the advocate's own professional knowledge. It is not the property of any specific client. It is not privileged.

This plugin operates **entirely within category (ii)**.

Every Indian advocate practising direct-tax appellate work accumulates this knowledge through years of practice, through study of Sampath Iyengar's *Law of Income Tax*, Chaturvedi & Pithisaria's *Income Tax Law*, Kanga, Palkhivala & Vyas on the *Law and Practice of Income Tax*, the CBDT Master Circulars, the ITAT Members' Reference Manual, and the case-law of the Supreme Court, the High Courts, and the Income-tax Appellate Tribunal on direct-tax appellate jurisprudence. The plugin codifies that accumulated procedural knowledge into machine-readable form. It does not codify any client's confidential information.

The plugin is, in this respect, identical in legal character to a published direct-tax-law textbook, a continuing legal education handout, or a senior advocate's drafting-style lecture. The medium is software. The content is procedural knowledge.

---

## 4. The author's professional position

The author is **Rushikesh R. Mahajan**, Advocate, enrolled with the Bar Council of Maharashtra and Goa, practising before the High Courts of India. The plugin is published under the open-source brand **wolfgang_rush**, which is the author's publishing handle for legal-technology infrastructure; the real-identity accountability declared in this section attaches to the author personally and is not displaced by the use of a publishing handle.

The author retains full enrolment, full responsibility, and full liability under the Advocates Act 1961, the Bar Council of India Rules, and the Standards of Professional Conduct and Etiquette.

The plugin is published as a personal contribution to the open-source legal-technology ecosystem. It is published without any commercial channel, without any solicitation of professional work, without any advertisement of professional services, and without any acceptance of work through this repository.

This NOTICE is filed of record in this open-source repository so that any person who reads, reviews, audits, or assesses this plugin has full transparency about its provenance and its scope from the moment of release.

---

## 5. Verification of clean provenance

The repository owner shall maintain, on a private offline record, a build log demonstrating that every line of every file in the plugin was either:

(a) authored from scratch as procedural skeleton, OR
(b) derived from public statute, public rule, public scheme, public judgment, or public direct-tax-law textbook, OR
(c) derived from the author's own original procedural knowledge as a practitioner.

No line of any file was, at any stage, copied from, paraphrased from, summarised from, or pattern-matched against any specific assessee matter, tax proceeding, client communication, or client document.

This NOTICE is the author's signed declaration of that position.

---

## 6. Reporting concerns

If any reader, regulator, fellow advocate, or member of the public believes any specific content in this plugin is derived from a specific client matter or specific confidential communication, the reader is requested to:

(a) identify the file and line at issue in the plugin,
(b) identify the specific assessee matter or communication believed to be the source,
(c) explain the basis of the belief,

and raise the concern via a GitHub Issue on this repository.

Concerns raised with these particulars will be investigated and the file or line will be removed or rewritten if the concern is well-founded. Concerns raised without these particulars cannot be acted upon.

---

## 7. Standing instruction to forks and derivatives

Any fork, derivative, downstream redistribution, or commercial integration of this plugin or its content shall preserve this NOTICE in unmodified form, and shall extend the same provenance discipline to any content added in the fork or derivative.

This NOTICE travels with the code under the same MIT licence that governs the source.

---

*Signed and dated by way of public commit history on the repository. The author stands by every line of this notice.*
