---
name: section-12a-registration-form-10a-draft
description: Draft an application for registration / re-registration of a charitable or religious trust or institution under Section 12A read with Section 12AB of the Income-tax Act 1961, on Form 10A under Rule 17A of the Income-tax Rules 1962. Covers (a) provisional registration for a newly formed entity under Section 12AB(1)(c), (b) regular registration on conversion of provisional registration under Section 12AB(1)(b), and (c) re-registration under the post-Finance-Act-2020 regime for an existing Section 12A / 12AA registered trust under Section 12AB(1)(a)(i). Encodes the Section 2(15) charitable-purpose definition, the Section 12A conditions, the Section 12AB procedure, the Section 13 denial-of-exemption framework, the Rule 17A Form 10A layout, and the post-Finance-Act-2020 re-registration window (extended multiple times by CBDT). Auto-fires on "draft Form 10A 12A registration", "draft trust registration application", "draft Section 12AB registration", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 12A / 12AB Form 10A Registration Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION FOR REGISTRATION OF CHARITABLE OR RELIGIOUS TRUST OR INSTITUTION UNDER CLAUSE (ac) OF SUB-SECTION (1) OF SECTION 12A OF THE INCOME-TAX ACT 1961, ON FORM 10A UNDER RULE 17A OF THE INCOME-TAX RULES 1962
case_short_code: FORM_10A_12AB
form_number: 10A
rule_reference: Rule 17A of the Income-tax Rules 1962
case_number_prefix: Application No. (assigned electronically by the Income-tax e-filing portal)
pleading_type: Application
typical_forum: Principal Commissioner of Income-tax (Exemptions) / Commissioner of Income-tax (Exemptions), [jurisdictional bench]
typical_parties: Applicant (the trust / institution) — Respondent (the Income-tax Department, formal-respondent character)
statutory_opening: "This application is filed under clause (ac) of sub-section (1) of Section 12A read with Section 12AB of the Income-tax Act 1961 and Rule 17A of the Income-tax Rules 1962, for [provisional registration under Section 12AB(1)(c) / regular registration under Section 12AB(1)(b) on conversion of provisional registration / re-registration under Section 12AB(1)(a)(i) of an existing Section 12A / 12AA registered trust under the post-Finance-Act-2020 regime] of the Applicant trust / institution, established for charitable / religious purposes within the meaning of Section 2(15) of the Income-tax Act 1961."
statement_of_objects_template: "The Applicant trust / institution is established with the following charitable / religious objects within the meaning of Section 2(15) of the Income-tax Act 1961 — [enumerate objects from the Trust Deed / MoA: relief of the poor / education / yoga / medical relief / preservation of environment / preservation of monuments / advancement of any other object of general public utility]. The objects are non-religious-non-charitable-purpose-free; no part of the corpus is applied for the benefit of any individual or family."
statement_of_activities_template: "The Applicant has carried on the following activities in furtherance of the said objects during the last three financial years — [enumerate activities with brief descriptions, amounts, beneficiaries-class, locations]. The activities are within Section 2(15) and within the objects set out in the Trust Deed / MoA."
ground_clauses_n_a: "Form 10A is an application, not an appeal — there are no Grounds of Appeal. The Form's prescribed Particulars block + Statement of Objects + Statement of Activities + accompanying declarations + Verification carry the body of the application."
relief_clauses:
  - "(a) Grant provisional registration to the Applicant trust / institution under Section 12AB(1)(c) of the Income-tax Act 1961 for an initial period of three years, OR"
  - "(b) Grant regular registration under Section 12AB(1)(b) on conversion of provisional registration, for a period of five years, OR"
  - "(c) Grant re-registration under Section 12AB(1)(a)(i) for a period of five years to the Applicant being an existing Section 12A / 12AA registered trust, in accordance with the post-Finance-Act-2020 regime;"
  - "(d) Grant such further and other reliefs as the Principal Commissioner / Commissioner of Income-tax (Exemptions) may deem fit and proper."
mandatory_enclosures:
  - trust_deed_or_memorandum_of_association_with_rules
  - certificate_of_registration_with_competent_authority_societies_registration_act_1860_or_maharashtra_public_trusts_act_1950_or_section_8_companies_act_2013
  - existing_section_12a_or_12aa_registration_certificate_where_re_registration_sought
  - existing_section_80g_registration_certificate_where_applicable
  - pan_of_the_trust_institution
  - audited_accounts_for_the_last_three_financial_years
  - income_tax_returns_for_the_last_three_financial_years
  - list_of_trustees_with_pan_and_address
  - self_certified_copy_of_the_documents_evidencing_creation_of_the_trust
  - foreign_contribution_regulation_act_2010_registration_where_applicable
accompanying_applications:
  - "Where re-registration is sought and the application is delayed beyond the CBDT-extended window — condonation-of-delay application under Section 119(2)(b) of the Income-tax Act 1961"
  - "Where Section 80G renewal sought in parallel — Form 10G under Rule 11AA"
  - "Where the trust has unspent income — application under Section 11(2) for accumulation"
filing_fee: "No separate fee for Form 10A — electronic filing on the Income-tax e-filing portal with digital signature of the authorised signatory."
limitation: "Per CBDT notification and successive extensions, the re-registration window for existing Section 12A / 12AA trusts under the post-Finance-Act-2020 regime has been extended multiple times. The Drafter notes the current operative deadline from `case-config.md` and flags for condonation-of-delay application under Section 119(2)(b) if delayed."
```

## Section 12AB regime (post-Finance-Act-2020) — discipline

Pre-Finance-Act-2020, registration was granted under Section 12AA (introduced by Finance Act 1996). Post-Finance-Act-2020, the regime is Section 12AB:

- **Section 12AB(1)(a)(i)** — regular registration on application by an existing registered trust (validity 5 years)
- **Section 12AB(1)(b)** — re-registration on conversion of provisional registration (validity 5 years)
- **Section 12AB(1)(c)** — provisional registration for a newly formed trust where activities have not yet commenced (validity 3 years)

The Drafter selects the correct clause from `case-config.md`'s registration-track field.

## Section 2(15) — charitable-purpose definition

"Charitable purpose" includes:
- Relief of the poor
- Education
- Yoga
- Medical relief
- Preservation of environment (including watersheds, forests, wildlife)
- Preservation of monuments / places / objects of artistic or historic interest
- Advancement of any other object of general public utility

**Proviso to Section 2(15):** "Advancement of any other object of general public utility" is NOT a charitable purpose if it involves trade / commerce / business or rendering of service in relation to trade / commerce / business for a fee, unless the receipts from such activity do not exceed 20% of total receipts of the trust for the previous year.

The Drafter pleads the trust's objects strictly within Section 2(15) and confirms compliance with the proviso where the trust falls within the "general public utility" sub-category.

## Statement of Objects + Statement of Activities

For Form 10A, the Statement of Objects is drawn directly from the Trust Deed / MoA; the Statement of Activities is drawn from the trust's last-three-years' activity records. Both are mandatory enclosures.

## Section 13 — denial-of-exemption discipline

The Drafter pre-empts Section 13 objections by confirming in the Statement of Objects that:
- No part of the income or property is applied for the benefit of the trustees or their relatives (Section 13(1)(c))
- No part of the income enures to a private religious trust which does not enure for the benefit of the public (Section 13(1)(a))
- No funds of the trust are invested or deposited otherwise than in the modes specified in Section 11(5) (Section 13(1)(d))

## Re-registration window — extension flags

The CBDT has extended the re-registration window for existing Section 12A / 12AA trusts under the post-Finance-Act-2020 regime multiple times by Circular. The Drafter pulls the current operative deadline from `case-config.md` (with a *"verify against current Circular"* flag) and, where delayed beyond the operative deadline, files a condonation-of-delay application under Section 119(2)(b) along with Form 10A.
