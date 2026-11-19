# popiv

a blog for my hobbies

## Run it locally

You need **Hugo extended v0.170.0 or newer** (`hugo version`).

```sh
hugo server -D        # http://localhost:1313, including drafts
hugo server           # what the public will see (drafts hidden)
hugo --minify         # production build into ./public
```

All sample posts are `draft: true`, so they only show with `-D`. To publish a post, set
`draft: false` (or delete the line).

## Creating posts

Every post is a **page bundle**: a folder with `index.md` and its images next to it.

```sh
HUGO_BUILDDRAFTS=true hugo new --kind read        read/the-glass-orchard/index.md
HUGO_BUILDDRAFTS=true hugo new --kind play        play/my-deck/index.md
HUGO_BUILDDRAFTS=true hugo new --kind restoration make/snes-controller/index.md
HUGO_BUILDDRAFTS=true hugo new --kind gallery     make/space-marine/index.md
HUGO_BUILDDRAFTS=true hugo new --kind watch       watch/some-film/index.md
HUGO_BUILDDRAFTS=true hugo new --kind roundup     roundups/2026-11/index.md
```

The archetype fills in the **next issue number** (the highest existing issue + 1), with a
comment asking you to double-check it. `HUGO_BUILDDRAFTS=true` makes it count draft posts too;
without it, drafts are ignored when it looks for the highest number.

Every new post starts as `draft: true`.

### Shortcodes for the body

```md
{{</* spoiler "Spoilers: the ending" */>}}Hidden until clicked.{{</* /spoiler */>}}
{{</* callout "Label" */>}}A generic callout box.{{</* /callout */>}}
{{</* takeaway */>}}My one-line takeaway.{{</* /takeaway */>}}
{{</* sessions */>}}   <!-- Play: puts the session log here (otherwise it goes after the body) -->
{{</* steps */>}}      <!-- Restoration: puts the step timeline here (otherwise it goes after the body) -->
```

### Photos in the body

Put the photo in the post's folder, then on its own line:

```md
![Ribbon cable soldered to the board](soldering.jpg "The IPS ribbon cable, soldered")
```

The text in `[ ]` is the alt text; the part in quotes is an optional caption shown under the photo.
The image is resized, served as WebP, lazy-loaded, and opens in the lightbox when clicked.
A missing file shows the placeholder and a build warning instead of a broken image.

## Front matter reference

### All posts

| Key | What it does |
|---|---|
| `title` | Post title |
| `linkTitle` | Optional shorter title, used in "Read next" lists |
| `date` | Publish date (shown on every post and card) |
| `lastmod` | Optional. If it's a later day than `date`, posts show "· updated Nov 20" |
| `issue` | Issue number, shown as `ISSUE #015` |
| `summary` | Subtitle under the title and the text on cards |
| `why` | The "Why I picked it up / Why this deck / project / mini" callout (Watch: "Chose it because") |
| `tags` | Free tags, lowercase (`marvel`, `nintendo`, `star-wars`…) |
| `featured` | `true` = candidate for the homepage featured slot; the newest featured post wins |
| `factcheck` | Optional "Fact-check note" callout at the end |
| `cover` | Optional image; empty = halftone placeholder |
| `subtype` | Optional first ghost tag in the crumbs (defaults: Play = game, Read = first genre, Make = "Restoration" / "Minifigure painting", Watch = `kind`) |
| `draft` | `true` hides the post unless you run with `-D` |
| `lang` | Optional language of the post, e.g. `"bg"`. Sets `lang` on the page's `<html>` and on its homepage/list card (defaults to the site's `en`) |

**Images.** Any image field (`cover`, `before`, `after`, `photos.*`, `steps[].image`, `wip[].image`)
takes either a filename in the bundle or a map:

```yaml
cover: "cover.jpg"
cover: { src: "cover.jpg", alt: "Cover of The Iron Choir" }
cover: { alt: "cover", c1: "#1d3c8f", c2: "#8fb0ff" }   # no image yet: coloured placeholder labelled "cover"
```

Images are resized and served as WebP with a JPEG/PNG fallback, lazy-loaded, with `alt` text taken from
`alt`, the caption or the title. A missing image never breaks the layout: you get the placeholder,
and the build prints a warning naming the missing file.

### Read (`content/read/`)

```yaml
book:
  title: "The Iron Choir"       # defaults to the post title
  author: "M. A. Reyes"         # comics: "Writer · Artist"
  series: "The Lantern Cycle, book 1 of 3"
  genre: "Fantasy · slow-burn"  # first part is the ghost tag and appears on the card
  length: "512 pages · audiobook 17h"   # comics: issue range
  format: "Paperback, library copy"
  started: 2026-10-12
  finished: 2026-11-02          # days read = finished − started; empty shows "still reading"
recommend_to: ["Slow-burn fans"]
glance:                         # "At a glance" box, in order; first value is bold
  - { k: "Verdict", v: "Keep reading the series" }
read_next: ["/read/comic-run", "/watch/low-orbit"]   # page paths
```

### Play (`content/play/`)

```yaml
games: "Marvel Champions"       # the games taxonomy (a string or a list)
hero: "Spider-Man · Justice"    # card shows "Hero" and "Aspect" split on " · "
hero_label: "Hero / aspect"     # optional stat label
record: "2W · 1L"
pool_as_of: "Nov 2026"
pool_label: "Card pool as of"   # optional stat label (e.g. "Patch")
sessions:
  - { date: "Nov 1 · solo", title: "vs Rhino", note: "…", result: "win" }   # win | loss | draw
deck:                           # optional; group counts are summed; Copy button copies "3x Name" lines
  - group: "Allies"
    cards: [ { name: "Daredevil", qty: 1 } ]
curve: { "0": 3, "1": 8, "2": 10, "3": 5, "4+": 2 }   # optional; keys are sorted as text, so keep them single-digit (+ "4+")
verdict: "tweak"                # retire | tweak | keep
main: { hero: "", role: "", hours: "", clicked: "" }   # video game "main diary": sidebar box instead of a decklist
```

### Make: restoration (`content/make/…`, `layout: restoration`)

```yaml
layout: restoration
status: "in-progress"           # in-progress | on-hold | done. "Step X of Y": X = steps with done: true
before: "before.jpg"            # before/after slider
after: "after.jpg"
project: [ { k: "Console", v: "Game Boy (DMG-01)" } ]
parts: [ { item: "Glass screen lens", url: "https://…", cost: 6.50 } ]   # url optional; total is summed
currency: "€"
tools: ["Soldering iron"]
steps:
  - { title: "", text: "", image: "", done: true }    # done: false renders faded
```

### Make: gallery (`layout: gallery`)

```yaml
layout: gallery
status: "done"
photos: { main: "front.jpg", back: "back.jpg", detail: "face.jpg" }
wip: [ { image: "wip1.jpg", caption: "Primed" } ]
recipe:
  - area: "Leather"
    paints: [ { name: "Dark brown", hex: "#5a3b22", role: "base" } ]
specs: [ { k: "Scale", v: "32mm" } ]
skills: ["Layering"]
```

### Watch (`content/watch/`)

```yaml
name: "Low Orbit"               # big title in the verdict card (defaults to the post title)
kind: "Film"                    # Film | Series | Special
year: 2026
runtime: "1h 32m"
where: "Streaming, at home"
verdict: "watch"                # watch | wait | skip
long: true                      # optional: turns off the 3-paragraph warning for this post
related: "/read/iron-choir"     # optional "If you liked this"
related_note: "has a similar quiet, patient pace."
```

Watch posts are meant to stay short: the build prints a warning if the body has more than 3 paragraphs.
Set `long: true` to turn the warning off for a single post.
Without a `cover`, Watch cards and the post show only the verdict stamp. With one, the image fills the top of the
feed card, and on the post it fills the right column of the verdict card (on top on phones), with the stamp in its
top-right corner. The column is narrower than a wide banner, so the image gets cropped; add `focus` to choose which
part stays in view (CSS `object-position`, horizontal then vertical):

```yaml
cover: { src: "poster.jpg", alt: "…", focus: "10% 50%" }   # keep the left side of the image
```

### Roundup (`content/roundups/`)

```yaml
month: "October"
finished: ["…"]
dropped: ["…"]
next: ["…"]
```

The newest roundup appears at the bottom of the homepage.

## The "Currently" strip

Edit `data/currently.yaml`: change `updated` and the four `items` (`label`, `title`, `note`,
`progress` 0–100, `section` = read/play/make/watch for the colour). Rebuild, or just save while
`hugo server` is running.

## Tags and games

- **New tag:** add it to a post's `tags:` list. Its page (`/tags/<tag>/`) is created automatically.
  Use lowercase and hyphens (`star-wars`) so URLs and the `#tag` labels stay consistent.
  To give a tag page an intro, create `content/tags/<tag>/_index.md` (see `content/tags/marvel/`).
- **New game:** set `games: "Star Wars Unlimited"` on a Play post. `/games/star-wars-unlimited/` appears automatically.
- The homepage `#marvel` pill links to `/tags/marvel/`. To change it, edit the filter pills in `layouts/home.html`.

## Feeds and SEO

- RSS: `/index.xml` (everything), `/read/index.xml` and so on for each section, and `/tags/<tag>/index.xml`
- `/sitemap.xml` and `/robots.txt`
- Open Graph and Twitter tags on every page (the image comes from `cover`, `after` or `photos.main`)

## Dark mode

The site follows the visitor's system light/dark setting. The header button cycles
**Auto → Light → Dark**; the choice is saved in the browser (`localStorage`), and Auto clears it.
Colours live as CSS variables at the top of `assets/css/style.css`: the light values are in `:root`,
and the dark values appear twice (system dark and forced dark), so change both copies together.

## Hosting: GitHub Pages

`.github/workflows/hugo.yml` builds with `hugo --minify` and deploys on every push to `main`.

1. Create a **public** GitHub repo and push this folder to `main`. (Pages on private repos needs a paid plan.)
2. In the repo, go to **Settings → Pages → Build and deployment → Source** and choose **GitHub Actions**.
3. The workflow sets `baseURL` automatically. If you add a custom domain, also set it in `hugo.toml`.

## Layout map

```
layouts/
  baseof.html              page shell (head, header, main, footer)
  home.html                homepage
  list.html                section lists (Read / Play / Make / Watch / Roundups), 12 per page
  taxonomy.html, term.html tag and game pages
  404.html
  read/page.html  play/page.html  watch/page.html  roundups/page.html
  make/restoration.html  make/gallery.html
  _partials/               head, header, footer, tag-row, placeholder, picture, card-*, …
  _shortcodes/             spoiler, callout, takeaway, sessions, steps
```
