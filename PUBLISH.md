# Publishing this repository

This folder is already a git repository with one commit on the `main` branch.
Nothing needs to be built. Publishing is two steps.

## 1. Create the repository on GitHub

Option A, GitHub CLI (if you have `gh` installed and signed in):

    cd keepingnewportsafe
    gh repo create keepingnewportsafe --public --source=. --remote=origin --push

That creates the repo and pushes in one command. Use `--private` instead of
`--public` if you want it private; Netlify can deploy from a private repo.

Option B, GitHub website:

1. Go to https://github.com/new
2. Repository name: `keepingnewportsafe`
3. Do NOT check "Add a README", "Add .gitignore", or "Choose a license".
   The repo already contains these files and initializing them on GitHub will
   cause a push conflict.
4. Create the repository, then run:

        cd keepingnewportsafe
        git remote add origin https://github.com/YOUR-USERNAME/keepingnewportsafe.git
        git push -u origin main

## 2. Connect Netlify

1. Netlify dashboard, Add new site, Import an existing project.
2. Choose GitHub and select `keepingnewportsafe`.
3. Build command: leave blank. Publish directory: `.` (already set in
   `netlify.toml`, so Netlify should fill this in automatically).
4. Deploy.

Then set the custom domain to keepingnewportsafe.com under Domain management.

## After the first deploy

- Confirm the comment form appears under Forms in the Netlify dashboard as
  `council-comments`. It is detected automatically from the `data-netlify`
  attribute in `index.html`; no configuration is needed.
- Add a form notification (Forms, Form notifications) so submissions email
  someone at the Association.
- Submit one test comment yourself to confirm the flow lands on `thanks.html`
  and the entry appears in the dashboard.

## Updating the site later

    git add -A
    git commit -m "Describe the change"
    git push

Netlify redeploys automatically on every push to `main`.

## Before promoting the site

See the PRE-PUBLISH CHECKLIST in `README.md`. The open items are the SMS
consent and privacy policy review, the campaign disclosure review, the
July 28 2026 resolution number, the Teamsters quotation, and the measured
Station 5 driving distance to the Spyglass area.
