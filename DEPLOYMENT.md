# DEPLOYMENT GUIDE — CLOTH X CLUB QR SYSTEM V2.0

Follow these step-by-step instructions to deploy the system.

### Step 1: Google Spreadsheet & Apps Script Setup
1. Create a new Google Sheet named `CLOTH_X_CLUB_DB`.
2. Click **Extensions > Apps Script**.
3. Replace all default code in `Code.gs` with the provided `backend/Code.gs`.
4. Run the `setupCXC()` function from the Apps Script editor menu.
5. Grant the necessary permissions when prompted.
6. Verify that four sheets are created: `Settings`, `Bills`, `Customers`, and `PointsLedger`.

### Step 2: Set Staff PIN (Script Properties)
1. In Apps Script, go to **Project Settings** (gear icon).
2. Scroll to **Script Properties** and click **Edit script properties**.
3. Add a new property:
   - **Property**: `CXC_STAFF_PIN`
   - **Value**: `YOUR_SECRET_PIN` (e.g., `4321`)
4. Click **Save script properties**.

### Step 3: Deploy Web App
1. Click **Deploy > New deployment**.
2. Select type: **Web app**.
3. Configuration:
   - **Execute as**: `Me`
   - **Who has access**: `Anyone`
4. Click **Deploy** and copy the **Web App URL** ending in `/exec`.

### Step 4: Configure Frontend
1. Open `qr/assets/config.js`.
2. Paste the Web App URL into the `API_URL` property:
   ```javascript
   API_URL: "[https://script.google.com/macros/s/.../exec](https://script.google.com/macros/s/.../exec)"