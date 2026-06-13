---
name: itat-appeal-form-36-draft
description: Draft an appeal before the Income-tax Appellate Tribunal on Form 36 under Rule 47(1) of the Income-tax Rules 1962 and the Income-tax (Appellate Tribunal) Rules 1963. For an assessee aggrieved by an order of the Commissioner of Income-tax (Appeals) under Section 250, or by certain orders of the Principal Commissioner / Commissioner under Section 263, or by DRP-direction-binding orders, OR for the Department aggrieved by a CIT(A) order in favour of the assessee. Encodes the Section 252 constitution of the Tribunal, the Section 253 appealable-orders catalogue, the Section 254 procedure-and-powers of the Tribunal, the Section 255 procedure-of-the-Tribunal framework, the ITAT Rules 1963 (esp Rule 5A on additional grounds and Rule 29 on additional evidence), the language-option flag (Hindi filing permitted at notified-State benches), and the filing-fee slab under Section 253(6). Auto-fires on "draft Form 36 ITAT appeal", "draft ITAT appeal", "draft tax tribunal appeal", "draft Section 253 appeal", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# ITAT Form 36 Appeal Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPEAL TO THE INCOME-TAX APPELLATE TRIBUNAL UNDER SECTION 253 OF THE INCOME-TAX ACT 1961, ON FORM 36 UNDER RULE 47(1) OF THE INCOME-TAX RULES 1962
case_short_code: ITAT_FORM_36
form_number: 36
rule_reference: Rule 47(1) of the Income-tax Rules 1962
case_number_prefix: I.T.A.
pleading_type: Appeal
typical_forum: Income-tax Appellate Tribunal — [Bench], [City] (e.g. ITAT Bench 'A', Mumbai / ITAT Bench, [bench city] / ITAT Delhi Bench 'D')
typical_parties: Appellant (assessee or Department) + Respondent (Department or assessee)
statutory_opening: "This appeal is preferred by the Appellant under Section 253(1)(a) / (b) / (c) / Section 253(2) of the Income-tax Act 1961 read with Rule 47(1) of the Income-tax Rules 1962 against the order dated ____ passed by the Commissioner of Income-tax (Appeals) / Principal Commissioner of Income-tax / Commissioner of Income-tax under Section [250 / 263 / 271 / etc.] of the Income-tax Act 1961 for Assessment Year ____."
ground_clauses:
  - "Erroneous appreciation of evidence — the learned Commissioner of Income-tax (Appeals) erred in confirming / partially confirming / setting aside (delete-as-applicable) the addition / disallowance / penalty of ₹___ made by the Assessing Officer under Section ____, without appreciating that ..."
  - "Misapplication of law — the learned CIT(A) misapplied [precedent / statutory provision] in coming to the conclusion that ..."
  - "Procedural defect — the order under appeal violates the Faceless Appeal Scheme 2021 in [specify defect]."
  - "Ground on facts — the learned CIT(A) ought to have appreciated that ..."
  - "Ground on law — the learned CIT(A) ought to have held that ..."
  - "Leave to file additional grounds under Rule 5A of the Income-tax (Appellate Tribunal) Rules 1963 — the Appellant craves leave to file additional grounds at the time of hearing."
  - "Order bad in law — the order under appeal is bad in law, against the facts of the case, and contrary to the principles of natural justice."
  - "Leave to amend — the Appellant craves leave to add to, alter, amend, modify, or substitute the above grounds of appeal at any stage of the proceedings."
relief_clauses:
  - "(a) Set aside the order of the learned Commissioner of Income-tax (Appeals) dated ____ for AY ____;"
  - "(b) Quash / modify (delete-as-applicable) the assessment order of the Assessing Officer dated ____ to the extent contended in the above grounds;"
  - "(c) Allow the grounds of appeal raised hereinabove with consequential relief;"
  - "(d) Grant such further and other reliefs as this Hon'ble Tribunal may deem fit and proper."
mandatory_enclosures:
  - certified_copy_of_order_of_cit_a_with_din
  - certified_copy_of_order_of_ao_with_din
  - form_35_filed_before_cit_a
  - statement_of_facts_filed_before_cit_a
  - grounds_of_appeal_filed_before_cit_a
  - return_of_income_for_the_ay
  - computation_of_income
  - audit_report_form_3ca_or_3cb_and_3cd_where_applicable
  - demand_notice_under_section_156
  - form_26_vakalatnama_or_letter_of_authority
  - tribunal_filing_fee_challan
accompanying_applications:
  - "Application for stay of demand under Section 220(6) read with Section 254(2A) — at the Tribunal level, stay applications proceed under Section 254(2A) with the 365-day outer limit framework"
  - "Application for condonation of delay under Section 253(5) where appeal is preferred beyond 60 days from the date of communication of order"
  - "Application for admission of additional evidence under Rule 29 of the Income-tax (Appellate Tribunal) Rules 1963 — Velji Deoraj line"
  - "Application for early hearing where revenue-stake / limitation-pressure justifies it"
  - "Cross-objection on Form 36A under Rule 47(2) where the Respondent wishes to support the order on alternate grounds or to challenge a portion of it"
filing_fee: "Slab fee under Section 253(6) of the Income-tax Act 1961 — scaled by total assessed income. Common slabs (verify against current notification): ₹500 where total income assessed ≤ ₹1 lakh; ₹1,500 where between ₹1 lakh and ₹2 lakh; 1% of assessed income (subject to a cap of ₹10,000) where above ₹2 lakh; and a different slab (typically ₹500) for non-assessment-context appeals. The Drafter computes the slab from `case-config.md` and reflects it in the Form 36 and the procedural endnotes with the verify-against-current-notification flag."
limitation: "Section 253(3) of the Income-tax Act 1961 — 60 days from the date on which the order appealed against is communicated to the assessee or the Department. Section 253(5) — power to condone delay on sufficient cause."
```

## Section 253 appealable-orders catalogue

- Section 253(1)(a) — order of CIT(A) under Section 250
- Section 253(1)(b) — order of an Income-tax Authority being a Principal Commissioner / Commissioner under Section 263 OR Section 271 in the rare residual cases
- Section 253(1)(c) — order passed by the AO pursuant to a DRP direction under Section 144C(13)
- Section 253(2) — order of CIT(A) where the Department is aggrieved

## Hindi-language filing option

Under the ITAT Rules 1963, appeals may be filed in Hindi at notified-State benches. The Drafter resolves the language disposition from `case-config.md` (default: English). The base skill encodes the bilingual permission.

## Rule 5A — additional grounds discipline

Under Rule 5A of the Income-tax (Appellate Tribunal) Rules 1963, the appellant may file additional grounds of appeal at the time of hearing with the Tribunal's leave. The Drafter includes a standard leave-to-file-additional-grounds clause in the Grounds.

## Rule 29 — additional evidence discipline

Under Rule 29 of the Income-tax (Appellate Tribunal) Rules 1963, additional evidence may be admitted at the Tribunal stage on satisfaction of the conditions in the rule (the evidence was not available at the time of original proceedings; the lower authority refused to admit relevant evidence; the Tribunal requires the evidence for substantial cause). The *Velji Deoraj* line frames the discipline.

## Stay of demand at the Tribunal — Section 254(2A) framework

Stay applications at the ITAT proceed under Section 254(2A) of the Income-tax Act 1961 — the Tribunal may grant stay subject to deposit of 20% of disputed demand or furnishing of security; the outer limit for disposal of the appeal is 365 days; failure to dispose within 365 days does not automatically vacate the stay (per the Supreme Court line in *DCIT v. Pepsi Foods Pvt. Ltd.* (2021) 433 ITR 295 — declaration that the un-amended Section 254(2A) third proviso is unconstitutional to the extent it provides for automatic vacation).
