---
name: section-144c-drp-objection-draft
description: Draft an objection before the Dispute Resolution Panel under Section 144C of the Income-tax Act 1961 against a draft assessment order in a transfer-pricing / international-tax case. For an eligible assessee (any person in whose case Transfer Pricing variation has been proposed under Section 92CA(3), OR a non-resident not being a company / foreign company) in receipt of a draft assessment order under Section 144C(1) — files objection before the DRP within 30 days. Encodes the Section 144C eligible-assessee framework, the Section 144C(1) draft-assessment-order requirement, the Section 144C(2) 30-day window, the Section 144C(5) DRP-issue-of-direction power, the Section 144C(13) AO-bound-by-DRP-direction discipline, the Section 92CA TPO reference framework, the Rule 44CA procedural framework, the Form 35A statutory layout, and the binding-direction principle. Auto-fires on "draft DRP objection Section 144C", "draft DRP Form 35A", "draft transfer pricing DRP", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 144C DRP Objection (Form 35A) Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: OBJECTIONS BEFORE THE DISPUTE RESOLUTION PANEL UNDER SUB-SECTION (2) OF SECTION 144C OF THE INCOME-TAX ACT 1961, ON FORM 35A UNDER RULE 44CA OF THE INCOME-TAX RULES 1962
case_short_code: DRP_FORM_35A
form_number: 35A
rule_reference: Rule 44CA of the Income-tax Rules 1962 read with Section 144C of the Income-tax Act 1961
case_number_prefix: per the DIN of the draft assessment order
pleading_type: Objection
typical_forum: Dispute Resolution Panel, [Seat] (DRP-1 Mumbai / DRP-2 Mumbai / DRP Delhi / DRP Bangalore / DRP Chennai / etc.)
typical_parties: Eligible Assessee (the Appellant) + Assessing Officer + Transfer Pricing Officer (where TP variation proposed)
statutory_opening: "These objections are filed by the Eligible Assessee under sub-section (2) of Section 144C of the Income-tax Act 1961 read with Rule 44CA of the Income-tax Rules 1962, on Form 35A, against the draft assessment order dated ____ (DIN ____) passed by the [Assessing Officer designation] under sub-section (1) of Section 144C for Assessment Year ____, proposing variations to the returned income (including the Transfer Pricing variation proposed by the Transfer Pricing Officer under sub-section (3) of Section 92CA in his order dated ____)."
eligible_assessee_assertion: "The Applicant is an Eligible Assessee within the meaning of clause (b) of sub-section (15) of Section 144C of the Income-tax Act 1961, being [a person in whose case Transfer Pricing variation has been proposed under Section 92CA(3) and the variation is prejudicial to the assessee / a non-resident not being a company / a foreign company]. The thirty-day window under Section 144C(2) is computed from the date of receipt of the draft assessment order on ____; the present objection is filed on ____, within limitation."
ground_clauses:
  - "Transfer Pricing — selection of comparables — the TPO erred in selecting [comparable companies] as comparables to the Assessee's [characterised] activity; the comparables suffer from [specify defects — functional dissimilarity / use of multi-year data inappropriately / inclusion of related-party transactions exceeding the related-party-transaction filter / Net Profit Margin filter failures / different turnover band / different geographic market / etc.]."
  - "Transfer Pricing — methodology selection — the TPO erred in applying [TNMM / CUP / RPM / CPM / PSM] as the most appropriate method, whereas the correct most-appropriate method per Section 92C and the Income-tax Rules 1962 Rule 10B is [other method] for the reasons set out below."
  - "Transfer Pricing — functions-assets-risks (FAR) analysis defect — the TPO failed to appreciate the Assessee's FAR profile as a [routine service provider / contract manufacturer / distributor / R&D centre]; the comparables chosen do not correspond to the Assessee's FAR profile."
  - "Transfer Pricing — arm's-length range and arithmetic mean — the TPO erred in applying the arithmetic-mean approach instead of the range-of-arm's-length-prices approach under the Rule 10CA / 10B(4) framework as applicable for the AY in question."
  - "Transfer Pricing — risk-adjustment / working-capital adjustment / capacity-utilisation adjustment denied — the TPO denied the legitimate adjustments which the Assessee is entitled to claim per the lineage of the High Court of Delhi / Bombay / Karnataka on TP adjustments."
  - "International-tax — characterisation of payment — the AO has wrongly characterised the [royalty / FTS / capital gains / business profits] payment in question; the correct characterisation under the relevant DTAA is [different]."
  - "International-tax — PE / business connection — the AO has wrongly held that the Assessee has a Permanent Establishment / business connection in India under Article ____ of the relevant DTAA / Section 9 of the Income-tax Act 1961; the correct position is that no PE / business connection exists."
  - "Procedural — draft assessment order beyond TPO order scope — the AO has incorporated variations beyond those proposed by the TPO under Section 92CA(3), in breach of Section 92CA(4) which binds the AO to the TPO's order."
  - "Procedural — natural-justice defect — the AO / TPO has passed the draft assessment order / TPO order without affording adequate opportunity / without supplying material relied upon / without responding to the Assessee's submissions on key issues."
  - "DRP-direction-binding-on-AO reminder — the DRP's direction under Section 144C(5) is binding on the AO under Section 144C(13); the DRP is requested to issue directions that finally dispose of the variations so that no scope for departure remains at the AO's end."
  - "Leave to file additional grounds — the Applicant craves leave to file additional objections at the time of hearing before the DRP."
relief_clauses:
  - "(a) That this Hon'ble Dispute Resolution Panel may be pleased to issue directions to the Assessing Officer under sub-section (5) of Section 144C of the Income-tax Act 1961, directing the Assessing Officer NOT to make the variations proposed in the draft assessment order dated ____ for AY ____;"
  - "(b) That the Transfer Pricing variation proposed by the Transfer Pricing Officer in his order dated ____ be set aside;"
  - "(c) That the Assessee's returned income be accepted in the final assessment order;"
  - "(d) That the directions of this Hon'ble Panel under Section 144C(5) be binding on the Assessing Officer under Section 144C(13);"
  - "(e) That a personal hearing be granted to the Applicant before this Hon'ble Panel under Section 144C(7);"
  - "(f) Grant such further and other reliefs as this Hon'ble Panel may deem fit and proper."
mandatory_enclosures:
  - copy_of_draft_assessment_order_under_section_144c_1_with_din
  - copy_of_tpo_order_under_section_92ca_3_with_din
  - copy_of_section_92ca_reference_order_by_ao
  - form_3ceb_filed_by_the_assessee
  - transfer_pricing_study_report_with_comparables_data
  - copies_of_intercompany_agreements_relevant_to_the_international_transactions
  - audited_financial_statements_of_the_assessee_and_of_the_comparables_relied_upon
  - copy_of_return_of_income_for_the_ay
  - copies_of_relevant_dtaa_text
  - copies_of_assessees_submissions_filed_before_ao_tpo
  - relevant_judicial_authorities_pdfs_relied_upon
  - form_26_vakalatnama_or_letter_of_authority
accompanying_applications:
  - "Application for personal hearing — included in the prayer above; under Section 144C(7), DRP may permit personal hearing"
  - "Application for stay of demand pending DRP disposal — typically Section 144C(4) bars finalisation of assessment until DRP direction, so no separate stay is required at this stage; the Assessee may, however, seek stay of any consequential proceedings"
  - "Application for additional objections — under the DRP's procedural latitude"
  - "Filing-form-set: Form 35A in quadruplicate (or as per the DRP's current registry requirement) with one set to the DRP, one to the AO, one to the TPO, and one retained"
filing_fee: "No separate fee for Form 35A — physical filing before the DRP registry / e-filing where the DRP has provisioned for electronic filing."
limitation: "Section 144C(2) of the Income-tax Act 1961 — 30 days from the date of receipt of the draft assessment order. NO power to condone delay. If the 30-day window is missed, the AO finalises the assessment under Section 144C(3) and the Assessee's remedy collapses to a Section 246A appeal before CIT(A) — a substantively inferior remedy because the binding-direction principle of Section 144C(13) is lost."
```

## Section 144C eligible-assessee framework

Section 144C(15)(b) defines "eligible assessee" as:
- Any person in whose case the variation referred to in sub-section (1) arises as a consequence of an order of the Transfer Pricing Officer passed under Section 92CA(3)
- A non-resident not being a company, OR a foreign company

The Drafter asserts eligibility in the opening recital.

## Section 144C four-stage procedure

| Stage | Provision | Action |
|---|---|---|
| 1 | Section 144C(1) | AO forwards draft assessment order to the eligible assessee |
| 2 | Section 144C(2) | Assessee files acceptance OR objection within 30 days |
| 3 | Section 144C(5) — (8) | DRP examines, may make further enquiry, issues binding direction |
| 4 | Section 144C(13) | AO passes final assessment in accordance with DRP direction |

## Section 144C(13) — binding direction

The direction issued by the DRP under Section 144C(5) shall be binding on the AO under Section 144C(13). The AO has no discretion to depart from the DRP direction. This is the cardinal advantage of the DRP route over the CIT(A) appellate route.

## Rule 44CA — procedural framework

Rule 44CA of the Income-tax Rules 1962 prescribes the procedure of the DRP — filing of objections on Form 35A, manner of disposal, opportunity of hearing under Section 144C(7), constitution and quorum of the Panel.

## No condonation of delay — strategic note

Section 144C(2) does NOT provide for condonation of delay. If the 30-day window is missed:
- The acceptance is deemed (the Assessee is deemed to have accepted the variations)
- The AO finalises the assessment under Section 144C(3) within 1 month from the end of the month in which the period of 30 days expires
- The Assessee's remedy then lies in a Section 246A appeal before CIT(A) — a substantively inferior remedy because the binding-direction principle of Section 144C(13) is lost; CIT(A) directions are NOT binding on the AO on remand in the same way

The Drafter flags the 30-day-no-condonation discipline in the strongest terms in the procedural endnotes.

## Transfer-pricing methodology framework

The five Indian TP methods under Section 92C read with Income-tax Rules 1962 Rule 10B / 10AB:
- Comparable Uncontrolled Price method (CUP)
- Resale Price Method (RPM)
- Cost Plus Method (CPM)
- Profit Split Method (PSM)
- Transactional Net Margin Method (TNMM)
- Such other method as may be prescribed (Rule 10AB — "any method which takes into account the price which has been charged or paid")

The Drafter argues for the most appropriate method per the Assessee's FAR profile, citing the lineage of decisions on selection-of-method disputes.
