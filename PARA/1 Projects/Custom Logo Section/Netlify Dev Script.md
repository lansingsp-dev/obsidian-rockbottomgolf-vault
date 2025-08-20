# Script

```bash
#!/bin/bash  
export NVM_DIR="$HOME/.nvm"  
source "$NVM_DIR/nvm.sh"  
  
nvm use 20.19.4  
netlify dev
```

# Console
![[Pasted image 20250804170339.png]]

# ✅ Netlify Dev + Vite Startup Explained

You successfully launched your development environment using `start-netlify.sh`.

---

## 🔍 Console Output Breakdown

- **Node version set by NVM**  
  ```
  Now using node v20.19.4 (npm v10.8.2)
  ```
  → Confirms `nvm use 20.19.4` was executed successfully.

- **Netlify CLI initialized**
  ```
  Injecting environment variable values for all scopes
  Setting up local dev server
  ```

- **Vite dev server started**
  ```
  VITE v6.3.5 ready in 78 ms
  ➜  Local:   http://localhost:5173/
  ```
  → This is your raw React frontend served by Vite.

- **Netlify function loaded**
  ```
  ✔ Loaded function pulseid-proxy
  ```

- **Netlify Dev server ready**
  ```
  Local dev server ready: http://localhost:8888
  ```
  → This is the full local server that routes:
    - React frontend via Vite
    - Serverless functions like `/.netlify/functions/pulseid-proxy`

---

## 💡 Important Notes

- **Use this URL in the browser:**
  ```
  http://localhost:8888
  ```

- **Do NOT use the Vite-only port (`5173`)**, as it cannot route to Netlify functions.

- **Your fetch should look like this:**
  ```js
  fetch('/.netlify/functions/pulseid-proxy?endpoint=Template/GetTemplates&variantId=...')
  ```

---

## 🛠 Optional Enhancement

To auto-open the correct Netlify port in your browser, update `start-netlify.sh` like this:

```bash
#!/bin/bash
export NVM_DIR="$HOME/.nvm"
source "$NVM_DIR/nvm.sh"

nvm use 20.19.4
netlify dev --open
```

---