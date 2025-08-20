# What is a Reverse Proxy?

A **reverse proxy** is a server that sits in front of your backend services (like APIs, frontend dev servers, or serverless functions) and **forwards client requests** to the correct service behind the scenes.

---

## 🔄 In Simple Terms

> It's like a **traffic controller** for your app — receiving requests and routing them to the correct internal service.

---

## 🧠 Analogy

When you visit: `http://localhost:8888`

You might:

- View the React app from the Vite dev server.
- Make a fetch call to an API route like `/api/pulseid-proxy?...`.

Here's how the reverse proxy handles it:

| Request Path                    | Routed To                            |
|---------------------------------|--------------------------------------|
| `/` or `/index.html`            | 👉 Vite dev server (port 5173)       |
| `/api/pulseid-proxy?...`        | 👉 Netlify function (pulseid-proxy.js) |
| `/static/js/main.js`            | 👉 Vite dev server again             |

---

## 🔧 Why Netlify Uses a Reverse Proxy in Dev Mode

When you run: `netlify dev`

Netlify:
	•	Starts your frontend server (Vite) on port 5173.
	•	Loads your serverless functions.
	•	Spins up a reverse proxy on port 8888.

This combines everything under a single origin (http://localhost:8888), just like in production.

## Benefits of a Reverse Proxy

| **Benefit**        | **Description**                                                |
| ------------------ | -------------------------------------------------------------- |
| 🔐 One Domain      | Avoids CORS by serving frontend + APIs from a single origin    |
| 🔄 Clean URLs      | Lets you use /api/* instead of hardcoding full function paths  |
| ⚖️ Load Balancing  | (In production) Can distribute traffic across multiple servers |
| 🔍 Central Logging | Enables centralized logging, caching, or security filtering    |

## In Your Project

You’re using Netlify Dev as a reverse proxy to:
	•	Serve the React app (Vite on port 5173)
	•	Handle API calls (/api/pulseid-proxy) via Netlify functions
	•	Provide a unified interface at: `http://localhost:8888`

This mimics your **production setup**, ensuring that API and frontend work together seamlessly.

# 🧠 How Serverless Functions Work in Your Netlify + React App

## 🖼️ Architecture Diagram (Text-based)

```text
+----------------------+        +-------------------------------+
|    Your Browser      |        |     React Frontend (Vite)     |
|                      |        |                               |
|  http://localhost:8888 ─────▶ |  Renders UI, calls fetch()    |
|                      |        |   to /api/pulseid-proxy?...   |
+----------------------+        +-------------------------------+
                                             │
                                             ▼
                           (Reverse Proxy: Netlify Dev)
                                             │
                                             ▼
+--------------------------------------------------------------+
|        Netlify Dev (port 8888 - acts as reverse proxy)       |
|                                                              |
|  /index.html → Vite dev server (port 5173)                   |
|  /api/pulseid-proxy → pulseid-proxy.js (Netlify Function)   |
+--------------------------------------------------------------+
                                             │
                                             ▼
+-------------------------------+     Calls via Fetch
|  Serverless Function:         |──────────────────────────────▶
|  pulseid-proxy.js             |     https://rockbottom.pulseidconnect.com/api/api/...
|-------------------------------|
| - Gets event from frontend    |
| - Calls PulseID API           |
| - Forwards response           |
+-------------------------------+

```


## **🔍 What Happens Step-by-Step**

1. User visits your app at http://localhost:8888.
2. React loads and makes a fetch() request to /api/pulseid-proxy?....
3. Netlify Dev intercepts the request using its **reverse proxy**.
4. The request is forwarded to the Netlify **serverless function** (pulseid-proxy.js).
5. The function makes a backend call to the **PulseID API**.
6. The response is returned back through Netlify → React → Browser.

## **Why Use Serverless Functions?**

- Keeps your API keys **hidden** (not exposed to frontend).
- Handles CORS, logging, and authentication server-side.
- Makes it easy to add backend logic without running a real server.

> It’s called “serverless” because **you don’t run or maintain the server** — the platform does that for you.


