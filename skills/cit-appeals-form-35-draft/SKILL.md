---
name: cit-appeals-form-35-draft
description: Draft an appeal before the Commissioner of Income-tax (Appeals) on Form 35 under Rule 45 of the Income-tax Rules 1962. For an assessee aggrieved by an Assessing Officer's assessment order under Section 143(3) / Section 144 / reassessment order under Section 147 read with Section 148A / penalty order under Section 270A or Section 271 / TDS-default order under Section 201 / any other appealable order listed in Section 246A. Encodes the Section 246A appealable-orders catalogue, the Section 249 form-of-appeal-limitation-and-fee scheme, the Section 250 procedure-in-appeal framework, the Section 251 powers of CIT(A), and the Faceless Appeal Scheme 2021 read with Section 250(6B). Auto-fires on "draft Form 35 CIT(A) appeal", "draft CIT(A) appeal", "draft income-tax appeal", "draft Section 246A appeal", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# CIT(Appeals) Form 35 Appeal Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPEAL TO THE COMMISSIONER OF INCOME-TAX (APPEALS) UNDER SECTION 246A OF THE INCOME-TAX ACT 1961, ON FORM 35 UNDER RULE 45 OF THE INCOME-TAX RULES 1962
case_short_code: CIT_A_FORM_35
form_number: 35
rule_reference: Rule 45 of the Income-tax Rules 1962
case_number_prefix: Appeal No.
pleading_type: Appeal
typical_forum: Commissioner of Income-tax (Appeals), National Faceless Appeal Centre, Delhi (default) OR physical-bench CIT(A) for cases excluded from the Faceless Appeal Scheme 2021
typical_parties: Appellant (the assessee) + Respondent (the Assessing Officer / Income-tax Authority)
statutory_opening: "This appeal is preferred by the Appellant under Section 246A of the Income-tax Act 1961 read with Rule 45 of the Income-tax Rules 1962 against the order dated ____ passed by the [Assessing Officer designation] under Section [143(3) / 144 / 147 read with 148A(d) / 270A / 271(1)(c) / 201 / etc.] of the Income-tax Act 1961 for Assessment Year ____."
ground_clauses:
  - "Erroneous addition under Section [68 / 69 / 14A / 40(a)(ia) / 40(b) / 36(1)(va) / etc.] of ₹___ — the learned Assessing Officer erred in law and on facts in adding ₹___ to the returned income, without appreciating that the Appellant had discharged the burden of proof, the addition is contrary to the documentary evidence on record at Enclosure ___, and the addition is contrary to the settled law of [relevant precedent]."
  - "Mechanical disallowance under Section ____ — the learned Assessing Officer mechanically disallowed ₹___ without recording independent satisfaction and without affording adequate opportunity to the Appellant."
  - "Reassessment / reopening defect — the order under appeal is barred by limitation under Section 149 / suffers from defective sanction under Section 151 / proceeds on a change of opinion / Section 148A(d) order is unsustainable on the material relied upon."
  - "Faceless-assessment procedural defect — the assessment violates the Faceless Assessment Scheme 2020 read with Section 144B of the Income-tax Act 1961 in [specify defect — non-supply of material relied upon / non-grant of personal hearing / order passed beyond the variation proposed in the show-cause notice / etc.]."
  - "DIN-absence ground (where applicable) — the order under appeal does not bear a Document Identification Number as mandated by CBDT Circular No. 19/2019 and is therefore non-est ab initio."
  - "Order bad in law — the order under appeal is bad in law, against the facts of the case, and contrary to the principles of natural justice."
  - "Leave to amend — the Appellant craves leave to add to, alter, amend, modify, or substitute the above grounds of appeal at any stage of the proceedings."
relief_clauses:
  - "(a) Set aside the order dated ____ passed by the [Assessing Officer designation] under Section ____ of the Income-tax Act 1961 for AY ____;"
  - "(b) Delete the additions / disallowances aggregating to ₹___ and accept the returned income;"
  - "(c) Direct that consequential relief be granted including refund of any tax paid pursuant to the order under appeal together with interest under Section 244A;"
  - "(d) Grant such further and other reliefs as this Hon'ble Commissioner of Income-tax (Appeals) may deem fit and proper."
mandatory_enclosures:
  - certified_copy_of_order_appealed_against_with_din
  - return_of_income_for_the_ay
  - computation_of_income
  - audit_report_form_3ca_or_3cb_and_3cd_where_applicable
  - reply_to_show_cause_filed_before_ao
  - ledger_extracts_and_books_of_account_extracts_for_disputed_items
  - third_party_confirmations_where_applicable
  - bank_statements_where_applicable
  - demand_notice_under_section_156
  - form_26_vakalatnama_or_letter_of_authority
accompanying_applications:
  - "Application for stay of demand under Section 220(6) of the Income-tax Act 1961 (first instance before the AO; escalated to PCIT / CIT and to the CIT(A) on refusal)"
  - "Application for condonation of delay under Section 249(3) where appeal is preferred beyond 30 days from the date of service of order"
  - "Application for admission of additional evidence under Rule 46A of the Income-tax Rules 1962 where the appellant seeks to lead evidence not previously placed on record before the AO"
  - "Application for early hearing where revenue-stake / limitation-pressure justifies it"
filing_fee: "Slab fee under Section 249(1) of the Income-tax Act 1961 — scaled by total assessed income. Common slabs (verify against current notification): ₹250 where total income assessed ≤ ₹1 lakh; ₹500 where between ₹1 lakh and ₹2 lakh; ₹1,000 where above ₹2 lakh; and a different slab for non-assessment-context appeals. The Drafter computes the slab from `case-config.md` and reflects it in the Form 35 and the procedural endnotes with the verify-against-current-notification flag."
limitation: "Section 249(2) of the Income-tax Act 1961 — 30 days from the date of service of the order appealed against. Section 249(3) — power to condone delay on sufficient cause."
```

## Faceless Appeal Scheme 2021 discipline

The Faceless Appeal Scheme 2021 read with Section 250(6B) — (6D) of the Income-tax Act 1961 brings most CIT(A) appeals within the National Faceless Appeal Centre, Delhi. Carve-outs: serious frauds, major tax-evasion investigation, sensitive search cases, international-taxation cases falling within DRP jurisdiction, Black Money Act cases. The Drafter resolves faceless / physical disposition from `case-config.md`.

## Section 246A appealable-orders catalogue (excerpt)

The Drafter identifies the appealable order under Section 246A by reference to:
- Section 143(3) assessment order
- Section 144 best-judgment assessment order
- Section 147 / 148A(d) reassessment order
- Section 154 rectification order
- Section 201(1) / 201(1A) TDS-default order
- Section 263 revision order (where the assessee is aggrieved by the consequential AO order; the Section 263 order itself goes to ITAT under Section 253(1)(c))
- Section 270A / 271 / 271AAA / 271AAB / 272A penalty orders
- Section 158BC / 158BD search-assessment orders (legacy)

## Statement of Facts (clause 8 of Form 35)

For Form 35, the Statement of Facts is a dedicated block. The Drafter populates it from `case-facts.md` with numbered narrative paragraphs covering: filing of return → notices issued by AO → replies filed → show-cause issued → reply to show-cause → assessment order with the AO's reasoning summary → demand notice → cause of action.

## Grounds drafting discipline

Grounds are numbered consecutively (Ground 1, Ground 2, ...) NOT bulleted. Each ground:
- Identifies the legal proposition
- Anchors to the statutory provision allegedly mis-applied
- Anchors to the document supporting the ground (Enclosure / paragraph of the order under appeal)
- Concludes with the prayer corresponding to the ground (delete / set aside / cancel / quash)

Standard concluding grounds always included.
