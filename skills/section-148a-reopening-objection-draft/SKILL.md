---
name: section-148a-reopening-objection-draft
description: Draft an objection to a Section 148A(b) show-cause notice issued under the Finance-Act-2021-overhauled reassessment regime. For an assessee in receipt of a show-cause notice from the Assessing Officer asking why a notice under Section 148 should not be issued. Encodes the Section 147 income-escaping-assessment framework, the Section 148 issue-of-notice procedure, the Section 148A four-stage procedure (148A(a) enquiry / 148A(b) show-cause / 148A(c) reply / 148A(d) order), the Section 149 time-limit framework (3 years / 6 years schemes), the Section 151 sanction-by-specified-authority framework, the Union of India v. Ashish Agarwal (4 May 2022) transitional discipline, and the post-Ashish-Agarwal High Court line. Auto-fires on "draft Section 148A objection", "draft reopening objection", "draft Section 148A(b) reply", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 148A(b) Show-Cause Objection Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: OBJECTION TO SHOW-CAUSE NOTICE UNDER SECTION 148A(b) OF THE INCOME-TAX ACT 1961
case_short_code: SECTION_148A_OBJECTION
form_number: n/a (open-form reply)
rule_reference: Section 148A of the Income-tax Act 1961 (inserted by the Finance Act 2021, operative 01-04-2021)
case_number_prefix: per the DIN of the show-cause notice
pleading_type: Objection / Reply
typical_forum: Assessing Officer / National Faceless Assessment Centre, Delhi (per the show-cause notice originating authority)
typical_parties: Assessee + Department (AO)
statutory_opening: "This reply is filed by the Assessee under Section 148A(c) of the Income-tax Act 1961 in response to the show-cause notice dated ____ (DIN ____) issued under Section 148A(b) of the Income-tax Act 1961 for Assessment Year ____, calling upon the Assessee to show cause why a notice under Section 148 should not be issued. The Assessee humbly submits the following objections within the prescribed window."
ground_clauses:
  - "No information that meets the Explanation 1 to Section 148 standard — the Department has not placed before the Assessee any 'information which suggests that income chargeable to tax has escaped assessment' within the meaning of Explanation 1 to Section 148. The material relied upon in the show-cause notice consists of [analyse the material] which does not constitute 'information' within the statutory definition."
  - "Change of opinion — the reopening proceeds on a mere change of opinion on facts already disclosed by the Assessee in the return / assessment proceedings. Per the Supreme Court in CIT v. Kelvinator of India Ltd. (2010) 320 ITR 561 (decided under the un-amended Section 147 but the doctrine survives in post-amendment jurisprudence per the High Court line), reassessment cannot be a substitute for review."
  - "Barred by limitation under Section 149 — the AY in question falls beyond the three-year window under Section 149(1)(a) AND does not satisfy the six-year window under Section 149(1)(b) (which requires the escaped income chargeable to tax to be represented in the form of an asset / expenditure / entry in books amounting to ₹50 lakh or more). The Department has not established that the income alleged to have escaped exceeds the ₹50 lakh threshold or is represented in the prescribed form."
  - "Sanction defect under Section 151 — the sanction to issue the show-cause notice has not been obtained from the specified authority of appropriate rank (Principal Chief Commissioner / Principal Director General / Chief Commissioner / Director General — for cases where more than three years have elapsed from the end of the relevant AY). Absence of valid sanction renders the notice non-est."
  - "Ashish Agarwal transitional defect (where applicable) — where the show-cause notice originated as a pre-01-04-2021 Section 148 notice retrospectively converted to a Section 148A(b) notice per the Supreme Court's direction in Union of India v. Ashish Agarwal (4 May 2022), the Department has not complied with the directions of the Supreme Court — [specify defect: non-supply of material relied upon / non-grant of personal hearing / order under Section 148A(d) passed without considering the Assessee's reply / etc.]."
  - "Reasons-recorded defect — the reasons recorded for forming the belief that income has escaped assessment are vague / mechanical / non-application-of-mind / based on borrowed satisfaction from a search or survey on a third party without independent application of mind."
  - "Material relied upon not supplied — the Department has not supplied to the Assessee the material relied upon to form the belief, in breach of the Supreme Court direction in Ashish Agarwal and the natural-justice requirement under Section 148A(b) read with the proviso."
  - "Disclosure complete in original assessment — the Assessee had made full and true disclosure of all material facts in the original return / assessment proceedings; reopening on the basis of facts already on the AO's record is impermissible per the first proviso to the un-amended Section 147 (the doctrine survives in the post-Finance-Act-2021 regime per the High Court line)."
relief_clauses:
  - "(a) That this Hon'ble Assessing Officer / Faceless Assessment Centre may be pleased to drop the proceedings under Section 148A(b) of the Income-tax Act 1961 and pass an order under Section 148A(d) holding that it is NOT a fit case for issuance of notice under Section 148;"
  - "(b) That no notice under Section 148 of the Income-tax Act 1961 be issued for AY ____;"
  - "(c) That a personal hearing be granted to the Assessee under the proviso to Section 148A(b) of the Income-tax Act 1961;"
  - "(d) That the material relied upon to form the belief be supplied to the Assessee in full, with adequate time to file further submissions thereon;"
  - "(e) Grant such further and other reliefs as this Hon'ble Authority may deem fit and proper."
mandatory_enclosures:
  - copy_of_show_cause_notice_under_section_148ab_with_din
  - copy_of_return_of_income_for_the_relevant_ay
  - copy_of_assessment_order_under_section_143_3_or_intimation_under_section_143_1_where_applicable
  - documentary_evidence_rebutting_the_material_relied_upon_in_the_show_cause
  - copy_of_form_26_vakalatnama_or_letter_of_authority
  - any_communications_made_to_the_ao_in_response_to_earlier_section_148a_a_enquiry_if_any
  - relevant_judicial_authorities_pdfs_relied_upon
accompanying_applications:
  - "Application for personal hearing under the proviso to Section 148A(b) — included in the prayer above; may be filed as a separate application for clarity"
  - "Application for extension of time under the proviso to Section 148A(b) where the prescribed reply-window is insufficient to address the material relied upon"
  - "Application for supply of material relied upon, where the show-cause notice has been issued without supplying the underlying material"
filing_fee: "No statutory fee for a Section 148A(b) reply — electronic filing on the Income-tax e-filing portal (where faceless) OR physical filing before the jurisdictional AO."
limitation: "Per the show-cause notice — typically two weeks from the date of receipt, extendable on application under the proviso to Section 148A(b). The Drafter notes the original reply-window from `case-config.md` and any extension granted."
```

## Section 148A four-stage procedure

| Stage | Provision | Action |
|---|---|---|
| (a) | Section 148A(a) | AO conducts enquiry with prior approval of specified authority |
| (b) | Section 148A(b) | AO issues show-cause notice with material relied upon |
| (c) | Section 148A(c) | Assessee files reply within prescribed window |
| (d) | Section 148A(d) | AO passes order on whether it is a fit case for issuance of notice under Section 148 |

If the Section 148A(d) order holds it is a fit case, the AO then issues the notice under Section 148. The Section 148A(d) order is itself appealable in writ jurisdiction; appeal under Section 246A lies only after the assessment / reassessment order is passed.

## Ashish Agarwal transitional discipline

*Union of India v. Ashish Agarwal* (Supreme Court, 4 May 2022 — Civil Appeal No. 3005 of 2022) — directions:

- All pre-01-04-2021 Section 148 notices issued under the un-amended Section 148 between 01-04-2021 and 30-06-2021 deemed to be Section 148A(b) show-cause notices
- AO required to supply the material relied upon to the Assessee within 30 days
- Assessee required to file reply within 2 weeks of receipt of material
- AO required to pass Section 148A(d) order in accordance with the post-amendment regime
- The order would then determine whether a fresh notice under Section 148 would issue
- All defences available to the Assessee in law preserved

Post-*Ashish Agarwal* High Court line (Allahabad / Delhi / Bombay / Calcutta / Gujarat / Madras) — the contours of the transitional regime, the *Ashish Agarwal* + *Rajeev Bansal* (Supreme Court, 03-10-2024) framework on TOLA 2020 limitation overlap.

## Section 149 — limitation map

- **3 years (general)** — Section 149(1)(a) — from end of the relevant AY
- **6 years** — Section 149(1)(b) — from end of the relevant AY, ONLY where the income chargeable to tax which has escaped assessment AND is represented in the form of an asset / expenditure in respect of a transaction OR an entry in the books of account amounts to or is likely to amount to ₹50 lakh or more
- **No notice beyond the above** unless under Section 149(1)(c) for cases of overseas-asset-related income escape

## Section 151 — sanction

- **Up to 3 years from end of AY** — sanction by Principal Commissioner / Principal Director / Commissioner / Director
- **Beyond 3 years from end of AY** — sanction by Principal Chief Commissioner / Principal Director General / Chief Commissioner / Director General

Absence of valid sanction is a substantive ground; the Verifier flags absence.
