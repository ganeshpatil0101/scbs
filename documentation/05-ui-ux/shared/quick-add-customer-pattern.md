# Quick Add Customer Pattern — Inline Popup from Customer Autocomplete

## Purpose

Define the standard **"+ नवीन ग्राहक जोडा" (Add New Customer)** button that appears beside a **Customer Autocomplete** field when the user cannot find the person in the customer list. Used on deposit account-opening Nominee tabs (Savings, FD, Daily, Recurring) and reusable on any screen that needs to create a customer without leaving the current workflow.

## Scope

Applies when:

1. A screen has a **Customer Autocomplete** lookup (`entityType: customer`).
2. The user may need to register a new person who is not yet in the customer master.
3. Full [New Customer](../customer/new-customer-screen.md) wizard (Address, KYC) is **not** required at this moment — only minimal identity fields.

**Out of scope for this pattern:** Primary account-holder lookup on Tab 1, Joint Holder lookup on Tab 3 (this pass wires the button to Nominee search only).

## UI Layout

| Element | Marathi | English | Notes |
| :--- | :--- | :--- | :--- |
| Autocomplete | ग्राहक निवडा | Select Customer | Same as [entity-autocomplete-pattern.md](entity-autocomplete-pattern.md) |
| Button | + नवीन ग्राहक जोडा | + Add New Customer | Placed **immediately to the right** of the Autocomplete input (same row on desktop; stacked on mobile) |

### Popup / Modal

Opens on button click. Modal title: **नवीन ग्राहक (New Customer)**.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री. / सौ. | Salutation | Dropdown | No | Same as [New Customer salutation](../customer/new-customer-screen.md): `श्री.`, `सौ.`, `श्रीमती`, `कुमारी.`, `चि.`, `मेसर्स`, blank. Default: `श्री.` |
| 2 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | Same row as Salutation (#1) on desktop |
| 3 | जन्म दिनांक | Date of Birth | Date | Yes | — |
| 4 | मोबाईल क्रमांक | Mobile Number | Textbox | Yes | — |

**Not shown in popup (auto-filled on save):**

| Field | Source |
| :--- | :--- |
| ग्राहक क्र. (Customer No.) | Auto-generated |
| शाखा (Branch) | Logged-in user's branch from session |

**Footer actions:** `जतन करा` (Save), `रद्द करा` (Cancel).

## Interaction Flow

1. User focuses the Customer Autocomplete and types; if no match, clicks **+ नवीन ग्राहक जोडा**.
2. Modal opens with empty minimal fields.
3. User fills required fields and clicks **जतन करा**.
4. System creates the customer record (branch = session branch, customer no. auto-generated).
5. Modal closes; the triggering Autocomplete displays `id — name` (e.g. `664 — New Customer Name`).
6. User continues the parent screen workflow (e.g. set Relation and Percentage, then **टाका** to add to nominee grid).
7. **रद्द करा** closes the modal without creating a customer; Autocomplete remains unchanged.

## Post-Create Expectations

- Full customer profile (Address, KYC, PAN, Aadhaar) is completed **later** from **ग्राहक > नवीन ग्राहक** or customer edit — the popup is intentionally minimal.
- Nominee tab does **not** duplicate contact/address from the customer record; grid shows customer no./name plus nomination-specific fields only.

## Spec Authoring Rules

1. Document the Autocomplete row and note: `Includes + नवीन ग्राहक जोडा per [quick-add-customer-pattern.md](quick-add-customer-pattern.md)`.
2. Do **not** repeat popup field tables on every screen — reference this document.
3. Mockups: use `.mockup-autocomplete-with-action` row + `.mockup-modal-overlay` / `.mockup-modal` from `mockups/shared/mockup-base.css`.

## Implementation Notes (Angular)

- Shared component: **`app-quick-add-customer`** — Material dialog (`MatDialog`).
- Inputs: none required beyond dialog open context; output: `{ customerId, displayName }` on successful save.
- Invoked from **`app-entity-autocomplete`** via an optional `@Input() showQuickAdd = false` or a sibling button in the parent template.
- Save calls `CustomerService.createMinimal(payload)`; service stub until `03-api-contracts/` exists.

## Related Documents

- [entity-autocomplete-pattern.md](entity-autocomplete-pattern.md)
- [ui-simplification-patterns.md](ui-simplification-patterns.md)
- [../customer/new-customer-screen.md](../customer/new-customer-screen.md)
