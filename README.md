# AI Acceleration Program: immersive presentation

A single-page, 3D walkthrough of the AI Acceleration Program proposal for the executive team.
It runs in the browser (Three.js, loaded from a CDN) and contains no organisation or personal names; roles only.

## Structure

```
public/index.html              the whole presentation (HTML, CSS, JS in one file)
vercel.json                    static hosting config + noindex headers
.github/workflows/deploy.yml   CI: preview deploys on PRs, production on main
```

## Presenting

Open the deployed URL in Edge or Chrome. Controls: ← → or Space to move, 1–9 to jump,
N narration, H hide panel, F full screen. Best narration voices: Edge, "Online (Natural)" en-AU voices.

Run locally: `npx serve public` (or open `public/index.html` directly).

## Deployment setup (one-off)

1. In Vercel, create a project for this repository (framework preset: **Other**, no build command).
   Turn off Vercel's automatic Git deployments for it if you want this workflow to be the only deploy path
   (Project Settings → Git), or skip the workflow and just use Vercel's Git integration.
2. Link it locally once to get the IDs: `npx vercel link`, then read `.vercel/project.json`
   for `orgId` and `projectId`.
3. Create a token at vercel.com/account/tokens.
4. Add GitHub repository secrets: `VERCEL_TOKEN`, `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID`.
5. Optional: add a repository variable `BLOCKED_TERMS` (a regex such as `name1|name2`)
   so the pipeline fails if an identifying term ever slips into the page.

## Access

The content is an internal proposal. Keep the repository private and turn on Vercel
Deployment Protection so the URL is not open to the public. The page also sends `noindex` headers.
