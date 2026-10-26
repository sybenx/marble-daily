# marble-daily

One glass marble a day for the [Marble](https://github.com/sybenx/marble) app. Each one is rendered
overnight on a Mac mini at home with a local image model, checked automatically, cut into a circle,
named, and kept private until its day. It is published here at 00:00 UTC on its day.

- Manifest: <https://sybenx.github.io/marble-daily/manifest.json>
- Images: `marbles/YYYY-MM-DD.png`, 768×768 PNG with a transparent background (just the marble; the app draws the shadow)

## manifest.json

```json
{
 "version": 1,
 "updated": "2026-10-26T09:12:40Z",
 "days": [
  {
   "id": "marble-2026-10-27",
   "date": "2026-10-27",
   "name": "Cobalt Comet",
   "style": "cobalt-swirl",
   "image": "https://sybenx.github.io/marble-daily/marbles/2026-10-27.png",
   "sha256": "…",
   "size": 768,
   "seed": 123456789,
   "model": "z-image-turbo-4bit (mac mini)",
   "status": "ok"
  }
 ]
}
```

- `days` is sorted by `date`, oldest first. Entries are never removed or renamed, so `id`, `date`, `name` and `image` are stable.
- `date` is a UTC calendar date. A marble is the marble of the day from 00:00 to 24:00 UTC on its `date`, the same day for everyone. The app should pick the entry whose `date` equals today's UTC date.
- An entry appears within about 10 minutes after 00:00 UTC on its day (plus GitHub Pages' build time and cache, up to ~10 more minutes). Future marbles are never in the manifest.
- `status` is `ok` or `vetoed` (vetoed after it went live). Treat `vetoed`, a missing day or a failed fetch the same way: show a marble from the app's bundled rotation. Re-fetch now and then during the day; a missing entry early in the day may still arrive.
