---
name: section-263-revision-objection-draft
description: Draft an objection to a Section 263 revision show-cause notice issued by the Principal Commissioner / Commissioner of Income-tax proposing to revise an Assessing Officer's order on the ground that it is erroneous in so far as it is prejudicial to the interests of the revenue. For an assessee in receipt of a Section 263 show-cause notice. Encodes the Section 263 statutory framework, the Malabar Industrial Co. Ltd. v. CIT (2000) 243 ITR 83 twin-condition doctrine (erroneous AND prejudicial to revenue — both must be satisfied), the CIT v. Max India Ltd. (2007) 295 ITR 282 one-of-two-views doctrine, the CIT v. Greenworld Corporation (2009) 314 ITR 81 substitution-of-view discipline, the Explanation 2 to Section 263 (deemed-erroneous categories), and the limitation under Section 263(2). Auto-fires on "draft Section 263 objection", "draft revision objection PCIT", "draft Malabar Industrial reply", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 263 Revision Show-Cause Objection Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: REPLY TO SHOW-CAUSE NOTICE UNDER SECTION 263 OF THE INCOME-TAX ACT 1961
case_short_code: SECTION_263_REPLY
form_number: n/a (open-form reply)
rule_reference: Section 263 of the Income-tax Act 1961
case_number_prefix: per the DIN of the Section 263 show-cause notice
pleading_type: Objection / Reply
typical_forum: Principal Commissioner of Income-tax / Commissioner of Income-tax, [City]
typical_parties: Assessee + Principal Commissioner / Commissioner of Income-tax
statutory_opening: "This reply is filed by the Assessee in response to the show-cause notice dated ____ (DIN ____) issued under Section 263 of the Income-tax Act 1961 for Assessment Year ____, proposing to revise the order dated ____ passed by the [AO designation] under Section ____ on the ground that the said order is erroneous in so far as it is prejudicial to the interests of the revenue. The Assessee humbly submits the following objections."
ground_clauses:
  - "Malabar Industrial twin-condition not satisfied — per the Supreme Court in Malabar Industrial Co. Ltd. v. CIT (2000) 243 ITR 83, jurisdiction under Section 263 vests only when the AO's order is BOTH erroneous AND prejudicial to the interests of the revenue. The two conditions are cumulative. The AO's order in question is NEITHER erroneous NOR prejudicial to revenue, for the reasons set out below."
  - "AO's order not erroneous — the AO conducted full and proper enquiry into the issue now sought to be revised (refer notices issued by the AO at Enclosure ____ and the Assessee's replies thereto at Enclosure ____). The AO applied his mind, considered the documentary evidence, and accepted the Assessee's position. The order is supported by reasons and proceeds on a possible view of law and facts."
  - "One-of-two-views possible — per CIT v. Max India Ltd. (2007) 295 ITR 282, where two views are possible and the AO has adopted one of them, the order is NOT erroneous merely because the PCIT prefers the other view. Reliance on Max India is well-settled across High Courts."
  - "Substitution of view impermissible — per CIT v. Greenworld Corporation (2009) 314 ITR 81, revision under Section 263 cannot be used to substitute the AO's view with the PCIT's view. The revisional power is supervisory, not appellate."
  - "Explanation 2 to Section 263 inapplicable — none of the deemed-erroneous categories in Explanation 2 (clauses (a) to (d)) applies on the facts: (a) the order was passed after enquiry on the issue; (b) the order was not passed without making necessary verifications; (c) the order was not passed allowing relief without inquiring into the claim; (d) the order is not contrary to any binding decision of jurisdictional High Court / Supreme Court."
  - "Not prejudicial to revenue — per Malabar Industrial, the order is not prejudicial to the revenue because [analyse: the addition would not, on a proper view, succeed; the deduction allowed is in fact admissible; the position adopted is in line with the consistent position taken in earlier and later years and accepted in scrutiny]."
  - "Change of opinion — the issue now sought to be revised was specifically considered by the AO during assessment proceedings; revision on a change of opinion is impermissible."
  - "Material relied upon not supplied — the PCIT has not supplied to the Assessee the material relied upon to form the prima facie view that the AO's order is erroneous and prejudicial; breach of natural justice."
  - "Limitation bar — the proposed revision is barred by limitation under Section 263(2) — the order to be revised was passed on ____; the two-year window from the end of the FY in which the AO's order was passed has expired (or the limitation runs to date ____ and the show-cause notice was issued out of time)."
relief_clauses:
  - "(a) That this Hon'ble Principal Commissioner / Commissioner of Income-tax may be pleased to drop the proposed revision proceedings under Section 263 of the Income-tax Act 1961 for AY ____;"
  - "(b) That a personal hearing be granted to the Assessee before any adverse order is passed;"
  - "(c) That the material relied upon be supplied to the Assessee in full;"
  - "(d) Grant such further and other reliefs as this Hon'ble Authority may deem fit and proper."
mandatory_enclosures:
  - copy_of_section_263_show_cause_notice_with_din
  - copy_of_assessment_order_with_din
  - copies_of_notices_issued_by_ao_under_section_142_1_and_143_2_demonstrating_enquiry_conducted
  - copies_of_assessees_replies_to_ao_demonstrating_disclosure
  - copy_of_return_of_income_for_the_ay
  - copies_of_relevant_judicial_authorities_pdfs_relied_upon_principally_malabar_industrial_max_india_greenworld
  - form_26_vakalatnama_or_letter_of_authority
accompanying_applications:
  - "Application for personal hearing — included in the prayer above"
  - "Application for supply of material relied upon by the PCIT, where the show-cause notice fails to enclose underlying material"
  - "Application for extension of time to file the reply, where the prescribed window is insufficient"
filing_fee: "No statutory fee for a Section 263 reply — typically physical or e-filed submission before the PCIT / CIT."
limitation: "Per the show-cause notice — the PCIT / CIT prescribes the reply-window in the notice itself. The Drafter notes the original reply-window from `case-config.md`."
```

## Section 263 statutory framework

Section 263 vests the Principal Commissioner / Commissioner with revisional jurisdiction to call for and examine the record of any proceeding under the Act, and if the PCIT / CIT considers that any order passed therein by the AO is **erroneous in so far as it is prejudicial to the interests of the revenue**, the PCIT / CIT may pass such order thereon as the circumstances of the case justify, including an order enhancing or modifying the assessment, or cancelling the assessment and directing a fresh assessment.

## Twin-condition doctrine — Malabar Industrial (2000) 243 ITR 83 (SC)

The two conditions are cumulative:
1. The AO's order must be **erroneous**
2. The order must be **prejudicial to the interests of the revenue**

Both must be satisfied. Defeating either prong defeats Section 263.

## One-of-two-views doctrine — Max India (2007) 295 ITR 282 (SC)

Where the AO has adopted one of two views legally tenable, the order is NOT erroneous merely because the PCIT prefers the other view. The AO's view, if a possible one, prevails against revisional substitution.

## Substitution-of-view doctrine — Greenworld Corporation (2009) 314 ITR 81 (SC)

Revision under Section 263 is supervisory, not appellate. It cannot be used to substitute the AO's reasoned view with the PCIT's preferred view.

## Explanation 2 to Section 263 — deemed-erroneous categories

Inserted by Finance Act 2015, Explanation 2 deems an AO's order erroneous if:
(a) the order is passed without making inquiries or verification which should have been made
(b) the order is passed allowing any relief without inquiring into the claim
(c) the order has not been made in accordance with any order, direction or instruction issued by the Board under Section 119
(d) the order has not been passed in accordance with any decision which is prejudicial to the assessee, rendered by the jurisdictional High Court or Supreme Court in the case of the assessee or any other person

The Assessee defeats Explanation 2 by demonstrating that (a) and (b) do not apply on facts (AO made enquiries; AO allowed relief after inquiring), (c) does not apply (no contrary CBDT instruction), and (d) does not apply (no contrary binding precedent).

## Limitation under Section 263(2)

No order of revision under Section 263 shall be made after the expiry of **two years from the end of the financial year** in which the order sought to be revised was passed. The Verifier checks for limitation compliance.

## Strategic note — reply vs writ vs ITAT appeal

If the Section 263 order is adverse, the Assessee's appeal lies to the ITAT under Section 253(1)(b) [for orders of Commissioner] within 60 days. Writ relief against a vexatious Section 263 show-cause notice is rare and granted only where the notice is wholly without jurisdiction; the ordinary course is to engage on merits and, if adverse, to appeal.
