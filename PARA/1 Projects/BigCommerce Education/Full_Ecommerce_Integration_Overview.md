# 🧩 BigCommerce + NetSuite + ChannelAdvisor + Nextopia Integration Overview

This document outlines how the core systems—**BigCommerce**, **NetSuite**, **ChannelAdvisor**, and **Nextopia (Searchspring)**—work together in a modern e-commerce stack.

---

## 🛍️ BigCommerce

**Role:** Customer-facing storefront  
BigCommerce serves as the **presentation and transaction layer**. It handles:

- Product catalog display
- Customer browsing experience
- Cart and checkout
- Order creation

BigCommerce is primarily driven by **data pushed in from upstream systems**.

---

## 📦 ChannelAdvisor

**Role:** Multi-channel syndication and product/inventory hub  
ChannelAdvisor is used to:

- Syndicate product data to BigCommerce, Amazon, eBay, Walmart, etc.
- Control pricing, availability, and promotions
- Centralize inventory feeds from NetSuite
- Route orders to ERP systems (like NetSuite)

BigCommerce is configured as a **"Webstore" channel** inside ChannelAdvisor.

---

## 🧾 Oracle NetSuite

**Role:** ERP and back-office system of record  
NetSuite is the **source of truth** for:

- Product master data
- Inventory levels
- Orders and fulfillment
- Financials and accounting

**Integration to ChannelAdvisor or BigCommerce** is typically done through:
- Celigo
- FarApp
- Dell Boomi
- Or custom RESTlets via SuiteScript

---

## 🔍 Nextopia (Searchspring)

**Role:** On-site search, dynamic merchandising, and product grid injection  
Nextopia replaces or enhances BigCommerce's native:

- Search autocomplete
- Category filtering
- Product list rendering
- Merchandising campaigns (e.g., banners, boost rules)

It loads via a JavaScript snippet and often **replaces the native product grid with dynamic content** based on search and merchandising rules.

---

## 🔁 Data Flow Diagram

```text
        [ Oracle NetSuite ]
                ↑   ↓
        Inventory, Orders, Products
                ↑   ↓
        [ ChannelAdvisor ]
            ↑         ↑
 Products, Price   Orders
            ↑         ↓
       [ BigCommerce Storefront ]
            ↓         ↑
  Product Grid  ←  Nextopia/Searchspring
```

---

## ✅ Summary Table

| System           | Role                                           | Integration Method                      |
|------------------|------------------------------------------------|------------------------------------------|
| **BigCommerce**  | Storefront (UI, Checkout)                     | REST API, App Scripts, Theme Injection   |
| **ChannelAdvisor**| Product/Inventory Syndication Hub             | BigCommerce API, NetSuite Middleware     |
| **NetSuite**     | ERP: Inventory, Orders, Fulfillment, Financials| Celigo, FarApp, Boomi, SuiteScript       |
| **Nextopia**     | Merchandising/Search Layer                     | JS Widget, Product Grid Injection        |

---

## 🧠 Tips for Managing the Stack

- **Product master data** should originate from NetSuite or ChannelAdvisor—avoid editing manually in BigCommerce.
- Ensure each system has a clear boundary: BigCommerce for UI, ChannelAdvisor for channels, NetSuite for operations, Nextopia for frontend search/UX.
- Use **staging environments** for each component if possible to avoid conflicts (especially with hardcoded domains in Nextopia scripts).

---

## 🧰 Optional Enhancements

- Use **Google Tag Manager** to track performance of Nextopia campaigns.
- Sync **custom fields** from NetSuite → ChannelAdvisor → BigCommerce for advanced filtering.
- Use **relative URLs** in Nextopia/Searchspring to prevent production links on staging.

---
