# Banas

**Languages:** [English](README.md) · [简体中文](README.zh-CN.md) · [繁體中文](README.zh-TW.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [ภาษาไทย](README.th.md) · [Tiếng Việt](README.vi.md)

Local library manager and metadata scraper: scan local videos, fill covers and titles by product code, and organize folders with Emby-style or custom templates.

Add your own content sources, download sources, and other site configs. Banas does not host or operate any third-party websites or online content.

UI languages: English, 简体中文, 繁體中文, 日本語, 한국어, ภาษาไทย, Tiếng Việt.

Works closely with Jasna (video decode), Transub (subtitles), and Transub Player. Set paths under **Settings → Tools** or **Settings → Live**.

**Docs:** [How to add content & download sources](HOW-TO-ADD-SOURCES.md) · [How to export & import sources](HOW-TO-IMPORT-EXPORT-SOURCES.md)

---

## Features at a glance

| Module | Purpose |
| --- | --- |
| **Library** | Scan local folders; fill covers / titles / subtitles; archive by template |
| **Covers** | Look up and save covers by product code (built-in rules; editable) |
| **Filter** | Actress, label, maker, and genre catalogs; search and random browse |
| **Content sources** | Custom site lists; HTML / JSON / browser render; visual field picking — [how to](HOW-TO-ADD-SOURCES.md) |
| **Download sources** | Find resources by code or keyword; copy or open results — [how to](HOW-TO-ADD-SOURCES.md) |
| **Watch** | Poll content sources for new items, or poll whether a code has downloads |
| **Live** | Browse streamers by category; favorites and recent; built-in page or Transub Player |
| **Shortcuts & Jobs** | Pin frequent sources; view and retry background jobs |
| **Privacy** | Tray hide, startup password, boss key |

---

## How to use

Left rail switches modules; the secondary sidebar lists and manages the current module; the main area shows cover grids, tables, or settings. Use the gear next to the sidebar title for manage (reorder, edit, delete).

### Library

1. Sidebar **Add folder** → pick a folder, name it, choose cover source (built-in rules / local images) → save.
2. Select a folder or **All folders** → **Scan**; use search and filters such as missing covers.
3. Toolbar: switch **by movie / by actress**, batch **fill covers, titles, subtitles**, plus **archive** and **Jasna decode**.
4. Click a cover for details (play, open folder, edit); right-click to look up title / cover, archive, or move to an actress folder.

Related settings: **Title & actresses**, **Movie archive** (path templates, `movie.nfo` / `poster.jpg`), **Tools** (Jasna, Transub).

### Covers (code lookup)

1. At the bottom of **Shortcuts**, enter one or more codes (or drop files into the main area; the filename is used as the code) → **Find**.
2. Click a result to preview and switch image sources; right-click to save the cover.
3. Edit and diagnose rules under **Settings → Movie covers**.

### Filter

1. Sidebar **Actresses / Labels / Makers / Genres** → search and pick an entry in the catalog popup.
2. Main area shows related videos; sidebar **Refresh** updates the catalog pack.
3. **Manage** to add, edit, remove, import, or export entries; data lives in `catalog.banascat`.

### Content sources

1. **Add** → enter a site URL → **smart parse** or **visual pick** (items, code, cover, paging, etc.) → test → save; optional groups.
2. Open a source: switch columns, search on-site, paginate the cover wall.
3. Covers can play (local first, otherwise parse then Transub Player), look up downloads, or join resource watch; source menu can enable aggregate watch or add to shortcuts.
4. Sidebar **Import / Export** encrypted packs for syncing across machines.

Detail: [How to add content & download sources](HOW-TO-ADD-SOURCES.md). Import / export: [How to export & import sources](HOW-TO-IMPORT-EXPORT-SOURCES.md).

### Download sources

1. **Add download source** → configure the search URL (with keyword placeholder) and list fields → save.
2. Open a source, enter a code → **Find resources** → open detail, copy magnet, or start download in the table.
3. Pin to shortcuts; import / export works the same. Default download source for resource watch is under **Settings → Watch**.

Detail: [How to add content & download sources](HOW-TO-ADD-SOURCES.md). Import / export: [How to export & import sources](HOW-TO-IMPORT-EXPORT-SOURCES.md).

### Watch

1. **Add watch**: **Aggregate** (pick content sources for new codes) or **Resource** (enter codes to watch for downloads).
2. View results under **Aggregate watch / Resource watch**; toolbar can **poll now** or clear.
3. Bells on content-source sidebar or covers also toggle watch. Intervals are under **Settings → Watch**.

### Live

1. Pick a category, or open **Favorites / Recent**; search for streamers.
2. Open a room: choose **built-in web** (interactive) or **Transub Player** (recording; public rooms) from the toolbar or **Settings → Live**.
3. Heart to favorite; category visibility and live mirrors are under **Settings → Live**.

### Shortcuts

1. Sidebar **+** → select content or download sources → save; one click opens browse or lookup.
2. Bottom **code lookup** finds covers directly.
3. **Settings → General → Startup page** sets which module opens in the main area (rail can stay on Shortcuts).

### Jobs

Left-rail **Jobs** shows the background queue (scan, cover download, watch poll, archive, decode, etc.). View progress, **retry** or **cancel**, and clear finished items.

### Privacy & tools

- **Settings → Privacy & security**: hide to tray on close/minimize, startup password, boss key.
- **Settings → Tools**: paths for Jasna, Transub, Transub Player; the Tools menu on the left rail can also launch them.
- **Settings → Backup**: back up / restore the database, or export / import config and source packs (excludes password and license key).

---

## Data

Video index, settings, and the filter catalog stay on your machine and are not uploaded.

```
Library & settings: <folder of Banas.exe>/data/javgt.sqlite
Filter catalog:     <folder of Banas.exe>/data/catalog.banascat
```

To back up or move the app, copy the entire `data` folder.

---

## License

Full trial for 3 days on first use. After the trial you can still scan, browse, and organize the local library; online fill, batch organize, content sources, download sources, and watch require Pro.

After purchasing on UniFans, wait for the activation code and paste it under **Settings → License**. Each code binds to one PC; rebind cooldown is 30 days. Durations: one year, two years, or lifetime.

---

## Notes

Settings, library, and license data are mainly local. When online, limited technical info (such as a device id) may be sent for license checks.

Availability and compliance of user-added sources (including filter catalogs, content sources, download sources), proxies, and third-party sites are the user’s responsibility.
