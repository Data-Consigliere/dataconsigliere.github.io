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

### Built from Scratch. Or Control Over Convenience

Rented platforms are fast and tempting: you pour your best thinking into them, they amplify it while it suits them — and then, one day, without warning or apology, they change the algorithm, change the rules, throttle your reach, or just shut the door.

*Medium* paywalls your readers. *Substack* pivots its model. *LinkedIn* quietly decides your content may compete with theirs.

No beef with any of them. I just **don't want to rent my voice**.

---

## The *"Just Use a Platform"* Question

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

> *Markdown file in VS Code  →  git push  →  live in seconds*

*Docs as Code* applied to personal thinking.

---

## From Thinking to Doing
*Step by step. No journey. No violins.*

### 1. The Repository (Github)

Created a public GitHub repo using the `username.github.io` convention. This matters: it's how GitHub Pages knows where your site root lives. Then, straight to the terminal:

```bash
git clone https://github.com/data-consigliere/data-consigliere.github.io.git
```

<br>

### 2. The Engine (Hugo)

Install Hugo on Windows the clean way — Winget, no *"next, next, finish"* wizard:

```bash
winget install Hugo.Hugo.Extended
```

> The **Extended** version matters: it handles SCSS processing, which themes like PaperMod require.

Verify it landed:

```bash
hugo version
```

Then scaffold the site inside the repo folder:

```bash
hugo new site . --force
```

The `--force` flag was needed because the folder already had a `.git` directory. Output: the standard folder structure — `content`, `layouts`, `static` — and the essential `config.yaml`.

<br>

### 3. The Aesthetics (PaperMod)

A technical blog needs to be readable, not pretty. I wasn't about to hand-roll HTML and CSS from scratch. PaperMod installed as a Git submodule — cleaner updates, no drama:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
```

In `config.yaml`:

```yaml
theme: "PaperMod"
```

<br>

### 4. Structure and Content

Because a site without pages is just a domain name with ambitions.

| File | Purpose |
|------|---------|
| `content/_index.md` | Homepage and intro |
| `content/about/index.md` | Background and project context |
| `content/start-here/index.md` | Front door for first-time visitors: what this is, who it's for, where to start |

Navigation wired up in `config.yaml`, mapping labels to URLs.

<br>

### 5. The Personal Touch (CSS)

PaperMod is great out of the box, but I wanted something closer to a classic editorial feel — serif body text, sans-serif headers. Created:

```
assets/css/extended/custom.css
```

Hugo and PaperMod auto-merge anything in that `extended` folder — no hacks, no aggressive overrides. That's where I set typography (Georgia for reading, Inter for headers) and capped content width for comfortable line lengths. Readability over real estate.

---

### Resources I Used

- [Hugo Quick Start](https://gohugo.io/getting-started/quick-start/) — official docs, surprisingly good
- [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki) — more configurable than it looks
- [GitHub Pages Docs](https://docs.github.com/en/pages) — no surprises
- 🎥 [Hugo + GitHub Pages Tutorial](https://www.youtube.com/watch?v=LIFvgrRxdt4) — what convinced me this was an afternoon project, not a week-long one

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
- backticks for filenames and inline commands
- **bold** to guide the reader's eye without shouting.

---

## Solid foundation. Now the Real Work Starts.

There's something genuinely satisfying about watching a system you built go live — accessible to anyone, anywhere, served from a repo that's yours.

The site's up. The workflow runs. The voice is taking shape.

What comes next is what actually matters: *stop talking about the tool and use the tool to talk about what's worth talking about* — data, decisions, architectures, and the choices that separate systems that serve you from systems that own you.

If you're reading this, you got here early. **We're just getting started**. That's a good sign for you.

---

*The Data Consigliere publishes at [data-consigliere.github.io](https://data-consigliere.github.io). No algorithm to appease. No engagement metrics to chase. Just structured thinking, shipped consistently.*