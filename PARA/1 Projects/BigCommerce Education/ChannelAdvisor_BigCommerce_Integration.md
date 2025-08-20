# ChannelAdvisor and BigCommerce Integration

## 🛍️ What is ChannelAdvisor?

**ChannelAdvisor** is a cloud-based platform that serves as a centralized hub for managing product data, inventory, pricing, and orders across multiple online sales channels — including BigCommerce, Amazon, eBay, Walmart, and Google Shopping.

---

## 🔗 How ChannelAdvisor Works with BigCommerce

| Feature               | Description |
|------------------------|-------------|
| **Product Sync**       | Products from ChannelAdvisor are pushed into BigCommerce using a feed or API. ChannelAdvisor controls product titles, descriptions, prices, and availability. |
| **Inventory Management** | Inventory is managed in ChannelAdvisor and updates are pushed to BigCommerce (and other channels). |
| **Order Routing**      | Orders from BigCommerce can be routed through ChannelAdvisor to an ERP, warehouse, or fulfillment service. |
| **Marketplace Syndication** | Allows publishing product data to Amazon, Walmart, Google Shopping, and more using the same master product data. |
| **Pricing & Promotions** | ChannelAdvisor can apply rules for pricing based on competitive analysis, stock levels, etc. |
| **Analytics**          | Unified dashboard for sales and channel performance, including BigCommerce. |

---

## 🔁 BigCommerce ↔ ChannelAdvisor Data Flow

```
[ ChannelAdvisor ]
      ↑    ↓
  Products, Inventory
      ↑    ↓
 [ BigCommerce Store ]
      ↑    ↓
  Orders and Fulfillment
```

- BigCommerce is treated as a **channel** within ChannelAdvisor.
- ChannelAdvisor communicates with BigCommerce via the **BigCommerce REST API**.
- Sync includes:  
  - Product catalog  
  - Inventory  
  - Prices  
  - Orders

---

## ⚙️ Technical Integration Details

ChannelAdvisor uses BigCommerce API endpoints like:

- `GET/POST /catalog/products` — Sync product listings
- `PUT /inventory` — Update stock levels
- `PATCH /price` — Adjust pricing
- `POST /orders` — Receive/store orders

Look in **BigCommerce Admin → Advanced → API Accounts** for a connection named `ChannelAdvisor`.

---

## 🔍 Where You'll See It

- Product data like **SKUs**, **descriptions**, and **pricing** may be read-only in BigCommerce if controlled by ChannelAdvisor.
- Product info may be **overwritten** if changed manually in BigCommerce (unless override is allowed).
- Some BigCommerce custom fields or meta fields are populated by ChannelAdvisor feeds.
- New products must be created in ChannelAdvisor first to sync into BigCommerce (unless reverse sync is configured).

---

## 🧠 How This Affects Your Workflow

| Scenario                                | Behavior |
|----------------------------------------|----------|
| Manual product edits in BigCommerce    | May be **overwritten** by ChannelAdvisor on next sync |
| New products created in BigCommerce    | May not appear in ChannelAdvisor unless imported |
| Layout or theme changes                | Not affected by ChannelAdvisor — it's only data-driven |
| Inventory or pricing issues            | Likely originate from ChannelAdvisor feeds or rules |

---

## ✅ Summary

- ChannelAdvisor is the **source of truth** for product and inventory data.
- BigCommerce acts as a **display and transaction layer**.
- Any third-party visual tools (like **Nextopia** or **PulseID**) sit on top of the product data injected via ChannelAdvisor.
