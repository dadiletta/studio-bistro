# Bistro — a Studio starter

A three-page restaurant site with a **YouTube background hero**, real
photography, a menu marked up as one, and a booking form built properly — with
the finish of a template you would pay for: photos that open large, sections
that rise into view, numbers that count, a back-to-top button that fills as you
read. Not a finished template you recolor — a professional structure you make
yours, and can defend every choice in.

**See it running: <https://dadiletta.github.io/studio-bistro/>** — that page is
built from this branch, so it is exactly what you get when you copy it.

That difference is the point. A team handed a finished site rearranges it. A
team handed a real structure builds one.

```
index.html         hero (video) · hours · dishes · story · photo carousel · private dining · quote · call to action
index-2.html       another home: the nav over a photo slider. Keep one home
elements.html      the parts page, seventeen parts: copy what you want, then delete it
menu.html          a photo header · jump links that follow you · dietary badges · a real menu with dotted leaders · print button
visit.html         a photo header · hours · map · getting here · a booking form built properly · FAQ
404.html           the page GitHub Pages shows for an address that does not exist
styles.css         your palette, your type, the hero video, the menu's leaders, the carousels, the nav over the hero, the motion, the lightbox, print rules
js/hero-video.js   the video, and what happens when YouTube is blocked
js/site.js         the phone menu, the footer year, the demo forms, the carousels, the nav over the hero, and the effects
img/               the photographs, and favicon.svg (the icon in the browser tab)
AGENTS.md          what AI help may and may not do on this project
```

## Start here

1. When VS Code offers to install this folder's recommended extensions, say
   yes. They are **Live Server**, which runs the site, and **Live Share**, which
   is how you show it to a teammate or your teacher when it misbehaves — click
   **Live Share** in the status bar, paste the link it copies into Google Chat,
   and go back to work.
2. Open `index.html` with **Live Server** — the **Go Live** button in the status
   bar. Not by double-clicking: see Unit 4 for why `file://` is not a website.
3. Change `data-theme="coffee"` on the `<html>` tag — **in every page**. Do
   this first. It takes five seconds and it is the fastest way to find the mood
   you want. Try `sunset`, `night`, `autumn`, `luxury`, `dracula`,
   `caramellatte`, `retro`. All 35 are at
   [daisyui.com/docs/themes](https://daisyui.com/docs/themes/).
4. Swap the hero video: `data-video="WhWc3b3KhnY"` in `index.html`. The id is
   the part after `v=` in a YouTube URL. Swap the poster photograph in
   `styles.css` to match, then fix both credits in the footer. Then set
   `data-start` and `data-end` to the seconds you want it to loop between.
5. Replace the words. Every one of them. Then the photographs.
6. Commit as you go. Push at least once a session — a commit is local until you
   push it.

## What is in it

- **A phone menu that needs no JavaScript.** It is a `<details>` element: it
  opens and closes on its own. `js/site.js` only adds "close when I tap away".
- **Real photographs, properly credited.** Every one is from Wikimedia Commons,
  under a license that lets you use it, and the footer's credits list says whose
  it is, where it came from, the license, and that it was cropped. That list is
  the model for yours.
- **Two typefaces from Google Fonts** — Fraunces for headings, Inter for body —
  set in `styles.css`.
- **A map** on the Visit page, from OpenStreetMap: free, no account, no key. The
  comment above it says how to move the pin.
- **Forms that check themselves.** `required` and `type="email"` make the
  browser check before anything is sent, and daisyUI's `validator` class turns a
  field red only after somebody has touched it.
- **A print button on the menu**, with print rules at the bottom of
  `styles.css` that drop the navbar and the colors.
- **A skip link**, the first thing a keyboard user reaches. Press Tab on any
  page to see it.
- **Photo headers with breadcrumbs** on the menu and visit pages: shorter than
  the home page's hero, on the same measured scrim.
- **The finish.** Sections fade up as they scroll into view, numbers count up,
  photos open large in a lightbox, the menu's jump links follow you down the
  page, and a back-to-top button fills its ring as you read. See
  [The effects](#the-effects) for how each one works and how to turn it off.
- **A 404 page.** GitHub Pages shows `404.html` for any address on your site
  that does not exist. Make its words yours, like every other page's.

## Two home pages and a box of parts

A professional template ships more than one home page, and a page of
"elements": every part it has, working, so you can see them before you choose.
This one does too.

- **`index-2.html`** is the same site with a different top: the nav sits over a
  full-screen photo slider and turns solid as you scroll. See it at
  <https://dadiletta.github.io/studio-bistro/index-2.html>. **Keep one home, not both**: delete the other and name
  the keeper `index.html`.
- **`elements.html`** is the parts page: a photo slider, a quote carousel,
  tabs, pricing, a team, a timeline, steps, a photo wall that opens in a
  lightbox, a call to action on a photo, questions, numbers that count, events,
  a menu with photos, a press strip, a video that plays in a lightbox, an
  Instagram grid, and a top bar for above the nav. Its nav is a part too, the
  centered one. See it at
  <https://dadiletta.github.io/studio-bistro/elements.html>. Each part sits between a `COPY FROM HERE` and a
  `TO HERE` comment: copy what you want into your pages, then **delete
  `elements.html`** before you hand in. Nothing links to it.

### How the carousels work

A carousel is daisyUI's `carousel`: a row that scrolls sideways and snaps to
each slide, with **no script at all**. Swipe it, or scroll it with a trackpad.
`js/site.js` adds the rest to anything marked `data-carousel`: the arrows
(`data-prev`, `data-next`), one dot per stop (`data-dots`), and, with
`data-autoplay="7000"`, turning every seven seconds. Those buttons stay hidden
until the script runs (`data-carousel-controls hidden`), because a button that
does nothing is worse than none.

A slider that turns by itself has to stop for people: it holds while the
pointer or the keyboard is on it, it has a pause button, and for anyone whose
computer asks for less motion it never turns at all. Keep all three. Add or
remove slides freely; every slide is one element inside the `carousel`.

## The effects

Every effect is switched on by an attribute or a class in the HTML, and every
one of them is extra: delete the attribute and the element simply sits there,
finished. `js/site.js` runs them, one numbered job each, and nothing on the
page waits for it — with the script blocked, nothing is hidden, and a photo
link just opens the photo. For anyone whose computer asks for less motion,
nothing moves at all. Keep that true for anything you add.

| Put this on an element | And it |
| --- | --- |
| `data-reveal` | fades up as it scrolls into view, once. `data-reveal="left"`, `"right"` or `"zoom"` change how it arrives. Several arriving together come in one after another. |
| `data-count` | counts up to the number in its own text: `12`, `1,200` and `40+` all work. `00` stays `00`. |
| `data-lightbox` | on a block of photo links, opens each photo large over the page, with arrows, the arrow keys and Escape. Each link's `href` is the big photo. |
| `data-video-popup` | on a link to a YouTube video, plays it over the page. `&t=90` in the link starts it 90 seconds in. Credit the video like a photo. |
| `class="hero-rise"` | on the block that holds the hero's words, raises each child in, one after another, as the page opens. |
| `class="eyebrow"` | on the small label over a heading, adds the short rule before it (and after it, in a centered block). |
| `data-spy` | on the menu's jump links, underlines the course on screen. |
| `data-sticky-nav` | on the sticky nav, adds a shadow once the page scrolls under it. |
| `data-to-top` | is the back-to-top button at the bottom of every page. |

Use them where they help somebody read, not everywhere. A page where every
paragraph slides in is a page that makes people wait.

## How the video hero works

Read `js/hero-video.js`; it explains itself. The short
version:

- The **photograph in `styles.css` is always painted.** Nothing has to succeed
  for the hero to look finished. Most visitors — anyone on a phone, anyone on a
  network that blocks YouTube — only ever see the photograph, so it has to be a
  good one.
- The script loads the video's **thumbnail** first, as a test: a school filter
  that blocks YouTube blocks its image host too. Only if the thumbnail loads
  does YouTube's player go on the page, and it stays invisible until YouTube
  says the video is **playing**. Nobody sees a loading screen, an error
  message or YouTube's buttons where your photograph was.
- **The clip loops.** `data-start` and `data-end` pick the seconds. The zoom
  in `styles.css` (`--video-zoom`) crops YouTube's title bar and any black
  bars off the edges; a new video may need a different number.
- **No video on a phone**, and none for a reader whose system asks for reduced
  motion. Both keep the photograph.

If you see the photograph and no video, that is the fallback working. Try it on
a different network before you go looking for a bug. And check the address
bar: opened as a `file://` page instead of through Live Server, YouTube refuses
to play at all, because it will not play for a page that cannot say where it is.

## Forms that go nowhere, on purpose

The booking form and the newsletter signup are marked `data-demo`. Press submit
and `js/site.js` shows a thank-you message instead of sending anything, because
a form needs a service to send to — Formspree, Netlify Forms, a Google Form —
and choosing one is your team's decision. To make one real: give the `<form>`
an `action`, delete `data-demo`, and test it with your own email.

## Things that will bite you

- **The pages must match.** Theme, nav, footer, fonts, credits, on every page,
  `404.html` included. A site that restyles itself between clicks reads as
  broken. This is the real cost of plain HTML, and Unit 8's build step is the
  fix.
- **The nav is in there twice** on every page — a row of links for wide screens
  and the phone dropdown. Add a page, add it to both, on every page.
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
- **daisyUI's colors come in steps of ten.** `bg-primary/10`, `/20` … `/90`
  work; `bg-primary/15` or `bg-base-100/85` silently does nothing, and the
  element shows through or picks up a color you did not choose. Lines between
  list items (`divide-y`) have no daisyUI color at all: use `divide-current/10`,
  which is the text color at 10%.
- **The sticky navbar covering your anchors.** Handled by `scroll-margin-top` in
  `styles.css`. Change the navbar's height, change that number.
- **Big photographs.** A photo straight off a phone is 4 MB. The ones here are
  under 250 KB. Resize yours before you commit them — nobody needs 4000 pixels
  of risotto.

## Check your own work before you hand it in

Tick this yourself first — auditing a page against a written spec is a graded
skill in its own right (`WD3.B`), and it is much better to find these than to
have them found.

- [ ] Every placeholder is gone. Search every HTML file for `Your`, `00`, `20XX`,
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
      with a mood sentence and a job for each color.
- [ ] Two type faces at most: one for headings, one for body.
- [ ] Body text against its background is at least **4.5:1**. Check it — do not
      guess.
- [ ] Every image has `alt` text that says what the image is FOR. Decorative
      images take an empty `alt=""`.
- [ ] Every image and every video has its creator, source and license in the
      footer. **If you cannot write that line, you are not allowed to use it.**
- [ ] Every form either sends somewhere real, or says plainly that it does not.
- [ ] The hero still looks deliberate with the video blocked. Turn wifi off and
      reload.
- [ ] If you used AI to generate any part of this, say so and say which part.
      That is the professional norm and it costs you nothing.
      AI help on this project follows `AGENTS.md`: a tutor until your final
      draft is done, then a hand with the polish.
- [ ] It works from a fresh clone — no absolute paths to your own disk.
- [ ] It is **pushed**.

## Credits

Component classes are [daisyUI](https://daisyui.com/) by Pouya Saadeghi (MIT),
on [Tailwind CSS](https://tailwindcss.com/) (MIT). Both load from a CDN via the
three tags in each file's `<head>`. Icons are from [Lucide](https://lucide.dev/)
(ISC), copied into the pages as inline SVG. Fraunces and Inter are from
[Google Fonts](https://fonts.google.com/), under the SIL Open Font License.

The hero video is **_Spring_ by Blender Studio**, CC BY 4.0. The photographs
in `img/` are from Wikimedia Commons, each under its own license — CC0, CC BY-SA
2.0, 3.0 or 4.0 — and each is credited by name in the footer. They are
placeholders: replace them with pictures you have the right to use, and replace
their lines with yours. The map is © OpenStreetMap contributors.

Everything else here was written for this course, MIT licensed. See `LICENSE`.
The MIT license covers the code and the words, not the photographs or the video.
