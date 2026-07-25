# Paddocks Hotel — Website

A faithful static copy of the Paddocks Hotel site (Ross-on-Wye), copied from the
temporary sub-domain `paddock.frog4u.com`. Pure HTML/CSS/JS + images — no build
step, no database. It can be hosted on any web server (Plesk, Apache, Nginx, etc.).

## Pages

| Page          | File                 |
|---------------|----------------------|
| Home          | `index.html`         |
| King Room     | `king-room.html`     |
| Double Room   | `double-room.html`   |
| Family Room   | `family-room.html`   |
| Twin Room     | `twin-room.html`     |
| Single Room   | `single-room.html`   |
| Weddings      | `weddings.html`      |
| Celebrations  | `celebrations.html`  |
| Dance         | `dance.html`         |
| Meeting Room  | `meeting-room.html`  |
| Bar           | `bar.html`           |
| Contact Us    | `contact.html`       |

All assets live under `wp-content/` and `wp-includes/` (kept as-is from the original).

## Address (used for the contact-page map)

**The Paddocks Hotel**, Wye View Ln, Symonds Yat West, Ross-on-Wye HR9 6BL — Tel: 01600 890 246

## Preview locally

```bash
python3 -m http.server 4188
# then open http://localhost:4188
```

## Auto-deploy to Plesk (every update goes live automatically)

Deployment is handled by GitHub Actions (`.github/workflows/deploy.yml`). Every push
to the `main` branch uploads the site to your Plesk server over secure FTP.

### One-time setup

1. Create a GitHub repo and push this folder to it (`main` branch).
2. In your Plesk panel, get / create FTP credentials for the hotel domain
   (Websites & Domains → the domain → FTP Access).
3. In the GitHub repo: **Settings → Secrets and variables → Actions → New repository secret**,
   and add these three secrets:
   - `FTP_HOST` — e.g. `ftp.paddockshotel.com` (or the server IP Plesk shows)
   - `FTP_USERNAME` — the Plesk FTP username
   - `FTP_PASSWORD` — the Plesk FTP password
4. Confirm the web root in `deploy.yml` (`server-dir: ./httpdocs/`) matches your
   Plesk document root. Most Plesk sites use `httpdocs`; some use `httpdocs/<domain>`.

After that, any change I (Claude) commit and push will publish to the live site
within a minute — no manual upload needed.
