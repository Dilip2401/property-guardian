# Property Guardian V37 — Friend Review Deployment

This package is prepared for a simple public demo deployment on Render.

## Demo accounts
- Admin: `admin@demo.com` / `admin123`
- Owner: `owner@demo.com` / `owner123`
- Guardian: `guardian@demo.com` / `guardian123`

## Simplest deployment

### Option A — Render Blueprint
1. Create a GitHub repository and upload the contents of this folder.
2. In Render, choose **New → Blueprint** and connect the GitHub repository.
3. Render will read `render.yaml` and create the web service.
4. Wait for deployment to finish.
5. Open the generated `onrender.com` URL and share it with your friend.

### Option B — Render Web Service
If Blueprint is not available in your account:
1. Create a new **Web Service** in Render.
2. Connect the GitHub repository.
3. Build Command: `npm install`
4. Start Command: `npm start`
5. Deploy.

The server already uses Render's `PORT` and listens on `0.0.0.0`.

## Important demo note
This is a prototype using local JSON/file storage. It is suitable for a friend review/demo, not production. Data written to a normal Render filesystem can be lost when the service is redeployed or restarted. Do not put real customer information into this demo.

## Suggested review flow
1. Login as **Admin**.
2. Open CRM & Control → add/onboard a property and customer.
3. Assign a Guardian and schedule a visit.
4. Login as **Guardian** and review the inspection workflow.
5. Submit an inspection with an Attention finding such as kitchen sink leakage.
6. Login as **Admin** and review the full Guardian report and individual finding.
7. Release the finding to the Owner.
8. Login as **Owner** and review the high-level report and decision actions.

## Product principle
Guardian observes → Admin validates → Owner decides → Vendor executes → Admin verifies → Property History improves.
