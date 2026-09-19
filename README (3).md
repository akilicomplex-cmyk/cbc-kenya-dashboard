# CBC Kenya Dashboard

A single-page, self-contained dashboard tracking Kenya's Competency-Based Curriculum (CBC):

- **Live education indicators** (primary enrollment, government spend on education, pupil–teacher ratio) pulled client-side from the [World Bank Open Data API](https://data.worldbank.org/).
- **Live news feed** of current CBC coverage, pulled client-side from Google News RSS via [rss2json.com](https://rss2json.com/).
- A reference timeline of the 2‑6‑3‑3 curriculum structure.

No backend, no build step, no API keys required to get started — it's one HTML file.

## Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `cbc-kenya-dashboard`).
2. Add `index.html` to the repo root (keep the filename `index.html`).
3. Push to GitHub.
4. In the repo: **Settings → Pages → Source**, choose the `main` branch and `/ (root)` folder → **Save**.
5. Your dashboard will be live at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## Notes on the live data

- **World Bank API** has no rate limit for casual use and requires no key.
- **rss2json.com** is used to convert the Google News RSS feed into JSON in the browser (RSS feeds can't be fetched directly from client-side JS due to CORS). The free tier works without a key but is rate-limited across all anonymous users. If headlines stop loading:
  - Get a free API key at [rss2json.com](https://rss2json.com/), and
  - In `index.html`, append `&api_key=YOUR_KEY` to the `RSS2JSON` constant near the bottom of the file.
- If either live source is temporarily unavailable, the dashboard degrades gracefully (shows "n/a" or a direct link to Google News) rather than breaking.

## Customizing

- Change the news search terms by editing `NEWS_QUERY` in the `<script>` section.
- Swap or add World Bank indicators by editing the `loadIndicator(...)` calls — any [World Bank indicator code](https://data.worldbank.org/indicator) works, e.g. `SE.SEC.NENR` for secondary enrollment.
- Colors, type and layout are all in the `<style>` block at the top of `index.html`.
