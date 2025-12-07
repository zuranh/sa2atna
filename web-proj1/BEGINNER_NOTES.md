# Beginner notes for location features

If you want the project to feel beginner-friendly, keep the geocoding setup simple and avoid UI pieces that look too advanced.

## Is Google Geocoding complicated?

Google's Geocoding API is straightforward but does require an API key and billing account. For a beginner-ready setup, expect these steps:

1. Create a free Google Cloud project and enable the **Geocoding API**.
2. Make an API key and restrict it to HTTP referrers or specific domains so it cannot be abused.
3. Call the endpoint from your server (not the browser) to keep the key secret, e.g. `https://maps.googleapis.com/maps/api/geocode/json?address=...&key=YOUR_KEY`.
4. Cache the returned `lat`/`lng` with your events to avoid hitting rate limits and to skip repeated lookups.
5. Add basic error handling (bad addresses, quota errors) and a tiny debounce if you ever geocode user input.

If you want something with fewer setup steps and no billing card, you can start with OpenStreetMap's Nominatim API. It is free but rate-limited, so you should still cache results server-side.

Keep the UI basic: a single text box for the address and a short helper line like "Enter a city or street address" is enough. You can add fancy maps or distance filters later when you're ready.
