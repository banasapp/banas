# How to export & import content and download sources

**Languages:** [English](HOW-TO-IMPORT-EXPORT-SOURCES.md) · [简体中文](HOW-TO-IMPORT-EXPORT-SOURCES.zh-CN.md) · [繁體中文](HOW-TO-IMPORT-EXPORT-SOURCES.zh-TW.md) · [日本語](HOW-TO-IMPORT-EXPORT-SOURCES.ja.md) · [한국어](HOW-TO-IMPORT-EXPORT-SOURCES.ko.md) · [ภาษาไทย](HOW-TO-IMPORT-EXPORT-SOURCES.th.md) · [Tiếng Việt](HOW-TO-IMPORT-EXPORT-SOURCES.vi.md)

Pack configured **content sources** or **download sources** into an encrypted `.banas` file for another PC, backup, or your other devices. Content-source packs and download-source packs are separate—do not mix them.

To create new sources: [How to add content & download sources](HOW-TO-ADD-SOURCES.md). Back to the main [README](README.md).

---

## Where to open

| What to export / import | Entry |
| --- | --- |
| Content sources | Left rail → **Content sources** → **Import / Export** beside the sidebar title (two-way arrow) |
| Download sources | Left rail → **Download sources** → **Import / Export** beside the sidebar title |

The dialog has two tabs: **Export** and **Import**. The hint says files are saved encrypted; on import you can select only the items you need.

---

## Export

1. Open **Import / Export** for that module and stay on the **Export** tab.
2. The list shows sources already on this machine (name + URL). All are selected by default; uncheck any you do not want.
3. Click **Export selected** → choose path and filename in the save dialog.
4. Default names look like:
   - Content sources: `banas-custom-sources-YYYY-MM-DD.banas`
   - Download sources: `banas-download-sources-YYYY-MM-DD.banas`
5. Success shows “Exported N item(s)”.

**What is in the pack**

| Kind | Included |
| --- | --- |
| Content sources | Name, list URL, cover/detail fields, full config (selectors, sections, watch flags, etc.); group name if any |
| Download sources | Name, search URL, full config (list / magnet selectors, etc.) |

The file is encrypted for this app only—import it in Banas; do not edit it as plain JSON.

If the sidebar has no sources yet, you see “Nothing to export”—add sources first, or import from elsewhere.

---

## Import

1. Open **Import / Export** in the **same** module (content pack → content sources; download pack → download sources), switch to **Import**.
2. Click **Choose import file…** and pick a previously exported `.banas` file.
3. After decrypt, items in the pack are listed; all selected by default—uncheck what you do not need.
4. Click **Import selected**. Result looks like: “Import done: added X, skipped Y, failed Z”.

**Result meanings**

| Result | Meaning |
| --- | --- |
| **Added** | No matching local item; written to the DB |
| **Skipped** | Local already has the same **name + URL**; local config is not overwritten |
| **Failed** | Invalid item, or hit free-tier limits / Pro required; on quota errors later items may stop |

**Content sources — extra**

- If the pack has group names and your license allows content-source groups, existing groups are reused by name or created when missing.
- Free tier has a source limit; over quota fails or asks for trial/Pro.
- Sources with **Watch new items** on re-init watch state for the new IDs after import.

**Notes**

- Import in the matching module only: a download pack will not open under content sources (and vice versa)—you get invalid/corrupt.
- Wrong extension, damaged file, or a pack not from this app → “Invalid or corrupt import file”.
- If you wait too long after choosing a file before importing, preview may expire → “Import preview expired; choose the file again”.

---

## Suggested uses

| Scenario | What to do |
| --- | --- |
| New PC / multi-machine sync | Export `.banas` on the old machine → copy → import in the matching module and select what you need |
| Back up only a few sources | Uncheck the rest on export |
| Pack from someone else | Check list URLs first, then select; same name+URL items are skipped |
| Full backup (settings, shortcuts, …) | Use **Settings → Backup** export/import (JSON data pack)—different from sidebar `.banas` source packs |

Sidebar packs move content or download sources only; Settings data packs cover broader config and library data. They do not replace each other.

---

## Common mistakes

1. **Importing a download pack under content sources (or the reverse)** — kinds must match.
2. **Expecting import to overwrite same-name sources** — dedupe is **name + URL**; existing rows are skipped. To refresh, edit/delete locally then import again.
3. **Editing `.banas` as text** — encrypted; only import/export inside the app.
4. **Free content-source slots full** — remove unused sources or upgrade, then import.
5. **Cannot find the exported file** — check the path from the save dialog; default names include the date and `custom` / `download`.
6. **Want groups and watch settings too** — sidebar content-source export already includes them in the pack; copying only the DB is a different path.
