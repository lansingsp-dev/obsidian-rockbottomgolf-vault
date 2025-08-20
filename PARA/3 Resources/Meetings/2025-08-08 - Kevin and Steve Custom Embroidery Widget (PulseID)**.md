# **Meeting Summary — Custom Embroidery Widget (PulseID)**

  

**Context:** Progress check on the custom embroidery design widget for Rock Bottom Golf, using PulseID APIs.
**Participants mentioned:** Steve, Kevin
**Platform/Tech:** BigCommerce + custom React widget; PulseID backend (Render, GetProduct, fonts/colors/templates).

---
## **Goals & Direction**

- **Keep the UI simple for v1:** one **global font** and **global color** applied to all text lines (like Callaway)—avoid per-line font/color in the first release.
- **Use globally configured assets:** pull **configured fonts & colors** from PulseID’s global lists rather than per-template/per-product where possible.
- **Template approach (phase 1):** treat a small, curated set of **global templates** as applicable to all golf bags to avoid heavy per-product configuration.
- **Mobile-first controls:** flyout/drawer pattern validated for mobile; keep desktop non-scrolling where possible.
    
---
## **Key Decisions**

- **Fonts & Colors:**
    - Start with **one font + one color for all lines** (simpler UX, aligns with other designers).
    - Query the **main font list** and **default color list**; filter in code if the API doesn’t support server-side filtering.
        
- **Templates:**
    - **Don’t depend on product-associated templates** for v1; maintain a global list (ball pocket focus).
    - Anticipate future locations (e.g., **side pocket**) and categories; design with extensibility in mind.
        
- **Environments:**
    - It’s acceptable to **develop against production** PulseID for rendering during early UI work (risk is low until ordering is involved).

---

## **UI/UX Notes**

- **Mobile:** flyout drawers for “Select Font,” “Select Color,” and text inputs; avoid long scrolling.
- **Desktop:** keep controls visible if space allows; consider making **template choices visible** above/below the image (not buried in a button) so users notice them.
- **Color control:** may present as a dropdown or grid; a dropdown affordance (arrow) improves clarity.
- **Design/Icon picker:** likely a **picker with categories** (e.g., flags, golf icons) in later phases; customLids-style gallery is a good reference.
- **Product variations (future):** optional in-wizard variation switcher so users can preview bag colorways without leaving the designer.
    
---

## **Technical Notes**

- **PulseID API behavior:**
    
    - **Personalizations[]** suggests per-line color/fonts are possible, but v1 will **standardize** on single selections.
    - Some endpoints lack filter params → **filter client-side** after fetching.
    - **GetProduct** can include available templates; for v1, rely on **global template list** and your own filtering.
    - Ensure the templates/fonts/colors you expect are **configured/active** in PulseID (some were missing until enabled).
        
- **Pricing/Upsell (future):**
    - Need a strategy for **combined pricing** (e.g., Text $10 + Icon $5) since Pulse templates often map to **one SKU/price**.
        
---

## **Open Questions / Risks**

- How to **source-of-truth** the global template list (hard-coded, JSON, or small internal DB)?
- Final **placement/visibility** of template selectors on desktop vs mobile.
- **Non-customizable variations:** need a storefront-level rule to **hide/disable** the customize entry point when a variation isn’t eligible.
- **Order placement coupling:** safeguard so dev/testing renders don’t accidentally create billable orders.
    
---

## **Phase Map**

- **Phase 1 (MVP):** global templates (ball pocket), single font & color for all lines, mobile drawers + tidy desktop layout, render preview.
- **Phase 2:** icon/design picker with categories, side pocket templates, better product-variation switching inside the widget.
- **Phase 3:** pricing composition (text + icon), robust per-product eligibility signals, richer template management.
    
---

## **Action Items**

- [ ] #task **Share templates/config**: Move the working templates (the set referenced in Postman examples) into the environment Steve uses for local dev.
- [ ] #task**Implement global lists**: Fetch **global fonts** and **global colors** at load; filter to configured/active; standardize selections across lines.
- [ ] #task**Template selection UI**: Add **visible template chooser** (above/below image on desktop; drawer on mobile if space is tight).
- [ ] #task**Guardrails**: Ensure no order submission occurs during dev; render-only flow for now.
- [ ] #task**Eligibility rules (future)**: Plan storefront logic to **hide “Customize”** for non-eligible variations.
- [ ] #task**Pricing design (future)**: Draft approach for **composed pricing** (text + icon) independent of Pulse single-SKU constraint.
- [ ] #task**Variation switcher (future)**: Spec a simple in-widget **bag variation** selector for later phase.
    

---

## **Quick References (mentioned)**

- **Endpoints:** GetProduct, Render, global Fonts/Colors (filter client-side).
- **Working example:** Using the **single-line 70x20** template during early development; shift to double-line after configuration stabilizes.
- **Comparables:** Callaway (single font/color); customLids (category gallery for designs).
    

---

## **Notes**

- Personal travel/life bits were discussed (flights, games, weddings), but no impact on deliverables beyond timing (config copy planned for weekend).
- Next immediate milestone is **getting the templates and configs into Steve’s environment** so the UI can hook up properly.