# **Meeting Summary — Custom Embroidery Widget & Search (Aug 10, 2025)**

  

## **Attendees**

  

Steve (dev), Kevin, Brian, Richard (Tom referenced as stakeholder)

  

## **Context**

- Steve demoed a first-pass custom embroidery widget using PulseID APIs (fonts/colors/text) with a mobile-friendly drawer/button UI.
- PulseID’s test server has been unstable; current work targets their production API.
    
## **Key Updates**

- **Widget status:** Basic text edit + color selection working. Font switching blocked by template config (“not configured” errors).
- **Mobile UX:** Drawer-style controls to avoid scrolling; buttons appear at small widths.
- **Integration plan:** Host our JS/widget ourselves (likely Azure) and inject into BigCommerce via a container/custom page.
- **Templates/data:** Need real templates/fonts/colors from our PulseID space to continue. Steve used PulseID’s example template as a stopgap.
- **Search vendors:** Bloomreach dashboard walkthrough scheduled; Algolia setup partially done in demo store but not functioning yet (likely selector/ID targeting issues).
    
## **Decisions**

- Keep text positioning **fixed/centered** based on template (no drag/drop) to reduce errors/liability.
- **Curved text** not required for v1 (nice-to-have only).
- Prefer **neutral backgrounds** with buttons styled to **pop** (match site brand subtly).
- Plan to **host widget externally** and embed in BigCommerce.
    
## **Requests/Ideas**

- Support **two color menus**: Standard vs **Metallic** (with +$5) — PulseID can flag metallic colors.
- Add a **three-line** text template (some demand, even if lower volume).
- Future: pre-populated **logos**, team/member flows, asset vaulting once self-hosted.
    
## **Risks / Blockers**

- PulseID test environment instability.
- Missing/incorrect template configuration causing font errors.
- Search vendor integrations won’t be “plug-and-play” due to our customizations.
    
## **Next Steps / Action Items**

- **Kevin:** Move relevant **templates/colors/fonts** to our **production PulseID** environment so Steve can integrate.
- **Kevin/Colin:** Create and publish a **3-line text template** in PulseID.
- **Steve:** Wire widget to our production PulseID data; re-enable **font selection** once config is live.
- **Steve:** Prototype **dual color menus** (Standard vs Metallic) and display price add-on for Metallic.
- **Steve:** Prepare **embedding** plan for BigCommerce (container/custom page) and add “**Customize**” entry point from product page.
- **Steve/Brian:** Iterate **button styling** (visibility/contrast) and mobile drawer polish.
- **Brian:** Keep **Steve on all search vendor calls**; verify **Algolia** meeting time and ensure access to their dashboard.
- **Brian/Kevin:** Share **Algolia implementation guide** + confirm correct CSS selectors/IDs in demo store.
- **Brian:** Proceed with **Bloomreach** test dashboard walkthrough.
## **Open Questions**

- How should template **selection UI** appear (pre-select dialog vs in-widget control)?
- Exact **price presentation** for Metallic colors (labeling and placement).
- Any additional **brand styling** requirements for the widget container on RBG site?
    

---

**Overall:** The custom widget approach is viable and progressing quickly. Unlocking real PulseID template/config data is the key to the next integration leap, followed by hosting + BigCommerce embedding and search integration alignment.