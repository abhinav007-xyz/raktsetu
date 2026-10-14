# LifeLink Pulse — Intelligent Blood Response Network

> *"Every request matters. Every response counts."*

LifeLink Pulse is a full-stack healthcare prototype designed for Smart India Hackathon and college-level presentations. It provides a real-time, unified coordination platform connecting potential blood donors, hospitals, trauma centers, and regional blood banks.

---

## 🚀 Core Innovations

1. **Predictive Blood Shortage Radar:**
   - 30-day historical time-series demand modeling with exponential smoothing ($\alpha = 0.3$).
   - Calculates 7-day and 14-day demand curves and projected closing stock:
     $$\text{Projected Closing Stock} = \text{Current Usable Stock} + \text{Expected Replenishment} - \text{Projected Demand}$$
   - Identifies critical deficit gaps before stock-outs occur and provides recommended clinical review actions.
   - Live "Recalculate Forecast" action updates timestamps and risk indicators in real time.

2. **Smart Donor Matching Engine (Explainable 0–100 Scoring):**
   - Preliminary ABO/Rh and component-specific compatibility rules (PRBC, Whole Blood, Platelets, FFP, Cryoprecipitate).
   - 5 transparent weighted scoring factors:
     - Profile Verification (+25 pts)
     - Fresh Availability Confirmation (+25 pts)
     - Proximity / Radius within 3.5km (+25 pts)
     - Response Reliability History (+15 pts)
     - Emergency Alert Consent (+10 pts)
   - Detailed point-by-point explainability avoids black-box claims and preserves donor privacy.

3. **Smart Donor Relay Chain (Key Workflow Innovation):**
   - Prevents donor notification fatigue by dispatching invitations in controlled, timed batches (2–3 donors per batch).
   - Real-time response tracking: Acceptance, Decline, or 15-minute Timeout.
   - Single-click **Backup Batch Activation** when initial candidates decline.
   - **Crucial Patient Safety Principle:** Donor acceptance marks the status as **"Hospital Confirmation Pending"**—it does *not* automatically fulfill the request. Final fulfillment requires an authorized physician's clinical sign-off following physical arrival and bedside cross-matching.

4. **Hospital-to-Hospital Stock Coordination:**
   - Real-time loaning and transfer tracking between 5 regional facilities.
   - Multi-stage pipeline: `Requested` &rarr; `Under Review` &rarr; `Approved` &rarr; `In Transit` &rarr; `Completed`.

5. **Emergency Surge Mode:**
   - High-visibility Incident Command war-room interface for mass casualty incidents.
   - Transparent tactical prioritization based on clinical urgency (Emergency STAT), time-to-SLA deadline, and unresolved relay status.

6. **LifeLink Assistant (Bilingual EN / HI):**
   - Offline knowledge base assistant available in **English** and **Hindi (हिंदी)**.
   - Explains the matching score, relay batches, shortage radar formulas, and clinical protocols without requiring external paid API keys.

---

## 👥 Demo Access & Role Personas

Switch between demo personas at any time from the top navigation or login screen:

1. **Hospital / Blood Bank (Lead):**
   - *Persona:* Dr. Rajesh Nair (Medical Superintendent, Apex Metro General)
   - *Capabilities:* Create requests, run matching engine, manage inventory, launch relays, authorize clinical fulfillment.
2. **Registered Donor:**
   - *Persona:* Rahul Verma (O- Regular Volunteer, DNR-103)
   - *Capabilities:* Toggle availability, receive emergency alerts, accept/decline simulated invitations.
3. **Network Administrator:**
   - *Persona:* City Operations Health Command
   - *Capabilities:* Verify donor profiles, engage Emergency Surge Mode, inspect immutable audit logs.

---

## ⏱️ The 3-Minute Hackathon Demonstration Workflow

LifeLink Pulse includes an interactive **"3-Min Demo Tour"** modal with 7 guided steps:

- **Step 1 — Dashboard:** Inspect open requests, potential donors, inventory deficits, and the live supply vs estimated demand chart.
- **Step 2 — Request Details:** Open demonstration request `LLP-REQ-1001` (Emergency 2 units O- PRBC for trauma surgery).
- **Step 3 — Matching Engine:** Run matching on `LLP-REQ-1001` to view ranked candidates and the 0–100 explainable factor breakdown.
- **Step 4 — Relay Chain Innovation:** Inspect Batch 1 (donor Vikram Sharma declined). Click **"Activate Backup Batch"** to engage Batch 2. Click **"Simulate Accept"** on Rahul Verma (97 pts). Note that status transitions to *Hospital Confirmation Pending*.
- **Step 5 — Shortage Radar:** Inspect 30-day demand curves and projected stock deficits. Click **"Recalculate Forecast"** to demonstrate reactive AI recalculation.
- **Step 6 — Hospital Coordination:** Track or create an inter-facility stock loan request from City Central Blood Bank.
- **Step 7 — Authorized Transfusion & Conclusion:** Perform physician sign-off in the fulfillment modal, inspect the immutable audit log, and return to the live synchronized dashboard.

*To repeat the demonstration:* Click the **Reset** button in the header or in Settings to restore factory seed data.

---

## 💻 Tech Stack

- **Frontend:** React 19, TypeScript, Vite
- **Styling:** Tailwind CSS v4, Lucide React icons
- **Visualizations:** Recharts (Area, Bar, Line)
- **Mapping:** Leaflet & OpenStreetMap with fallback list view
- **State & Persistence:** Reactive local storage data service with event subscriptions and audit logging
- **Zero API Key Requirement:** Works completely offline with rich synthetic data

---

## 🛠️ Running Locally / in Replit

```bash
# 1. Install dependencies
npm install

# 2. Run the development server
npm run dev
```

The application runs on `http://localhost:3000`.
