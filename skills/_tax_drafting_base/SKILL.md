---
name: _tax_drafting_base
description: Universal Indian direct-tax pleading skeleton. Shared base for all 10 case-type drafting skills. Holds the standard structure (Form identifier + Rule reference -> Descriptive title -> Particulars block -> Statement of Facts where applicable -> Grounds of Appeal -> Relief Claimed -> Verification -> Signature block -> Procedural endnotes -> Enclosures -> Accompanying applications), the Income-tax Act 1961 + Income-tax Rules 1962 + ITAT Rules 1963 + Faceless Schemes statutory authority stack, the Form-correspondence rules (Form 35 / Rule 45, Form 36 / Rule 47, Form 10A / Rule 17A, Form 35A / Rule 44CA), the assessment-year vs financial-year discipline, the limitation discipline, and the Finance Act 2021 reassessment overhaul (Section 148A) cross-reference. NOT invoked directly — extended by every case-type skill in this plugin.
allowed-tools: Read
---

# `_tax_drafting_base` — universal Indian direct-tax pleading skeleton

This base skill defines the **structural shape** of any direct-tax appellate pleading or statutory registration application drafted by the plugin. Case-type skills extend this base with case-type-specific Form layouts, Statement-of-Facts patterns, Grounds-of-Appeal patterns, Relief Claimed clauses, and accompanying applications.

## Universal skeleton

```
1. FORM IDENTIFIER + RULE REFERENCE (where the pleading is on a statutorily-prescribed Form)
   FORM NO. {{form_number}}
   [See rule {{rule_number}}]

   (Where the pleading is an open-form reply — Section 148A objection / Section 263
   reply / Section 271-270A reply / Section 201 reply — the head is the descriptive
   title with the section reference.)

2. DESCRIPTIVE TITLE
   {{case_type.descriptive_title}}

3. PARTICULARS BLOCK (statutorily prescribed for each Form)
   For Form 35:
     1. Name and address of the appellant
     2. Permanent Account Number
     3. Aadhaar-linked-PAN status
     4. Assessment Year in connection with which the appeal is preferred
     5. Designation of the Officer passing the order appealed against
     6. Address of the Officer
     7. Section and sub-section of the Income-tax Act under which the order
        appealed against was passed
     8. Date of order appealed against
     9. Date of service of the order appealed against
     10. Document Identification Number (DIN) of the order appealed against
     11. Total income assessed
     12. Total tax including surcharge and cess
     13. Amount of addition / disallowance challenged
     14. Amount of penalty (if applicable)
     15. Demand under Section 156
     16. Whether tax determined in the order has been paid (Yes / No / Part)
     17. Section under which appeal is preferred
     18. Authorised Representative particulars (Name / Enrolment / Vakalatnama)

   For Form 36 (ITAT):
     Similar particulars adapted to ITAT — order of CIT(A) reference + date + DIN;
     details of the Income-tax Authority passing the orders appealed against;
     Section under which appeal is preferred (Section 253(1)(a) / (b) / (c) /
     Section 253(2)).

   For Form 10A (Section 12A registration):
     Particulars of the applicant trust / institution — Name, Date of creation,
     Address, PAN, Authorised signatory, Status (trust / society / Section 8
     company), Section under which application is made (provisional under
     Section 12AB(1)(c) / regular under 12AB(1)(a)(i) / re-registration under
     12AB(1)(b)).

   For Form 35A (DRP):
     Particulars adapted to DRP — Name, PAN, AY, AO designation, TPO designation,
     DIN of draft assessment order.

   For open-form replies (Section 148A / Section 263 / Section 270A-271 /
   Section 201):
     Particulars block adapted to the show-cause notice — Reference of the
     show-cause notice, Section under which issued, Date of issue, DIN of the
     show-cause notice, AY in question, Name and PAN of the assessee.

4. STATEMENT OF FACTS (where applicable — Form 35 clause; open-form-reply chronology)
   Numbered narrative paragraphs anchored on dates and on enclosure markers.
   Standard fact-sequence for an appeal:
     4.1 Return of income filed on ____ declaring income of ₹___ (Enclosure 1).
     4.2 Notice under Section 143(2) issued on ____ (Enclosure 2).
     4.3 Notice under Section 142(1) issued on ____ (Enclosure 3).
     4.4 Reply / written submissions filed by the Appellant on ____ (Enclosure 4).
     4.5 Show-cause pre-assessment issued on ____ (Enclosure 5).
     4.6 Reply to show-cause filed by the Appellant on ____ (Enclosure 6).
     4.7 Assessment order under Section 143(3) / 144 / 147 r/w 148A(d) passed
         on ____ by the [AO designation], adding ₹___ under Section [68 / 69 /
         14A / 40(a)(ia) / 40(b) / etc.] (Enclosure 7).
     4.8 Demand notice under Section 156 issued on ____ for ₹___ (Enclosure 8).
     4.9 Cause of action — the present appeal is preferred against the order
         under appeal on the grounds set out hereinafter.

5. GROUNDS OF APPEAL (numbered consecutively)
   Ground 1. {{case_type.ground_1}}
   Ground 2. {{case_type.ground_2}}
   Ground 3. {{case_type.ground_3}}
   ...
   (Each ground identifies the legal proposition, anchors to the statutory
   provision allegedly mis-applied or breached, anchors to the document
   supporting the ground, and concludes with the prayer logically corresponding
   to the ground.)

   Standard concluding grounds:
   - "The order under appeal is bad in law, against the facts of the case, and
     contrary to the principles of natural justice."
   - "The Appellant craves leave to add to, alter, amend, modify, or substitute
     the above grounds of appeal at any stage of the proceedings."

6. RELIEF CLAIMED / PRAYER
   {{case_type.relief_clauses}}

   For these and such further and other reliefs as this Hon'ble [authority] may
   deem fit and proper.

7. VERIFICATION (statutorily prescribed text)
   For Form 35: "I, [Name of the appellant / authorised signatory], the appellant,
   do hereby declare that what is stated above is true to the best of my
   information and belief. Verified today, the ____ day of ____, 20____ at
   [Place]."

   For Form 36: similar text adapted to ITAT.

   For Form 10A: the statutorily-prescribed declaration by the authorised
   signatory of the trust / institution.

   For open-form replies: verification declaration adapted to the matter.

                                       [Appellant / Authorised Signatory]
                                       [Designation]
                                       [Assessee]

8. SIGNATURE BLOCK
   Signed by the appellant / applicant / authorised signatory.
   For ITAT (Form 36), additional signature space for the Authorised
   Representative.

9. PROCEDURAL ENDNOTES
   - Number of copies to be filed (electronically uploaded — single set
     on Income-tax e-filing portal where Faceless Scheme applies; physical
     filing in triplicate where physical bench applies)
   - Filing-fee tender (Section 249(1) / Section 253(6) slab — VERIFY against
     current notification)
   - Mandatory enclosures (certified copy of order appealed against with DIN;
     statement of facts; grounds of appeal; demand notice under Section 156
     where applicable; Form 26 Vakalatnama or letter of authority)
   - Electronic filing instruction (where the Income-tax e-filing portal
     applies — Section 12A / Form 10A; Section 148A objection; Faceless
     Appeal Scheme 2021 filings)
   - Hindi-language filing option (for ITAT appeals in notified-State benches
     under the ITAT Rules)

10. LIST OF ENCLOSURES
    Enclosure 1 — [description] dated ____
    Enclosure 2 — [description] dated ____
    ...
    (Standard enclosures: certified copy of order appealed against with DIN;
    return of income for the AY; computation of income; audit report in
    Form 3CA / 3CB / 3CD where applicable; ledger extracts of disputed items;
    bank statements; confirmations from third parties; valuation reports;
    agreements / loan documents / sale deeds; demand notice under Section 156;
    show-cause notices and replies; Form 26 Vakalatnama / letter of authority.)

11. ACCOMPANYING APPLICATIONS (case-type-specific)
    Common examples:
    - Application for stay of demand under Section 220(6) / 220(3) of the
      Income-tax Act 1961
    - Application for condonation of delay under Section 249(3) / 253(5) /
      260A(2A)
    - Application for additional evidence under Rule 46A of the Income-tax
      Rules 1962 (CIT(A) level) / Rule 29 of the Income-tax (Appellate
      Tribunal) Rules 1963 (ITAT level)
    - Application for immunity from penalty under Section 270AA
    - Application for early hearing
    - Application for exemption from personal appearance (faceless cases)
```

## Statute and Scheme references the plugin handles

- Income-tax Act 1961 (operative statute — most recently amended by the Finance Act of the relevant year)
- Income-tax Rules 1962 (esp Rule 45 / Rule 47 / Rule 17A / Rule 44CA / Rule 46A / Rule 11AA)
- Income-tax (Appellate Tribunal) Rules 1963 (esp Rule 5A on additional grounds; Rule 29 on additional evidence)
- Finance Act 2021 — Section 148A reassessment overhaul (operative 01-04-2021)
- Finance Act 2020 — Section 12AB charitable-trust registration overhaul + Section 270A interim refinements
- Finance Act 2016 — Section 270A introduction (operative AY 2017-18 onwards)
- Faceless Assessment Scheme 2020 (read with Section 144B Income-tax Act 1961)
- Faceless Appeal Scheme 2021 (read with Section 250(6B) — (6D))
- Faceless Penalty Scheme 2021 (read with Section 274(2A))
- e-Verification Scheme 2021 (read with Section 135A)
- e-Settlement Scheme 2021 (read with Section 245AA — post-abolition-of-Settlement-Commission regime)
- Direct Tax Vivad se Vishwas Act 2020 (where transitional revival arises)
- Bharatiya Nagarik Suraksha Sanhita 2023 (where prosecution-context cross-cites arise — Section 276B / 276C / 277 / 277A / 278 / 278A / 278B / 278C)
- Bharatiya Sakshya Adhiniyam 2023 (where evidence-context cross-cites arise — Section 63 for electronic records; Section 132 for advocate-client privilege)
- Limitation Act 1963 (Section 5 cross-reference for sufficient-cause-condonation analogy)
- CBDT Circulars and Instructions (public-domain only — esp Circular No. 19/2019 on DIN, Circular on monetary limits for Department appeals, Circular on Section 270AA immunity procedure)

## Form correspondence (canonical)

| Form | Rule | Pleading |
|---|---|---|
| FORM NO. 35 | Rule 45 of the Income-tax Rules 1962 | CIT(A) appeal |
| FORM NO. 36 | Rule 47(1) of the Income-tax Rules 1962 | ITAT appeal |
| FORM NO. 36A | Rule 47(2) of the Income-tax Rules 1962 | ITAT cross-objection |
| FORM NO. 10A | Rule 17A of the Income-tax Rules 1962 | Section 12A / 12AB registration |
| FORM NO. 10G | Rule 11AA | Section 80G renewal |
| FORM NO. 35A | Rule 44CA of the Income-tax Rules 1962 | DRP objection |
| FORM NO. 13 | Rule 28 | Section 197 lower-deduction TDS certificate |

## Assessment Year (AY) vs Financial Year (FY) convention

- **Financial Year (FY)** — the year in which income is earned. Runs 01-April to 31-March (e.g. FY 2023-24 = 01-04-2023 to 31-03-2024).
- **Assessment Year (AY)** — the year in which the income of the previous financial year is assessed. AY corresponds to FY + 1 (e.g. AY 2024-25 corresponds to FY 2023-24).
- Pleadings always identify the AY in question. The Statement of Facts narrates the FY events.

## Limitation map (statutory cross-reference)

| Pleading | Section | Limitation |
|---|---|---|
| CIT(A) Form 35 appeal | Section 249(2) | 30 days from date of service of order |
| ITAT Form 36 appeal | Section 253(3) | 60 days from date of communication of order |
| ITAT cross-objection Form 36A | Section 253(4) | 30 days from date of receipt of notice |
| High Court appeal under Section 260A | Section 260A(2) | 120 days from date of receipt of ITAT order |
| Supreme Court appeal under Section 261 | Section 261(1) | special leave / certified case (limitation per Supreme Court Rules) |
| DRP objection Form 35A | Section 144C(2) | 30 days from date of receipt of draft assessment order |
| Section 264 revision application | Section 264(3) | 1 year from date of communication of order |
| Section 154 rectification application | Section 154(7) | 4 years from end of FY in which order was passed |
| Section 270AA immunity application | Section 270AA(2) | 1 month from end of month of receipt of assessment order |

## Reassessment regime — Section 148A discipline (Finance Act 2021)

Post-Finance-Act-2021 (operative 01-04-2021), the reassessment regime under Sections 147 — 151 was overhauled. Section 148A introduced a pre-issue-of-notice procedure:

- **Section 148A(a)** — AO conducts enquiry with prior approval of specified authority
- **Section 148A(b)** — AO issues show-cause notice to assessee, supplying material relied upon and giving opportunity to be heard
- **Section 148A(c)** — assessee files reply within prescribed window (typically two weeks, extendable)
- **Section 148A(d)** — AO passes order on whether or not it is a fit case for issuance of notice under Section 148

*Union of India v. Ashish Agarwal* (Supreme Court, 4 May 2022) — pre-01-04-2021 Section 148 notices issued under the unamended Section 148 were retrospectively converted to Section 148A(b) show-cause notices, with directions on the supply of material relied upon, opportunity of hearing, and procedure to be followed thereafter.

The Drafter pleads the post-Finance-Act-2021 regime by default; the Verifier flags any Section 147 / 148 reference WITHOUT the Section 148A flag as legacy-pre-Finance-Act-2021.

## Charitable-trust registration regime — Section 12AB discipline (Finance Act 2020)

Post-Finance-Act-2020 (operative 01-04-2021), the charitable-trust registration regime under Section 12AA was replaced by Section 12AB. Every existing Section 12A / 12AA registered trust required to re-apply under Form 10A within the prescribed window (extended multiple times by CBDT).

- **Section 12AB(1)(a)(i)** — regular registration on application by an existing registered trust
- **Section 12AB(1)(b)** — re-registration on conversion of provisional registration
- **Section 12AB(1)(c)** — provisional registration for a newly formed trust

The Drafter pleads the post-Finance-Act-2020 regime by default for any new Form 10A.

## Penalty regime — Section 270A vs Section 271(1)(c) discipline

- **AYs up to and including 2016-17** — Section 271(1)(c) (concealment / inaccurate particulars) applies; Section 271AAA / 271AAB apply to search years.
- **AYs 2017-18 onwards** — Section 270A applies (under-reporting / misreporting of income); Section 270AA provides immunity election on conditions.

The Drafter selects the correct penalty section by reference to the AY in `case-config.md`.
