# SHPE Purdue website

Static site (`index.html`) + a small Google Apps Script API (`Code.gs`) that reads the chapter's Google Sheet.

## How it fits together
- **Content** lives in the Google Sheet "SHPE Purdue - Datos" (tabs: Eboard, Sponsors, Alumni, optional Niveles and Contenido).
- **Images** live in the Drive folder "SHPE Web - Imagenes" (shared as "anyone with the link can view").
  Name each file after the person (`First Last`), the company (`Company Name`), or `logo-shpe` / `logo-purdue`.
- **Apps Script** (`Code.gs`, owned by the SHPE Google account) returns the Sheet as JSON.
  Deployed as a Web app: Execute as *Me*, access *Anyone*.
- **Website** (`index.html`) is hosted on Cloudflare Pages and calls the Apps Script URL set in `API_URL` at the top of the file.

## Updating content (no code)
Edit the Sheet or add images to the Drive folder. Changes show up on the site within about 10 minutes.
To see a change immediately, run `limpiarCache` in the Apps Script editor.

## Changing code
- Apps Script: after editing `Code.gs`, go to Deploy > Manage deployments > edit > **New version**.
- Website: commit `index.html` to the GitHub repo; Cloudflare Pages publishes it automatically.

## Handoff checklist (every year)
- [ ] The Google account, GitHub organization, Cloudflare account and domain registrar belong to the chapter (shared email), not to one person.
- [ ] A new webmaster is added as editor to the Sheet, the Apps Script project, the Drive folder and the GitHub repository.
- [ ] The domain's auto-renewal is on and the payment method is current.
