# Where to host the docs

The whole site is **one folder**: `index.html` plus `assets/`. No build step, no framework, no
account to sign up for. Everything is inline — styles, the nav script, the lot.

That is deliberate. The plugin itself has no build step, and **a docs site that needs npm to publish
a typo fix is a docs site that stops getting typo fixes.**

Open `index.html` in a browser right now to see it.

---

## ⭐ Recommended: GitHub Pages on the repo you already have

You already own `github.com/nkcourses/versionup-updates` and it is already public — it serves
`updates.json` to the panel. Adding docs to it costs nothing and adds no new account.

1. Put this `docs` folder into the repo, so you have `versionup-updates/docs/index.html`
2. Repo → **Settings → Pages**
3. Source: **Deploy from a branch** · Branch: **main** · Folder: **/docs**
4. Save. A minute later it is live at
   `https://nkcourses.github.io/versionup-updates/`

### Then put it on your own domain

`nkcourses.github.io/versionup-updates` is not a link you want to print. You own the domain, so use
a subdomain — the same shape as the site you liked.

1. In **Settings → Pages → Custom domain**, enter `docs.nkcourses.co.uk` and save. GitHub writes a
   `CNAME` file into the repo.
2. In **Squarespace → Settings → Domains → your domain → DNS**, add a **CNAME** record:
   host `docs`, pointing to `nkcourses.github.io`
3. Wait for it to verify, then tick **Enforce HTTPS**

Now it lives at `https://docs.nkcourses.co.uk` and costs nothing.

**Why this over the alternatives:** free, no build, no third party, and the docs sit in the same repo
as the release notes — so publishing an update and updating the docs is one commit rather than two
systems.

---

## The alternatives, honestly

### Squarespace, as a code block

You already pay for it, so it is tempting. But:

- Squarespace wraps everything in its own template — the sidebar navigation and sticky "on this
  page" behaviour will fight it
- every GIF has to be uploaded through the Squarespace file manager and the paths rewritten
- there is no search

**Worth it only if** you want the docs inside your site navigation and are willing to lose the
sidebar. If you go this way, paste the contents of `<body>` into a Code Block and upload the assets
via **Settings → Files**, then fix each `assets/…` path to the URL Squarespace gives you.

### Starlight / Astro — what docs.jakeinmotion.com uses

Genuinely the best tool for this: proper search, versioning, dark mode, multi-page. But it needs
Node, a build step and a deploy pipeline, and it is a lot of machinery for eleven sections.

**Worth it when** you have three or four products documented and the single page has become unwieldy.
Not before. The page you have now converts to Starlight easily — each `<h2>` becomes a markdown file.

### GitBook, Notion, Mintlify

All fine, all free tiers, all a third party between you and your customers who can change their
pricing. For a £9.99 plugin I would not add the dependency.

---

## Keeping it honest

🔴 **The facts on this page came from the panel, not from memory** — the menu labels, the
`Window > UXP Plugins` path, the 25.6 minimum. They are listed in a comment at the top of
`index.html`. **If you rename a menu item, this page is wrong and nothing will tell you.**

The same trap the install PDF has. Worth a skim of both whenever the panel's wording changes.

## Link it from three places

Docs nobody can find are docs nobody reads:

1. **The product page** — under the buy button, "Full documentation"
2. **The receipt email** — beside the install guide
3. **The panel itself** — worth adding a "Help" item to the ☰ menu that opens the docs URL.
   `shell.openExternal` already works for `https` and the About link proves it.
