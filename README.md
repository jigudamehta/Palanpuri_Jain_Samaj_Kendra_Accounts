# Palanpuri Jain Samaj Kendra (Surat) — Membership & Expense Manager

<p align="center">
  <img src="./logo.png" alt="Palanpuri Jain Samaj Kendra Emblem" width="180" style="border-radius: 50%; box-shadow: 0 8px 24px rgba(0,0,0,0.25);" />
</p>

<p align="center">
  <strong>Comprehensive Community Membership, Event Fee Counter & Financial Management Suite</strong><br>
  <em>Powered by Google Apps Script, Google Sheets & Modern Vanilla HTML5/CSS3/JavaScript</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Google%20Apps%20Script-4285F4?style=for-the-badge&logo=google&logoColor=white" alt="Google Apps Script" />
  <img src="https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white" alt="Google Sheets" />
  <img src="https://img.shields.io/badge/PWA-Ready-10b981?style=for-the-badge&logo=pwa&logoColor=white" alt="PWA Ready" />
  <img src="https://img.shields.io/badge/License-Proprietary-orange?style=for-the-badge" alt="License" />
</p>

---

## 🏛️ About the Emblem

The official emblem is inspired by the iconic **Kirti Stambh** (Tower of Fame / Victory Tower) of **Palanpur, Gujarat**, the revered ancestral homeland of the Palanpuri community. The tiered balconies, ornate chhatri dome, and golden laurel wreath represent cultural pride, unity, transparency, and progress.

---

## 🌟 Key Modules

### 1. ⚡ Rapid Bulk Counter (`BulkPayments.html` & `BulkPayments.gs`)
Built specifically for high-speed, high-volume fee collection counters during annual community gatherings (Samaj Snehmilan, AGM, Diwali events):
* **Live Auto-Populated Directory**: Instant rendering of 200+ members with pagination and status badges.
* **Smart Substring Search**: Search across **any part of a member's name**, Member ID, mobile number, or village.
* **Dynamic Fee Dues Calculation**: Automatically identifies unpaid financial years (where status is `FALSE` or blank) at the configured annual fee rate (e.g., ₹500/year).
* **Multi-Volunteer Concurrent Logging**: Each volunteer signs in with their assigned username & password. Every transaction logs `Prepared By` for full auditability.
* **Admin Event Counter Lock**: Admins can lock the counter at the end of the event day with a single click, preventing any volunteer from registering retroactive entries without knowledge.
* **1-Click WhatsApp Dispatch Hub**: Tracks pending vs forwarded PDF receipts per volunteer or for the whole counter.
* **Offline-First Resilience**: Records entries to IndexedDB/LocalStorage if WiFi or cellular network drops, and syncs to Google Sheets when connection is restored.

---

### 2. 📊 Master Management Dashboard (`index.html` & `Code.gs`)
The executive management portal for administrators and treasurers:
* **Member Directory & Family Records**: Full CRUD operations for member records, join dates, and family counts.
* **Income & Payments Ledger**: Direct reconciliation with multi-year fee tracking.
* **Expense Management**: Multi-category expense tracking with voucher generation.
* **Bank & Cash Accounts**: Opening balances, real-time ledgers, and inter-account transfers.
* **Automated PDF Generation**: Automatically formats, builds, and saves high-resolution printable PDF receipts and vouchers directly to designated Google Drive folders.
* **User & Volunteer Management**: Configure volunteer credentials, admin rights, and display names directly in the `Users` sheet.

---

## 📁 Repository Structure

```
├── Code.gs               # Primary Google Apps Script backend (Dashboard, Ledger, PDF Generator)
├── BulkPayments.gs       # Rapid Counter backend (Bulk sync, user verification, dispatch API)
├── index.html            # Main Single-Page App (Admin & Management Dashboard)
├── BulkPayments.html     # Rapid Counter & WhatsApp Dispatch Hub Web App
├── appsscript.json       # Apps Script manifest declaring required OAuth scopes
├── manifest.json         # Progressive Web App (PWA) manifest
├── sw.js                 # Service Worker providing offline caching
├── icon.svg              # Scalable vector Kirti Stambh emblem
├── logo.svg              # Vector logo asset
├── logo.jpg              # High-resolution emblem artwork
├── logo_reference.jpeg   # Original Palanpur Kirti Stambh reference photograph
├── .gitignore            # Git exclusion rules for Google Drive sync & temporary files
└── README.md             # Project documentation
```

---

## 🚀 Setup & Deployment Guide

### Step 1: Prepare the Google Spreadsheet
1. Create a new Google Spreadsheet (e.g. `Palapuri Samaj Kendra Management`).
2. Open **Extensions** > **Apps Script**.

### Step 2: Add Code Files
1. In the Apps Script code editor:
   - Paste `Code.gs` into the primary script file.
   - Click **+** > **Script** and create `BulkPayments.gs`, then paste `BulkPayments.gs`.
   - Click **+** > **HTML** and create `index.html`, then paste `index.html`.
   - Click **+** > **HTML** and create `BulkPayments.html`, then paste `BulkPayments.html`.
2. Under **Project Settings** (gear icon), check **Show "appsscript.json" manifest file in editor** and paste the content from `appsscript.json`.

### Step 3: Initialize Database Sheets
1. In the Apps Script toolbar, select the `initializeSheetsIfNeeded` function and click **Run**.
2. Grant the necessary Google Drive and Google Sheets permissions.
3. This will create the required sheets:
   - `Members`
   - `Payments Received`
   - `Expenses`
   - `Accounts`
   - `Settings`
   - `Users`

### Step 4: Deploy as Web App
1. Click **Deploy** > **New deployment**.
2. Select type: **Web app**.
3. Set:
   - **Execute as**: `Me (your Google account)`
   - **Who has access**: `Anyone` (required so volunteers can submit payments via the web interface)
4. Click **Deploy** and copy the **Web App URL** (`https://script.google.com/macros/s/.../exec`).

### Step 5: Launch
- You can access the system either directly via the Google Apps Script Web App URL or by opening `index.html` and `BulkPayments.html` locally / hosting them on GitHub Pages or any static web host.
- Both HTML applications have the production Google Apps Script API endpoint pre-configured for seamless connection.

---

## 🔒 Security & Volunteer Access Control

* **Credentials Store**: User logins and roles are maintained in the secure `Users` tab of your spreadsheet.
* **Role Separation**:
  - `Admin`: Can lock/unlock the counter, edit settings, manage bank accounts, delete records, and view all volunteers' dispatch queues.
  - `Volunteer`: Can search members, record payments in the rapid counter, view their own collections, and dispatch WhatsApp receipts.
* **Audit Trail**: Every transaction is timestamped and tagged with the volunteer's username.

---

## 📱 Mobile PWA Support
Both `index.html` and `BulkPayments.html` are PWA-enabled with `sw.js` and `manifest.json`. You can tap **Add to Home screen** on iOS Safari or Android Chrome to use the app in full-screen standalone mode like a native mobile app.

---

© Palanpuri Jain Samaj Kendra (Surat). All rights reserved.
