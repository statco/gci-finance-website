# GCI Finance — Business Context
**Groupe de Commerce Intercontinental Inc.**
*Last updated: 2026-07-08 | v1.1 | Maintained by: Patrick B. Pierre*

> This is the business/state-of-the-world doc — who, what, which files, which
> lenders, what's owed. For architecture and build plan, see
> `GCIF_WORKFLOW_CONTEXT.md`. For the founding rationale, see
> `GCIF_PROJECT_CHARTER.md`.

---

## 1. Company Identity

| Field | Details |
|---|---|
| Legal name | Groupe de Commerce Intercontinental Inc. |
| Operating name | GCI Finance |
| NEQ | 1178796265 |
| BN9 | 706255346 |
| GST/HST | 706255346 RT 0001 |
| Corp tax | 706255346 RC 0001 |
| QC corp tax | 1230704330-TQ0001 |
| Address | 1014 Chemin des Conifères, Rouyn-Noranda, QC J0Z 3J0 |
| Phone | (438) 402-6616 |
| Email | info@gci-finance.ca — **accessed manually** (not connected to Claude workspace as of 2026-07-08) |
| Website | gci-finance.ca — live, repo `gci-finance-website` (Vercel project `prj_TKb4inReDTpvrt4A9yEcfZS0RSrB`) |
| President | Patrick B. Pierre |

**Same legal entity as GCI Tires.** Groupe de Commerce Intercontinental Inc.
operates both GCI Finance and GCI Tires as commercial names under one
corporation. This matters for accounting (see §4) and for any shared
compliance/legal exposure.

**REQ Commercial Names:**
- GCI Finance — En vigueur 2026-05-14
- Pneus GCI Canada / GCI Tires Canada — En vigueur 2026-05-12
- GCI — En vigueur 2025-09-29

---

## 2. Lender Network

| Lender | Contact | Email | Phone | Notes |
|---|---|---|---|---|
| **Equilease Corp.** | Brendan J. Smyth | Bsmyth@equilease.com | 416.270.0158 | Agency Agreement signed May 20, 2026. 60/40 split. 6-month clawback. Portal credentials pending. |
| **TD Equipment Finance** | Charles-Eric Bryson | Charles-Eric.Bryson@td.com | 514-842-7008 | Active relationship — not yet used on a file |
| **Roynat Capital** | TBD | — | — | Identified for Gauthier Phase 2 |
| **Affiliated Financial Services** | Katy Copin | — | — | Operations Manager, National Bank-affiliated. Sub-broker questionnaire submitted. |
| **GC Crédit-Bail / Grenke** | Guyane Hébert Potter | — | — | Onboarding in progress. Does NOT handle refinancing. |
| **BDC** | — | — | — | Direct lender only — does not pay brokers. |

**Key rules:**
- Never disclose lender names to clients
- Never reveal which lenders passed on a file
- Always submit complete, professional packages — not raw lead forwarding

---

## 3. Active Files

### FILE L-2083 — Bois Ellen Lumber / 12420015 Canada Inc.

**Status:** CLOSED — PPSA audit in progress (commission pending)

| Field | Details |
|---|---|
| Client | 12420015 Canada Inc. f.a.s.r.s. Bois Ellen Lumber |
| Contact | Marco Barone — mbarone@boisellen.ca |
| Equipment | 2023 Load Lifter 12,000 lbs, Model 2415-12G, S/N 5193 |
| Structure | 59-month lease-to-own, 10% down, $500 buyout |
| Lender | Equilease Corp. / Vault Credit Corporation |
| Balance refinanced | ~$104,471.98 CAD (Desjardins) |
| Commission | $3,139.20 + HST $408.10 = **$3,547.30 CAD** |
| Invoice | INV-2026-001 — sent to Brendan Smyth |
| Void cheque | Sent for EFT payment |

**PPSA Audit — Outstanding Items (Vault Credit Corp.):**

| # | Item | Responsible | Status |
|---|---|---|---|
| 1 | Desjardins Capital Dette Privée waiver | Chantal Robineau + Dominic (Prêts spéciaux) | 🟡 Alternative proposed: Desjardins letterhead letter confirming lien release upon payout. Email sent to Chantal + Dominic. |
| 2 | Caisse Pop. Desjardins Canadienne Italienne waiver | Brendan to issue waiver form | 🔴 Third waiver flagged to Brendan — awaiting |
| 3 | TD Bank waiver | Marco Barone → TD branch contact | 🟡 Sent to Marco |
| 4 | Marco Barone driver's licence | Marco Barone | 🔴 Requested |
| 5 | 12420015 GST/QST numbers | Marco Barone | 🔴 Requested |

**Key contacts — Desjardins:**
- Chantal Robineau, Analyste — chantal.robineau@desjardins.com — 450 773-1842 x7051303
- Dominic (last name TBD), Prêts spéciaux, Entreprises, Gestion des risques — Saint-Hyacinthe — in CC on email thread

**Ownership structure (12420015 Canada Inc.):**
- Vigesco Holdings Inc. (50%) → Andrea Barone 25% + Marco Barone 25%
- Magisco Investments Inc. (50%) → Lisa Krystyna Fusco 33% + Nicolino Fusco 34% + Vivian Magini 33%

**Security note (2026-07-08):** An email in this file's thread (TD credit line
confirmation to Lisa Fusco) was flagged and manually verified as legitimate
GCI Finance client work, not business email compromise. See
`GCIF_WORKFLOW_CONTEXT.md` §6 for the verification protocol this triggered —
any future payment-redirection-shaped email on a GCI Finance thread should be
verbally confirmed with both parties before acting, regardless of how routine
it looks.

---

### FILE GAUTHIER — Produits Non Ferreux Gauthier Inc.

**Status:** Active — lender review in progress (Equilease)

| Field | Details |
|---|---|
| Client | Gauthier Non Ferrous Products Inc. / Produits Non Ferreux Gauthier Inc. |
| Contact | Marco Barone — mbarone@pnfg.com |
| Also CC | Dan Leavitt (514-642-4090) |
| Lender | Equilease / Brendan Smyth (verbally hesitant) |
| Excluded lenders | RBC, Desjardins |

**Tranche 1 — Yomato Die-Casting Machines (China)**

| Field | Details |
|---|---|
| Supplier | Guangxi Yomato Industry & Trade Co., Ltd. |
| PI No. | YMT25-03-12S — dated March 3, 2026 |
| Equipment | 3× DM300 + 5× DM500 lead alloy die-casting machines + auxiliary equipment |
| Total value | **$1,428,558 USD** FOB Guangzhou |
| Paid to date | ~$623,338 USD |
| Balance owing | ~$805,220 USD |
| Status | Machines ready in China. Marco willing to pay 100% import to Canada then finance on Canadian soil. |
| Finance approach | Working capital scenario still open; equipment financing upon Canadian delivery is simpler path |

**Tranche 2 — Fanuc Robots (USA)**

| Field | Details |
|---|---|
| Supplier | iGAM Solutions, 6501 Nevada Ave, Detroit MI 48234 |
| Invoice | INV004667 — dated January 6, 2026 |
| Equipment | 7× Fanuc R-2000/iB/210F + 12× Fanuc LR Mate 200iD (refurbished, 6-month warranty) |
| Total value | **$200,000 USD** |
| Paid to date | $43,645 USD |
| Balance owing | **$156,355 USD** |
| Status | In US, deliverable upon payment of balance |
| Blocker | Invoice reads "Test Gauthier Non Ferrous Products" — corrected invoice needed before lender submission |

**Gauthier Financial Summary:**

| Year | Revenue | Net Income | Notes |
|---|---|---|---|
| FY2023 (Jan 31) | $14,539,835 | $608,310 | Reviewed by Provencher & associé |
| FY2024 (Jan 31) | $11,292,792 | $705,847 | Revenue declined 22% |
| 2025 Actual/Fcst | $12,774,873 | $171,278 | Weak — includes $973K in govt grants |
| 2026 Forecast | ~$17,814,090 | n/a | Contingent on Yomato machines operational |

**Outstanding lender requirements:**
1. Financial statements — Vigesco Holdings Inc.
2. Financial statements — Magisco Investments Inc.
3. Personal net worth statement — Vivian Magini
4. Clarification on Remo Barone's role (referenced by lender, not in organigramme)
5. Corrected iGAM invoice (legal name: Gauthier Non Ferrous Products Inc.)
6. Clarification on $4,634,205 Trojan Battery figure — it is one customer's revenue subset, not total sales
7. Brief narrative on basis for 2026 revenue forecast

**Note:** Bois Ellen financials submitted intentionally as supporting entity
(family-related). Not offered as guarantors — for review purposes only. Marco
does not want cross-guarantee between Gauthier and Bois Ellen.

---

### MARCO BARONE FILE 2 — Direct Equipment Purchase

**Status:** Open — lender TBD. Details pending from Marco.

---

## 4. Accounting & Compliance

### Xero (RESOLVED 2026-07-08)
GCI Finance's books live in the **same Xero organization as GCI Tires**
(tenant `00a59a78-...`), since both are commercial names of the same legal
entity, Groupe de Commerce Intercontinental Inc. This means:
- The existing rotation-safe `api/xero.ts` pattern (from `gci-command-center`)
  is directly reusable — no second org/connection needed.
- INV-2026-001 (Bois Ellen commission, $3,547.30) needs to be confirmed as
  actually entered in that Xero org under GCI Finance's own numbering, or
  reconciled if it was only ever a manually-issued PDF. **Still open:** verify
  this specific invoice's Xero status (not whether Xero is the right org —
  that part is resolved).

### FINTRAC AML/ATF Compliance Program
- Version 1.0 — drafted May 2026
- 13 sections, moderate risk rating
- Compliance Officer: Patrick B. Pierre
- **Action needed:** Print, sign Section 13, and create F2R portal account at fintrac-canafe.gc.ca
- Review cycle: Annual (next review: May 2027)

### Quebec Legal Standing
- AMF licence: **Not required** for commercial equipment finance brokerage (B2B only)
- Consumer protection (LPC): **Not applicable** (B2B transactions only)
- Language (Law 101): **Compliant** — bilingual operations
- Privacy (Law 25 / PIPEDA): Privacy policy and data governance required — in progress
- GST/HST: Registered (706255346 RT 0001) — remit HST on all commissions

---

## 5. Commission Tracking

| Invoice | File | Amount | HST | Total | Status |
|---|---|---|---|---|---|
| INV-2026-001 | L-2083 Bois Ellen | $3,139.20 | $408.10 | $3,547.30 | Sent — EFT pending; Xero entry to be confirmed (see §4) |

**Clawback reserve:** Keep 6-month reserve on all commissions per Equilease Agency Agreement.
**HST remittance:** $408.10 from INV-2026-001 must be remitted to CRA on next GST/HST return.

---

## 6. Marketing & Brand Assets

### Digital Presence
| Platform | Name / URL | Status |
|---|---|---|
| Website | gci-finance.ca | **Live — intake/application form confirmed live and tested (2026-07-08)** |
| Google Business Profile | GCI-Finance Canada | Verified ✅ — profile optimized |
| LinkedIn Showcase Page | gci-finance-canada | Content drafted — needs publishing |
| LinkedIn Company Page | groupe-de-commerce-intercontinental-inc | Updated May 2026 |

**GBP posting rules:** No phone numbers or URLs in post body (Google policy). Bilingual posts only.

### Marketing Materials Completed
- Tri-fold brochure (EN/FR, print-ready PDF)
- Business card (front/back, standard 3.5×2")
- 8 LinkedIn personal posts (Patrick B. Pierre profile) — 30-day calendar
- 4 GBP posts — Month 1
- Square logo for GBP profile (720×720px)
- Transparent e-signature PNG (Signature_PBP_transparent.png + doc_size version)

### Vendor Partners
| Partner | Contact | Status | Next step |
|---|---|---|---|
| Location Équipement Rounda | TBD | Verbal agreement — brochure delivered in person | Thank-you email + staff meeting request |

**Note:** Do NOT send blank credit application to vendor partners. Create Vendor Partner Reference Card instead.

---

## 7. Operations & Tools

### Standard Workflow — New File
1. **Intake:** Client inquiry → collect KYC documents (ID, financials, equipment details). Website form is live/tested as of 2026-07-08 — confirm it currently lands somewhere Pat monitors (see `GCIF_WORKFLOW_CONTEXT.md` §5, Phase 0).
2. **FINTRAC compliance check:** Complete new client checklist before any lender submission.
3. **File preparation:** Structure deal, select lender, prepare submission package.
4. **Submission:** Use lender's standard format (Equilease: use portal).
5. **Follow-up:** Track approval, manage document collection, close.
6. **Commission:** Invoice lender upon funding confirmation. Keep 6-month clawback reserve.
7. **Record-keeping:** Save all documents to Google Drive. Update HubSpot CRM.

### Document Signing
- Tool: PDF-XChange
- Signature: Signature_PBP_doc_size.png — insert via Edit → Add Image
- Place on signature line, resize, flatten, save

### Email
`info@gci-finance.ca` is accessed **manually** — not connected to the Claude
workspace as of 2026-07-08. Any workflow step that says "system drafts,
Pat sends" currently means: content prepared here, Pat copies/pastes/sends
manually. This is a candidate for a future Gmail connector addition, but is
explicitly not assumed to exist yet.

### Claude Code Workflow
- All repository file edits: Claude Code (separate instance)
- Send explicit instruction prompts with file paths, line-level changes, commit messages
- Paste commit hashes and change summaries back here for review

### Planned Technology
- **HubSpot CRM:** Free plan — setup in progress. 8-stage pipeline: Lead → Funded/Declined. Portal 343105488, owner `info@gci-finance.ca`.
- **GCI Finance App:** Next.js/Vercel (repo: `gci-finance-app`) — AI-powered intake, lender matching, doc tracking, commission tracking. Strategic priority — **not yet built** as of 2026-07-08 (see `GCIF_WORKFLOW_CONTEXT.md` for build plan).

---

## 8. Key Contacts Master List

| Name | Role | Email | Phone |
|---|---|---|---|
| Patrick B. Pierre | President, GCI Finance | info@gci-finance.ca | (438) 402-6616 |
| Brendan J. Smyth | President, Equilease Corp. | Bsmyth@equilease.com | 416.270.0158 |
| Marco Barone | Contact — Bois Ellen + Gauthier | mbarone@boisellen.ca / mbarone@pnfg.com | — |
| Dan Leavitt | Contact — Gauthier file | — | 514-642-4090 |
| Chantal Robineau | Analyste, Desjardins Prêts spéciaux | chantal.robineau@desjardins.com | 450 773-1842 x7051303 |
| Dominic (last name TBD) | Prêts spéciaux, Desjardins Saint-Hyacinthe | TBD — in email CC | — |
| Charles-Eric Bryson | TD Equipment Finance | Charles-Eric.Bryson@td.com | 514-842-7008 |
| Katy Copin | Affiliated Financial Services | — | — |
| Guyane Hébert Potter | GC Crédit-Bail / Grenke | — | — |
| Amanda Muise | Canada Tire (Net 30 credit) | amuise@cdatire.com | — |

---

## 9. Immediate Priority Actions

| Priority | Action | Owner | Deadline |
|---|---|---|---|
| 🔴 1 | Desjardins letterhead letter — follow up with Dominic | Patrick | This week |
| 🔴 2 | FINTRAC: Print, sign, create F2R portal account | Patrick | This week |
| 🔴 3 | Gauthier: Receive Vigesco + Magisco financials from Marco | Marco | ASAP |
| 🔴 4 | Equilease portal credentials from Brendan | Patrick → Brendan | ASAP |
| 🟡 5 | Marco: DL + GST/QST + TD waiver | Marco | ASAP |
| 🟡 6 | Gauthier: Corrected iGAM invoice | Marco → iGAM | ASAP |
| 🟢 7 | Confirm INV-2026-001 is entered in the shared Xero org (see §4) | Patrick | This month |
| 🟢 8 | Location Équipement Rounda: thank-you email + staff meeting | Patrick | This week |
| 🟢 9 | LinkedIn + GBP: publish remaining content | Patrick | Rolling |
| 🟢 10 | HubSpot CRM: complete setup, input all active files | Patrick | This month |
| ✅ | REQ: Confirm GCI Finance commercial name visible on public register | Patrick | Done |
| ✅ | Website intake form: live + tested | Patrick | Done 2026-07-08 |

---

## 10. Changelog

- **v1.1 (2026-07-08):** Resolved 3 open questions from `GCIF_PROJECT_CHARTER.md`
  §7 (Xero = shared org with Tires; Gmail = manual access only; website
  intake form = live and tested). Added security note to L-2083 re: the
  payment-redirection verification that occurred on this file's email thread.
  Added `GCIF_WORKFLOW_CONTEXT.md` as companion doc.
- **v1.0 (2026-06):** Initial version.
