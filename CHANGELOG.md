# Changelog

All notable changes to Banas are documented in this file.

## [0.4.0] — 2026-10-29

### Added

- **Settings → Download** — Choose what the cover download button does: open the download-source list, or open Find directly with a preferred source; optional **downloaded mark** (orange icon after opening a magnet from Find).
- **Download sources / covers** — With only one download source configured, the cover download button opens Find directly (skips the source picker).
- **Content sources — playback** — When a page resolves multiple streams, the built-in player shows a compact source control (hover to switch); the system player still opens the best URL only.
- **Content sources — covers** — Better support for CSS `background-image` thumbnails, `blob:` list images (browser / Camoufox materialize), and page JSON / RSC cover maps when `<img>` is empty.
- **Covers / content sources** — Context menu **Look up rule** opens **Settings → Cover rules → Find** with the card’s code prefilled; **Refresh cover** rebuilds the tile from current cover rules.
- **Settings → Cover rules → Find** — **Add to rules** after copying a cover URL: fills **Parse from cover URL** and runs parse / fill.
- **License (free after trial)** — Partial access instead of blocking all online modules: **5 download searches per day**, browse **one** content source (first added), **Live** browse without play; **Watch** and **Filter** stay fully locked; the license page shows daily download-search usage.

### Changed

- **License** — After the 3-day trial, free tier is granular (above); local library scan / browse / organize remain free. Pro is still required for unlimited download search, multiple content sources, Live play, Watch, Filter, and other paid modules.
- **Content sources** — Cloudflare / Camoufox browsing reuses clearance cookies across pages, avoids redundant cold browser passes, shows the list sooner, and loads covers asynchronously on blob-heavy sites.
- **Content sources — visual add** — Age-gate flow: picking pauses while you click through gates; **Open in Camoufox** for hard Cloudflare during visual setup.
- **Dock / license UI** — Free users see Pro-required hints on **Watch** and **Filter**; Live, Content sources, and Download sources remain partially usable under the free caps.

### Fixed

- **Watch** — Aggregate watch refreshes the results view when a poll finishes with new items.
- **Covers / UI** — Context menus on the bottom row of cover grids reposition to stay inside the window.
- **Content sources — playback** — Extra background audio no longer plays when switching multiple streams in the built-in player.
- **Content sources** — CF-heavy sources (e.g. Manko / SUPJAV): stuck anti-bot states, missing covers, and slow paging after cookie / session changes.

### Notes

- Multilingual **How to add content & download sources** guides ship with the public distribution docs (`HOW-TO-ADD-SOURCES*.md`).

## [0.3.0] — 2026-10-23

### Added

- **Settings → Display** — Cover button visibility: **Always visible** (default) or **Show on hover**; when set to hover, overlay actions on cover cards appear only while the pointer is over the card.

## [0.2.0] — 2026-10-21

### Added

- **Onboarding** — First-run dock spotlight tour for each left-rail module (skip / back / next); replay from **Settings → General**.
- **Filter** — Encrypted filter API origin pack (`data/filter-origin.banascfg`); configure and export under **Settings → Developer**; lookups use the installed pack (fallback when missing).
- **Filter** — Sidebar **Update** (beside Manage): pull origin from `banasapp/banas`, incrementally refresh the actress catalog, republish `catalog.banascat`; progress dialog with cancel.
- **Library** — Move videos between local folders (single or batch); optional actress-folder layout preserved when moving.
- **Library** — Context menu **Browse actress films** — match a tagged actress against the filter catalog and open her online list (submenu when several are tagged).
- **Library** — Title-only videos without a product code: filename as title; scan, index, and archive without forcing a code.
- **Watch** — Aggregate watch lists watched content sources with result counts and an **All** row; per-source status dots.
- **Content sources** — MacCMS-style play pages (`/index.php/vod/play/...`): parse `player_aaaa` / encrypted play URLs for source-site playback.

### Fixed

- **Library** — Opening a folder no longer waits on scan while Jasna decode (or other long jobs) holds the heavy queue; indexed library shows immediately, scan finishes in the background and refreshes quietly.
- **Jobs** — Jasna decode no longer blocks scan / organize / download / title-fill heavy jobs.
- **Library** — Switching folders could show the wrong grid, stay stale, or go blank; selection and loads track the active folder reliably.
- **Library** — **By actress** view showed video counts on cards instead of actress names.
- **Content sources** — Source-site playback for Apple CMS–style pages that embed the stream in page JSON rather than plain `https://` links.

### Changed

- **Library** — Opening a folder loads the index first; background rescan only if never scanned or last scan was more than 5 minutes ago (manual **Scan folder** unchanged).
- **Filter** — Catalog update continues with the local origin if GitHub fetch fails; actress catch-up stops after two consecutive pages with no new entries; origin URL hidden in the update UI.
- **Privacy** — System tray uses the BANAS logo when the packaged window `.ico` is missing.
- **Covers / UI** — Cover tiles use zoom (`object-cover`) so posters are less clipped; content-source title hover shows the title.

### Notes

- Public filter origin pack: `banasapp/banas` → `data/filter-origin.banascfg` (GitHub raw / jsDelivr).

## [0.1.0] — 2026-10-20

First public release.

### Added

- **Library** — Add local folders, scan videos, browse by movie or actress; fill covers, titles, and subtitles; archive with Emby-style or custom templates (`movie.nfo`, `poster.jpg`, etc.); Jasna decode and Transub subtitle helpers.
- **Covers** — Look up covers by product code; built-in CDN/rule presets; custom rules with manage and diagnose tools.
- **Filter** — Actress, label, maker, and genre catalogs; search, random browse, and local manage/import/export (`catalog.banascat`).
- **Content sources** — Custom site lists (HTML / JSON / browser render); smart parse and visual field picking; groups; encrypted import/export packs.
- **Download sources** — Search by code or keyword; copy magnet or open results; pin to shortcuts; import/export.
- **Watch** — Aggregate watch (new items on content sources) and resource watch (whether a code has downloads); configurable poll interval.
- **Live** — Browse by category, favorites and recent; built-in web page or Transub Player (recording on public rooms).
- **Shortcuts & Jobs** — Pin frequent sources and code lookup; background job queue with progress, retry, and cancel.
- **Privacy** — Hide to system tray, startup password, boss key.
- **Settings** — General/display, title & actress sources, archive templates, cover rules, watch, live, network/VPN, tools paths, backup/restore, license.
- **Localization** — English, 简体中文, 繁體中文, 日本語, 한국어, ภาษาไทย, Tiếng Việt.
- **License** — 3-day full trial; after trial, local library scan/browse/organize remain free; online fill, batch organize, sources, download, and watch require Pro (UniFans activation; one PC per code, 30-day rebind cooldown).

### Notes

- All library indexes and configs stay on disk under `data/` next to the app; nothing is uploaded except limited license-check metadata when online.
- User-added sources, proxies, and third-party sites are the user’s responsibility. Banas does not host or operate any third-party content.
