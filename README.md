# EVEMAILER

Bulk evemail sender for EVE Online. Paste in a list of character names, write your mail, and send it off. Useful for alliance pings, corp recruitment, fleet notifications, etc.

Live at **[evemailer.connorjc.io](https://evemailer.connorjc.io)**

## How it works

Single static page, no backend. Authenticates directly with EVE SSO using the OAuth2 PKCE flow and sends mail through ESI. Everything runs in your browser.

- Resolves character names to IDs via ESI
- Sends mail one at a time with a 15s delay to stay under rate limits
- Handles token refresh, retries on transient errors, and ESI error budget tracking
- Templates saved to localStorage so you can reuse common mails

## Setup (self-hosting)

1. Register an application at [developers.eveonline.com](https://developers.eveonline.com/) with the `esi-mail.send_mail.v1` scope
2. Set the callback URL to wherever you're hosting the page
3. Replace the `CLIENT_ID` constant at the top of the script in `index.html` with your application's client ID
4. Serve `index.html` and `mail.webp` from any static host (GitHub Pages, nginx, whatever)

## License

MIT
