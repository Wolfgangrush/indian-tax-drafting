---
name: section-264-revision-application-draft
description: Draft a taxpayer-initiated application for revision before the Principal Commissioner / Commissioner of Income-tax under Section 264 of the Income-tax Act 1961. For an assessee aggrieved by an order of the Assessing Officer who elects the Section 264 revisional remedy in lieu of the Section 246A appellate remedy (e.g. where the appellate remedy is barred by limitation or where the issue is purely on a question of law and the assessee prefers the lighter revisional remedy). Encodes the Section 264 statutory framework, the Section 264(3) one-year limitation, the Section 264(4) bar on revision where the order is the subject of an appeal pending or disposed of, the Section 264 powers to revise in favour of the assessee, and the strategic comparison with Section 246A appeal. Auto-fires on "draft Section 264 revision", "draft Section 264 application", "draft revision application to CIT", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 264 Revision Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION FOR REVISION UNDER SECTION 264 OF THE INCOME-TAX ACT 1961
case_short_code: SECTION_264_APPLICATION
form_number: n/a (open-form application; some PCIT / CIT offices prescribe a local template)
rule_reference: Section 264 of the Income-tax Act 1961
case_number_prefix: Revision Application No. ____ of ____
pleading_type: Revision Application
typical_forum: Principal Commissioner of Income-tax / Commissioner of Income-tax, [City]
typical_parties: Applicant (the assessee) + Department (the Assessing Officer who passed the order under revision)
statutory_opening: "This application is filed by the Applicant under Section 264 of the Income-tax Act 1961, for revision of the order dated ____ passed by the [AO designation] under Section ____ for Assessment Year ____. The Applicant has elected the revisional remedy under Section 264 in lieu of the appellate remedy under Section 246A, on the ground that ____. The Applicant submits that the order under revision is liable to be revised in the Applicant's favour for the reasons set out hereinafter."
section_264_4_election: "The Applicant submits, in compliance with Section 264(4) of the Income-tax Act 1961, that the order under revision is NOT the subject of any appeal currently pending OR disposed of before any appellate authority. The Applicant has not preferred any appeal under Section 246A or Section 253 against the order under revision; the time for filing an appeal has expired / the Applicant has elected not to appeal."
ground_clauses:
  - "Mistake apparent from the record — the order under revision contains a mistake apparent from the record in [specify: misreading of the return entry / arithmetic error / non-application of an admitted deduction / failure to give credit for tax paid / etc.]; the mistake is patent and demands revision."
  - "Order contrary to law — the order under revision is contrary to the settled law of [precedent], in that the AO [specify: applied a wrong section / disallowed a deduction in the teeth of binding authority / made an addition contrary to the express statutory exemption / etc.]."
  - "Order based on wrong facts — the AO's findings of fact in paragraph ____ of the order under revision are contrary to the documentary evidence on record at Enclosure ____."
  - "Order in violation of natural justice — the AO passed the order without affording adequate opportunity of hearing / without considering the Applicant's replies / without supplying the material relied upon."
  - "Order assessing income not legitimately earned — the AO has assessed income that is not chargeable to tax / that is exempt under Section ____ / that has already been taxed in the hands of another / that is not the Applicant's income at all."
  - "Election under Section 264(4) — the Applicant repeats and re-affirms that the order under revision is not the subject of any pending or disposed-of appeal."
relief_clauses:
  - "(a) That this Hon'ble Principal Commissioner / Commissioner of Income-tax may be pleased to revise the order dated ____ passed by the [AO designation] under Section 264 of the Income-tax Act 1961 for AY ____;"
  - "(b) Delete the additions / disallowances aggregating to ₹___ and direct the AO to accept the returned income / grant the deduction claimed / give credit for tax paid;"
  - "(c) Direct that consequential relief be granted including refund of any tax paid pursuant to the order under revision together with interest under Section 244A;"
  - "(d) Grant a personal hearing to the Applicant before any adverse order is passed;"
  - "(e) Grant such further and other reliefs as this Hon'ble Authority may deem fit and proper."
mandatory_enclosures:
  - copy_of_order_under_revision_with_din
  - copy_of_return_of_income_for_the_ay
  - computation_of_income
  - documentary_evidence_supporting_the_grounds_of_revision
  - copy_of_demand_notice_under_section_156
  - copy_of_challan_evidencing_payment_of_tax_demanded_or_application_for_stay_under_section_220_6
  - form_26_vakalatnama_or_letter_of_authority
  - judicial_authorities_pdfs_relied_upon
accompanying_applications:
  - "Application for stay of demand under Section 220(6) pending disposal of the revision"
  - "Application for condonation of delay (where the revision application is filed beyond the one-year limitation under Section 264(3); the PCIT / CIT has discretion under the third proviso to Section 264(3) to admit beyond the period on sufficient cause)"
  - "Application for personal hearing — included in the prayer above"
filing_fee: "Fixed fee under Section 264(7) — currently ₹500 (verify against current notification). The Drafter reflects the fee with the verify-against-current-notification flag."
limitation: "Section 264(3) of the Income-tax Act 1961 — within 1 year from the date on which the order sought to be revised was communicated to the Applicant. The PCIT / CIT has discretion to admit the application beyond the 1-year period on sufficient cause."
```

## Section 264 statutory framework

Section 264 vests the PCIT / CIT with revisional jurisdiction at the **instance of the assessee**, in respect of any order passed by an authority subordinate to the PCIT / CIT (not being an order passed under Section 263). The PCIT / CIT may, on application by the assessee, call for the record and pass such order as the circumstances justify, **subject to the condition that no order shall be passed prejudicial to the assessee** (Section 264(6)).

## Section 264(4) bar — important

No revision shall be made under Section 264:
(a) where an appeal against the order lies to the Deputy Commissioner (Appeals) / CIT(A) / ITAT and time has not expired
(b) where the order is the subject of an appeal pending or disposed of by the Deputy Commissioner (Appeals) / CIT(A) / ITAT

The Drafter's election under Section 264(4) is mandatory in every Section 264 application — the Applicant must affirm that no appeal is pending or disposed of.

## Strategic comparison — Section 264 vs Section 246A appeal

| Feature | Section 246A appeal (CIT(A)) | Section 264 revision (PCIT / CIT) |
|---|---|---|
| Limitation | 30 days | 1 year |
| Fee | Scaled per Section 249(1) | ₹500 fixed (verify) |
| Power to enhance | Yes (CIT(A) may enhance) | No order prejudicial to assessee (Section 264(6)) |
| Power to remand | Yes | Limited |
| Personal hearing | Yes | Discretionary |
| Onward appeal | ITAT under Section 253(1)(a) | Writ jurisdiction (no statutory appeal) |
| Suited for | Substantive appeal with grounds for enhancement-of-relief | Mistake apparent / debatable lesser issues / time-barred appellate remedy |

The Drafter notes the election rationale in the Statement of Facts.

## Onward route — writ on Section 264 order

No statutory appeal lies from a Section 264 order. If the PCIT / CIT's order is adverse, the Applicant's remedy is a writ petition under Article 226 of the Constitution before the jurisdictional High Court (the sibling plugin `indian-hc-drafting` covers writ petitions).
