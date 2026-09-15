# glyphette.com

Static portfolio site for Glyphette (Anna Dutton). Hosted on GitHub Pages. No build step — edit, commit, push.

## Editing
- `index.html`: all content. Each work item is a `.card` holding an `<img>` inside `.art`, plus a title and client line. Add `class="art fit"` when a piece should be shown whole on white instead of cropped to fill the card (posters, logos, page spreads); add `pad` alongside it to inset a logo.
- `style.css`: colors and type. Teal #0CB4B7, ink #1C1B19, stone #6B6862, paper #FAF8F4.
- Artwork lives in `work/`, exported to sRGB JPEG, long edge capped at 1400px, quality 80, progressive. Convert CMYK sources first — browsers render CMYK JPEGs unpredictably.
- Keep each category a multiple of three so no row is left short at the three-column breakpoint.
- `width`/`height` on every `<img>` must match the file on disk. They prevent layout shift; re-resizing an image without updating them reintroduces it.

## The hero
The hero crossfades through every card that shares its aspect ratio (`4/5`), collected from the DOM at runtime — add a 4/5 card and it joins the rotation automatically. It only warms the *next* slide, never the whole set. `.hero-art` overrides `.art`'s `overflow:hidden` so the tilt and shadow aren't clipped, and the shadow is `filter: drop-shadow` (not `box-shadow`) so it follows the artwork rather than the letterboxed element box.

## Email protection
The contact address is never written literally into the markup. It is assembled at runtime from `data-u` / `data-d` attributes, and the `<noscript>` fallback is stored back-to-front and flipped with CSS (`.rev`). **Do not** add the plain address to markup, structured data, alt text, or commit messages. Commits use the GitHub `noreply` author address for the same reason — the commits API exposes author emails on public repos, which is a known harvesting vector.

## Search engines
The site is indexable: `robots.txt` allows crawling, `sitemap.xml` lists the single page, and `index.html` carries canonical, Open Graph, Twitter Card and `ProfessionalService` JSON-LD. The social preview is `assets/og-image.jpg` (1200×630) — regenerate it if the featured work changes.

## Publishing
Push to `main`. Settings > Pages > Source: Deploy from a branch, `main`, `/ (root)`. The `CNAME` file sets the custom domain. GitHub Pages will not serve a **private** repo on a free plan.
