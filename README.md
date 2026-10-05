# Electrical panel site

The published map of one electrical panel, made with [epanel](https://github.com/swchck/epanel). A QR code on the panel door opens this site: it asks for the password, or opens the panel right away when the password comes in the link.

This repository holds a single file, `panel.enc.json`: the panel, the floor plan, photos and documents, encrypted with AES-256-GCM. Without the password it is unreadable, so the repository can stay public.

## Editing

The site only shows the panel. Edit it in the [epanel desktop app](https://github.com/swchck/epanel/releases/latest): open the editor, sign in with GitHub in **Save & publish**, pick this repository and press **Publish**. GitHub rebuilds the site in a minute or two.

## How the site is built

On every push, the workflow in `.github/workflows/pages.yml` checks out the epanel app, builds its viewer with this repository's `panel.enc.json` inside, and deploys it to GitHub Pages. The viewer has no landing page, no demo and no editor.

Optional settings in **Settings → Secrets and variables → Actions**:

| Name | Kind | What for |
|---|---|---|
| `PANEL_PASSWORD` | secret | Lets the build check the panel data itself, not only the file format |
| `EPANEL_REF` | variable | Builds the viewer from a tag or branch of the app instead of `main` |
| `EPANEL_REPO` | variable | Builds the viewer from a fork of the app instead of `swchck/epanel` |
