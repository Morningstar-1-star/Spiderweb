# Spiderweb upgrade (mobile-friendly deployment)

## Cloudflare Worker
1. Open the existing Worker and replace all of `worker.js` with the supplied `worker.js`.
2. Deploy it.
3. Optional: add Worker secret `SERPER_API_KEY` if you already have a Serper key. Without it, `/s` automatically uses SearXNG; no key is required.
4. Optional: set Worker variable `SEARX_URL` to `https://spiderweb-w77l.onrender.com` (the code already has this default).

## Frontend
Upload/commit the updated `index.html` to the existing GitHub Pages repository. In Spiderweb Settings, keep your Worker URL as `https://spiderweb.samdem612.workers.dev`.

## SearXNG secret rotation
The old secret was committed publicly. In Render → your SearXNG service → Environment, add `SEARXNG_SECRET` with a newly generated random value (at least 32 random characters), then redeploy. The updated `settings.yml` reads it from the environment, so the actual secret is no longer in Git. Do not paste the secret into chat or commit it.

## Torrent search v1
The new Torrents tab searches Internet Archive and only displays records that have a `.torrent` file. It does not invent seed/peer counts or magnet links. Check each item's licence and terms before downloading or redistributing. More providers can be added later through the Worker route `/api/torrents/search`.

## Test URLs
- `https://YOUR-WORKER.workers.dev/health`
- `https://YOUR-WORKER.workers.dev/search?q=test&format=json`
- `https://YOUR-WORKER.workers.dev/s?type=search&q=test&page=1`
- `https://YOUR-WORKER.workers.dev/api/torrents/search?q=big%20buck%20bunny&media=movies`
