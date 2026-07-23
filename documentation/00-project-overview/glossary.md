# Glossary — CBS SaaS Platform for Cooperative Banks

## Purpose

Defines project-wide terms used across vision, business goals, architecture, and UI specifications. AI agents and developers must use these definitions consistently. Module-specific business rules (e.g., minimum balance, interest calculation formulas) belong in `02-business-domains/*/business-rules.md`, not here.

## Scope

Covers platform, commercial, accounting, membership, and product terms referenced in existing documentation. Does **not** define field-level validation rules or dropdown master-data lists — those are captured per screen in `05-ui-ux/` and will move to domain business rules as modules are documented.

## How to Use This Document

- Terms are grouped by category, then listed alphabetically within each category.
- Where the UI or architecture docs name a concept but the **business distinction** is not yet confirmed, the entry is marked `TODO:` — do not infer rules from these entries until resolved.
- Marathi labels match those used in `05-ui-ux/` screen specs.

---

## Platform & Commercial Terms

### AMC (Annual Maintenance Contract)

Recurring annual fee charged to a tenant bank, separate from the per-branch subscription. One of three revenue components defined in BG-007 (alongside per-branch subscription and on-demand custom functionality). Specific amount/percentage is not yet defined — see BG-003 open item.

**See also:** [business-goals.md](business-goals.md) BG-003, BG-007.

### Branch (शाखा)

An operating unit of a cooperative bank tenant. Branch is a master entity used across customer, account, and transaction screens (branch number, branch name, branch-scoped lookups). Users may be assigned branch-level access via roles.

**UI reference:** Autocomplete lookup per [entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md).

### Control Catalog

A small internal database (not tenant financial data) that maps `tenant_id` to the tenant's PostgreSQL database name and connection credentials. Queried by the API connection router on first use per tenant per API node, then cached.

**See also:** [architecture-overview.md](../01-architecture/architecture-overview.md) Section 3.

### Organization (संस्था / संघटना)

The cooperative society (bank) entity within a tenant. Displayed as read-only context on membership and GL screens (e.g., society name on New Membership Tab 1). In a single-tenant Year 1 deployment, one organization per tenant is expected; multi-organization per tenant is not documented.

**TODO:** Confirm whether a tenant bank can operate multiple registered societies under one CBS instance.

### Tenant

One cooperative bank customer of the CBS SaaS platform. Each tenant receives a dedicated PostgreSQL database on the shared RDS instance (DEC-001). The JWT issued at login carries a `tenant_id` claim used to route API requests to the correct database.

**Year 1 target:** exactly one tenant (BG-001). **Year 2–3 target:** 5–10 tenants, Maharashtra only (BG-002).

**See also:** [architecture-overview.md](../01-architecture/architecture-overview.md) DEC-001.

---

## People & Membership Terms

### Customer (ग्राहक)

A person or non-individual entity registered in the CBS with a **customer number** (ग्राहक क्र.). Customer registration (New Customer screen) captures KYC, address, and contact details. A customer is **not** automatically a cooperative society member — membership is a separate workflow (New Membership).

**Customer types** (from New Customer screen): Individual (वैयक्तिक), Proprietorship Firm (मालमत्ता फर्म), Self Help Group (एसजी), Other Institution (दुसरी संस्था).

### Member (सभासद)

A customer who holds **membership** (सभासदत्व) in the cooperative society — i.e., a share-capital member with a member number (सभासद क्रमांक), share limit, resolution details, and dividend eligibility. Created via the New Membership screen. Member type radio default: `सभासद` (Member).

**Distinction from Customer:** Customer = identity/KYC record. Member = cooperative ownership stake with share account.

### Nominal Member (नाममात्र सभासद)

A membership category equivalent to **Class B Member (ब वर्ग)**. Selectable alongside full Member on New Membership, Membership Transaction, Share Rules, and Dividend Calculation screens. Shares Transfer screens use the Class B radio option for the same class.

**Confirmed distinction from full Member (सभासद / Class A):** Nominal Member and Class B represent the same membership class. Full Member is the default Class A membership. Detailed rights rules (voting, share limits, dividend treatment, fees) will be documented in `02-business-domains/membership/business-rules.md` — not invented here.

**See also:** Class B Member below.

### Class B Member (ब वर्ग)

Same membership class as **Nominal Member (नाममात्र सभासद)**. Referenced on Shares Transfer screens (radio: Class B) and as a charge type (`ब वर्ग सभासद फी` / Class B Member Fee) on all New Scheme screens.

**TODO:** Share limits, dividend rights, and transfer rules for Class B vs Class A will be documented in `02-business-domains/membership/business-rules.md`.

### Account Holder (खातेधारक)

The party linked to an operational account (savings, FD, loan, etc.). Selected via Autocomplete on transaction and account screens. May be the primary customer, joint holder, or nominee depending on account setup.

### Introducer (परिचयकर्ता / सूचक)

A referring member recorded on New Membership Tab 2 (customer number + member name).

### Nominee (वारसदार)

Beneficiary recorded on membership and deposit account screens (nominee tab pattern shared across FD, Daily, Recurring, Savings).

### Joint Holder (संयुक्त खातेदार)

Secondary party on an account or membership, recorded on New Membership Tab 2 and deposit account nominee/joint tabs.

---

## Accounting & GL Terms

### GL Group (जी.एल. ग्रुप)

A grouping level in the chart of accounts hierarchy, above GL Heads. Created via Settings > Accounting > [GL Account Setup](../05-ui-ux/settings/accounting/gl-account-setup-screen.md) (Tab 1).

**Business rules:** [02-business-domains/settings/accounting/](../02-business-domains/settings/accounting/overview.md).

### GL Head (जी. एल. हेड / जीएल हेड)

A General Ledger account head — the atomic unit in the chart of accounts. Each GL Head has a number (जी. एल. हेड क्र.), name, account group, balance type (credit/debit), and category (general, branch, member-like, contra). Product **schemes** are linked to a GL Head number at creation time.

**UI reference:** [gl-account-setup-screen.md](../05-ui-ux/settings/accounting/gl-account-setup-screen.md) (Tab 2).

**Business rules:** [02-business-domains/settings/accounting/](../02-business-domains/settings/accounting/overview.md).

### Jama (जमा)

Credit entry — increases liability/income or decreases asset/expense depending on account nature. Used as the transaction direction on Jama (Receipt), Transfer, Multi-GL, and product transaction screens.

**English UI label:** Credit / Receipt.

### Nave (नावे)

Debit entry — opposite of Jama. Used on Nave (Payment), Transfer, Multi-GL, and product transaction screens.

**English UI label:** Debit / Payment.

### Transfer (ट्रान्सफर)

An accounting transaction that debits one GL/account and credits another in a single voucher (Settings > Accounting > Transfer screen).

### Rokhapal (रोखपाल)

Cashier transaction screen with cash denomination tracking. Handles cash receipt/payment at the teller counter with voucher and scroll references.

**English UI label:** Cashier.

### Multi-GL Transaction (एकाधिक जीएल व्यवहार)

A single voucher posting debits and credits across multiple GL heads/accounts with a balancing check (total debit = total credit).

### Note Exchange (नोटांची अदलाबदल)

Cash denomination exchange transaction (no net cash in/out of the bank — e.g., exchanging note denominations).

### Member-like Account (सभासदाप्रमाणे खाते)

A GL Head category flag indicating the account behaves like a member-level sub-ledger (per-member balances under one GL Head). Selected on GL Account Setup Advanced Settings.

### Contra (कॉन्ट्रा)

A GL Head flag for contra accounts (offsetting/balance-sheet offset entries).

---

## Product & Scheme Terms

### Scheme (योजना)

A **product configuration template** defined under Settings for a deposit or loan product type. A scheme captures interest rules, duration slabs, charges, GL Head linkage, and product-specific parameters. Accounts are opened **under** a scheme (e.g., "Select Scheme" on New Savings Account, New Loan).

**Scheme types** (Settings > Schemes):

| Marathi | English | Settings Screen |
| :--- | :--- | :--- |
| डेली | Daily (Pigmy) | [new-scheme-screen.md](../05-ui-ux/settings/schemes/new-scheme-screen.md) (Scheme Type = डेली) |
| बचत | Savings | [new-scheme-screen.md](../05-ui-ux/settings/schemes/new-scheme-screen.md) (Scheme Type = बचत) |
| मुदत ठेव | Fixed Deposit | [new-scheme-screen.md](../05-ui-ux/settings/schemes/new-scheme-screen.md) (Scheme Type = मुदत ठेव) |
| रिकरिंग | Recurring | [new-scheme-screen.md](../05-ui-ux/settings/schemes/new-scheme-screen.md) (Scheme Type = रिकरिंग) |
| कर्ज | Loan | [new-scheme-screen.md](../05-ui-ux/settings/schemes/new-scheme-screen.md) (Scheme Type = कर्ज) |

**Business rules:** [02-business-domains/settings/schemes/](../02-business-domains/settings/schemes/overview.md).

**Note:** GL Head number validation differs by product (e.g., Daily schemes require GL Head No. ≤ 99 per screen spec validation message).

### Account (खाते)

An operational financial record opened for a customer under a scheme — savings account, FD account, loan account, etc. Distinct from GL Head (chart of accounts) and from Customer/Member identity records.

### Savings (बचत)

Standard savings deposit product module.

### Fixed Deposit / FD (मुदत ठेव)

Term deposit with fixed duration and interest rules.

### Daily / Pigmy (डेली / पिग्मी)

Daily collection deposit product. **Agent** (एजंट) collects small daily installments from account holders; agent collection and agent-to-agent transfer screens exist in the Daily module.

**Note:** "Pigmy" and "Daily" are used interchangeably in UI specs and charge labels (e.g., `पिग्मी कमिशन` / Pigmy Commission).

### Recurring (रिकरिंग)

Recurring installment deposit product (periodic credit transactions).

### Loan (कर्ज)

General loan product — unsecured/secured loans per scheme configuration.

### Deposit Loan (ठेव कर्ज)

Loan issued **against** a fixed deposit (lien on FD as collateral). Separate screens: New Deposit Loan, Deposit Loan Installment Payment. Loan scheme config includes `कायम ठेव कर्ज` (Fixed Deposit Loan) as a scheme sub-type.

### Drawing Power / DP (उचल मर्यादा / डी.पी.)

The maximum amount that can be drawn/availed against collateral (typically deposit-backed loans). Loan scheme configuration includes **Drawing Power (D.P.) Reduction Rate** (उचल मर्यादा कमी करण्याचे प्रमाण) — a parameter that reduces available DP over time or under defined conditions.

**TODO:** Exact DP calculation formula and reduction schedule are not yet documented in business rules. Referenced on [loan-new-scheme-screen.md](../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) only.

### Interest Multiplier (व्याज गुणक)

A configuration/calculation screen for adjusting interest calculation multipliers (exists in Daily, FD, and Recurring modules).

### Dividend (लाभांश)

Profit distribution to members based on shareholding. Screens: Dividend Transaction, Dividend Calculation (Settings), Share Rules (Settings).

### Shares (शेअर्स)

Cooperative share capital units held by members. Shares Transfer and Shares Transfer List screens handle transfer between members.

### Agent (एजंट)

A field collection agent for the Daily/Pigmy product. Has agent code, branch, and linked GL accounts (New Agent screen).

---

## Transaction & Operations Terms

### Voucher (व्हाउचर)

An accounting document number attached to a financial transaction (visible on Rokhapal, Multi-GL, and transaction screens).

### Scroll (स्क्रोल)

A batch/counter reference used on cashier (Rokhapal) transactions.

**TODO:** Exact scroll lifecycle (open, close, reconcile) not yet documented.

### Transaction Mode (व्यवहार मोड)

Payment channel/method selector on Multi-GL and transaction screens. **v1 supported modes:** Cash and Cheque (receipt/issue recording only — no live cheque clearing or payment-rail integration).

### Charges (चार्जेस)

Fees applied on account/loan operations, configured per scheme. Shared charge types across all New Scheme screens include: Borrower Welfare Fund, Pigmy Commission, Processing Fee, Class B Member Fee, Stationery Fee.

---

## User & Access Terms

### User (युजर)

A CBS login identity (New User screen) — distinct from Employee (कर्मचारी) master record. Users are assigned roles.

### Role (युजर रोल)

Permission profile defining access per screen/form: **All Rights**, **View Only**, or **No Rights** (User Role screen).

### Employee (कर्मचारी)

Bank staff master record (New Employee screen). May be linked to a User account.

---

## Compliance & KYC Terms

### KYC (Know Your Customer)

Customer identity verification. New Customer Tab 3 captures KYC documents; transaction screens include KYC Information tabs for certain operations.

### PAN / Aadhaar

Indian identity documents captured on customer and transaction screens. **e-Verification (ई-पडताळणी) buttons are out of scope for v1** — removed from UI until a later phase; manual entry and document upload only.

---

## Open Glossary Items (require business confirmation)

| Term | Question |
| :--- | :--- |
| Class A vs Class B | Share limits, dividend rights, transfer rules (membership domain) |
| Drawing Power | Calculation formula and reduction rate semantics |
| Organization (multi) | One or many societies per tenant? |
| Scroll | Operational lifecycle definition |

---

## Related Documents

- [vision.md](vision.md)
- [business-goals.md](business-goals.md)
- [system-boundaries.md](system-boundaries.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../AI_INDEX.md](../AI_INDEX.md)
