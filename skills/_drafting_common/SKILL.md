---
name: _drafting_common
description: Shared reference for all 10 direct-tax drafting skills. Holds the anti-pollution rules, the direct-tax privacy firewall protocol (assessee names + PAN + Aadhaar references + TAN + AO names + DIN + quantum figures substituted with placeholders before downstream AI processing; real-value re-substitution local-only in the Refiner step), the AI-style-marker blacklist, citation discipline, statutory currency rules (Income-tax Act 1961 / Income-tax Rules 1962 / Income-tax (Appellate Tribunal) Rules 1963 / Finance Act 2021 reassessment overhaul (Section 148A) / Section 12AB post-2020 registration regime / Section 270A AY-2017-18-onwards penalty regime / Faceless Appeal Scheme 2021 / Faceless Assessment Scheme 2020 / BNSS / BSA penal cross-cites), the Form-correspondence rules (Form 35 / Rule 45, Form 36 / Rule 47, Form 10A / Rule 17A, Form 35A / Rule 44CA), the limitation map (Section 249(2) 30d CIT(A) / Section 253(3) 60d ITAT / Section 260A(2) 120d HC / Section 144C(2) 30d DRP / Section 264(3) 1yr revision), the DIN-presence discipline (CBDT Circular No. 19/2019), the PAN-format discipline, the AY-vs-FY discipline, and the faceless-vs-physical jurisdiction discipline. NOT invoked directly — referenced from every case-type skill in this plugin.
allowed-tools: Read
---

# `_drafting_common` — shared direct-tax drafting infrastructure

## Privacy firewall

Direct-tax pleadings routinely contain highly sensitive material — KYC data of the assessee, PAN, Aadhaar-linked-PAN status, TAN, complete financial figures (total income / income from each head / additions and disallowances / penalty quantum / demand under Section 156 / TDS-default quantum / TP-adjustment quantum), DIN of the order under appeal, AO identity and designation, faceless-centre designation, audit-report references, transfer-pricing data, deductee particulars. Section 138 of the Income-tax Act 1961 protects taxpayer-specific information at the Department's end; the plugin's discipline mirrors this:

1. **Reader** substitutes every assessee name, every PAN, every Aadhaar reference, every TAN, every AO name, every DIN, every quantum figure, and every authorised-signatory name with structural placeholders before downstream processing.
2. The placeholder → real-value mapping is stored in the header of `case-facts.md` on the user's local machine **only**.
3. **Format / Drafter / Verifier / Overseer** operate **only** on placeholder-substituted content. The underlying AI runtime never holds raw PANs or raw financial figures.
4. **Refiner** re-substitutes real values into the final `.docx`, strictly on the user's machine.
5. `.gitignore` excludes `case-facts.md` and `case-config.md` so they cannot be committed accidentally.

## AI-style-marker blacklist

Stripped by the Refiner before output:

- Em-dash (`—`) used as sentence-internal pause (replaced with semicolon or comma-bounded clause)
- Sentence-final *thereby* / *hereby* / *whereby* without an attached verb
- *Moreover*, *furthermore*, *additionally*, *in addition* as sentence-openers — replaced with *"The Appellant submits that"* / *"The Appellant further submits that"*
- *Navigate*, *delve*, *foster*, *robust*, *seamless* (metaphorical uses)
- *It is important to note that*, *it should be noted that*, *worthy of note* — replaced with direct prose
- Bullet-list-style structure in operative paragraphs (operative paragraphs are numbered Grounds, not bulleted)

## Citation discipline

The Drafter does **not** generate case names + citations from training memory. Every case citation in any explanatory note or recital must trace to a user-supplied source. Untraceable citations become `[CITATION NEEDED]` placeholders.

Headline cases the Verifier scans for fabrication (citations conventionally encountered in direct-tax appellate practice):

- *Malabar Industrial Co. Ltd. v. CIT* (2000) 243 ITR 83 (SC) — twin conditions for Section 263 revision (erroneous AND prejudicial to revenue)
- *CIT v. Max India Ltd.* (2007) 295 ITR 282 (SC) — one of two views permissible to AO is not erroneous within Section 263
- *CIT v. Greenworld Corporation* (2009) 314 ITR 81 (SC) — revision cannot substitute the AO's view with the PCIT's
- *CIT v. Reliance Petroproducts Pvt. Ltd.* (2010) 322 ITR 158 (SC) — Section 271(1)(c) — incorrect claim does not amount to furnishing inaccurate particulars
- *T. Ashok Pai v. CIT* (2007) 292 ITR 11 (SC) — strict construction of penal provisions in tax statutes
- *Dilip N. Shroff v. JCIT* (2007) 291 ITR 519 (SC) — Section 271(1)(c) requires conscious concealment
- *Union of India v. Ashish Agarwal* (4 May 2022 — SC direction) — transitional reassessment regime; pre-01-04-2021 Section 148 notices retrospectively converted to Section 148A(b) show-cause notices
- *Sir Chunilal V. Mehta v. Century Spinning* (1962) — *Santosh Hazari v. Purushottam Tiwari* (2001) 3 SCC 179 — *Hero Vinoth v. Seshammal* (2006) 5 SCC 545 — framework for what constitutes a substantial question of law under Section 260A
- *CIT v. Samson Perinchery* (Bombay HC, 2017) — requirement of specifying the limb under Section 271(1)(c) in the show-cause notice
- *Collector, Land Acquisition, Anantnag v. Mst. Katiji* (1987) 167 ITR 471 (SC) — liberal approach to condonation of delay in appeals
- *Velji Deoraj* line under Rule 29 ITAT Rules 1963 — additional evidence at the Tribunal stage
- *GE India Technology Centre Pvt. Ltd. v. CIT* (2010) 327 ITR 456 (SC) — Section 195 TDS on payments to non-residents — chargeability test
- *Vodafone International Holdings BV v. UoI* (2012) 6 SCC 613 — non-resident transactions and Section 195
- *PCIT v. Maruti Suzuki India Ltd.* (2019) 416 ITR 613 (SC) — assessment on non-existent entity (amalgamated company) is void ab initio

## Statutory currency rules

Every pleading filed today should cite the operative statutory provision in its post-amendment form. Common substitution checks:

- **Section 147 / 148 → Section 148A regime** for any reassessment-context pleading post-01-04-2021 (Finance Act 2021 overhaul). Pre-01-04-2021 Section 148 notices retrospectively converted to Section 148A(b) per *Ashish Agarwal* — pleading must engage with the transitional regime.
- **Section 12AA → Section 12AB regime** for any charitable-trust-registration pleading post-Finance-Act-2020. Every existing Section 12A / 12AA registered trust required to re-apply under Form 10A within the prescribed window.
- **Section 271(1)(c) → Section 270A** for AYs 2017-18 and onwards. AYs up to and including 2016-17 stay under Section 271(1)(c) (with parallel application of Section 271AAA / 271AAB for search years).
- **Section 200 CrPC 1973 → Section 223 BNSS 2023** where Magistrate-court cross-cite arises (e.g. Section 276B / 276C / 277 / 278 prosecution complaints under the Income-tax Act 1961 filed post-BNSS-commencement).
- **Section 482 CrPC 1973 → Section 528 BNSS 2023** for inherent-power petitions cross-referenced from tax prosecution.
- **Section 65B Indian Evidence Act 1872 → Section 63 Bharatiya Sakshya Adhiniyam 2023** for admissibility of electronic records / digital printouts.
- **Section 126 IEA 1872 → Section 132 BSA 2023** for advocate-client privilege references.

Dual-citation is acceptable in any transitional pleading.

## Form-correspondence rules

| Pleading | Statutory Form | Rule |
|---|---|---|
| CIT(A) appeal | Form 35 | Rule 45 of the Income-tax Rules 1962 |
| ITAT appeal | Form 36 | Rule 47(1) of the Income-tax Rules 1962 |
| ITAT cross-objection | Form 36A | Rule 47(2) of the Income-tax Rules 1962 |
| Section 12A registration | Form 10A | Rule 17A of the Income-tax Rules 1962 |
| Section 80G renewal | Form 10G | Rule 11AA |
| DRP objection | Form 35A | Rule 44CA of the Income-tax Rules 1962 |
| Section 197 lower-deduction-of-TDS certificate application | Form 13 | Rule 28 |
| Section 154 rectification application | Letter to AO | n/a (open-form) |
| Section 148A(b) objection | Open-form reply | n/a |
| Section 263 / 264 reply | Open-form reply / application | n/a |
| Section 270A / 271(1)(c) reply | Open-form reply | n/a |
| Section 201 TDS reply | Open-form reply | n/a |
| Section 260A High Court appeal | Memorandum of Appeal | State High Court (Tax Bench) Rules |

The Drafter follows the prescribed Form layout in the exact clause order and the exact clause numbering — no re-ordering, no renumbering, no omission. Clauses not applicable to the matter rendered as *"Not applicable"* or *"Nil"*.

## Limitation map

| Pleading | Statutory anchor | Limitation |
|---|---|---|
| CIT(A) Form 35 appeal | Section 249(2) | 30 days from date of service of order |
| ITAT Form 36 appeal | Section 253(3) | 60 days from date of communication of order |
| High Court appeal Section 260A | Section 260A(2) | 120 days from date of receipt of ITAT order |
| Supreme Court appeal Section 261 | Section 261(1) | special leave / certified case |
| DRP objection Form 35A | Section 144C(2) | 30 days from date of receipt of draft assessment order |
| Section 264 revision application | Section 264(3) | 1 year from date of communication of order (PCIT / CIT may admit beyond on sufficient cause) |
| Section 154 rectification application | Section 154(7) | 4 years from end of FY in which order sought to be amended was passed |
| Section 270AA immunity application | Section 270AA(2) | 1 month from end of month in which assessment order is received |
| Condonation of delay — CIT(A) | Section 249(3) | discretionary, on sufficient cause |
| Condonation of delay — ITAT | Section 253(5) | discretionary, on sufficient cause |
| Condonation of delay — High Court | Section 260A(2A) | discretionary, on sufficient cause |
| Section 148A(b) reply | per the show-cause notice | typically 2 weeks, extendable on application |
| Section 263 reply | per the show-cause notice | per PCIT / CIT direction |
| Section 270A / 271(1)(c) reply | per the show-cause notice | per AO / Faceless Penalty Centre direction |
| Section 201 reply | per the show-cause notice | per AO (TDS) direction |

The Drafter pleads the limitation paragraph for every case-type using the applicable section + date-of-receipt-or-communication + date-of-filing + days-within-limitation. Where out of time, an accompanying condonation-of-delay application is filed.

## DIN-presence discipline (CBDT Circular No. 19/2019)

Every Income-tax authority order / notice / summons / letter issued on or after 01-10-2019 must bear a unique Document Identification Number on the face of the document. Orders without a DIN are non-est per the Circular. The Verifier checks:

1. The order under appeal carries a DIN (captured in the Particulars block of the pleading).
2. Where the order does NOT carry a DIN despite issuance after 01-10-2019, the Drafter pleads DIN-absence as a substantive ground of challenge (the order is non-est ab initio per the Circular and the High Court line in *Brandix Mauritius Holdings* (Delhi HC, 2023) and the Bombay High Court line).

## PAN-format discipline

PAN is a ten-character alphanumeric in the AAAAA9999A format: five letters + four digits + one letter. The fourth character indicates the assessee status (P for Individual, H for HUF, F for Firm, L for LLP, C for Company, T for Trust, A for AOP, B for BOI, J for Artificial Juridical Person, G for Government). The Verifier validates format on every PAN in the Particulars block.

## Assessment-Year vs Financial-Year discipline

- **Financial Year (FY)** — the year in which the income is earned (e.g. FY 2023-24 runs 01-04-2023 to 31-03-2024).
- **Assessment Year (AY)** — the year in which the income earned in the previous FY is assessed (e.g. AY 2024-25 corresponds to FY 2023-24).

Direct-tax pleadings frequently conflate the two. The Verifier catches AY / FY conflation and flags for correction.

## Faceless-vs-physical jurisdiction discipline

Under the **Faceless Assessment Scheme 2020** read with Section 144B of the Income-tax Act 1961, scrutiny assessments are conducted by the National Faceless Assessment Centre, Delhi, except for cases expressly excluded.

Under the **Faceless Appeal Scheme 2021** read with Section 250(6B) — (6D) of the Income-tax Act 1961, CIT(A) appeals are heard by the National Faceless Appeal Centre, Delhi, except for cases expressly excluded (serious frauds, major tax-evasion investigation, sensitive search cases, international-taxation cases falling within DRP jurisdiction, Black Money Act cases).

Under the **Faceless Penalty Scheme 2021**, penalty proceedings under Section 270A / 271 / 271AAB are conducted faceless except for cases expressly excluded.

The Drafter resolves the faceless-vs-physical disposition from `case-config.md` and renders the correct forum designation. The Verifier flags any mis-mapping.

## Filing-fee scaling

| Pleading | Statutory anchor | Slab basis |
|---|---|---|
| Form 35 CIT(A) appeal | Section 249(1) | Scaled by total assessed income; verify against current notification |
| Form 36 ITAT appeal | Section 253(6) | Scaled by total assessed income; verify against current notification |
| Section 260A HC appeal | State High Court (Tax Bench) Rules | Ad valorem under State Court-Fees Act |
| Section 264 revision application | Section 264(7) | Fixed fee per current notification |
| Section 12A Form 10A | Income-tax Rules 1962 | No separate fee (electronic filing on Income-tax portal) |
| DRP Form 35A | Section 144C | No separate fee |

**Anomaly flag (per the 2050 corpus digest):** fee thresholds in Section 249(1) and Section 253(6) are subject to periodic amendment in the Finance Act. The Verifier always flags fee figures with *"verify against current notification"*.

## Faceless Schemes — public references

- **Faceless Assessment Scheme 2020** — notified under Section 144B; National Faceless Assessment Centre, Delhi.
- **Faceless Appeal Scheme 2021** — notified under Section 250(6B); National Faceless Appeal Centre, Delhi.
- **Faceless Penalty Scheme 2021** — notified under Section 274(2A); Faceless Penalty Centres.
- **e-Verification Scheme 2021** — for verification under Section 135A.
- **e-Settlement Scheme 2021** — for proceedings before the Interim Board for Settlement under Section 245AA (post-abolition-of-Settlement-Commission regime).

The Drafter cites the applicable Scheme where the pleading lies before a Faceless Centre.
