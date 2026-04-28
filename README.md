# Gil Tal Personal Website — Deployment and Maintenance Guide

## Files in this package

- **index_v6.html** — the website. Rename to `index.html` before uploading.
- **profile.jpg** — your headshot (the brown fedora photo).
- **profile_alt.jpg** — alternate headshot (the professional blazer photo). If you prefer this one, rename it to `profile.jpg` before uploading.
- **cv.pdf** — you need to provide this. Put your latest CV in the repo with this exact filename.

---

## Part 1: One-time setup, deploy to GitHub Pages

You will do this exactly once. Plan for 20 minutes.

**Step 1.** Go to https://github.com and create a free account if you do not have one. Choose a username carefully because it appears in your URL. Suggestions: `giltal`, `giltalevc`, `giltalucdavis`. Avoid hyphens if possible.

**Step 2.** Click the green "New" button to create a new repository. Name it exactly: `yourusername.github.io`. So if your username is `giltal`, the repo name is `giltal.github.io`. Set it to Public. Do not initialize with a README.

**Step 3.** On the next page, click "uploading an existing file." Drag in three files: `index.html` (after renaming from `index_v6.html`), `profile.jpg`, and `cv.pdf`. Scroll down. Type "initial site" in the commit message box. Click "Commit changes."

**Step 4.** Click the "Settings" tab at the top of the repo. In the left sidebar, click "Pages." Under "Branch," select `main`. Click Save.

**Step 5.** Wait two to three minutes. Refresh the Settings/Pages page. You will see a green box with your live URL: `https://yourusername.github.io`. The site is live.

**Step 6.** Bookmark the URL. Add it to your email signature, faculty profile, LinkedIn, business cards, and the Wikipedia draft.

---

## Part 2: Routine updates

Every update follows the same pattern. Plan for 5 minutes per update.

### To add a news item to the home page

1. Go to your GitHub repo at `https://github.com/yourusername/yourusername.github.io`
2. Click `index.html` in the file list.
3. Click the pencil icon (top right) to edit.
4. Press Ctrl+F (or Cmd+F on Mac) and search for: `<div class="news-list">`
5. Right after that line, paste this block, edited with your update:

```html
<div class="news-item">
  <div class="news-date">May 15, 2026</div>
  <div class="news-text"><strong>Headline.</strong> One-sentence description, with optional <a href="URL">link</a>.</div>
</div>
```

6. Scroll to the bottom. Type a short commit message ("add news item: SF Climate Week panel"). Click "Commit changes."
7. Wait 60 seconds. Refresh your live site. The new item is at the top of the news list.

### To prune the news section back to the last 60 days

Once a month, open `index.html` in the GitHub editor and delete `<div class="news-item">...</div>` blocks where the date is older than 60 days from today. Each block is 4 lines including the wrapper. Commit with message "prune old news."

### To add a publication

Same pattern as news, but find the right year section in the Publications block. The pattern is:

```html
<li>
  <span class="pub-title">Title of the paper</span>
  <span class="pub-authors">Last1, F1., Last2, F2., &amp; Tal, G.</span>
  <span class="pub-venue">Journal Name, volume(issue), pages, year</span>
</li>
```

Note: use `&amp;` instead of `&` and rewrite any em-dashes as commas or "to" for ranges (per your custom instructions, the file is already em-dash-free).

### To add a media item

Same pattern. Find the right year section in the Media block:

```html
<li>
  <span class="media-date">May 2026</span>
  <div>
    <span class="media-outlet">Outlet Name</span>
    <span class="media-desc">Brief description in quotes if it is a headline.</span>
  </div>
</li>
```

### To replace the CV PDF

1. In the repo, click the existing `cv.pdf` file.
2. Click the trash can icon to delete it. Commit.
3. Drag the new CV file in (renamed to `cv.pdf`). Commit.
4. Site updates within 60 seconds.

### To replace the profile photo

Same as CV: delete the old one, upload a new one with the exact same filename (`profile.jpg`).

### To update the citation count

Find this line in `index.html`:

```html
<span class="stat-num">7,446</span>
```

Change the number to whatever Scholar shows today. Same for h-index two lines below.

---

## Part 3: Things that go wrong, and how to fix them

**The page renders blank or broken after my edit.**
You probably have an unclosed tag or a missing quote. Go to the repo's commit history (the clock icon at the top of the file list), find the last working version, and click "Revert this commit." This puts the working version back. Then try your edit again, more carefully.

**The site does not update after I commit.**
Wait three full minutes. GitHub Pages can take that long. If it still does not update, do a hard refresh in your browser (Ctrl+Shift+R or Cmd+Shift+R) to bypass cache.

**Photos look blurry.**
Photos are square 367 to 600 pixels. If you replace with a much larger photo, browsers handle it fine. If you replace with a smaller one (like 200×200), it will look blurry. Aim for at least 400×400 square.

**I want a custom domain like giltal.org.**
Buy the domain from Namecheap or Cloudflare ($12 to $15 per year). In the repo, go to Settings, Pages, and under "Custom domain" type in your domain. Then at your domain registrar, point an A record to GitHub Pages IP addresses (instructions are in GitHub's docs). One-time setup, then it just works.

---

## Part 4: When to ask for help

Ask Claude (or anyone) for help when:
- You want to add a whole new section (like "Teaching" or "Lab")
- You want to change the visual design (colors, fonts, layout)
- You want to migrate to a different platform later
- The site breaks and you cannot figure out why

Do not ask for help when:
- You just need to add a news item, paper, or media mention. The patterns above will get you 95% of the way.

---

## Final note

The website at this URL exists for two reasons: to be a stable, professional landing page when people Google your name, and to host a current CV. Everything else is bonus. If maintenance starts to feel like a chore, prioritize keeping the CV PDF and contact info current. The news section can be quarterly rather than monthly. The publication list updates can lag Scholar by six months without anyone noticing.

The goal is a site that is current enough to look maintained, not a site that is a second job.
