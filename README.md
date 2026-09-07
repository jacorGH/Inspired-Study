# Berea

A single-file study Bible for the browser. Works offline, runs from GitHub Pages for free, and lets a group read together over a peer-to-peer connection.

The name is from Acts 17:11 — the Bereans "searched the scriptures daily, whether those things were so." That's the design goal: compare translations, follow cross-references, check the original languages, verify rather than assume.

---

## Contents

- [What's in it](#whats-in-it)
- [Setting it up](#setting-it-up)
- [Using it](#using-it)
  - [Reading and marking up](#reading-and-marking-up)
  - [Compare](#compare)
  - [Tabs](#tabs)
  - [Search](#search)
  - [Study sessions](#study-sessions)
  - [Hebrew and Greek](#hebrew-and-greek)
  - [Cross-references](#cross-references)
  - [Apologetics practice](#apologetics-practice)
  - [Backup and restore](#backup-and-restore)
- [Data sources and licences](#data-sources-and-licences)
- [Why no NIV or NKJV](#why-no-niv-or-nkjv)
- [How it's built](#how-its-built)
- [Troubleshooting](#troubleshooting)

---

## What's in it

- **Six public-domain translations** — KJV, WEB, ASV, BBE, Darby, YLT (New Testament only)
- **Full offline reading and search** once a translation is downloaded
- **Side-by-side compare** of any two translations, rendered as facing pages
- **Cross-reference tabs** holding several passages at once, side by side
- **Highlights and per-verse notes**, attached to the verse rather than the translation
- **Peer-to-peer study sessions** with host migration and optional shared markup
- **Strong's Concordance** with tap-a-word Hebrew/Greek lookup
- **Treasury of Scripture Knowledge** — the classic cross-reference set
- **Nave's Topical Bible** — study by subject rather than by passage
- **AI cross-reference prompts** that work with any AI chat, no API key needed
- **Apologetics practice** — six common objections with response outlines
- **Backup and restore** to a file
- **Installable** to a phone home screen as a full-screen app

---

## Setting it up

1. Create a GitHub repository (public, if you want free Pages hosting).
2. Add these files to the root:
   - `berea.html`
   - `icon.png` — square, **180×180**, **no transparency** (iOS renders transparent areas black)
3. In **Settings → Pages**, set the source to your `main` branch, root folder.
4. Open `https://<your-username>.github.io/<repo>/berea.html`.

To use `berea.html` as the site's landing page, rename it `index.html`.

**On iPhone:** open the page in Safari, then Share → *Add to Home Screen*. It launches full screen with your icon. If you'd already added it before setting up the icon, remove it and re-add — iOS caches aggressively and won't re-check on its own.

No build step, no dependencies to install, no server. The only external file is the PeerJS library, loaded from a CDN and used solely for study sessions.

---

## Using it

Nothing needs configuring to read. Tap the reference in the top bar to jump to any book and chapter; the dropdown beside it switches translation.

**Worth doing first:** open **Library → Translations** and download KJV or WEB. That makes the whole Bible available offline and switches on full-text search. Everything else in Library is optional.

### Reading and marking up

Tap any verse for its menu:

- **Highlight** in five colours. Highlights are keyed to the verse, so marking John 3:16 marks it in every translation.
- **Write a note.** Notes save on every exit path — colour tap, Close, or tapping the backdrop — so a typed note can't be lost by dismissing the sheet the "wrong" way. A small ✎ marks any verse that has one.
- **Pin as a tab**, or add to an existing tab.
- **Cross-references**, traditional or AI-assisted.

### Compare

Shows one chapter in two translations as facing pages with a spine between them. Choose a translation per page. Highlights and notes appear on both sides.

### Tabs

A tab holds a *set* of passages and displays them side by side. This is what makes connections visible — put Matthew 27:46 beside Psalm 22:1 and you can see Jesus quoting the psalm from the cross. Two tabs ship pre-made as examples.

Tabs sit in the strip above the bottom bar. Tap to open, **+ tab** to create one from the current chapter, × to remove.

Inside an open tab, **+ Add a cross-reference passage** accepts plain references — `Romans 8:38-39`, `ps 22`, `1 cor 13:4-7`, `jn 3:16` all parse. Single-chapter books resolve sensibly too: `2 John 5` means chapter 1, verse 5.

### Search

Three modes:

| Mode | Searches |
|---|---|
| **Verses** | Full text of downloaded/cached translations. Tap to jump, or pin straight to a tab. |
| **Tabs** | Your saved tabs, by name or by any reference inside them. |
| **Topics** | Nave's Topical Bible, once downloaded — by subject rather than wording. |

Search only covers text stored on your device, so downloading a translation makes it substantially more useful.

### Study sessions

Tap **Start a Study**, then share the link through any messaging app. Whoever opens it joins immediately — no code to type, since the room code travels in the URL.

- **Leading** — the leader's navigation moves everyone following along. Anyone can *Take the lead*; anyone can switch off *Follow along* to read independently.
- **Sharing highlights and notes** — off by default. Switch it on and your marks go to everyone else who also has it on, and theirs are saved to your copy. Leave it off to read along and mark up privately. Turning it on mid-study? *Send my existing marks* catches the group up on the current chapter.

It's a full mesh — everyone connects directly to everyone else — so the session continues even if the person who started it closes their tab. If someone new needs to join after that, a surviving peer automatically takes over the "findable" slot. Reopening the same link rejoins.

Conflicts on shared marks are last-write-wins.

### Hebrew and Greek

Two separate downloads under **Library → Hebrew & Greek**:

- **Strong's dictionaries** (Hebrew and Greek) — then search by English word, transliteration, or number: `agape`, `H7225`, `G26`.
- **Tap-a-word text** — a Strong's-tagged KJV or ASV. Once downloaded, the **Strong's** button appears at the top of the Read view. Tagged words get a dotted underline; tap one for lexeme, transliteration, pronunciation, and definition. Words carrying several roots show each entry.

Lookups run offline once the dictionaries are downloaded, and fall back to an online lexicon otherwise. The sheet tells you which source it used.

### Cross-references

**Treasury of Scripture Knowledge** — several hundred thousand verse-to-verse links compiled over more than a century, ranked by how many editors flagged each one. Download it, then reach it from any verse's menu. Large download; do it on Wi-Fi.

**AI-assisted** — Berea writes the prompt; you paste it into whatever AI you already use and paste the reply back to import. No account or API key required. The prompt asks for quotations, fulfilments, thematic parallels, and *undesigned coincidences*, and returns structured JSON that the app parses into selectable suggestions. You choose which become a tab.

Optionally you can connect an API key (Claude, OpenAI, or any OpenAI-compatible endpoint) for one-tap lookups instead of copy/paste. The key is stored only in your browser and sent only to that provider.

> Treat AI suggestions as leads to verify, not answers. Check every reference before building on it.

### Apologetics practice

Six common objections — suffering, alleged contradictions, Gospel reliability, Old Testament violence, hell and exclusivity, science — each with the objection stated fairly, a response outline, and the passages behind it. Save any as a tab to work through the verses side by side.

### Backup and restore

Tabs, highlights, and notes live **only in the browser**. Clearing site data or switching devices loses them, so save a backup file occasionally.

- **Save backup** downloads a dated JSON file.
- **Restore** *merges* rather than replaces — it won't wipe work already on the device. Where both have something for the same verse or tab, the restored file wins.

Backups deliberately exclude downloaded scripture, dictionaries, cross-references, and your AI key. The first three are large and re-downloadable; the key stays out because backup files get emailed and synced around.

---

## Data sources and licences

All scripture text is public domain. Reference works likewise, with one dataset under CC BY.

| Resource | Source | Licence |
|---|---|---|
| KJV, WEB (bulk) | [aruljohn/Bible-kjv](https://github.com/aruljohn/Bible-kjv), [Bible-wmb](https://github.com/aruljohn/Bible-wmb) | Public domain |
| ASV, BBE, Darby, YLT (live) | [bible-api.com](https://bible-api.com/) | Public domain |
| Strong's tagged KJV / ASV | [bolls.life](https://bolls.life/) whole-translation JSON | Public domain texts |
| Strong's dictionaries | [openscriptures/strongs](https://github.com/openscriptures/strongs) | Public domain |
| Hebrew/Greek lexicon | Brown-Driver-Briggs / Thayer's via [bolls.life](https://bolls.life/) | Public domain |
| Cross-references (TSK) | `cross_references.txt` from [openbible.info](https://www.openbible.info/labs/cross-references/), mirrored in the `bible_databases` repos | Public domain |
| Nave's Topical Bible | [BradyStephenson/bible-data](https://github.com/BradyStephenson/bible-data) | **CC BY 4.0** |

**Attribution note:** the Nave's dataset is CC BY 4.0, which *requires* credit. The app displays it in the Library card. Keep that attribution if you fork or redistribute.

Bolls hosts many modern translations with no stated licence. Berea uses only KJV and ASV from it, both public domain. Its "use and abuse it" wording refers to server load, not a grant of rights in the text — worth knowing if you're tempted to add more from there.

---

## Why no NIV or NKJV

Both are under active copyright — NIV to Biblica, NKJV to Thomas Nelson. There's no legal way to bulk-download and redistribute their text inside a static file.

Adding them means a licensed API (such as API.Bible) with a user-supplied key, fetched live rather than cached. The translation registry in the source is structured to make that a contained change if you pursue it.

---

## How it's built

Single HTML file. No build step, no framework, no bundler — so it can be dropped straight onto GitHub Pages and edited with any text editor.

- **Storage** — IndexedDB for scripture, dictionaries, cross-references, topics, highlights and notes; `localStorage` for tabs and preferences.
- **Scripture is not bundled.** Downloads fetch from public repositories and cache locally, which keeps the file editable and the texts updatable.
- **Networking** — PeerJS for WebRTC study sessions. A public signalling service helps browsers find each other; once connected, all session traffic is peer-to-peer.
- **Privacy** — no account, no analytics, no server storing your work.

Some notes for anyone modifying it:

- Verse keys are `Book|Chapter|Verse` throughout — highlights, notes, cross-references and tagged text all share that format.
- Data-source parsers are deliberately defensive. The Strong's tag parser auto-detects between markup conventions; the Nave's CSV loader detects column names and fails with a readable error naming the actual headers rather than importing nothing silently.
- Bulk-import code is batched into chunked IndexedDB transactions to avoid blocking on large datasets.
- The in-app how-to (the `HELP` array) mirrors this README. Change behaviour, update both.

---

## Troubleshooting

**Home screen icon not showing (iPhone).** `icon.png` must exist next to `berea.html`, be square (180×180 ideal), and have **no transparency**. If you added the app to your home screen before fixing it, remove and re-add — iOS won't re-check.

**A download button errors out.** These pull from third-party repositories, and file paths do occasionally move. The fetch URL for each source is isolated at the top of its module in the source — search for the resource name to find it. The error toast usually names the cause.

**Tagged text downloaded but tapping words does nothing.** The Library card reports what it found. If it says *"no Strong's tags were found"*, the source text isn't tagged in a format the parser recognises — try the other translation, or check the source URL in `BOLLS_TAGGED`.

**Nave's download fails with a column error.** The message names the actual CSV headers it found. Add the relevant one to `TOPIC_COLUMNS` or `ENTRY_COLUMNS` at the top of that module. Note that Nave's has no reference column — citations are scanned out of the `entry` prose by `extractReferences`, so a topic whose entry contains no recognisable citation is skipped by design.

**Cross-references download fails.** `downloadCrossReferences` tries several known mirrors of `cross_references.txt` in turn and reports failure only if all are unreachable. If that happens, add a working URL to `XREF_URLS`.

**Search returns nothing.** Search only covers text stored on your device. Download a translation under Library, or read a few chapters first.

**Study session won't connect.** Both devices need internet access for the initial handshake. Corporate or school networks sometimes block WebRTC. If a session drops after backgrounding the app, reopening the link rejoins.

**Lost tabs, highlights, or notes.** Browser storage was probably cleared. Restore from a backup file if you have one. If not, save backups going forward — this is the one loss that can't be undone.
