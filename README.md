# AI engineering portfolio

Static React + TypeScript + Vite portfolio, styled with Tailwind CSS and custom CSS. No runtime API calls, backend, external fonts, or animation library.

## Setup

Use Node.js 22 or newer. From this directory:

```sh
npm install
npm run dev
npm run check
npm run build
npm run preview
```

## Edit content

All personal information, projects, experience, and technology entries live in `src/data/portfolio.ts`. Fill in the TODO name, personal GitHub URL, email, and Telegram URL. Missing contact links display honest TODO labels. The GitHub button falls back to the organization until a personal profile is supplied. Update the generic title and social metadata in `index.html` after entering your name. Add your final canonical URL and Open Graph image once hosting is known.

## GitHub Pages

Push **the contents of this directory** as the root of your portfolio repository. The included `.github/workflows/deploy.yml` assumes this layout. In Settings → Pages, select GitHub Actions. Push to `main` or run the workflow manually. The Pages configuration supplies the base path for both project URLs and user/organization sites.

For a custom domain, configure it in repository Pages settings, add the appropriate DNS records, and set repository Actions variable `VITE_BASE_PATH` to `/`. A project path can be explicitly set to `/repository-name/`. Locally, set environment variable `VITE_BASE_PATH` before building to test a subpath. Do not put secrets in Vite variables.

This workspace keeps the portfolio isolated to preserve the pre-existing Python project. If keeping this nested layout in a repository, move the workflow to the repository root and set npm working-directory, cache-dependency-path, and upload path to `portfolio` equivalents.

## Content evidence and limits

Inspected https://github.com/PrikoI/campuspulse-ai : its public README describes a Firestore-backed student/teacher LMS and API/MCP layer. The tree includes Python package, web, tests, docs, and dependency manifests. Source files, dependencies, contributors, screenshots, and commit details were not independently accessible/inspected. No personal authorship claim is made.

The GitHub public API was inaccessible from this environment; organization and all six supplied repository pages returned fetch failures. Their names appear as unverified organization references without invented descriptions or technology claims. Revisit these repositories before selecting featured organization work.

JARVIS, SocialBridge, hackathon participation, university background, and interests are based on information supplied by the owner. Experimental concepts are not presented as completed features. Project art is a conceptual CSS illustration, not a product screenshot. No awards or dates are invented.

## Accessibility and performance

Semantic landmarks, skip link, keyboard focus indicators, labelled mobile navigation, reduced-motion overrides, responsive grids, system fonts, and local SVG favicon. Static anchor navigation works without routing or SPA fallback. No secret files are needed or included in the portfolio. Review desktop/mobile rendering in a browser before publishing; automated builds do not replace visual inspection.

## Publication commands (PowerShell)

Git is initialized locally on `main`; no remote is configured. Create an empty GitHub repository without an initial README, license, or gitignore, then replace the URL below with the URL you provide:

```powershell
Set-Location 'C:\Users\Astan\OneDrive\PythonProject1\portfolio'
npm.cmd ci
npm.cmd run check
npm.cmd run build
git add .
git diff --cached --stat
git commit -m "Prepare AI engineering portfolio for GitHub Pages"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

In the GitHub repository, open Settings → Pages → Build and deployment → Source and choose GitHub Actions. Then open Actions → Deploy portfolio → Run workflow → main. This reruns deployment if the initial push occurred before Pages was enabled. The successful deployment exposes the live URL in the workflow's github-pages environment.

The workflow installs the committed lockfile using npm ci, checks TypeScript during the production build, uploads only dist, and deploys using the Pages OIDC token. No repository secrets are required. The configured Pages base path is normalized with a trailing slash for Vite asset URLs. Keep VITE_BASE_PATH unset for automatic project-path detection; set it to / when using a custom domain.
