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
year12/index.html                 Year 12 module list
year12/module5-heredity.html                Module 5 — Heredity
year12/module6-genetic-change.html          Module 6 — Genetic Change
year12/module7-infectious-disease.html      Module 7 — Infectious Disease
year12/module8-non-infectious-disease.html  Module 8 — Non-infectious Disease and Disorders
```

All eight modules now follow the same structure: Syllabus dot points → Notes → Practice questions (with hideable worked answers) → Resources. Each still has one or two dashed orange **"Note to self"** boxes flagging where a diagram would strengthen the page (e.g. a labelled cell membrane, a Punnett square, an immune response diagram) — add these as you create or source them, with descriptive alt text.

Treat the notes on each page as a solid starting draft rather than a finished textbook: they're accurate to the syllabus dot points, but you'll want to check them against your own teaching emphasis, add worked examples specific to your class, and expand anywhere your students need more depth.

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
