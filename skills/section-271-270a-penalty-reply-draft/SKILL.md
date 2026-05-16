---
name: section-271-270a-penalty-reply-draft
description: Draft a reply to a penalty show-cause notice under Section 270A (under-reporting and misreporting of income — applies AY 2017-18 onwards) or Section 271(1)(c) (legacy concealment / inaccurate particulars — applies AYs up to and including 2016-17). For an assessee in receipt of a penalty show-cause notice under Section 274 read with Section 270A or Section 271(1)(c). Encodes the Section 270A two-tier framework (under-reporting at 50% of tax / misreporting at 200% of tax), the Section 270AA immunity election regime, the Section 271(1)(c) Explanation 1 burden-shift framework, the Section 274 opportunity-of-hearing discipline, the Section 275 limitation-for-penalty-order framework, the Reliance Petroproducts incorrect-claim doctrine, the T. Ashok Pai strict-construction-of-penal-provisions doctrine, the Samson Perinchery limb-specification discipline, and the Faceless Penalty Scheme 2021. Auto-fires on "draft Section 270A penalty reply", "draft penalty reply Section 271(1)(c)", "draft Section 274 reply", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 270A / Section 271(1)(c) Penalty Reply Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: REPLY TO PENALTY SHOW-CAUSE NOTICE UNDER SECTION 274 READ WITH SECTION [270A / 271(1)(c)] OF THE INCOME-TAX ACT 1961
case_short_code: SECTION_270A_271_REPLY
form_number: n/a (open-form reply)
rule_reference: Section 270A / Section 271(1)(c) / Section 274 / Section 275 of the Income-tax Act 1961 + Faceless Penalty Scheme 2021
case_number_prefix: per the DIN of the penalty show-cause notice
pleading_type: Reply
typical_forum: Assessing Officer / Faceless Penalty Centre (per Faceless Penalty Scheme 2021)
typical_parties: Assessee + Department (AO / Faceless Penalty Centre)
statutory_opening: "This reply is filed by the Assessee in response to the show-cause notice dated ____ (DIN ____) issued under Section 274 read with Section [270A / 271(1)(c)] of the Income-tax Act 1961 for Assessment Year ____, calling upon the Assessee to show cause why penalty under the said section should not be imposed. The Assessee humbly submits the following defences."
section_selection_rule: "For AYs up to and including 2016-17 — Section 271(1)(c) (concealment OR inaccurate particulars); Section 271AAA / 271AAB for search years. For AYs 2017-18 onwards — Section 270A (under-reporting at 50% of tax payable on under-reported income; misreporting at 200% of tax payable on under-reported income consequent on misreporting). The Drafter selects from `case-config.md`'s AY field; the Verifier catches mis-mapping."
ground_clauses:
  - "Two-views-possible doctrine — the issue on which the addition was made is debatable, with two views legally tenable. Per the Supreme Court in CIT v. Reliance Petroproducts Pvt. Ltd. (2010) 322 ITR 158, a mere disallowance / addition does not amount to under-reporting / inaccurate particulars; the Assessee's claim was bona fide and the rejection thereof does not justify penalty."
  - "Bona fide explanation — the Assessee's explanation in respect of the addition is bona fide and is substantiated by material on record (refer reply to show-cause filed before the AO at Enclosure ____). The Explanation 1 burden-shift under Section 271(1)(c) has been adequately discharged; Section 270A(6)(a) bona-fide-and-substantiated-explanation safe-harbour applies."
  - "Limb-specification defect (Section 271(1)(c) only) — the show-cause notice does not specify under which limb (concealment of income OR furnishing of inaccurate particulars of income) the penalty is proposed. Per CIT v. Samson Perinchery (Bombay HC, 2017) and the lineage thereafter, a vague show-cause notice not specifying the limb vitiates the penalty proceedings."
  - "Section 270A safe-harbour exclusion (Section 270A only) — the under-reporting falls within one or more of the exclusions in Section 270A(6) — bona-fide explanation / estimate-of-income difference within 10% / additional income on revised return / TP adjustment in good-faith reliance on a documented study / addition on account of advance pricing agreement application / amount of disallowance on which transfer-pricing adjustment is based already declared in good faith."
  - "Misreporting allegation unsustained (Section 270A only) — the Department has not established any of the six grounds for misreporting under Section 270A(9): (a) misrepresentation or suppression of facts; (b) failure to record investments in the books of account; (c) claim of expenditure not substantiated by evidence; (d) recording of false entry in books of account; (e) failure to record any receipt in books of account having a bearing on total income; (f) failure to report any international transaction or specified domestic transaction. Without establishing one of the six grounds, the 200% misreporting penalty is unavailable."
  - "Section 270AA immunity election (where eligible) — the Assessee has paid the tax and interest demanded under Section 156 and has filed Form 68 within one month from the end of the month in which the assessment order was received, electing immunity from penalty under Section 270AA. The conditions in Section 270AA(1) — (3) are satisfied: (a) no appeal is pending against the assessment order; (b) the case is not one of misreporting; (c) the tax and interest have been paid. The Assessing Officer is required to grant immunity under Section 270AA(4) within one month from the end of the month in which the immunity application is received."
  - "Limitation bar under Section 275 — the proposed penalty proceedings are barred by limitation under Section 275 of the Income-tax Act 1961: the period of six months from the end of the month in which the order of CIT(A) / ITAT was received OR the financial year in which the assessment proceedings were completed (whichever is later) has expired."
  - "Strict construction of penal provisions — per T. Ashok Pai v. CIT (2007) 292 ITR 11 (SC), penal provisions in tax statutes are to be strictly construed; ambiguity is resolved in favour of the assessee. Penalty is not automatic on every disallowance; it requires conscious concealment / misreporting."
relief_clauses:
  - "(a) That this Hon'ble Authority may be pleased to drop the proposed penalty proceedings under Section [270A / 271(1)(c)] of the Income-tax Act 1961 for AY ____;"
  - "(b) That where the Assessee has elected immunity under Section 270AA, immunity from penalty be granted by an order under Section 270AA(4) within the prescribed window;"
  - "(c) That a personal hearing be granted to the Assessee before any adverse order is passed;"
  - "(d) Grant such further and other reliefs as this Hon'ble Authority may deem fit and proper."
mandatory_enclosures:
  - copy_of_penalty_show_cause_notice_with_din
  - copy_of_assessment_order_with_din
  - copy_of_return_of_income_for_the_ay
  - documentary_evidence_substantiating_the_assessees_explanation
  - copy_of_form_68_immunity_election_under_section_270aa_where_filed
  - challan_evidencing_payment_of_tax_and_interest_under_section_156
  - copies_of_relevant_judicial_authorities_pdfs_relied_upon
  - form_26_vakalatnama_or_letter_of_authority
accompanying_applications:
  - "Where Section 270AA immunity election made — Form 68 filed within one month from the end of the month of receipt of the assessment order"
  - "Application for personal hearing — included in the prayer above"
  - "Application for extension of time to file the reply, where the prescribed window is insufficient"
filing_fee: "No statutory fee for a Section 274 reply — electronic filing on the Income-tax e-filing portal (where faceless) OR physical filing before the jurisdictional AO."
limitation: "Per the show-cause notice — the AO prescribes the reply-window in the notice itself, typically 7 to 15 days from the date of receipt, extendable on application. The Drafter notes the original reply-window from `case-config.md`."
```

## Section 270A two-tier framework

- **Under-reporting** (Section 270A(2)): penalty at 50% of the tax payable on under-reported income
- **Misreporting** (Section 270A(9)): penalty at 200% of the tax payable on under-reported income consequent on misreporting

Six grounds for misreporting (Section 270A(9)):
(a) misrepresentation or suppression of facts
(b) failure to record investments in the books of account
(c) claim of expenditure not substantiated by evidence
(d) recording of false entry in books of account
(e) failure to record any receipt in books of account having a bearing on total income
(f) failure to report any international transaction or specified domestic transaction

## Section 270A(6) safe-harbour exclusions

The amount of under-reported income shall NOT include amounts:
(a) on account of which a bona fide explanation has been offered and substantiated
(b) determined on the basis of an estimate where accounts are correct but accuracy is rejected
(c) on account of an estimate of income where the assessee had disclosed all material facts but the AO has made a different estimate (≤ 10% difference exclusion)
(d) representing addition on account of TP adjustment where transactions are at arm's length supported by Form 3CEB study
(e) representing income recorded in books but treated by AO as falling under a different head
(f) on which tax has been paid under Section 115JB / 115JC and the assessee is a domestic company under MAT
(g) representing addition based on a different estimate without misreporting

## Section 270AA — immunity election

The Assessee can elect immunity from Section 270A penalty AND prosecution under Section 276C / 276CC if:
- Tax and interest under the assessment order are paid
- Form 68 application is filed within one month from the end of the month in which the assessment order is received
- No appeal has been preferred against the assessment order in respect of which immunity is sought
- The case is not one of misreporting under Section 270A(9)

The AO grants immunity by order under Section 270AA(4) within one month from the end of the month of receipt of the application. The Verifier flags whether the Assessee is eligible.

## Section 271(1)(c) — legacy regime (AYs up to 2016-17)

For AYs up to and including 2016-17, Section 271(1)(c) governs:
- Concealment of income — penalty of 100% to 300% of tax sought to be evaded
- Furnishing of inaccurate particulars — same penalty range

**Limb-specification rule** — per *CIT v. Samson Perinchery* (Bombay HC, 2017), *CIT v. Manjunatha Cotton & Ginning Factory* (Karnataka HC), and the lineage, the show-cause notice MUST specify under which limb (concealment OR inaccurate particulars) the penalty is proposed. A vague show-cause notice vitiates the penalty proceedings.

**Explanation 1 burden-shift** — if the assessee fails to offer an explanation OR offers an explanation that is not substantiated or not bona fide, the addition is deemed to represent concealed income. The assessee can defeat the Explanation 1 deeming by offering a bona fide and substantiated explanation.

## Faceless Penalty Scheme 2021

Penalty proceedings under Section 270A / 271 / 271AAB are conducted faceless under the Faceless Penalty Scheme 2021 notified under Section 274(2A), except where excluded. The Drafter resolves the faceless / physical disposition from `case-config.md`.
