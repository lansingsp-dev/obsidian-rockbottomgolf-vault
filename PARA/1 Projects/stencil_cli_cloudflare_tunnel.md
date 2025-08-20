# 🌐 Run Stencil CLI with Cloudflare Tunnel (from Your Laptop)

## ✅ Goal
Run `stencil start` on your **local machine**, and expose it securely using **Cloudflare Tunnel** to a **static, public URL** like:

```
https://preview.yourdomain.com
```

Stakeholders can access your BigCommerce theme preview without deploying to the cloud.

---

## 🧰 Prerequisites

- A Mac, Windows, or Linux machine
- [`stencil-cli`](https://developer.bigcommerce.com/stencil-docs/installing-stencil-cli/installing-stencil) installed
- [Cloudflare account](https://dash.cloudflare.com/) (free)
- A domain name (use Cloudflare Registrar or import from Namecheap, etc.)
- [`cloudflared`](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/) CLI installed

---

## 🪜 Step-by-Step: Set Up Cloudflare Tunnel

### 1. 🛒 Buy or Use an Existing Domain

Register a domain like `yourpreviewsite.com`, or use one you already own.

> [!tip]
> You can register directly through [Cloudflare Registrar](https://www.cloudflare.com/products/registrar/) or use Namecheap and update nameservers later.

---

### 2. ➕ Add Domain to Cloudflare

1. Log into [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Click **“Add a Site”**
3. Point your domain’s nameservers to Cloudflare’s (Cloudflare will give you the correct ones)

---

### 3. 🧰 Install `cloudflared`

#### macOS:

```bash
brew install cloudflared
```

#### Windows (PowerShell):

```powershell
choco install cloudflared
```

#### Ubuntu/Debian:

```bash
sudo apt install cloudflared
```

---

### 4. 🔐 Login to Cloudflare

```bash
cloudflared tunnel login
```

This opens your browser for authentication and grants access to manage tunnels.

---

### 5. 🧱 Create a Tunnel

```bash
cloudflared tunnel create preview-tunnel
```

This sets up a tunnel and creates a credential file (JSON).

---

### 6. 🛠 Create Tunnel Config File

Create `~/.cloudflared/config.yml` (or `%HOMEPATH%\.cloudflared\config.yml` on Windows):

```yaml
tunnel: preview-tunnel
credentials-file: /Users/yourusername/.cloudflared/preview-tunnel.json

ingress:
  - hostname: preview.yourdomain.com
    service: http://localhost:3000
  - service: http_status:404
```

> [!tip]
> Replace `yourusername` and `yourdomain.com` accordingly.

---

### 7. 🌐 Set DNS Record in Cloudflare

- Go to **DNS → Records**
- Add a **CNAME** record:
  - **Name**: `preview`
  - **Target**: your tunnel ID (Cloudflare will autofill)

---

### 8. ▶️ Start `stencil start`

In your theme folder, run:

```bash
stencil start
```

This starts your theme preview on `http://localhost:3000`.

---

### 9. 🚀 Start the Tunnel

```bash
cloudflared tunnel run preview-tunnel
```

Now your preview is live at:

```
https://preview.yourdomain.com
```

---

## 🔒 Optional: Restrict Access (Cloudflare Access)

1. Go to **Cloudflare Zero Trust → Access → Applications**
2. Add your tunnel URL: `preview.yourdomain.com`
3. Set rules (e.g., require login, limit to company emails)

Free for up to 50 users!

---

## ✅ Summary

| Step | Task |
|------|------|
| 1 | Register or import domain |
| 2 | Add domain to Cloudflare |
| 3 | Install cloudflared |
| 4 | Authenticate with Cloudflare |
| 5 | Create and configure tunnel |
| 6 | Point DNS to tunnel |
| 7 | Run `stencil start` locally |
| 8 | Start tunnel → share your static URL |
| 9 | (Optional) Lock it down with Cloudflare Access |

---

## 📌 Notes

- This approach keeps hosting local but URL public and secure
- No need for Azure, Netlify, or VPS
- Zero hosting cost aside from your domain name
