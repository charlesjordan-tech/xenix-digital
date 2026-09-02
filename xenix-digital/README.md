# XENIX DIGITAL — Website

A static, multi-page website for XENIX DIGITAL, a digital solutions and creative media agency.

## Project structure

```
xenix-digital/
├── index.html          Home / welcome dashboard
├── about.html           About Us (mission, vision, values)
├── services.html         All 10 services
├── agency.html           Team / staff profiles
├── contact.html          Contact info + enquiry form
├── css/
│   └── style.css        All site styling (design tokens at the top)
├── js/
│   └── script.js        Mobile nav, scroll reveals, form handling
└── assets/
    ├── images/           General photos, video posters, portfolio stills
    ├── staff/             Team photos (staff-01.jpg, staff-02.jpg, ...)
    ├── videos/            Portfolio videos (project-01.mp4, ...)
    ├── icons/             Optional custom SVG icons (Font Awesome is used by default)
    └── logos/             favicon.svg and xenix-logo.svg
```

## Running it locally

No build step or server is required — it's plain HTML/CSS/JS.

- **Simplest:** double-click `index.html` to open it in a browser.
- **Recommended** (so relative paths and any future fetch calls behave exactly
  like a real server): serve the folder locally, e.g.
  - VS Code: install the "Live Server" extension, right-click `index.html` → *Open with Live Server*.
  - Python: `python3 -m http.server 8000` from inside the `xenix-digital` folder, then visit `http://localhost:8000`.
  - Node: `npx serve .`

## Replacing placeholder content

| What | Where | How |
|---|---|---|
| **Logo** | `assets/logos/` | Replace `favicon.svg` / `xenix-logo.svg`, or swap the inline `.signal-mark` bars in each page's header for an `<img>` tag pointing at your own logo file. |
| **Staff photos** | `assets/staff/` | Drop in `staff-01.jpg`, `staff-02.jpg`, etc. (same filenames referenced in `agency.html`), or add new files and update the `src` attributes. Edit names, roles, bios, skills and social links directly in `agency.html`. |
| **Portfolio videos** | `assets/videos/` | Add `project-01.mp4` (+ optional `.webm`) etc. The `<video>` tags in `index.html` already point at these paths. |
| **Images** | `assets/images/` | Add hero/about/portfolio images and update `src`/`poster` attributes where referenced. |
| **Social media links** | every page's footer, plus `contact.html` and `agency.html` | Find/replace `YOUR_FACEBOOK_LINK`, `YOUR_INSTAGRAM_LINK`, `YOUR_TIKTOK_LINK`, `YOUR_YOUTUBE_LINK`, `YOUR_LINKEDIN_LINK`, `YOUR_X_LINK` with real URLs. |
| **Phone number** | footer (all pages) + `contact.html` | Find/replace `YOUR_PHONE_NUMBER`. |
| **WhatsApp number** | `contact.html` | Find/replace `YOUR_WHATSAPP_NUMBER` (used in the `wa.me/` link and displayed text). |
| **Email** | footer (all pages) + `contact.html` | Find/replace `YOUR_EMAIL`. |
| **Location** | footer (all pages) + `contact.html` | Find/replace `YOUR_LOCATION`, and optionally embed a real Google Maps `<iframe>` in the `.map-embed` block on `contact.html`. |

A project-wide find/replace for `YOUR_` in your editor will surface every
placeholder that still needs a real value.

## Connecting the contact form

The form on `contact.html` (`#contact-form`) currently just shows a
confirmation message via `js/script.js` — there's no backend yet, since this
is a static site. To make it actually send messages, pick one:

1. **Formspree** — create a form at formspree.io, then set the form's
   `action` attribute to your Formspree endpoint and `method="POST"`.
2. **Netlify Forms** — if hosting on Netlify, add `data-netlify="true"` and a
   hidden `form-name` input to the `<form>` tag; Netlify handles the rest.
3. **Your own backend** — point `action` at your API endpoint (PHP, Node.js,
   etc.) and adjust `js/script.js` if you want an AJAX submission instead of
   a full page reload.

## Adding more staff members or services

- **Staff:** duplicate an existing `.staff-card` block in `agency.html` and
  edit its contents — the grid re-flows automatically.
- **Services:** duplicate a `.service-card` block in `services.html` (and,
  if desired, a `.card` block in the homepage's services preview).

## Design system

Brand colors, fonts and spacing are defined as CSS variables at the top of
`css/style.css` (`:root { ... }`) — change a value there and it updates
across every page.

## Icons

Icons are loaded live via the Font Awesome CDN (linked in every page's
`<head>`), so no local icon files are required for standard icons.
