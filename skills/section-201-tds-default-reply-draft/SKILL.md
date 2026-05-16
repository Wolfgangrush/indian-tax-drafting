---
name: section-201-tds-default-reply-draft
description: Draft a reply to a Section 201 / 201(1A) TDS-default show-cause notice issued by the Assessing Officer (TDS). For a deductor alleged to have failed to deduct tax at source under the Section 194 family of provisions OR to have deducted but failed to deposit, and thereby deemed to be assessee-in-default under Section 201. Encodes the Section 200 duty-to-deposit framework, the Section 201 deemed-default framework, the Section 201(1A) interest framework, the Section 194 family of TDS provisions (194A interest / 194C contractor / 194H commission / 194I rent / 194J professional fees / 194Q purchase of goods etc.), the proviso to Section 201(1) deductee-side-paid-tax defence, the Section 271C penalty-for-failure-to-deduct framework, the Section 273B reasonable-cause discipline, the GE India Technology and Vodafone line on Section 195 non-resident TDS, and the public-domain CBDT TDS Circulars. Auto-fires on "draft Section 201 TDS reply", "draft TDS default reply", "draft 201(1A) reply", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 201 / 201(1A) TDS Default Reply Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: REPLY TO SHOW-CAUSE NOTICE UNDER SECTION 201 / 201(1A) OF THE INCOME-TAX ACT 1961
case_short_code: SECTION_201_REPLY
form_number: n/a (open-form reply)
rule_reference: Section 201 of the Income-tax Act 1961 read with Section 200 and the Section 194 family
case_number_prefix: per the DIN of the Section 201 show-cause notice
pleading_type: Reply
typical_forum: Assessing Officer (TDS) / TDS Ward / Centralised Processing Cell (TDS), Vaishali, Ghaziabad (for TDS-CPC originated proceedings)
typical_parties: Deductor (the Assessee) + Department (AO-TDS / TDS-CPC)
statutory_opening: "This reply is filed by the Deductor in response to the show-cause notice dated ____ (DIN ____) issued under Section 201 / 201(1A) of the Income-tax Act 1961 for the financial year ____, alleging that the Deductor has failed to [deduct tax at source / deposit deducted tax / both] under Section [194A / 194C / 194H / 194I / 194J / 194Q / 195 / etc.] of the Income-tax Act 1961, and proposing to treat the Deductor as assessee-in-default under Section 201 with consequential interest under Section 201(1A) and penalty under Section 271C. The Deductor humbly submits the following defences."
ground_clauses:
  - "Deductee-side-paid-tax defence under the proviso to Section 201(1) — the deductee in question, [Third-Party-A] ([Third-Party-PAN]), has furnished a return of income under Section 139 declaring the amount in question as part of total income, has paid the tax due thereon, and has filed Form 26A certificate of an accountant certifying compliance with the proviso to Section 201(1). The certificate is at Enclosure ____. Per the proviso to Section 201(1), the Deductor is NOT to be treated as assessee-in-default."
  - "No obligation to deduct — the payment in question does not attract Section [194A / 194C / 194H / 194I / 194J / 194Q] for the reason that [analyse: the payee is below threshold / the payment is to a transporter with PAN / the payment is reimbursement / the payment is to an exempted body / the recipient holds a valid Section 197 certificate at Enclosure ____ / the recipient holds a valid Section 197A self-declaration in Form 15G / 15H at Enclosure ____]."
  - "Re-characterisation defence — the payment characterised by the AO as falling under Section ____ properly falls under Section ____ on the doctrine of [contractor-vs-employee / principal-to-principal vs principal-to-agent / etc.]. The TDS rate applicable, if any, is therefore [different rate / nil rate]."
  - "Section 195 / non-resident TDS defence (where applicable) — the payment to the non-resident is not chargeable to tax in India under Section 5 read with the relevant Double Taxation Avoidance Agreement. Per GE India Technology Centre Pvt. Ltd. v. CIT (2010) 327 ITR 456 (SC) and Vodafone International Holdings BV v. UoI (2012) 6 SCC 613, Section 195 obligation to withhold arises only on chargeable sums. Where the payment is not chargeable under the Act read with the DTAA, no Section 195 obligation arises and consequently no Section 201 default."
  - "Reasonable cause under Section 273B — the failure (if any) to deduct or to deposit was occasioned by reasonable cause within the meaning of Section 273B of the Income-tax Act 1961: [specify cause — bona fide interpretational doubt / sudden incapacitation / banking-system failure on the deposit-due date / dispute on chargeability with reliance on contemporaneous CA opinion / etc.]. Per the lineage on Section 273B, reasonable cause defeats Section 271C penalty."
  - "Interest computation error under Section 201(1A) — the interest computed in the show-cause notice is contrary to the formula under Section 201(1A): 1% per month for failure to deduct, 1.5% per month for failure to pay. The computation should run [from date of accrual / from date of payment due / etc.] and not [as computed by the AO]. The correct interest is ₹___."
  - "Limitation bar — the proposed Section 201 proceedings are barred by limitation under Section 201(3) (where applicable — for resident-payee defaults, the present limitation is 7 years from the end of the FY in which payment was made / credit was given; for non-resident-payee defaults under Section 195, no statutory limitation but the principle of reasonable time per the General Insurance Council line)."
  - "Mechanical notice — the show-cause notice is mechanical, computer-generated, without independent application of mind by the AO-TDS, and proceeds on the basis of TDS-CPC-flagged mismatches that have been since reconciled by the Deductor in its quarterly TDS statements at Enclosure ____."
relief_clauses:
  - "(a) That this Hon'ble Assessing Officer (TDS) / TDS-CPC may be pleased to drop the proposed proceedings under Section 201 / 201(1A) of the Income-tax Act 1961 for the FY ____;"
  - "(b) That the Deductor be not treated as assessee-in-default under Section 201;"
  - "(c) That no interest under Section 201(1A) be charged / that interest be re-computed correctly;"
  - "(d) That no penalty under Section 271C be initiated in view of the reasonable cause established under Section 273B;"
  - "(e) That a personal hearing be granted to the Deductor before any adverse order is passed;"
  - "(f) Grant such further and other reliefs as this Hon'ble Authority may deem fit and proper."
mandatory_enclosures:
  - copy_of_section_201_show_cause_notice_with_din
  - copy_of_quarterly_tds_statements_form_24q_or_26q_or_27q_or_27eq_for_the_fy
  - copies_of_form_26a_certificates_from_chartered_accountant_where_deductee_side_paid_tax_defence
  - copies_of_form_15g_15h_or_section_197_lower_deduction_certificates_where_applicable
  - copies_of_payment_vouchers_and_ledger_extracts
  - copies_of_contracts_or_agreements_relevant_to_re_characterisation_grounds
  - relevant_dtaa_text_where_section_195_defence_invoked
  - tan_registration_certificate
  - relevant_judicial_authorities_pdfs_relied_upon
  - form_26_vakalatnama_or_letter_of_authority
accompanying_applications:
  - "Application for filing Form 26A certificate post-show-cause — Rule 31ACB of the Income-tax Rules 1962 procedure"
  - "Application for personal hearing — included in the prayer above"
  - "Application for extension of time to file the reply, where the prescribed window is insufficient"
filing_fee: "No statutory fee for a Section 201 reply — physical filing before the AO-TDS OR e-filing via the e-filing portal where applicable."
limitation: "Per the show-cause notice — the AO prescribes the reply-window in the notice itself, typically 7 to 15 days from the date of receipt, extendable on application. The Drafter notes the original reply-window from `case-config.md`."
```

## Section 201 statutory framework

Section 201(1) — where any person required to deduct tax at source fails to deduct or, having deducted, fails to pay the deducted tax to the credit of the Central Government, such person shall be deemed to be assessee-in-default in respect of the tax so not deducted or paid.

**Proviso to Section 201(1):** No person shall be deemed to be assessee-in-default in respect of TDS not deducted from a resident-payee if:
- The payee has furnished a return of income under Section 139
- The payee has taken into account the sum for the purpose of computing income in the return
- The payee has paid the tax due on the income declared
- The deductor furnishes a certificate from an accountant in Form 26A under Rule 31ACB

The deductee-side-paid-tax defence is the most common and most powerful defence in Section 201 proceedings.

## Section 201(1A) — interest

- Interest at **1% per month or part thereof** on the amount of tax NOT deducted, from the date on which tax was deductible to the date on which it is actually deducted
- Interest at **1.5% per month or part thereof** on the amount of tax deducted but not deposited, from the date of deduction to the date of actual payment

Interest is mandatory and not subject to reasonable-cause waiver (per the consistent line — interest is compensatory, not penal).

## Section 271C — penalty for failure to deduct

Section 271C provides for penalty equal to the amount of tax not deducted. Section 273B provides that no penalty shall be imposable if the assessee proves that there was reasonable cause for the failure. The Drafter pleads reasonable cause where applicable.

## Section 194 family — common TDS provisions

| Section | Payment type | Threshold | Rate |
|---|---|---|---|
| 192 | Salary | Slab | Average rate per slab |
| 192A | EPF withdrawal | ₹50,000 | 10% |
| 194A | Interest other than securities | ₹40,000 (banks) / ₹5,000 (other) | 10% |
| 194B | Lottery / crossword puzzle winnings | ₹10,000 | 30% |
| 194C | Contractor / sub-contractor payment | ₹30,000 single / ₹1,00,000 aggregate | 1% (individual / HUF) / 2% (other) |
| 194H | Commission or brokerage | ₹15,000 | 5% |
| 194I | Rent | ₹2,40,000 | 10% (land / building) / 2% (plant / machinery) |
| 194J | Fees for professional or technical services | ₹30,000 | 10% (professional) / 2% (technical) |
| 194Q | Purchase of goods | ₹50 lakh | 0.1% |
| 195 | Payments to non-residents | n/a — chargeability test | varies per Act / DTAA |

(Verify rates and thresholds against the Finance Act of the relevant FY.)

## GE India Technology and Vodafone line — Section 195

For Section 195 TDS on payments to non-residents, the obligation to withhold arises ONLY on sums chargeable to tax in India:
- *GE India Technology Centre Pvt. Ltd. v. CIT* (2010) 327 ITR 456 (SC) — chargeability is the threshold
- *Vodafone International Holdings BV v. UoI* (2012) 6 SCC 613 — indirect transfer chargeability framework (subsequently modified by retrospective Section 9 amendment by Finance Act 2012, which was itself substantially walked back by the Taxation Laws (Amendment) Act 2021)
- DTAA over-ride per Section 90(2) — the more beneficial of Act / DTAA applies

## Limitation under Section 201(3)

For resident-payee defaults, the current limitation is **7 years from the end of the FY** in which payment was made or credit was given. For non-resident-payee defaults under Section 195, no statutory limitation; the principle of reasonable time per the *General Insurance Council* line and other High Court precedent.
