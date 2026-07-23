# HSC Biology Course Site

A static site for the Year 11 (Preliminary) and Year 12 (HSC) Biology Stage 6 course: notes, syllabus dot points, tiered practice questions, and links to NESA and other resources.

No build tools, frameworks or installs are needed — it's just HTML, CSS, and plain text files, which is what makes it easy to publish for free and simple to keep editing over time.

## Folder structure

```
index.html                        Home page
css/style.css                     All styling (colours, fonts, layout)
year11/index.html                 Year 11 module list
year11/module1-cells.html          Module 1 — Cells as the Basis of Life
year11/module2-organisation.html   Module 2 — Organisation of Living Things
year11/module3-diversity.html      Module 3 — Biological Diversity
year11/module4-ecosystems.html     Module 4 — Ecosystem Dynamics
year11/flashcards.html            Year 11 flash cards (all 4 modules)
year11/exam-tips.html             Preliminary exam preparation
year12/index.html                 Year 12 module list
year12/module5-heredity.html                Module 5 — Heredity
year12/module6-genetic-change.html          Module 6 — Genetic Change
year12/module7-infectious-disease.html      Module 7 — Infectious Disease
year12/module8-non-infectious-disease.html  Module 8 — Non-infectious Disease and Disorders
year12/flashcards.html            Year 12 flash cards (all 4 modules)
year12/exam-tips.html             HSC exam preparation
reference/index.html              Reference materials hub
reference/band-descriptors.html   Biology performance band descriptors (Bands 1–6)
reference/hsc-verbs.html          HSC key words / command verbs glossary
```

Every module page now follows the same structure: **Syllabus checklist** (the exact NESA dot points, for quick reference) → **Course content by syllabus dot point** (one detailed subsection per dot point — this is the expanded teaching content) → **Glossary** (module-specific key terms) → **Practice questions** (tiered, with hideable worked answers and an HSC key-word tag on each) → **Resources**.

Treat the dot-point notes as a strong, detailed first draft rather than a finished textbook — they cover every syllabus dot point in real depth, but you should still check them against your own teaching emphasis, add worked examples specific to your class, and expand anywhere your students need more. A genuinely complete 100-hour teaching resource is something that develops over a year or more of use — this gives you a thorough head start rather than a from-scratch build.

### Image placeholders

Each dot-point section includes a dashed-border placeholder box like this:

```html
<figure class="image-placeholder">
  <strong>[Image placeholder]</strong> — suggested search: "fluid mosaic model cell membrane diagram labelled".
  <figcaption>Replace this box with an &lt;img&gt; tag once you've sourced a diagram.</figcaption>
</figure>
```

To add a real image once you've found one (e.g. via Google Images — right-click an image → "Copy image address"), replace the whole `<figure>...</figure>` block with:

```html
<figure>
  <img src="PASTE_IMAGE_URL_HERE" alt="Describe what the image shows, e.g. a labelled diagram of the phospholipid bilayer with embedded proteins" style="max-width:100%; border-radius:6px;">
  <figcaption>Source: [where the image came from]</figcaption>
</figure>
```

A few notes on this:
- **Check image licensing before publishing.** Google Images search results are not automatically free to use — look for images marked for reuse (Google's "Usage rights" filter, or sources like Wikimedia Commons, NASA, or your own diagrams) rather than hotlinking an arbitrary result, especially since this site will be public.
- **Always write real alt text** describing what the image shows, not just the filename — this matters both for accessibility and because it's required by the site's own accessibility standard (see below).
- Hotlinked image URLs can break if the source site reorganises its content — downloading the image and hosting it yourself in an `assets/` folder (then using `src="../assets/your-image.png"`) is more reliable for anything you intend to keep long-term.

### Flash cards

`year11/flashcards.html` and `year12/flashcards.html` are self-contained interactive pages (plain JavaScript, no external libraries) — tap a card to flip it. To add more cards, find the `cards` array near the bottom of the file and add an object with `module`, `q` and `a` fields, following the existing pattern.

### Band descriptors and HSC key words

`reference/band-descriptors.html` and `reference/hsc-verbs.html` are paraphrased, plain-language summaries intended for classroom teaching use — both link out to the official NESA source for anything used in formal grading or assessment design.

## Publishing with GitHub Pages (free hosting)

1. Create a free GitHub account at [github.com](https://github.com) if you don't have one.
2. Create a new repository (e.g. `hsc-biology-notes`). Keep it **Public** — GitHub Pages' free tier requires this for personal accounts.
3. Upload all the files in this folder to the repository, keeping the same folder structure (drag-and-drop works fine on the GitHub website — no command line needed).
4. In the repository, go to **Settings → Pages**.
5. Under "Build and deployment", set **Source** to "Deploy from a branch", choose the `main` branch and the `/ (root)` folder, then save.
6. After a minute or two, GitHub will publish your site at `https://<your-username>.github.io/<repository-name>/`.

Any time you edit a file and upload the change (or "commit" it), the live site updates automatically within a minute or two.

## Editing content

Every page is plain HTML — you don't need to know how to code to add a paragraph or a new practice question. A few patterns to copy and paste:

**Add a paragraph of notes:**
```html
<p>Your explanation goes here.</p>
```

**Add a practice question with a hideable answer:**
```html
<li class="question">
  <span class="marks">3 marks</span>
  <p><strong>Q1 (Application).</strong> Your question text here.</p>
  <details class="answer">
    <summary>Show suggested answer</summary>
    <p>Your answer here.</p>
  </details>
</li>
```

**Add a resource link:**
```html
<li><span class="tag">Video</span> <a href="https://example.com" target="_blank" rel="noopener">Link text here</a></li>
```

## Accessibility notes (please keep these when editing)

- **Headings stay in order.** Each page uses one `<h1>`, then `<h2>` for major sections, then `<h3>` for sub-sections. Don't skip levels (e.g. don't jump from `<h2>` straight to `<h4>`) — screen reader users navigate by heading structure.
- **Every image needs alt text.** When you add a diagram, use `<img src="..." alt="A description of what the image shows">`. Describe what the image communicates, not just its filename.
- **Link text should describe the destination**, e.g. "NESA Biology Syllabus (PDF)" rather than "click here".
- **Don't rely on colour alone** to convey meaning (e.g. don't colour-code difficulty levels without also labelling them in text — this site already labels question difficulty in words: Recall / Application / Extended response).
- The site already includes a "Skip to main content" link and visible keyboard focus outlines — these are built into `css/style.css` and don't need to be touched.

## The Outcome / Adjustments / Register table

If you want to bring in the lesson-table structure from your teaching program (with Outcome, Adjustments and Register columns for NCCD purposes), a ready-made table style is already included in `css/style.css` under `.teacher-table`. Add it to any page like this:

```html
<div class="teacher-table-wrap">
  <table class="teacher-table">
    <caption>Lesson 1</caption>
    <thead>
      <tr><th>Outcome</th><th>Adjustments</th><th>Register</th></tr>
    </thead>
    <tbody>
      <tr><td>P2.2</td><td></td><td></td></tr>
    </tbody>
  </table>
</div>
```

This is intended for your own program/planning pages rather than the student-facing module pages — you may want to keep those on a separate, teacher-only page or in your school's LMS rather than the public site, since NCCD adjustment details are sensitive student information.
