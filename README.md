# SHPE Purdue website

Static site (`index.html`) + a small Google Apps Script API (`Code.gs`) that reads the chapter's Google Sheet.

## How it fits together
- **Content** lives in the Google Sheet "SHPE Purdue - Datos" (tabs: Eboard, Sponsors, Alumni, Highlights, optional Niveles and Contenido).
- **Highlights tab** columns: Titulo, Tipo (Company Event / Social Event / Service Event / Coffee Break), Semestre (e.g. Fall 2026), Descripcion, Foto (file name in the images folder; if empty, a file named like the Titulo), Empresa (matches a sponsor Nombre to show its logo), Destacado (`si` = big featured card). Newest semester first.
- **Sponsors page** shows a names belt (links to each sponsor's Sitio) built from the Sponsors tab; "Coming Soon" rows are skipped.
- **Home page intro** is a scroll-driven sequence in `index.html` (search for `Secuencia de bienvenida`): Welcome with the SHPE symbol drawing in, a map of Latin America whose dots merge into Indiana (it plays by itself once scrolled to), and four numbers (events in the latest Highlights semester, sponsors, officers in history, current E-Board size). **Alumni page** starts with a 1986-to-today counter that shows each president (from the Alumni tab, plus the current President from Eboard); it needs Year in the form "2000-2001" and Cargo "President". Nothing here needs extra Sheet columns. To list a country's dot, edit `SQ_DOTS`. People who prefer reduced motion get a static version, and both intros have a skip link.
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
