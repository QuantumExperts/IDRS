# International Dispute Resolution — website

A clean, monochrome, single-scroll landing site with one click-through enquiry page.
Concept: confident and restrained (Palantir-style), engineered to move visitors toward
a confidential enquiry. The splash makes no reference to any named individual or to
Expert Services International; those appear only on the enquiry page.

## Files

```
index.html        The splash / scrolling landing page
contact.html      The click-through enquiry page (names Neil Kirkpatrick, routes to ESI)
assets/favicon.svg
robots.txt
sitemap.xml
```

Everything is self-contained static HTML/CSS/JS. No build step, no dependencies
(fonts load from Google Fonts). It will run on any static host.

## Deploy options

**GitHub Pages** — push these files to the repo root, then Settings → Pages →
Deploy from branch → `main` / root.

**Netlify** — drag the `idrs-site` folder onto the Netlify dashboard, or connect the
GitHub repo. No build command needed; publish directory = the folder root.

**Cloudflare Pages** — Create project → connect the GitHub repo → Framework preset:
`None` → Build output directory: `/`.

## When you connect a domain

1. Search/replace `REPLACE-WITH-YOUR-DOMAIN` in `robots.txt` and `sitemap.xml`.
2. Update the `<link rel="canonical">` and `og:` URL in `index.html` to your real domain.
3. Point the domain's DNS at your host (Cloudflare Pages / Netlify give exact records).

## Enquiry form → ESI SharePoint register

`contact.html` has a confidential enquiry form that feeds **Expert Services
International's existing SharePoint enquiry register** — IDRS does not run a separate
inbox. Paste ESI's existing Power Automate **"When an HTTP request is received"** trigger
URL into the `ENQUIRY_ENDPOINT` constant in the `<script>` at the bottom of
`contact.html`.

Submissions POST this JSON:
`{ name, organisation, email, matter, submittedAt, source:"IDRS",
origin:"International Dispute Resolution Services", operatedBy:"Expert Services International" }`
— so each one lands in the ESI register clearly tagged as an IDRS enquiry.

Until an endpoint is set, the form validates and confirms but does not send (the payload
is logged to the browser console for testing).

## Operator credit

Both pages carry a discreet footer line — *"Managed & operated by Expert Services
International"* — linking to expertservices.international, so the operating relationship
is transparent without appearing in the splash narrative.

## Easy things to change

- **Copy** — headline is in the `.hero h1` of `index.html`; capabilities are the
  five `.row` blocks; the confidential attribution line is the `.trail` paragraph in
  `contact.html`.
- **Accent** — the site is deliberately pure monochrome. All colour is defined in the
  `:root` variables at the top of each file.
