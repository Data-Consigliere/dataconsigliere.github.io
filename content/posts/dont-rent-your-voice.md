---
title: "Don't Rent Your Voice"
date: 2026-02-22T11:30:00Z
draft: false
description: "Your voice on someone else's terms is just borrowed time."
tags: ["Meta", "Opinion"]
categories: ["Learning in Public"]
cover:
  image: "/images/Laptop.jpg"
  alt: "White desk with laptop, earbuds, smartphone and notebook — a minimal personal workspace"
  caption: "A workspace you own. A voice you keep."
  relative: false
  hiddenInList: false
  hiddenInSingle: false
---

Rented platforms are fast and tempting: you pour your best thinking into them, they amplify it while it suits them — and then, one day, without warning or apology, they change the algorithm, change the rules, throttle your reach, or just shut the door.

*Medium* paywalls your readers. *Substack* pivots its model. *LinkedIn* quietly decides your content may compete with theirs.

No beef with any of them. I just **don't want to rent my voice**.

---

## Built from Scratch. Or Control Over Convenience

When I started thinking about building a digital presence, the advice was immediate and unanimous:

> *"Use something off the shelf. Don't waste time on infrastructure."*

Solid advice. And exactly why it bothered me.

I've worked in data for decades. I've seen this movie too many times: an organization builds critical workflows on systems it doesn't own, and before long it's locked in. Paying rent. Moving slow. And when it finally tries to leave, the migration cost is the real tax — no receipt included.

Not doing that with my own thinking.

---

## Choosing the Stack

*Minimalism as a lifestyle.*

The decision came fast: **GitHub Pages + Hugo + PaperMod**

- **GitHub Pages** serves static files for free, with HTTPS and global redundancy. Infrastructure that's basically invisible — exactly how it should be.
- **Hugo** is written in Go and builds a site with hundreds of posts in under a second. No database. No server babysitting. No *"we need to patch this Friday night at 11pm."* It's a binary. It works. *(Yes, it's almost offensively simple — that's the point.)*
- **PaperMod** is a theme that respects the reader. Clean, fast, excellent dark mode. No carousels. No pop-ups. No dark patterns grabbing for your attention like a toddler in a toy store. The writing is the product.

The workflow:

> *Markdown file in VS Code → git push → live in seconds*

*Docs as Code* applied to personal thinking.

---

## From Thinking to Doing

*Step by step. No journey. No violins.*

### 1. The Repository (GitHub)

Created a public GitHub repo using the `username.github.io` convention. This matters: it's how GitHub Pages knows where your site root lives. Then, straight to the terminal:

```bash
git clone https://github.com/data-consigliere/data-consigliere.github.io.git
```

### 2. The Engine (Hugo)

Install Hugo on Windows the clean way — Winget, no *"next, next, finish"* wizard:

```bash
winget install Hugo.Hugo.Extended
```

> **Note:** The **Extended** version matters — it handles SCSS processing, which themes like PaperMod require.

Verify it landed:

```bash
hugo version
```

Then scaffold the site inside the repo folder:

```bash
hugo new site . --force
```

The `--force` flag was needed because the folder already had a `.git` directory. Output: the standard folder structure — `content/`, `layouts/`, `static/` — and the essential `config.yaml`.

### 3. The Aesthetics (PaperMod)

A technical blog needs to be readable, not pretty. I wasn't about to hand-roll HTML and CSS from scratch. PaperMod installed as a Git submodule — cleaner updates, no drama:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
```

Then declare it in `config.yaml`:

```yaml
theme: "PaperMod"
```

### 4. Structure and Content

Because a site without pages is just a domain name with ambitions.

| File | Purpose |
|------|---------|
| `content/_index.md` | Homepage and intro |
| `content/about/index.md` | Background and project context |
| `content/start-here/index.md` | Front door for first-time visitors: what this is, who it's for, where to start |

Navigation wired up in `config.yaml`, mapping labels to URLs.

### 5. The Personal Touch (CSS)

PaperMod is great out of the box, but I wanted something closer to a classic editorial feel — serif body text, sans-serif headers. Created:

```text
assets/css/extended/custom.css
```

Hugo and PaperMod auto-merge anything in that `extended/` folder — no hacks, no aggressive overrides. That's where I set typography (Georgia for reading, Inter for headers) and capped content width for comfortable line lengths. Readability over real estate.

---

## Resources I Used

These are the things that actually helped — not the endless rabbit holes, not the "10‑step ultimate guides," just the resources that moved the needle.

### 🧱 Core Documentation

- [Hugo Quick Start](https://gohugo.io/getting-started/quick-start/) — The official docs. Clear, fast, and shockingly better than most "framework" documentation.
- [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki) — The theme looks simple, but the wiki reveals how much control you actually have.
- [GitHub Pages Documentation](https://docs.github.com/en/pages) — Straightforward, predictable, and exactly what you need when deploying.
- [Popular Hugo Themes](https://themes.gohugo.io/tags/popular/) — Useful for exploring alternatives and understanding how other themes structure layouts.

### 🎥 Video Tutorials (The Ones That Didn't Waste My Time)

- [Hugo + GitHub Pages Tutorial](https://www.youtube.com/watch?v=LIFvgrRxdt4) — The video that made me realize this was an afternoon project, not a week‑long ordeal.
- [How to Host a Website on GitHub Pages](https://www.youtube.com/watch?v=OltY8JIaP-4) — A clean walkthrough of the GitHub Pages flow, no fluff.
- [How to Use GitHub Pages in 2026 (Beginner's Guide)](https://www.youtube.com/watch?v=5XhxR9Vs6zc) — Updated, beginner‑friendly, and good for validating that nothing major changed.
- [How to Create a Free Website Using GitHub Pages](https://www.youtube.com/watch?v=o5g-lUuFgpg) — Another solid perspective on the Pages workflow; helpful if you like seeing multiple approaches.
- [Hugo Actually Explained — Websites, Themes, Layouts, Scripting](https://www.youtube.com/watch?v=ZFL09qhKi5I) — The best conceptual explanation of how Hugo thinks. Great for avoiding future confusion.
- [Getting Started With Hugo — Free Course](https://www.youtube.com/watch?v=hjD9jTi_DQ4) — A full, structured intro if you want to go deeper than "just enough to ship."

### 📝 Markdown & Writing Helpers

- [Markdown Cheatsheet](https://github.com/im-luka/markdown-cheatsheet) — Minimal, readable, and perfect when you forget the syntax for that one thing you use once a month.

---

## What the Machines Don't Tell You (and Neither Do the Humans)

Deployment was the classic humility check.
Good news: the problems were dumb.
Bad news: dumb problems are still annoying.

**Case sensitivity is real — and it will get you.**
On Windows, `About.jpg` and `about.jpg` are the same file. On GitHub's Linux servers, they're not. My 404 rabbit hole had a laughably simple root cause: inconsistent capitalization. The lesson isn't technical — it's about never assuming your dev environment matches production.
*Rule I kept: lowercase everything, always.*

**GitHub Pages "wants to help." Decline politely.**
By default, it tries to process your site with Jekyll — its own static generator. On a Hugo site, this is a silent disaster. The fix? An empty file named `.nojekyll` in the repo root.

*One. Empty. File.* Changes everything. There's a metaphor about organizational bureaucracy here, but I'll save it for another post.

**Maximum security means maximum friction.**
Hugo can generate cryptographic hashes of your CSS (fingerprinting) as a security measure. If the file changes during upload — even one byte — the browser blocks it, no explanation offered.

I turned off fingerprinting. Learned (again) that security and pragmatism don't coexist without conscious negotiation.

**Markdown has tricks worth knowing.** Small conventions that add up:

- `---` to break sections and let the text breathe
- `> Note` for callouts and context
- Backticks for filenames and inline commands — `config.yaml`, `.nojekyll`, `custom.css`
- **Bold** to guide the reader's eye without shouting

---

## Solid Foundation. Now the Real Work Starts.

There's something genuinely satisfying about watching a system you built go live — accessible to anyone, anywhere, served from a repo that's yours.

The site's up. The workflow runs. The voice is taking shape.

What comes next is what actually matters: *stop talking about the tool and use the tool to talk about what's worth talking about* — data, decisions, architectures, and the choices that separate systems that serve you from systems that own you.

**We're just getting started.**

---

*The Data Consigliere publishes at [data-consigliere.github.io](https://data-consigliere.github.io). No algorithm to appease. No engagement metrics to chase. Just structured thinking, shipped consistently.*
