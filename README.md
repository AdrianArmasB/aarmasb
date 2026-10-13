# Adrian Armas Braithwaite — Academic Website

A clean, modern, multi-page personal site. Plain HTML and CSS, no build step,
no JavaScript framework. Just two Google Fonts loaded from CDN.

## File structure

```
website/
├── index.html      ← Home: About, Research and Teaching on one scrolling page
├── research.html   ← Same research content as a standalone page (keeps old links working)
├── teaching.html   ← Same teaching content as a standalone page (keeps old links working)
├── cv.html         ← Online CV
├── cv.pdf          ← Your CV PDF (already in place)
├── styles.css      ← All styling
└── README.md       ← This file
```

## What's already personalized

Everything has been pre-filled from your CV:

- All four pages with your name, title (PhD Candidate), and affiliation
- Bio paragraph on the home page
- Three working papers on the Research page with abstracts edited lightly for
  the web (the FXI paper includes its conference list)
- Three earlier works (SBS Peru Working Paper Series)
- Teaching history at Michigan and Universidad del Pacífico
- Online CV with education, experience, RA history, awards, skills, references
- `cv.pdf` is the file you uploaded — the download button on the CV page
  already works

## What to do before deploying

1. **Add a photo.** Save a square photo (around 480×480px) as
   `assets/photo.jpg`, then in `index.html` find this block:

   ```html
   <div class="profile-placeholder">photo<br>(240×240px)</div>
   ```

   Replace with:

   ```html
   <img src="assets/photo.jpg" alt="Adrian Armas Braithwaite">
   ```

2. **Update the social links** in `index.html`. The five rows at the bottom
   of the hero — Google Scholar, CV (PDF), SSRN, GitHub, LinkedIn — have
   placeholder `href="#"` values except CV. Either fill in real URLs or
   delete the rows you don't have. The CV link is already working.

3. **Add paper PDFs** when you have drafts ready. The Research page has
   commented-out `<a>` tags where the PDF link belongs:

   ```html
   <!-- <a href="papers/dollarization_hysteresis.pdf">PDF</a> -->
   ```

   Drop the file in a `papers/` folder, uncomment the link, and you're done.

4. **Research and teaching content** appears both on the home page and on
   research.html / teaching.html. If you edit one by hand, edit the other too.

## Deploying to GitHub Pages

1. Create a new GitHub repository. The simplest naming convention: call it
   `aarmasb.github.io` (replace with your actual GitHub username), and the
   site will live at `https://aarmasb.github.io`. If you'd rather name the
   repo something else (e.g., `website`), it'll live at
   `https://yourusername.github.io/website/` — both work.
2. Upload the contents of this folder to the root of the repo. The web
   uploader at github.com works for this; you don't need git on the command
   line.
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to **Deploy from a branch**,
   choose the `main` branch and the `/ (root)` folder, save.
5. Wait about a minute and refresh the Pages settings page — the URL will
   appear at the top.

For a custom domain later (e.g., `adrianarmas.com`): add a `CNAME` file
containing just your domain, and follow GitHub's DNS instructions.

## Tweaking the look

All colors and fonts live in CSS variables at the top of `styles.css`:

```css
:root {
  --bg: #fafaf7;            /* warm off-white background */
  --text: #1a1a18;          /* near-black text */
  --text-muted: #5c5c58;    /* secondary text */
  --accent: #8c2f3a;        /* muted burgundy — links, highlights */
  --border: #e6e3db;        /* hairline dividers */
}
```

Change `--accent` and the whole site picks up the new color. A few
alternatives that pair well with the typography:

- Deep navy: `#1d3557`
- Oxford blue: `#0a2540`
- Forest green: `#2d5d3e`
- Warm rust: `#a14b29`

Fonts are **Fraunces** (serif, for headings) and **DM Sans** (for body),
loaded from Google Fonts at the top of `styles.css`. Easy to swap if you
want something different.

## Adding a paper

In `research.html`, copy an entire `<article class="paper">...</article>`
block and edit. Skeleton:

```html
<article class="paper">
  <h3 class="paper-title">
    Paper Title
    <span class="paper-status">New</span>     <!-- optional badge -->
  </h3>
  <p class="paper-meta">with Coauthor · 2026</p>
  <details>
    <summary>Abstract</summary>
    <div class="paper-abstract">The abstract text...</div>
  </details>
  <div class="paper-links">
    <a href="papers/paper.pdf">PDF</a>
    <a href="https://...">SSRN</a>
  </div>
</article>
```

Status badges: "New", "R&R", "Forthcoming", "In progress" all work. Remove
the `<span class="paper-status">` if you don't want one.
