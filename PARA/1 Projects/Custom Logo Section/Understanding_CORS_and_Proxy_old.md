
# 🛡️ Understanding CORS (Cross-Origin Resource Sharing)

## 🤔 What is CORS?

**CORS** is a security feature built into all web browsers. It stands for:

> **Cross-Origin Resource Sharing**

It protects users by **stopping malicious websites** from making unauthorized requests to other servers on behalf of a user.

---

## 🎨 Simple Analogy

Imagine you're at **Website A (localhost:3000)**, and it tries to talk to **Server B (pulseidconnect.com)**.

The browser says:

> "Hold up! That’s a different origin. Let me check with Server B to see if that’s allowed."

Unless Server B replies with something like:

```http
Access-Control-Allow-Origin: http://localhost:3000
```

...the browser will **block the request** — even if the server is up and working.

---

## 🧱 Why This Affects You

You're running Stencil CLI at:

```
http://localhost:3000
```

And trying to `fetch()` data from:

```
https://rockbottom.pulseidconnect.com
```

But PulseID **doesn’t allow requests from localhost**, so your browser blocks the call before it’s sent.

---

## 🔄 The Solution: Use a Proxy

Instead of calling PulseID directly, you set up a **Netlify Function** (a tiny backend server).

### 🧠 What Happens Now:

1. Your browser calls:
    ```
    https://your-site.netlify.app/.netlify/functions/pulseid-proxy
    ```

2. Netlify (on the server) calls:
    ```
    https://rockbottom.pulseidconnect.com
    ```

3. Netlify sends back the data to your browser with:
    ```http
    Access-Control-Allow-Origin: *
    ```

✅ Now the browser is happy — no CORS error!

---

## 📊 Visual Diagram

```
[ Your JS in localhost:3000 ]
             |
     fetch('/.netlify/functions/pulseid-proxy')
             |
             V
[ Netlify Function Server ]  -->  [ PulseID API Server ]
             |
             V
     Response with CORS OK
             |
             V
[ Your JS Receives the Data 🎉 ]


---

## 🛫 What is a Preflight Request?

When your JavaScript makes a complex request (like sending custom headers or using POST/PUT), the browser **doesn’t send it right away**.

Instead, it first sends a small "test" request called a **preflight**:

```http
OPTIONS /api/endpoint HTTP/1.1
Origin: http://localhost:3000
Access-Control-Request-Method: POST
Access-Control-Request-Headers: Authorization, Content-Type
```

### 📋 Why?

The browser is asking the server:

> “Hey, if I send a POST request with these headers, will you allow it?”

If the server replies with the right headers:

```http
Access-Control-Allow-Origin: http://localhost:3000
Access-Control-Allow-Methods: POST
Access-Control-Allow-Headers: Authorization, Content-Type
```

✅ Then the browser sends the real request.

❌ If not, the browser **cancels it entirely** — and you get a CORS error **before your code even runs**.

---

## 🖼️ Real Example: What Your Screenshot Shows

You shared a Chrome Network tab showing two lines related to a failed API call.

| Name | Status | Type | Meaning |
|------|--------|------|---------|
| `GetProduct?...` | **400** | **preflight** | The browser sent an OPTIONS request asking if it’s allowed to call the API |
| `GetProduct?...` | **CORS error** | **fetch** | The actual fetch request failed because the preflight didn’t succeed |

### Step-by-Step: What Happened

1. JS called:
   ```
   fetch('https://rockbottom.pulseidconnect.com/api/api/Designer/GetProduct?...')
   ```
2. Browser sends **preflight OPTIONS** request.
3. Server returns **400 Bad Request**, no CORS headers.
4. Browser cancels the real request.
5. You see a **CORS error** in Chrome DevTools.

---

## 🔐 If CORS Can Be Bypassed With a Proxy… What Good Is It?

CORS **protects the end user**, not the server or developer.

### 🛡 Example:
Shady website `evil.com` tries to:
```js
fetch("https://bank.com/withdraw?amount=1000");
```
Blocked by CORS, because `bank.com` didn’t approve `evil.com`.

---

### 🔄 Why a Netlify Proxy Works

You control the proxy:
- You add your API keys
- You decide what endpoints to call

That’s **not a loophole**, it’s **intentional architecture**.

---

### CORS Doesn’t Affect Tools Like:

- curl
- Postman
- Netlify Functions
- Backend services

---

### What CORS Prevents

| Risk | CORS Benefit |
|------|--------------|
| CSRF | Stops browser-based attacks on logged-in users |
| API Theft | Prevents other sites from calling your private APIs |
| Session Hijack | Stops JavaScript from other origins using your cookies |

---

### ✅ TL;DR

| Myth | Reality |
|------|---------|
| “CORS is useless” | ❌ It’s a vital user-protection mechanism |
| “I can bypass it” | ✅ But only via **trusted backend** you control |
| “It’s outdated” | ❌ Still essential in all modern web apps |

---



---

## 🌐 What Happens When Running in Production?

If your custom widget runs on your live BigCommerce store (like `https://www.rockbottomgolf.com`), then:

> **PulseID must allow your production site URL in their CORS configuration.**

---

### 🔧 How PulseID Configures CORS

They’ll need to update their backend server to include your origin in this header:

```http
Access-Control-Allow-Origin: https://www.rockbottomgolf.com
```

---

### 🧰 Common Ways CORS is Configured

#### ✅ 1. Allow Just Your Production Site (Best Practice)
```http
Access-Control-Allow-Origin: https://www.rockbottomgolf.com
```
- Most secure
- Won’t allow staging or localhost unless added too

---

#### 🔄 2. Allow Multiple Trusted Origins (Server-side logic)
```http
If Origin in [list_of_allowed_origins]:
    Set Access-Control-Allow-Origin = request Origin
```
- Useful for supporting both production and staging
- Still must be carefully validated server-side

---

#### ⚠️ 3. Wildcard or Reflect-All (Not Recommended)
```http
Access-Control-Allow-Origin: *
```
or
```http
Access-Control-Allow-Origin: <incoming origin>
```
- Easier for dev, but insecure unless locked down

---

## ✅ What You Should Do

1. Provide PulseID with your live domain(s):
   - e.g., `https://www.rockbottomgolf.com`
   - plus `https://staging.rockbottomgolf.com` if needed
2. Ask them to **add these to their CORS configuration**
3. Deploy your widget and test — CORS errors should disappear in production

---

### 🧪 Do You Still Need the Proxy?

| Environment | Use Netlify Proxy? |
|-------------|--------------------|
| Development (`localhost:3000`) | ✅ Yes, CORS will fail otherwise |
| Production (`www.rockbottomgolf.com`) | ❌ Not needed, if PulseID allows your domain |

---



---

## ❓ Does PulseID Need to Whitelist Your Netlify Domain?

> ✅ **No — PulseID does NOT need to whitelist your Netlify domain when using a proxy.**

---

### 🔍 Why Not?

Because your browser isn’t calling PulseID directly — it’s calling your **Netlify Function**, which is trusted and under your control.

Here’s the flow:

```
[Browser: fetch()]
   |
   | -->  https://your-site.netlify.app/.netlify/functions/pulseid-proxy
   |
[Netlify Server (backend)]
   |
   | -->  https://pulseidconnect.com/api (with API key + headers)
   |
[PulseID API]
```

---

### 📋 What This Means

| Call Type | CORS Applies? | Does PulseID Need to Allow? |
|-----------|----------------|------------------------------|
| Browser → PulseID | ✅ Yes | ✅ Yes — must allow `Origin` |
| Netlify Function → PulseID | ❌ No | ❌ No — it's server-to-server |
| Browser → Netlify Function | ✅ Yes | ✅ You control the CORS headers |

When Nelify calls PulseID it does not make the preFlight call. This is the key point to fully understand why Neflify works.


---

### ✅ Result

- PulseID **never sees the browser’s origin** (`localhost`, `Netlify`, etc.)
- PulseID **only sees** a normal server-side HTTP request from Netlify
- You can access PulseID APIs securely, without needing their CORS changes

---

