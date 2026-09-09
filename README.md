# glyphette.com

Static portfolio site for Glyphette (Anna Dutton). Hosted on GitHub Pages.

## Editing
- `index.html`: all content. Each work item is a `.card`; replace the placeholder `<span>` inside `.art` with `<img src="work/filename.jpg" alt="...">` and update title and client line.
- `style.css`: colors and type. Teal #0CB4B7, ink #1C1B19, stone #6B6862, paper #FAF8F4.
- Put artwork in `work/`.

## Publishing
Push to `main`. Settings > Pages > Source: Deploy from a branch, `main`, `/ (root)`. The `CNAME` file sets the custom domain.

## Search engines
While the site is in progress it is kept out of search results by `<meta name="robots" content="noindex, nofollow">` in `index.html`. `robots.txt` deliberately allows crawling so that tag can be read. To go live: delete that meta tag (and add it to any new page until then).
