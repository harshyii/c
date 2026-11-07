# CLOTH X CLUB QR System v2.0

**Stack:** GitHub Pages frontend + Google Apps Script Web App + Google Sheets database.  
**Payment:** UPI deep link to `9050623210@sbi`; payment is manually confirmed by staff.  
**Loyalty:** customer registration by mobile, purchase points, point redemption, and a points ledger.

## Project structure

- `site/staff.html` — staff PIN, bill QR, payment confirmation, loyalty lookup.
- `site/pay.html` — customer UPI payment, optional rewards registration, Google review and Instagram links.
- `site/assets/config.js` — store URLs and UPI details.
- `site/assets/style.css` — mobile-first styling.
- `Code.gs` — Google Sheets backend.
- `DEPLOYMENT.md` — setup and publishing guide.

## Loyalty rules in this build

- Earn **1 point per ₹100** of net amount paid (rounded down).
- **100 points = ₹10** reward value.
- Minimum redemption: **100 points**.
- Redemption is deducted and earned points are credited only when staff confirms payment.
- Customer must register with a valid Indian mobile number and accept rewards registration.
- Marketing consent is separate and optional.
- These rules are configurable in `Code.gs`; tell customers the terms clearly.

## Payment limitation

This is a direct UPI intent flow. It prefills the amount but **does not verify payment automatically**. Staff must confirm the credit in the receiving bank/UPI app before pressing “CONFIRM PAYMENT RECEIVED”. A customer tapping DONE or registering for rewards is not proof of payment.

## Important deployment security note

The Apps Script web app is configured for public access so customer phones can open bill details and submit rewards registration. Staff-only actions require the PIN checked by Apps Script. Use a strong PIN, restrict who has access to the staff device, and do not publish the PIN in `config.js`. This is a lightweight small-store setup, not a high-assurance payment processor. For production-scale use, add stronger staff authentication and server-side abuse controls.
