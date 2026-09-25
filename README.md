# Bistro — a Studio starter

A three-page restaurant site with a **YouTube background hero**, real
photography, a menu marked up as one, and a booking form built properly. Not a
finished template you recolour — a professional structure you make yours, and
can defend every choice in.

**See it running: <https://ladiletta.github.io/studio-bistro/>** — that page is
built from this branch, so it is exactly what you get when you copy it.

That difference is the point. A team handed a finished site rearranges it. A
team handed a real structure builds one.

```
index.html         hero (video) · hours · dishes · story · private dining · quote · call to action
menu.html          jump links · dietary badges · a real menu with dotted leaders · print button
visit.html         hours · map · getting here · a booking form built properly · FAQ
styles.css         your palette, your type, the hero video, the menu's leaders, print rules
js/hero-video.js   the video, and what happens when YouTube is blocked
js/site.js         the phone menu, the footer year, and the demo forms
img/               the photographs, and favicon.svg (the icon in the browser tab)
```

## Start here

1. When VS Code offers to install this folder's recommended extensions, say
   yes. They are **Live Server**, which runs the site, and **Live Share**, which
   is how you show it to a teammate or your teacher when it misbehaves — click
   **Live Share** in the status bar, paste the link it copies into Google Chat,
   and go back to work.
2. Open `index.html` with **Live Server** — the **Go Live** button in the status
   bar. Not by double-clicking: see Unit 4 for why `file://` is not a website.
3. Change `data-theme="coffee"` on the `<html>` tag — **in all three pages**. Do
   this first. It takes five seconds and it is the fastest way to find the mood
   you want. Try `sunset`, `night`, `autumn`, `luxury`, `dracula`,
   `caramellatte`, `retro`. All 35 are at
   [daisyui.com/docs/themes](https://daisyui.com/docs/themes/).
4. Swap the hero video: `data-video="WhWc3b3KhnY"` in `index.html`. The id is
   the part after `v=` in a YouTube URL. Swap the poster photograph in
   `styles.css` to match, then fix both credits in the footer.
5. Replace the words. Every one of them. Then the photographs.
6. Commit as you go. Push at least once a session — a commit is local until you
   push it.

## What is in it

- **A phone menu that needs no JavaScript.** It is a `<details>` element: it
  opens and closes on its own. `js/site.js` only adds "close when I tap away".
- **Real photographs, properly credited.** Every one is from Wikimedia Commons,
  under a licence that lets you use it, and the footer's credits list says whose
  it is, where it came from, the licence, and that it was cropped. That list is
  the model for yours.
- **Two typefaces from Google Fonts** — Fraunces for headings, Inter for body —
  set in `styles.css`.
- **A map** on the Visit page, from OpenStreetMap: free, no account, no key. The
  comment above it says how to move the pin.
- **Forms that check themselves.** `required` and `type="email"` make the
  browser check before anything is sent, and daisyUI's `validator` class turns a
  field red only after somebody has touched it.
- **A print button on the menu**, with print rules at the bottom of
  `styles.css` that drop the navbar and the colours.
- **A skip link**, the first thing a keyboard user reaches. Press Tab on any
  page to see it.

## How the video hero works

Read `js/hero-video.js`; it is thirty lines and it explains itself. The short
version:

- The **photograph in `styles.css` is always painted.** Nothing has to succeed
  for the hero to look finished. Most visitors — anyone on a phone, anyone on a
  network that blocks YouTube — only ever see the photograph, so it has to be a
  good one.
- The script loads the video's **thumbnail** first, as a test: a school filter
  that blocks YouTube blocks its image host too. Only if the thumbnail loads
  does an `<iframe>` go on the page, fading in over the photograph.
- **No video on a phone**, and none for a reader whose system asks for reduced
  motion. Both keep the photograph.

If you see the photograph and no video, that is the fallback working. Try it on
a different network before you go looking for a bug.

## Forms that go nowhere, on purpose

The booking form and the newsletter signup are marked `data-demo`. Press submit
and `js/site.js` shows a thank-you message instead of sending anything, because
a form needs a service to send to — Formspree, Netlify Forms, a Google Form —
and choosing one is your team's decision. To make one real: give the `<form>`
an `action`, delete `data-demo`, and test it with your own email.

## Things that will bite you

- **The three pages must match.** Theme, nav, footer, fonts, credits. A site
  that restyles itself between clicks reads as broken. This is the real cost of
  plain HTML, and Unit 8's build step is the fix.
- **The nav is in there twice** on every page — a row of links for wide screens
  and the phone dropdown. Add a page, add it to both, on all three pages.
- **Deleting structure to "simplify".** `card-body` inside `card`,
  `collapse-title` inside `collapse` — these look like extra wrappers and are
  not. Remove one and the component stops laying out.
- **Lightening the scrim.** The dark layer over the video is what makes the
  headline readable. It is measured, not guessed: at 65% black over a pure
  white frame, white text sits near 6.9:1. Lighten it and measure again.
- **Changing the theme changes every contrast.** This starter was measured on
  `coffee`: every piece of text clears WCAG's floor against what is behind it
  — 4.5:1, or 3:1 for large headings.
  Muted text (`opacity-80`) is the first thing to fail on a new theme. Measure
  again after you switch.
- **The sticky navbar covering your anchors.** Handled by `scroll-margin-top` in
  `styles.css`. Change the navbar's height, change that number.
- **Big photographs.** A photo straight off a phone is 4 MB. The ones here are
  under 250 KB. Resize yours before you commit them — nobody needs 4000 pixels
  of risotto.

## Check your own work before you hand it in

Tick this yourself first — auditing a page against a written spec is a graded
skill in its own right (`WD3.B`), and it is much better to find these than to
have them found.

- [ ] Every placeholder is gone. Search all three files for `Your`, `00`, `20XX`,
      `Their name` and `______`.
- [ ] Every section is the element it should be — `nav`, `header`, `main`,
      `footer`, `article` — not a `div` wearing a class.
- [ ] The headings outline each page. Read `h1`, `h2`, `h3` alone, in order: one
      `h1` per page, no levels skipped.
- [ ] One column on a phone, more on wider screens. Check at 380px, 768px and
      full width. Nothing scrolls sideways at 380px.
- [ ] There is **one** obvious call to action per page, and its label says what
      happens. Not "Click here".
- [ ] Your palette is recorded as a comment block at the top of `styles.css`,
      with a mood sentence and a job for each colour.
- [ ] Two type faces at most: one for headings, one for body.
- [ ] Body text against its background is at least **4.5:1**. Check it — do not
      guess.
- [ ] Every image has `alt` text that says what the image is FOR. Decorative
      images take an empty `alt=""`.
- [ ] Every image and every video has its creator, source and licence in the
      footer. **If you cannot write that line, you are not allowed to use it.**
- [ ] Every form either sends somewhere real, or says plainly that it does not.
- [ ] The hero still looks deliberate with the video blocked. Turn wifi off and
      reload.
- [ ] If you used AI to generate any part of this, say so and say which part.
      That is the professional norm and it costs you nothing.
- [ ] It works from a fresh clone — no absolute paths to your own disk.
- [ ] It is **pushed**.

## Credits

Component classes are [daisyUI](https://daisyui.com/) by Pouya Saadeghi (MIT),
on [Tailwind CSS](https://tailwindcss.com/) (MIT). Both load from a CDN via the
three tags in each file's `<head>`. Icons are from [Lucide](https://lucide.dev/)
(ISC), copied into the pages as inline SVG. Fraunces and Inter are from
[Google Fonts](https://fonts.google.com/), under the SIL Open Font License.

The hero video is **_Spring_ by Blender Studio**, CC BY 4.0. The photographs
in `img/` are from Wikimedia Commons, each under its own licence — CC0, CC BY-SA
2.0, 3.0 or 4.0 — and each is credited by name in the footer. They are
placeholders: replace them with pictures you have the right to use, and replace
their lines with yours. The map is © OpenStreetMap contributors.

Everything else here was written for this course, MIT licensed. See `LICENSE`.
The MIT licence covers the code and the words, not the photographs or the video.
