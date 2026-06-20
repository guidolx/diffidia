# Publishing the DIFFIDIA mock to GitHub Pages

The deployable site is the `site/` folder:

```
site/
├── index.html     ← landing page (site root)
├── console.html   ← interactive console mock
├── slide.html     ← product slide
└── .nojekyll      ← (optional) tells Pages to skip Jekyll
```

All files are self-contained (no build step, no dependencies). Once published, the site will be at:

```
https://<your-username>.github.io/diffidia/
```

---

## Option A — github.com, no command line

1. Go to https://github.com/new → **Repository name:** `diffidia` → **Public** → *do not* add a README → **Create repository**.
2. On the empty repo page, click **uploading an existing file**.
3. Drag in the files from this `site/` folder: `index.html`, `console.html`, `slide.html` (and `.nojekyll` if visible — it's optional).
4. Click **Commit changes**.
5. Go to **Settings → Pages**. Under **Build and deployment → Source**, choose **Deploy from a branch**; set branch to **main** and folder to **/ (root)**; **Save**.
6. Wait ~1 minute, then open `https://<your-username>.github.io/diffidia/`.

> Tip: you can upload `DIFFIDIA-site.zip` after extracting it, or just drag the files straight from this folder — GitHub's web uploader does **not** auto-extract zips.

---

## Option B — command line (git)

Run from inside this `site/` folder. Replace `<your-username>`.

```bash
git init -b main
git add .
git commit -m "Publish DIFFIDIA mock"
git remote add origin https://github.com/<your-username>/diffidia.git
git push -u origin main
```

Then enable Pages once (needs the GitHub CLI `gh`, authenticated):

```bash
gh api -X POST repos/<your-username>/diffidia/pages -f "source[branch]=main" -f "source[path]=/"
```

…or just turn it on via **Settings → Pages** as in step 5 above.

---

## Notes
- This is a prototype/mock for demonstration — the landing page states so.
- To publish at the root (`<your-username>.github.io`) instead of a project path, name the repo `<your-username>.github.io` and use the same steps.
