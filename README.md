# RENDEVO — Beauty Salons

A French, mobile-first appointment request frontend for beauty salons.

## Files
- `index.html` — booking flow and page structure
- `styles.css` — responsive visual design
- `app.js` — service, availability and booking interactions
- `config.js` — Apps Script endpoint and booking limits

## Backend
The frontend is configured to use the Google Apps Script Web App endpoint supplied for RENDEVO Beauty. It expects:
- GET `?action=services`
- GET `?action=availability&date=YYYY-MM-DD&service=...&staff=...`
- POST JSON body with `action: "book"`, `name`, `email`, `phone`, `service`, `date`, `time`, `staff`, and `notes`.

POST uses `text/plain` to avoid a browser JSON preflight request. The Apps Script response must still permit cross-origin reads for the frontend to display the result.

## Publish with GitHub Pages
In the repository, open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, select **main** and **/(root)**, then Save. The published site will be:
`https://wadietaghzouti20-dot.github.io/beauty-salons-/`

## Before accepting real bookings
1. Confirm the Apps Script deployment is accessible to anyone who needs to submit a booking.
2. Test service loading, available slots, a test booking, email delivery, Calendar event creation and cancellation.
3. Replace the generic salon name and default service/staff/hours in the backend sheet with the actual salon's details.
4. Confirm the browser can read Apps Script responses (CORS). Do not use `no-cors`: it hides the response and prevents reliable confirmation.
5. This page does not collect online payments. Booking requests are not final confirmations unless the salon confirms them.

Timezone: Africa/Algiers.
