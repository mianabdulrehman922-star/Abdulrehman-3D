# Abdulrehman | 3D Developer Portfolio

A premium, dark, 3D portfolio for Abdulrehman, Frontend Web Developer based in Faisalabad, Pakistan.

Built with React, Vite, Three.js, GSAP and Lucide icons. No paid APIs or services are used.

---

## Features

- **Hero** with an interactive Three.js laptop, floating technology labels, a particle field and pointer-driven camera movement
- **About** with a CSS 3D orbit illustration
- **Skills** in animated, grouped cards
- **Projects** with filtering by category, a featured project, 3D tilt cards and live demo links
- **Services**, **Experience** timeline, **Work Process** and **Why Work With Me**
- **Contact** form with validation, honeypot protection, success and error messages, a mailto fallback, and WhatsApp and email buttons
- **Responsive** layouts, mobile navigation, sticky navbar, active-section highlighting and smooth scrolling
- **Accessibility**: semantic HTML, skip link, ARIA labels, visible focus states, reduced-motion support
- **Performance**: lighter 3D scene on mobile, rendering paused when off-screen or in a hidden tab, full cleanup of WebGL resources, code splitting for three, gsap and react
- **SEO**: title, meta description, Open Graph, JSON-LD Person schema, favicon, `robots.txt` and `sitemap.xml`

---

## Project structure

```
abdulrehman-3d-portfolio/
  public/
    favicon/favicon.svg
    resume/README.md          <- place Abdulrehman-Resume.pdf here
    images/                   <- add real project screenshots here
    robots.txt
    sitemap.xml
  src/
    components/               <- reusable UI (Navbar, Footer, ProjectCard, ...)
    sections/                 <- one file per page section
    three/heroScene.js        <- Three.js hero scene (no React wrapper needed)
    hooks/                    <- useMediaQuery, useActiveSection, useScrollReveal
    data/                     <- all content: profile, projects, skills, services, ...
    styles/global.css
    utils/contact.js          <- form validation and mailto builder
    App.jsx
    main.jsx
  index.html
  package.json
  vite.config.js
  README.md
```

**Most edits happen in `src/data/`.** You do not need to touch the components to change text, links, projects or services.

---

## Run locally

Requirements: Node.js 18 or newer and npm.

```bash
cd abdulrehman-3d-portfolio
npm install
npm run dev          # http://localhost:5173
```

Production build and preview:

```bash
npm run build        # outputs to dist/
npm run preview      # serves dist/ at http://localhost:4173
```

---

## Things to complete before going live

| Item | Where | Notes |
|---|---|---|
| Resume PDF | `public/resume/Abdulrehman-Resume.pdf` | Download buttons point here. Until the file exists, the link returns a 404. |
| Domain in SEO tags | `index.html`, `public/robots.txt`, `public/sitemap.xml` | Replace `YOUR-DOMAIN-HERE` after deployment. |
| LinkedIn and GitHub profile URLs | `src/data/profile.js` → `socials` | Left empty on purpose. Paste the full URLs to activate them. |
| Project descriptions | `src/data/projects.js` | Currently neutral placeholders. Replace them with verified descriptions of each project's features. |
| Project tags | `src/data/projects.js` → `tags` | Tags are inferred from each category and hosting URL. Check them. |
| Project screenshots | `src/components/ProjectThumb.jsx` | Cards use original placeholder visuals, not screenshots. To use real images, capture screenshots and render an `<img>` in place of the placeholder, with alt text. |
| GitHub repository links | `src/data/projects.js` → `repoUrl` | Set each project's repository URL to show a GitHub button. Leave `null` otherwise. |
| Dispatch Mailing Assistant and Prime Pass details | `src/data/journey.js` | Brief entries only. Add verified details if you want them shown. |
| Contact form backend | `src/sections/Contact.jsx` | No backend is configured. The form opens the visitor's email app with the message filled in. See below for connecting a real service. |

### Connecting a real contact service later

The form currently calls `buildMailto()` in `src/utils/contact.js`. To send messages through a service such as Formspree, Web3Forms or your own API endpoint:

1. Replace the `window.location.href = href` call in `handleSubmit` (in `src/sections/Contact.jsx`) with a `fetch` POST to your endpoint.
2. Keep the existing validation, and show the success or error message based on the response.
3. Store any API key as an environment variable (`import.meta.env.VITE_...`) in the hosting dashboard. Never commit keys to the repository.

---

## Deploy on Vercel

1. Push the project to a GitHub repository.
2. In Vercel, choose **Add New → Project** and import the repository.
3. Vercel detects Vite automatically. Confirm these settings:
   - Build command: `npm run build`
   - Output directory: `dist`
4. Click **Deploy**. Then update the domain placeholders in `index.html`, `robots.txt` and `sitemap.xml`.

## Deploy on GitHub Pages

The `base: './'` setting in `vite.config.js` lets the build run from a sub-path.

Option A, using the `gh-pages` package:

```bash
npm install --save-dev gh-pages
```

Add these scripts to `package.json`:

```json
"predeploy": "npm run build",
"deploy": "gh-pages -d dist"
```

Then run:

```bash
npm run deploy
```

In the repository settings, set **Pages → Source** to the `gh-pages` branch.

Option B: build locally with `npm run build` and upload the contents of `dist/` through the repository's Pages settings or a GitHub Actions workflow.

---

## Verification status

The code was written without the ability to run `npm install` in the environment where it was produced. Before deploying, run through this checklist yourself:

- [ ] `npm install` and `npm run build` complete without errors
- [ ] `npm run dev` runs and the hero 3D scene renders
- [ ] Every navigation link scrolls to the correct section
- [ ] All five project "Live Demo" links open
- [ ] Filter buttons show the right projects
- [ ] Contact form shows validation messages and opens the email app when valid
- [ ] WhatsApp button opens `wa.me/923079657528`
- [ ] Layout checked at phone width (around 390px) with no horizontal scrolling
- [ ] Resume download works once the PDF is in place
- [ ] Reduced motion (OS setting) turns off the animations

---

## Credits and licences

Libraries used: React (MIT), Vite (MIT), Three.js (MIT), GSAP (free, including commercial use), Lucide (ISC). Fonts: Inter, Space Grotesk and JetBrains Mono from Google Fonts (SIL Open Font License).
