# How to add content & download sources

**Languages:** [English](HOW-TO-ADD-SOURCES.md) · [简体中文](HOW-TO-ADD-SOURCES.zh-CN.md) · [繁體中文](HOW-TO-ADD-SOURCES.zh-TW.md) · [日本語](HOW-TO-ADD-SOURCES.ja.md) · [한국어](HOW-TO-ADD-SOURCES.ko.md) · [ภาษาไทย](HOW-TO-ADD-SOURCES.th.md) · [Tiếng Việt](HOW-TO-ADD-SOURCES.vi.md)

**Content sources** browse site lists and cover walls. **Download sources** search magnets (or similar) by product code. Banas does not host third-party sites—you configure the URLs and selectors yourself.

Back to the main [README](README.md).

---

## Content sources

Left rail → **Content sources** → sidebar **Add**.

### Step 1 — Target URL

| Option | What it does |
| --- | --- |
| **Target URL** | List page or home, e.g. `https://example.com/` |
| **Enable VPN** | Requires nodes/subscription under **Settings → Network** |
| **Visual add** (recommended, on by default) | Pick fields on the live page; no hand-written CSS |
| **Auto parse** | Available when Visual add is off; the app guesses selectors |
| **Bypass anti-bot detection** | For Cloudflare-style checks; Visual add uses the embedded page |

Enter the URL → **Next**.

### Visual picking (recommended)

Follow the panel steps and click matching elements:

1. **Items** — a list card (whole row/card)
2. **Code/title** — the code or title text inside an item
3. **Cover** (optional) — cover image inside an item
4. **Studio / Actress / Pagination** (optional)
5. **Sections** — category / nav links

Toggle **Pick / Click**: use **Click** for age gates or login; use **Pick** to capture selectors. If Cloudflare never clears, use **Open in Camoufox**. When done, continue to the confirm form.

### Step 2 — Confirm source details

#### Basics

| Field | How to fill |
| --- | --- |
| **Name** | Label in the sidebar (required) |
| **Group** | Pro; create a group first if needed |
| **List URL** | List template; may include tags below |
| **Fetch mode** | `HTML page` / `JSON API` / `JS render (browser)` |
| **Watch new items** | Pro; feeds aggregate watch |

**List URL tags** (use **Tag help** to copy):

| Tag | Meaning | Example |
| --- | --- | --- |
| `${page}` | Page number; with `/page/${page}`, page 1 drops `/page/1` | `https://xxx.com/page/${page}` |
| `${page*}` | Optional pager; page 1 omits the whole segment | `https://xxx.com/?page=${page*}` |
| `${keyword}` / `${wd}` / `${q}` | Search keyword | Use in search URL templates |
| `${date}` | Today `YYYY-MM-DD` | `?dateFrom=${date}` |

#### Parsing (HTML / browser)

| Field | How to fill |
| --- | --- |
| **Smart parse** | On: extract codes by rules. Off: you must fill selectors |
| **Item selector** | Each list row, e.g. `.movie-box`, `article.item` |
| **Code/title selector** | Relative to each item |
| **Studio / Actress / Date** | Optional, relative to each item |
| **Skip titles (codes only)** | When titles mix other languages with the code |
| **Code regex** | Pull the code from the title text |
| **Wait selector** | Browser mode: wait for this element before parsing |

JSON mode uses list path, title/cover/detail ID fields, detail URL template (MacCMS preset available).

#### Cover

| Option | Meaning |
| --- | --- |
| **Hybrid** (common) | Built-in HD rules first, then site image |
| **Built-in** | Built-in rules by code only |
| **Site source** | List-page image selectors only |

Site / hybrid need **Image selector** and **Image attributes** (e.g. `data-src, src`).

#### Advanced (common)

| Field | How to fill |
| --- | --- |
| **Publish page URL** | If the main URL dies, fetch a new address from this page and retry |
| **Site search** | Enable and set a search URL, e.g. `/search?q=${keyword}` |
| **Play on source site** | Pro; resolve m3u8/direct from the cover |

Right panel **Sections**: **Fetch sections** or add name + URL template manually.

Click **Test** until items appear, then **Save**.

---

## Download sources

Left rail → **Download sources** → **Add download source**.

### Step 1 — Target URL

Enter the site home or search page, e.g. `https://1cili.net/`. Optional:

- **Enable VPN**
- **Bypass anti-bot detection** (slower; use on challenge sites)

**Next** — the app tries to detect the search URL and list fields.

### Step 2 — Confirm search rules

| Field | How to fill |
| --- | --- |
| **Name** | Display name |
| **Host match** | Usually filled from the host |
| **Search URL** | **Must include a keyword placeholder**, e.g. `https://xxx.com/search?q=${keyword}` |
| **List** | Selector for each result row |
| **Title / Size / Date** | Relative to each list item |
| **Magnet** | Selector for a `magnet:` link on the list |
| **Detail page** | Detail link selector |
| **Magnet is on the detail page** | When the list has no magnet; open detail to fetch it |
| **Test keyword** | e.g. `IPX-001` — use **Test** before saving |

Search URL also accepts `${wd}`, `${q}`, `${code}`, `${CODE}` (uppercase), `{0}` (keyword), `{1}` / `${page}` (page).

When the test returns rows, **Save**. Open the source, enter a code → **Find resources** → copy magnet or open detail.

---

## After saving

| Goal | Action |
| --- | --- |
| Browse covers | Content source → open it → sections / search / paging |
| Find downloads | Cover download button, or search inside a download source |
| Watch new titles | Enable **Watch new items**, or add aggregate watch |
| Watch a code for magnets | Need a download source first → cover bell or resource watch |
| Sync machines | Sidebar **Import / Export** (encrypted packs) — see [How to export & import sources](HOW-TO-IMPORT-EXPORT-SOURCES.md) |

Default download sources for resource watch: **Settings → Watch**.

---

## Common mistakes

1. **Search URL without `${keyword}`** — queries never hit the right page.
2. **Picked a detail block instead of a list card** — choose a grid/list card in Visual add.
3. **Selectors scoped to the whole page** — title/magnet selectors should be relative to the **item**.
4. **Challenge site without Camoufox / Visual add** — empty parse or failures.
5. **VPN on without network config** — set **Settings → Network** first.
6. **Plan limits** — free plan allows limited content sources; download / watch need trial or Pro.
