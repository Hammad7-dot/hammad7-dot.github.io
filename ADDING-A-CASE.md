# How to add the next case study

For `hammad7-dot.github.io`. Static HTML, no build step — adding a case is copy, edit, commit. Budget: ~45 minutes if the notes exist, plus however long the writing takes.

## The shape every case uses (don't invent a new one)

Three beats, in this order, as `<div class="case-block">` sections:

1. **The problem** — what was actually hard or annoying, in plain language. No "in today's fast-paced world."
2. **What I did** — the build, the stack, and the decisions I made and why. This is where a demo GIF goes.
3. **What came of it** — what works, what it proves. Then an honest gap block if anything isn't live yet.

Optional extra blocks between 2 and 3 when the project earns them: a "fixing it for real" block (the bug rounds), a "how it's built" block (the actual flow, no mystery code). `case-docket.html` has all four — use it as the template.

Standing rules: real screenshots only, no mockups. If it isn't deployed, say so in a `<div class="gap-note">` instead of implying it is. Write it the way I'd explain it to a person, not the way a job board would.

## Steps

**0. Dump raw notes first (10 min, no editing).** Project name, repo URL, stack, what broke and how I fixed it, what actually runs today, what doesn't. Five to eight bullets is enough — the draft comes from these, so don't skip straight to writing prose.

**1. Draft in the Claude Project.** Open the portfolio Claude Project (it already holds my voice, stack, and identity kit). Paste the raw notes and ask for a case study in the three-beat shape, matching `case-docket.html`. Do not start a fresh chat — that's a rebuild, this is a conversation.

**2. Create the page.** `cp case-docket.html case-<slug>.html`, then replace, in order:
- `<title>`, `<meta name="description">`
- `<link rel="canonical">`, all `og:*` and `twitter:*` tags (title, description, url — 7 URLs and titles total, easy to miss one)
- `<p class="eyebrow">Case 0N · <theme></p>` and the `<h1>`
- `.case-meta` — Stack / Role / repo link
- the `case-block` sections and the `gap-note`

**3. Add the card to `work.html`.** Copy an existing `<a class="card">` block inside `<div class="grid">`, at the end. Update `href`, `id`, the poster image, `card-tag` ("Case 0N · <theme>"), `<h3>`, and the one-line summary. Update the `<h1>` count — it currently says "Five builds"; it becomes "Six builds" with the next one.

**4. Wire `case-nav` both ways.** The newest case page always had no "Next" link, so:
- add `<a href="case-<slug>.html">Next: <Name> →</a>` to the previously-last case page (currently `case-docket.html`)
- give the new page `<a href="case-<previous-slug>.html">← <Previous Name></a>` and leave it without a Next until the case after it exists

**5. Assets.** Screenshots and GIFs go in `assets/img/` as `<slug>-demo.gif` plus a `<slug>-demo-poster.jpg` for the work.html card. Keep GIFs under a few MB.

**6. Check, commit, push.** `python -m http.server` from the repo root, open the new page and `work.html`, click every nav link including the new "Next". Then:

```
git add case-<slug>.html work.html case-<previous-slug>.html assets/img/
git commit -m "Add <Name> case study"
git push
```

GitHub Pages redeploys in a minute or two. Load the live URL and confirm the case renders and the card links.

## Next piece of work

**Universal AI Conversation Memory → Obsidian** — case 06. Reminder set: Google Calendar, **Sat 13 Sep 2026, 10:00 PKT**, with the steps above in the event description and popup reminders a day and an hour ahead.

After it ships, name the one after that on the same day and move the reminder forward. The habit is the point — a portfolio with one case is a class assignment; a portfolio that grows is a track record.
