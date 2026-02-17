# 🚀 Interstellar Transmission Hub — Setup Guide

## Files Overview
- `index.html` → Sister's Space Portal (Commander Nova)
- `brother.html` → Brother's Earth Base Terminal
- This guide

---

## ─── STEP 1: Set Up EmailJS (Free — Real Emails!) ───

EmailJS sends real emails when you hit "Launch Transmission" or "Transmit Reply."
**Free tier: 200 emails/month — more than enough.**

### 1A. Create Your Account
1. Go to **https://www.emailjs.com/** and sign up (free)
2. Confirm your email

### 1B. Add an Email Service
1. In the EmailJS dashboard → click **Email Services** → **Add New Service**
2. Choose **Gmail** (easiest)
3. Connect your Gmail account and click **Connect Account**
4. Note down your **Service ID** (looks like `service_abc123`)

### 1C. Create Email Templates

You need **two templates** — one for each direction.

#### Template 1: Sister → Brother
1. Click **Email Templates** → **Create New Template**
2. Set **To Email**: your brother's email address (or yours for now)
3. Set **Subject**: `{{subject}}`
4. Set **Body**:
```
Hi {{to_name}}! 🚀

New transmission from {{from_name}}:

{{message}}

━━━━━━━━━━━━━━━━
🌌 Space Fact of the Day:
{{space_fact}}

Date: {{date}}
Log ID: {{log_id}}

— Interstellar Transmission Hub
```
5. Save and note down the **Template ID** (looks like `template_abc123`)

#### Template 2: Brother → Sister  
1. Create another template
2. Set **To Email**: the sister's email
3. Set **Subject**: `{{subject}}`
4. Set **Body**:
```
Hi {{to_name}}! 🌿

Reply from {{from_name}} at Earth Base:

{{message}}

━━━━━━━━━━━━━━━━
🌿 Eco/Biotech Fact:
{{eco_fact}}

Date: {{date}}

— Earth Base Terminal
```
5. Save and note down this **Template ID**

### 1D. Get Your Public Key
1. In the EmailJS dashboard → click your **profile icon** (top right) → **Account**
2. Find **Public Key** (looks like `user_abc123xyz`)

### 1E. Add Keys to Your HTML Files

**In `index.html`** (Sister's portal), find these 3 lines near the top of the `<script>` tag:
```js
const EMAILJS_PUBLIC_KEY  = 'YOUR_PUBLIC_KEY';
const EMAILJS_SERVICE_ID  = 'YOUR_SERVICE_ID';
const EMAILJS_TEMPLATE_ID = 'YOUR_TEMPLATE_ID';   // Template 1 (sis → bro)
```
Replace the placeholder strings with your real values.

**In `brother.html`**, find the same 3 lines:
```js
const EMAILJS_PUBLIC_KEY   = 'YOUR_PUBLIC_KEY';      // same key
const EMAILJS_SERVICE_ID   = 'YOUR_SERVICE_ID';      // same service
const EMAILJS_TEMPLATE_ID  = 'YOUR_TEMPLATE_ID_BRO'; // Template 2 (bro → sis)
```
Replace with your real values (Template ID is the second one you made).

---

## ─── STEP 2: Deploy to GitHub Pages ───

### 2A. Create a GitHub Repository
1. Go to **https://github.com** → **New repository**
2. Name it something like `interstellar-hub` or `transmission-hub`
3. Set it to **Public** (required for free GitHub Pages)
4. Click **Create repository**

### 2B. Upload Your Files
**Option A — Drag & Drop (easiest):**
1. Open your new repository on GitHub
2. Click **Add file** → **Upload files**
3. Drag both `index.html` and `brother.html` into the upload area
4. Scroll down → click **Commit changes**

**Option B — GitHub Desktop or git CLI:**
```bash
git init
git add index.html brother.html
git commit -m "🚀 Launch Interstellar Transmission Hub"
git remote add origin https://github.com/YOUR_USERNAME/interstellar-hub.git
git push -u origin main
```

### 2C. Enable GitHub Pages
1. In your repository → click **Settings** tab
2. Scroll down to **Pages** (left sidebar)
3. Under **Source** → select **Deploy from a branch**
4. Choose branch: **main**, folder: **/ (root)**
5. Click **Save**
6. Wait ~60 seconds, then GitHub will show you your live URL:
   ```
   https://YOUR_USERNAME.github.io/interstellar-hub/
   ```

### 2D. Share the Links
- **Sister's portal:** `https://YOUR_USERNAME.github.io/interstellar-hub/`
- **Brother's portal:** `https://YOUR_USERNAME.github.io/interstellar-hub/brother.html`

Bookmark both — or set them as browser home pages! 🌌

---

## ─── STEP 3: How It Works Day-to-Day ───

### Sister's Flow:
1. Opens her portal URL
2. Clicks **▶ Start Camera** → smiles → **📸 Capture Photo**
3. Types a message title + message text
4. Edits the space fact (or clicks ⟳ for a random one)
5. Clicks **🚀 LAUNCH TRANSMISSION**
6. A rocket animation fires! Brother gets an email notification.
7. When she visits her portal later, she'll see a **🌿 New reply** badge if her brother replied

### Brother's Flow:
1. Opens his portal URL
2. A **🛸 spaceship** flies in from the edge of the screen with a "INCOMING TRANSMISSION" alert
3. He clicks **⚡ OPEN MESSAGE** — an **explosion of stars** bursts across the screen
4. His sister's message + photo appears
5. He can reply with his own message + webcam photo + eco fact
6. A **🌿 leaf animation** launches his reply
7. Both build up a **daily streak star** ⭐ counting their exchanges

### Message Persistence:
- Messages are saved in **localStorage** — they persist across visits on the **same browser/device**
- This is great for shared family computers or when you each use your own device's bookmark
- The sister and brother portals communicate through localStorage (same domain = shared storage)

---

## ─── STEP 4: Customizing Names ───

To change "Commander Nova" and "Little Bro":
- In `index.html`, find: `document.getElementById('cmdName').textContent = 'Commander Nova';`
  — change `'Commander Nova'` to whatever name you like
- In `brother.html`, find: `document.getElementById('agentName').textContent = 'Little Bro';`
  — change `'Little Bro'` to your brother's actual name or codename

To change the launch date (for the "Days Since Launch" counter):
- In `index.html`, find the line: `localStorage.getItem('sis_launch') || new Date()...`
- Replace with a hardcoded date: `let launchDate = '2026-02-16';`

---

## ─── TIPS ───

- **Webcam photos** are embedded as base64 data — they're stored in localStorage, not uploaded anywhere. Privacy-first! 🔒
- **Streak stars** grow each day you send/reply. Try not to break the streak!
- The **explosion reveal** only triggers when there's a brand-new unread message. Once opened, it archives normally.
- You can add more space facts or eco facts by editing the `SPACE_FACTS` / `ECO_FACTS` arrays in the script sections.
- For the best experience on mobile, **add to Home Screen** so it feels like an app.

---

*Made with ❤️ — a private cosmos between a big sister and her space-obsessed little brother.*
