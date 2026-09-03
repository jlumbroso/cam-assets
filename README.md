# cam-assets

Large static files for **Computationally Assisted Metacognition** — podcast
audio, episode video, cover art, and anything else too big to sit in a site repo
that should stay fast to clone and quick to deploy.

Served over GitHub Pages at **cdn.metacognition.computer**.

## Two rules, and the second one is why this repo exists at all

**1. No Git LFS. Ever.** LFS pointers do not resolve over GitHub Pages: Pages
serves the *pointer file* — a ~130-byte text stub — in place of your audio, and
every podcast client then fails in its own confusing way, with nothing reporting
an error. Plain files only. GitHub's hard limit is **100 MB per file**; a
22-minute episode is about 42 MB, so episodes fit with room to spare. A file
that exceeds 100 MB does not belong here — split it or re-encode it.

**2. Never overwrite a published file.** Podcast clients, Apple's artwork cache,
and browser caches all key on URL. Replacing a file in place means some
consumers keep the old bytes indefinitely and never learn otherwise. New
version, new filename — which is why names here carry a term or a date.

## Why files live here rather than in the site repo

The feed URL is `https://metacognition.computer/podcast/feed.xml` and it stays
there permanently. Where the *audio* sits is invisible to every subscriber,
because subscribers only ever hold the feed URL. So this repo can be
reorganised, replaced by a commercial CDN, or emptied and rebuilt without a
single listener noticing.

That is the same property that made self-hosting the feed the right call
(cam-hq ADR-0009, ADR-0015): decisions you can reverse for free are worth making
early, and decisions you cannot should wait.

## Layout

    podcast/    episode audio and cover art, named with the term
    video/      episode video, for YouTube uploads and for the archive

## Bandwidth

GitHub Pages documents a soft 100 GB/month limit. Jérémie is on a GitHub Team
plan with unmetered bandwidth through the academic programme, so that ceiling is
not currently a constraint — and his own note stands: *"success is a good
problem to have; if we have a big audience, I can move the CDN to something
else."* Moving it costs one DNS change, and no listener notices.
