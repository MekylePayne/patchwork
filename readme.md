# 🧩 Patchwork

**HTML Click-Edit Studio — click the words on your page, watch the code rewrite itself.**
  
![version](https://img.shields.io/badge/version-2.0-c8f14f)![deps](https://img.shields.io/badge/dependencies-zero-c8f14f)![build](https://img.shields.io/badge/build%20step-none-c8f14f)![privacy](https://img.shields.io/badge/privacy-100%25%20local-c8f14f)![](data://7f2381d8-0c8f-46df-ae0e-ddfd25f104d2)

* * *

## What is it?

Patchwork loads any single-page HTML file, renders it live, and lets you edit the text **directly on the page** — headings, paragraphs, buttons, links, list items, table cells. Click it, type over it, and the source code panel rewrites itself in real time.
Think of it as a click-to-edit CMS for static HTML, running entirely client-side.

```
📄 Load pages as tabs  →  🖱️ Click text & type  →  ⚡ Code updates live  →  🧾 Track, diff, snapshot  →  📦 Export
```

## ✨ Features

### Visual editing

*   **Click any text and type** — headings, paragraphs, buttons, links, labels, list items, table cells, quotes, and more
    
*   **Plain-text safe** — edits can't inject markup or break layout; pasted text is flattened automatically
    
*   **Text mode** — rewrite the whole page's copy in one pass, proofreader-style
    
*   **Live word & character count** in the footer while you work
    
*   **Links & buttons never navigate** in preview — you edit their words; URLs in the code stay untouched
    

### Multi-page workflow

*   **Tabs** — open a whole client bundle at once; every page keeps its own undo history, snapshots, and change log
    
*   **Rename** tabs (double-click) to match your export filenames; add pages on the fly
    
*   **Per-page Reset** — each tab remembers its own originally loaded file
    

### Code intelligence

*   **Live code panel** — syntax-highlighted HTML that syncs both directions; hand-edit and hit Apply for instant re-render
    
*   **Click-to-locate** — click any element (even ones built by the page's own scripts) and its exact line **flashes three times**, then stops. Tracing order: id → class → attributes → visible text → a scan of the page's own JavaScript & CSS
    
*   **Locate info bar** — locate an image, script, or stylesheet and a bar appears with **copy URL / open / swap URL** actions; it stays until you move on
    
*   **Find in code** (`Ctrl+F`) — live match counter, highlight overlays synced to scroll, Enter / Shift+Enter to hop
    
*   **Replace all** — one-shot case-insensitive replace across the whole page; perfect for rebrands
    

### Track & compare

*   **Changes log** — every text edit recorded with the exact changed snippet; click any entry to flash its line in the code. Doubles as a client-facing "here's what changed" summary
    
*   **Snapshots** — name and save up to 12 checkpoints per page (`Ctrl+D` for quick snapshots); restoring auto-saves a safety snapshot first
    
*   **Diff view** — side-by-side original vs current with `-`/`+` line stats, so you can review everything before export
    
*   **Safe re-indent on export** (optional) — readable whitespace without touching content, attributes, or `script/style/pre` bodies
    

### Safety nets

*   **Undo / redo** (80 steps deep, per page) plus one-click **Reset to original**
    
*   **Autosave** for all open tabs, with a _Resume_ prompt on return
    
*   **100% local** — no uploads, no accounts, no telemetry; the network is only touched by whatever fonts/images _your page itself_ references
    

### Workspace

*   **Device widths** — full / tablet (768px) / phone (390px), plus 30–200% zoom
    
*   **Resizable split** — drag the divider, resize with arrow keys, double-click to reset
    
*   **Full-width Code mode** when you want to go heads-down
    
*   **Load anything** — drag & drop, file picker, paste source, or the built-in demo page
    

## 🚀 Quick start

### Run locally

1.  Download `patchwork.html`
    
2.  Open it in Chrome, Edge, or Firefox
    

That's it. The file is the entire application.

### Host on GitHub Pages

1.  Create a repository and upload this file renamed to `index.html`
    
2.  **Settings → Pages →** Deploy from a branch → `main` / `/(root)` → Save
    
3.  Live at `https://your-username.github.io/patchwork/` in about a minute
    

No build step, no dependencies, no configuration. Sessions autosave per-browser, so exported files remain your source of truth across machines.

## 🎮 How to use

1.  **Load** — drop a `.html` file in, paste source, or hit _Try the demo page_. Repeat for as many pages as you like — they open as tabs
    
2.  **Edit** — click text and type (`Esc` to finish). Click anything else — or `Alt+Click` — to locate it in the code
    
3.  **Track** — check the Changes log, snap checkpoints with History, review with Diff
    
4.  **Export** — download the finished `.html` or copy it, with optional whitespace re-indent
    

### Keyboard shortcuts

| Key | Action |
| --- | --- |
| `Click` | Edit that text |
| `Alt+Click` | Locate any element in code |
| `Ctrl+F` | Find in code |
| `Ctrl+D` | Save a quick snapshot |
| `Enter` / `Shift+Enter` | Next / previous match |
| `Esc` | Finish editing / close search |
| `Ctrl+Z` / `Ctrl+Y` | Undo / redo (or `Ctrl+Shift+Z`) |
| `Ctrl+S` | Save session locally |
| `Ctrl+Enter` | Apply hand-edited code |
| `Tab` | Indent in the code panel |

## ⚠️ Honest limitations

*   Text written by the page's **own JavaScript after load** isn't click-editable — but clicking it locates the JS line that produces it
    
*   **Relative paths** (`style.css`, `./img/…`) don't resolve inside the sandboxed preview — use full `https://` URLs or inline CSS
    
*   Click-to-locate shows the **best match**, not every occurrence — `Ctrl+F` finds the rest
    
*   Changes-log entries for **deleted-only** edits (text removed, nothing added) can't jump to a line — there's nothing left to find
    
*   Replace-all is **case-insensitive and literal** — no regex mode by design
    
*   Diff skips the middle of files over ~2600 lines so the browser doesn't choke
    
*   Autosave is **per-browser**; sessions don't roam between computers (export early, export often)
    

## 🔧 How it works (for the curious)

*   The page renders inside a **sandboxed iframe**; a small editing engine is injected into it
    
*   Edited elements are matched back to the source via an **ancestor-index path**, so changes survive re-renders, whitespace differences, and attribute reordering
    
*   Change-log entries are computed by **diffing the before/after code**, so each entry names exactly what changed
    
*   Engine artifacts (highlights, editing state, helper elements) are **stripped from every snapshot** before display and export — exported code stays clean
    
*   Vanilla JavaScript, zero dependencies, one file, ~75 KB
    

## 📄 License

MIT — take it, use it, sell it, break it, fix it.

* * *

**Patchwork** — because clients change their minds about _one sentence_, and that shouldn't take an IDE.
