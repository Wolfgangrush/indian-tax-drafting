---
name: high-court-appeal-section-260a-draft
description: Draft an appeal to the High Court on a substantial question of law under Section 260A of the Income-tax Act 1961. For an assessee or the Department aggrieved by an order of the Income-tax Appellate Tribunal where a substantial question of law arises within the Sir Chunilal V. Mehta / Santosh Hazari / Hero Vinoth framework. Encodes the Section 260A statutory framework, the Section 260B two-judge-bench composition, the substantial-question-of-law gateway, the Section 261 Supreme Court onward route, the relevant State High Court Tax Bench Rules, and the limitation under Section 260A(2) read with Section 260A(2A) condonation. Auto-fires on "draft Section 260A appeal", "draft High Court tax appeal", "draft High Court appeal from ITAT", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# High Court Appeal under Section 260A Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_tax_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPEAL TO THE HIGH COURT UNDER SECTION 260A OF THE INCOME-TAX ACT 1961 FROM AN ORDER OF THE INCOME-TAX APPELLATE TRIBUNAL
case_short_code: HC_260A
form_number: n/a (Memorandum of Appeal per State High Court Tax Bench Rules)
rule_reference: Section 260A of the Income-tax Act 1961 + the High Court Rules of the relevant State (Bombay High Court Tax Appeal Rules / Delhi High Court Rules / Gujarat High Court Rules / Karnataka High Court Rules / etc.)
case_number_prefix: Income-tax Appeal No. / Tax Appeal No. (per State High Court convention)
pleading_type: Memorandum of Appeal
typical_forum: High Court — Tax Bench (e.g. High Court of Judicature at Bombay, Nagpur Bench / High Court of Delhi / High Court of Gujarat / etc.)
typical_parties: Appellant (assessee or Commissioner of Income-tax) + Respondent (Commissioner of Income-tax or assessee)
statutory_opening: "This appeal is preferred under Section 260A of the Income-tax Act 1961 against the order dated ____ passed by the Income-tax Appellate Tribunal, [Bench], [City] in I.T.A. No. ____ of ____ for Assessment Year ____, on the substantial questions of law set out hereinafter."
substantial_questions_of_law_framework: "Per Sir Chunilal V. Mehta v. Century Spinning & Manufacturing Co. (1962) read in Santosh Hazari v. Purushottam Tiwari (2001) 3 SCC 179 and Hero Vinoth v. Seshammal (2006) 5 SCC 545, a 'substantial question of law' is one (a) of general public importance, OR (b) directly and substantially affecting the rights of the parties, AND (c) not previously settled by the Supreme Court / Privy Council, AND (d) not free from difficulty / calling for fresh consideration. The questions must be FORMULATED at the threshold of the appeal — the gateway to the High Court's jurisdiction under Section 260A."
substantial_questions_of_law_drafted:
  - "Question 1 — Whether, on the facts and in the circumstances of the case, the Income-tax Appellate Tribunal erred in law in confirming the addition of ₹___ under Section ___ of the Income-tax Act 1961 made by the Assessing Officer, despite the documentary evidence on record establishing ____?"
  - "Question 2 — Whether the Tribunal's finding that ___ is perverse and based on no evidence, and therefore a substantial question of law arises?"
  - "Question 3 — Whether the Tribunal erred in law in misapplying [precedent] to the facts of the present case?"
ground_clauses:
  - "The Tribunal erred in law in [specify legal error] without appreciating that [specify the correct legal position with authority]."
  - "The Tribunal's findings are perverse and based on no evidence on record, raising a substantial question of law."
  - "The Tribunal failed to consider [specific argument / precedent] urged on behalf of the Appellant, rendering the order under appeal liable to be set aside."
  - "The Tribunal misapplied [precedent of Supreme Court / jurisdictional High Court] to the facts of the present case."
  - "The order under appeal is bad in law, against the facts of the case, and contrary to the principles of natural justice."
relief_clauses:
  - "(a) Admit this appeal and formulate the substantial questions of law set out at the threshold;"
  - "(b) Answer the said substantial questions of law in favour of the Appellant;"
  - "(c) Set aside the order of the Income-tax Appellate Tribunal dated ____ in I.T.A. No. ____ of ____;"
  - "(d) Either decide the matter finally under Section 260A(7) of the Income-tax Act 1961 OR remand the matter to the Tribunal for fresh decision in accordance with the answers given;"
  - "(e) Grant such further and other reliefs as this Hon'ble Court may deem fit and proper."
mandatory_enclosures:
  - certified_copy_of_itat_order_with_din
  - certified_copy_of_cit_a_order_with_din
  - certified_copy_of_ao_order_with_din
  - form_36_filed_before_itat
  - grounds_of_appeal_before_itat
  - return_of_income_and_computation_for_the_ay
  - form_26_vakalatnama
  - court_fee_per_state_high_court_rules
accompanying_applications:
  - "Application for stay of demand pendente lite — typically Section 220(6) refused / Section 254(2A) order needs to continue / fresh stay sought from the High Court"
  - "Application for condonation of delay under Section 260A(2A) where appeal is preferred beyond 120 days"
  - "Civil Application for early hearing where revenue-stake / public-importance justifies it"
  - "Application for exemption from filing typed paper-book where the ITAT record is voluminous"
filing_fee: "Court fee per the applicable State Court-Fees Act on the Memorandum of Appeal in a Tax Appeal — varies by State (Bombay Court-Fees Act 1959 / Delhi Court-Fees Act 1870 as applicable / Karnataka Court-Fees and Suits Valuation Act 1958 / etc.). The Drafter computes the court fee from `case-config.md`'s State-High-Court setting."
limitation: "Section 260A(2) of the Income-tax Act 1961 — 120 days from the date on which the order appealed against is received by the assessee or the Chief Commissioner / Commissioner. Section 260A(2A) — power to condone delay on sufficient cause (added by Finance Act 2010)."
```

## Section 260B — Division Bench composition

Section 260B of the Income-tax Act 1961 mandates that a Section 260A appeal be heard by a Bench of not less than two judges of the High Court. The Drafter notes this when the appeal is listed for admission.

## Section 261 — onward route to Supreme Court

Section 261 of the Income-tax Act 1961 provides for appeal to the Supreme Court from a Section 260A High Court order, on certification by the High Court that the case involves a substantial question of law of general importance OR by special leave under Article 136 of the Constitution. The Drafter notes the onward route but does NOT draft the SLP — the sibling plugin `supreme-court-drafting` covers SLPs.

## State High Court Tax Bench Rules

The Drafter pulls the State-specific High Court Tax Bench Rules from `case-config.md`. Variations across States:
- **Bombay High Court** — Tax Appeals heard at Mumbai / Nagpur / Aurangabad / Panaji benches; paper-book format per the Bombay High Court (Original Side) Rules; substantial-questions-of-law admission framework per the *CIT v. Vijaya Bank* (2010) line.
- **Delhi High Court** — Tax Appeals heard by the Tax Bench; Section 260A admission framework per the *CIT v. Sotheby's* (2017) line.
- **Gujarat High Court** — Tax Appeals admission per the *CIT v. Gujarat Narmada Valley Fertilisers* (2014) line.
- Other States follow analogous patterns.

The Drafter formats the Cause Title and the case-number convention per the State High Court chosen in `case-config.md`.

## Substantial question of law — the gateway

The Section 260A appeal is sustainable ONLY if a substantial question of law arises. The Drafter formulates the questions at the THRESHOLD of the appeal (immediately after the cause title) — the questions are the gateway to the High Court's jurisdiction. A question of fact / a question of perverse finding (which is a mixed question of law and fact within *Hero Vinoth*) is the only fact-anchored gateway.

The Drafter does not draft "questions" that are really arguments — every question must satisfy the substantial-question-of-law test.
