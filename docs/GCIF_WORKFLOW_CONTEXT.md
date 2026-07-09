# GCI Finance — Workflow & Architecture Context
**Groupe de Commerce Intercontinental Inc.**
*Created: 2026-07-08 | v0.1 (skeleton) | Maintained by: Patrick B. Pierre*

> Technical twin of `GCIFinance_Context.md`. That doc is "what is true about
> the business." This doc is "how the system is built and how to work on it
> safely." Read `GCIF_PROJECT_CHARTER.md` first for the founding rationale —
> this doc is where build decisions accumulate as they're made, the same way
> `GCI_WORKFLOW_CONTEXT.md` grew for GCI Tires.

---

## 1. How to use this document (read this first, every session)

1. **Don't assume — verify.** This doc records what was true when last
   updated. Before building on any claim ("HubSpot pipeline has 8 stages,"
   "Xero shares Tires' org"), check live state if the action depends on it
   being correct. Tires' hardest lessons were things that were documented
   as done but weren't actually deployed, or automations that failed
   silently for months uncaught (see §6).
2. **Update this doc when you make a build decision**, not at the end of a
   project. It's a running log, not a retrospective.
3. **Session start checklist:**
   - Read `GCIF_PROJECT_CHARTER.md` (why), `GCIFinance_Context.md` (what's
     true about the business right now), this doc (how it's built / build
     plan), in that order.
   - Check §2 (verified state) against what you're about to touch — if it's
     stale, verify live before proceeding, and update it.

---

## 2. Verified state snapshot

| Asset | State as of 2026-07-08 |
|---|---|
| `gci-finance-website` | EXISTS. Vercel project `prj_TKb4inReDTpvrt4A9yEcfZS0RSrB`, live at gci-finance.ca. Intake/contact form confirmed live and tested (resolves charter open question #3). |
| `gci-finance-app` | DOES NOT EXIST yet. Green-field. Named strategic priority in `GCIFinance_Context.md` §7. |
| HubSpot CRM | Portal 343105488, owner `info@gci-finance.ca`. Connected to Claude workspace (direct read/write available via HubSpot tools). 8-stage pipeline (Lead → Funded/Declined) — **setup status "in progress" not yet re-verified live; do this before Phase 1.** |
| Xero | **RESOLVED:** same org as GCI Tires (tenant `00a59a78-...`) — Groupe de Commerce Intercontinental Inc. is one legal entity behind both commercial names. `api/xero.ts` rotation-safe pattern from `gci-command-center` is directly reusable. Still unverified: whether INV-2026-001 is actually entered in that org under its own numbering. |
| Gmail (`info@gci-finance.ca`) | **RESOLVED:** manual access only, not connected to Claude workspace. Any "system drafts / Pat sends" workflow step is copy-paste today, not an API integration. |
| Business state | 1 deal closed (L-2083, $3,547.30 commission invoiced, EFT pending, PPSA audit open), 1 active file (Gauthier, ~$1.6M USD equipment, 2 tranches), 1 open file (Marco File 2), 6 lenders in network at varying onboarding stages. |
| Compliance | FINTRAC program v1.0 drafted, unsigned; F2R portal account not yet created. Law 25 privacy policy in progress. |
| Supabase | No GCI Finance project created yet. Decision (§3) is to use a **new, separate** project — not the shared Tires one. |
| Vercel team | `team_R6Xs0ja1g8YT3dbWt3u0Dv2r` (same team as all other GCI projects). |

---

## 3. Architecture decision record

**Decision: Option A — one repo (`gci-finance-app`) + leverage what exists,
rather than a six-repo mirror of the Tires architecture.**

Rationale: deal volume here is single-digit active files, document-driven and
high-value, not high-volume/low-touch like Tires. Automation target is
different — not "zero-human transactions" but "nothing falls through the
cracks, Pat only does judgment and relationships, compliance is systematic."
A six-repo split would be over-engineering at this volume (revisit only if
deal flow grows ~10x). Pure no-code (HubSpot + Zapier/Make) was rejected as
the *primary* path — the two-month silent Make.com outage on Tires showed
third-party automation still needs health-checking, and free-tier HubSpot
lacks the automation depth needed for the document-chasing workflow — but
HubSpot remains the CRM/pipeline system of record either way.

### Component map

| Component | Choice | Rationale |
|---|---|---|
| App repo | `gci-finance-app`, Next.js, Vercel (same team) | Green-field, single deployable |
| CRM / pipeline | HubSpot (existing portal, already connected) | Don't rebuild what's in progress and already wired up |
| App database | **New**, separate Supabase project | Finance files contain corporate financials + KYC identity documents; must not share a service key with tire-price scrapers. Same RLS/service-role discipline as Tires tables. |
| Document storage | Google Drive + checklist state in Supabase | Drive already holds all file docs per current workflow (`GCIFinance_Context.md` §7) |
| Accounting | Xero — same org as Tires (resolved, §2) | Reuse `api/xero.ts` verbatim if the pattern still holds after a quick read of the current file |
| Alerts | Same Telegram bot/chat as Tires | One channel Pat already watches; **remember env vars do not propagate across Vercel projects** — must be set per-project |
| Email | Gmail (`info@gci-finance.ca`) — manual today | System can prepare draft text; Pat sends. Auto-send is explicitly out of scope for relationship-sensitive messages (see Charter §8) |
| Content/marketing | Phase 4; LinkedIn + GBP only (not Instagram/FB/Pinterest) | Reuse fixed content-generation patterns (no-preamble, validatePayload) from `gci-brain` |

---

## 4. Build phases

### Phase 0 — Discovery + plumbing audit (do this before writing app code)
- [x] Audit `gci-finance-website` intake form — **DONE, confirmed live 2026-07-08.** Next: confirm where submissions actually land (email? HubSpot? nowhere yet?) and that Pat sees them.
- [ ] Audit actual HubSpot state: pipeline stages, existing contacts/deals, what's real vs. "in progress."
- [ ] Enter the 3 existing files (L-2083, Gauthier, Marco File 2) into HubSpot as real deals with real stages — system must start from true state, not a clean slate.
- [x] Xero question — **RESOLVED** (§2): same org as Tires.
- [x] Gmail question — **RESOLVED** (§2): manual access only.
- [ ] Confirm INV-2026-001's actual status in the shared Xero org (entered under its own numbering, or only ever a manual PDF).

### Phase 1 — Skeleton + observability FIRST
*(Tires lesson: observability came last there and cost 2 months of silent failure — do it first here.)*
- [ ] Create `gci-finance-app` repo + Vercel project + new Supabase project.
- [x] This doc committed from day one.
- [ ] Telegram alerting wired and verified with a real received message (not just "code looks right").
- [ ] Daily health-check cron pattern established — port `gci-order-hub/api/health-check-make.ts`. Every future cross-system dependency gets a health check at the moment it's added, not after it breaks.

### Phase 2 — Core: the Deal File engine (the revenue cycle)
1. **Intake** — web form → HubSpot deal + Supabase file record + Telegram alert. Server-side, post-validation — no client-side-only side effects (Tires checkout lesson).
2. **Document checklist per file** — templated by deal type (KYC set, FINTRAC checklist, lender-specific requirements). Tracks who owes what (client/lender/Pat), with age.
3. **Automated chasing** — biggest visible time-sink today (Marco's DL/GST numbers, Desjardins letter, Brendan's portal credentials are ALL "waiting on someone"). Draft follow-up emails on a cadence; escalate to Telegram when items go stale past N days.
4. **Commission ledger** — invoice tracking, 6-month clawback reserve schedule (per Equilease agreement), HST remittance amounts owed per filing period. Alert on clawback window expiry and HST remittance due dates.
5. **Deadline/aging dashboard** — one page: every file, its stage, its oldest outstanding item, its next action and owner.

### Phase 3 — Lender + compliance layer
1. Lender directory with rules engine (e.g., "Grenke: no refinancing," "BDC: doesn't pay brokers," "never disclose lender names to clients") — encoded so submissions can't violate them.
2. FINTRAC new-client checklist enforced as a gate before any file can move to "Submitted" stage.
3. Annual compliance review reminder (FINTRAC program review: May 2027).

### Phase 4 — Marketing engine
1. LinkedIn + GBP content pipeline (bilingual; GBP rule: no phones/URLs in body) — reuse fixed generation patterns with validatePayload-style guards and publish-side verification from day one.
2. Vendor partner tracking (Rounda et al.) — partner reference cards, not blank credit apps.

### Phase 5 — Reporting
Xero integration (rotation-safe pattern), P&L per file, pipeline value reporting, commission receivables aging.

---

## 5. Reference documents (from the Tires system — read before building)

| Document | Where | Why |
|---|---|---|
| `GCI_WORKFLOW_CONTEXT.md` | any of the 6 Tires repos | Architecture conventions, the Make.com blind-spot lesson, the documented≠deployed lesson |
| `api/xero.ts` | `gci-command-center` | Rotation-safe Xero integration — copy verbatim, same org |
| `api/health-check-make.ts` | `gci-order-hub` | Health-check-per-dependency pattern |
| `api/social-scheduler.ts`, `api/blog-publisher.ts` | `gci-brain` (post-#131/#132) | Fixed content-generation patterns |
| `api/submit-installer-application.ts` | `gci-brain` | Form→CRM write pattern incl. typecast lesson |
| `api/installer-outreach.ts` | `gci-brain` (post-#134) | Drip sequence + skip-visibility alerting — reusable for document chasing |
| `docs/SESSION-CONTEXT.md` | `gci-walmart-sync` | Best-in-family "prime a new session" doc format |

---

## 6. Verification methodology (inherited lessons — non-negotiable)

- **Documented ≠ deployed.** A doc saying a feature exists doesn't mean it's live. Verify via a real trigger + a source-of-truth query, not by reading code.
- **A success log only proves the hop you can see.** Silent failure further downstream (e.g. the two-month Make.com outage) is invisible unless something specifically checks the end state.
- **No client-side-only side effects.** Anything that matters (form submission, payment, deal creation) must have server-side confirmation.
- **Add a health check the moment a new cross-system dependency is introduced** — not after it breaks.
- **Sensitive-action confirmation.** For GCI Finance specifically, the sensitive action is client/lender email (relationship + money movement), analogous to social posts being the sensitive action for Tires. A live example: the L-2083 TD-account-confirmation thread was flagged as a potential business-email-compromise pattern (payment redirection, urgency, cross-domain confirmation) before being manually verified as legitimate. **Standing rule:** any email thread involving a bank/account change on a GCI Finance file gets verbal (not reply-to-thread) confirmation from both parties before anyone acts on it, no matter how routine it looks.

---

## 7. Open items / not yet built

These are named in `GCIF_PROJECT_CHARTER.md` §6 as future companion docs.
Explicitly deferred for now — do not assume they exist:

- `GCIF_INTEGRATIONS_INVENTORY.md` — every external system, auth pattern, credential location. Build this as Phase 1 integrations get added, rather than reconstructing it later (reconstructing this for Tires required real archaeology).
- `GCIF_COMPLIANCE_CALENDAR.md` — FINTRAC review cycle, HST remittance dates, clawback reserve release dates, licence/registration renewals.
- `VERIFICATION_PLAYBOOK.md` — §6 above, codified into a repeatable checklist once there's more than one integration to check.

---

## 8. Explicitly out of scope (for now)

- Building a custom CRM (HubSpot is the CRM)
- Any consumer-facing lending features (B2B only — also what keeps AMF licensing not-required; do not change without legal review)
- Auto-sending relationship-sensitive email (system drafts; Pat sends)
- Multi-tenant/commercial productization (GCI-internal only, unlike `gci-walmart-sync`)

---

## 9. Changelog

- **v0.1 (2026-07-08):** Initial skeleton, built from `GCIF_PROJECT_CHARTER.md`
  §§3–8. Charter's three open questions (Xero, Gmail, website intake form)
  resolved and reflected in §2. Committed alongside `GCIFinance_Context.md`
  v1.1 as the two-document anchor point for all future GCI Finance sessions.
