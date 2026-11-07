# Changelog

All notable changes to Banas are documented in this file.

## [0.6.0] — 2026-11-06

### Added

- **Settings → Tags — Treat as done** — When editing a tag, check **Embedded subtitles** and/or **Decoded**; assigned videos light the matching cover icons and are skipped by **Fill missing subtitles** and **Jasna decode** auto-selection (per-video decode from the cover icon still works).
- **Settings → Tags — Show outside library** — When editing a tag, enable **Show tag outside library** so tagged videos show the badge on cards in **content sources**, **Lookup**, **filter**, and **Watch** (not only the local library).
- **Library — Batch set tags** — With multiple videos selected, use **Tags (n)** in the toolbar; **Add**, **Remove**, or **Replace** tags with per-tag coverage counts.
- **Settings → Tools — FFmpeg** — Set the path to `ffmpeg.exe` (or rely on PATH / `FFMPEG_PATH`); required for batch remux.
- **Library — Batch FFmpeg remux** — **Remux selected (n)** opens a batch dialog like Jasna decode (options on the left, video list on the right); same output destination and post-job actions as batch decode. Supports stream-copy remux or re-encode (container, codecs, CRF/preset, scale, hardware accel, video bitrate, extra args).
- **Settings → Display — Code prefix blacklist** — Add/remove prefixes (e.g. `SSIS`); matching titles are hidden in content sources, aggregate watch, and filter browse.
- **Content sources / Filter / Watch — Blacklist** — Context menu **Blacklist code prefix** on a card; pager can show **Ignored n blacklisted code(s)** when any were filtered on that page.
- **Content sources / Filter / Watch — Find subtitles** — Context menu **Find subtitles** runs online subtitle lookup only (same flow as the library subtitle finder).
- **Download sources — Visual pick** — **Visual pick** in the add/edit wizard (webview or Camoufox) to step through list, title, size, date, magnet, and detail selectors, aligned with content-source visual setup.
- **Download sources — URL templates** — **`${keyword+suffix}`** (and **`${wd+}`** / **`${q+}`** aliases) append custom text before encoding, e.g. `${keyword+-c}` or `${keyword+ LTX}`; shared with content-source list/search URL building.
- **Download sources — Tag help** — **Tag help** on the add/edit wizard footer (same sheet as content sources), including documentation for **`${keyword+}`**.
- **Watch — Aggregate watch** — In **Manage** mode, each watched content source shows **Disable watch** to turn off aggregate watch without leaving the Watch pane.
- **Watch — Clear results** — Aggregate watch toolbar adds **Clear downloaded** and **Clear in library** (alongside existing clear-all), scoped to the current source.
- **Watch — Date filter** — Top-right **button group**: All, Today, Yesterday, This week, This month, and **Date range** (dropdown panel); default All. Poll/clear controls stay on the top bar; per-source status moves to the **left of the bottom pager**.
- **Dock — Lookup** — Dock entry renamed from code-only search to **Lookup**; recognized product codes still open the cover card, otherwise input is treated as an **actress name** and opens her works from the filter catalog when matched.
- **Settings → Cover rules** — **Export** / **Import** full cover-rule packs (user rules, base URLs, URL preset, Papakatsu segment, prefix overrides); import replaces current cover-rule settings after confirmation.
- **Filter — Actresses I like** — **Add to actresses I like** / **Remove** on the actress browse header (top right).

### Changed

- **Download sources — Search URL hint** — Copy explains **`${keyword+suffix}`** alongside plain **`${keyword}`**.
- **Content sources — Search/list URLs** — **`${keyword+suffix}`** expansion uses the same template helper as download sources.
- **Content sources / Filter — Blacklist paging** — If every item on a page is blacklisted and the next page might have visible results, the app **auto-advances** to the next page (does not loop when nothing was blacklisted on that page).
- **Filter — Actresses I like** — **Add to actresses I like** is **rejected** with a catalog hint when the actress is not in the filter library (remove unchanged).
- **App — Quit while jobs run** — Closing the app while **Jasna decode** or **FFmpeg remux** is active shows a confirm dialog (quit aborts running jobs).

### Fixed

- **Download sources — Laowang-class sites** — Crafted `/search?…` URLs that redirect to the homepage now use **Camoufox homepage form search**, reject homepage HTML as empty results, and wait for real result panels; **magnet-from-detail** follows the live search session instead of opening crafted detail URLs that bounce home.
- **Download sources — Laowang-class pagination** — Page 2+ avoids redundant full cold CF passes where possible; pager clicks wait for the active page to advance.
- **Download sources — List selectors** — Auto-parse favors panels that contain `/detail/` links; custom selectors like `div.search-panel:nth-child(n+3)` map more reliably to result rows.
- **Download sources — `${keyword+ LTX}`** — Form-based search submits the **expanded** query (e.g. `MIDV-777 LTX`), not the bare code.
- **Download / content sources — Camoufox visual pick** — Clears stale profile locks and coordinates shutdown of silent fetch before headed Camoufox launch, reducing “profile in use” / launch failures when switching between background fetch and visual picker.
- **Content sources — JAVDB** — JAVDB listings no longer hard-block Camoufox; HTML mode uses HTTP with **automatic Cloudflare fallback**, browser mode can force Camoufox, and the **over18** age gate is dismissed when needed.
- **Settings → Cover rules — MGStage-style URLs** — Cover URL parse/add supports paths like `image.mgstage.com/.../022sparf/.../pb_p_sparf-2004.jpg` (maker folder + stem patterns).
- **Startup** — Fixed infinite re-render after blacklist/tag-outside-library work that left the app stuck on **Loading content…**.
- **Library — Move & archive on NAS/SMB** — Cross-volume move/archive progress and speed track **flushed bytes** (not write-cache only), reducing fake hundreds-of-MB/s and long **99%** stalls; archive uses async transfer with job **%/speed/ETA** instead of blocking `copyFileSync`.
- **Library — Move** — If the database update fails after a successful file transfer, the video file is **rolled back** to the original path when possible.
- **Watch** — Removing a watch result from the context menu updates the grid **only after** the remove IPC succeeds (no optimistic drop on failure).
- **Content sources — Search** — Clearing or emptying search no longer leaves the **previous section’s** grid visible.
- **Library — Scan** — Transient `stat` failures (AV lock, etc.) no longer cause videos to be **pruned** from the library; directory walks guard against symlink/junction loops.
- **Download sources — Free tier** — Daily download-search quota is consumed **before** the search write/network work, not after.
- **Filter — Actress catalog** — Large actress matching uses **SQL pagination/chunking** instead of loading the full table into memory.
- **Stability** — Camoufox worker single-flight/timeouts, watch resource-probe abort on timeout, bounded cover-URL cache (LRU), library sidebar root sync with persisted selection.

### Notes

- Tag **done-mark** flags migrate automatically (`marks_embedded_subtitle`, `marks_decoded` on `user_tags`).
- **Code prefix blacklist** and **show tag outside library** persist in local settings / tag rows (no cloud sync).
- **Cover rules export** uses pack format `banas-cover-rules` v1 (full settings snapshot).

## [0.5.0] — 2026-11-02

**How to add content sources and download sources:** ++[https://github.com/banasapp/banas/blob/main/HOW-TO-ADD-SOURCES.md](https://github.com/banasapp/banas/blob/main/HOW-TO-ADD-SOURCES.md)++

**[Download Sources & a quick how-to guide for everyone!]:** [https://github.com/banasapp/banas/issues/1](https://github.com/banasapp/banas/issues/1)

**[Content source file]:** [Sharing my Content Sources · Issue #2 · banasapp/banas](https://github.com/banasapp/banas/issues/2)

### Added

- **Settings → Tags** — Create and manage custom library tags (name, text/background colors, optional icon); assign from a cover’s context menu; badges on the cover (bottom-right) and on the movie detail page.
- **Filter — Actresses I like** — Sidebar entry under **Filter** lists manually added actresses; open an actress’s online film list from the filter catalog when matched.
- **Dock — Actresses I like** — Heart button on the left rail (between Jobs and code lookup) opens a searchable, paginated list; tap a name to open her filter browse.
- **Covers / library / content sources** — Context menu **Add to actresses I like** / **Remove from actresses I like**; when the card has no actress, lookup title/actress first (same flow for library and content sources).
- **Filter — actress browse** — **Local only** checkbox on the pager (left of pagination) switches the actress page to paginated films from your local library instead of the online catalog list.
- **Download sources — query results** — When a resource title contains a recognized product code and a cover resolves, an image icon appears before the name; hover shows a cover preview (no icon if unmatched).
- **Library — Jasna decode** — **LTX Basic** restoration model for **Jasna v0.12.1+**; decode dialog copy updated (0.11.x LTX weights may need re-download).

### Changed

- **Filter — liked actresses** — Opening a liked actress from the dock or filter menu follows the same online allowance as other filter browse (`allowOnline`), consistent with the free-tier rules.
- **Covers — liked actresses** — Adding to **Actresses I like** plays a short heart animation from the actress name (or cover) to the dock heart button (respects reduced motion).

### Fixed

- **Covers / library / content sources — liked actresses** — **Add to actresses I like** no longer overwrites existing title or actress metadata when both are already set; lookup runs only when actress names are missing.
- **Filter — actress browse** — Actress film lists no longer reload repeatedly when online detail backfills the actress name on the card.

### Notes

- Liked-actress and tag data stay in the local database; nothing is synced to the cloud.

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
- Multilingual **How to export & import content and download sources** guides (`HOW-TO-IMPORT-EXPORT-SOURCES*.md`) cover sidebar encrypted `.banas` packs.

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
