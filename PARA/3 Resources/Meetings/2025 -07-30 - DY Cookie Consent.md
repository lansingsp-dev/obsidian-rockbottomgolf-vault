# Meeting Summary – DY Cookie Consent

Call between Rock Bottom Golf and Dynamic Yield to review Active Cookie Consent best practices:

1. Review Rock Bottom Current Consent Setup
2. DY (Dynamic Yield) Active Consent Overview
3. Implementation Plan & Next Steps (Validation)

**Date:** _(Not specified)_  
**Attendees:** Matthew, Christopher, Josh, Kevin, Steve  

---

## **Overview**
The team discussed the DY cookie consent implementation and the upcoming activation of the **Active Cookie Consent** flag in production. The current consent status defaults to "true" for U.S. users (assumed consent), and the functionality for toggling personalization consent is in place but requires a category change.

---

## **Key Points**
- **Current Functionality:**
  - Cookie consent toggle works, but personalization is currently under **Targeted Advertising**.
  - Status changes correctly when toggled, even under the wrong category.
  - In the U.S., consent defaults to true (assumed consent).
  - DY cookies are placed under the **Essential** category, which cannot be opted out of.

- **Category Change:**
  - Agreement to move from **Targeted Advertising** to **Personalization** for accuracy.
  - Christopher updated implementation to use the **Personalization** flag.

- **Active Cookie Consent Flag:**
  - Flag not yet active in production.
  - Once enabled, consent changes should be immediate when settings are updated in the Osano panel.
  - Testing will occur in production since no staging environment exists:
    1. Validation team checks current functionality.
    2. Flag is activated.
    3. QA re-tests to confirm instant updates.

- **Compliance Considerations:**
  - European compliance typically requires users to be able to opt out, updating consent status to `false`.
  - Opt-out handling is up to the client/legal team.

---

## **Action Items**
1. **Christopher:** Update cookie consent to use **Personalization** category – ✅ Completed.
2. **Matthew:** Submit validation ticket tonight.
3. **Validation & QA Teams:** Perform pre- and post-flag activation testing.
4. **Team:** Review opt-out process for EU compliance (optional/legal decision).

---

## **Decisions**
- Move cookie consent category from **Targeted Advertising** to **Personalization**.
- Proceed with validation before activating the flag in production.

---

## **Next Steps**
- Wait for Matthew to submit the ticket and schedule validation.
- Post-flag activation, confirm immediate consent status updates.

---