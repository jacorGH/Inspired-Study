# Berea

A single-file study Bible for the browser. Works offline, runs from GitHub Pages for free, and lets a group read together over a peer-to-peer connection.

The name is from Acts 17:11 — the Bereans "searched the scriptures daily, whether those things were so." That's the design goal: compare translations, follow cross-references, check the original languages, verify rather than assume.

---

## Contents

- [What's in it](#whats-in-it)
- [Setting it up](#setting-it-up)
- [Using it](#using-it)
  - [Getting around](#getting-around)
  - [Reading, marking up, and listening](#reading-marking-up-and-listening)
  - [Compare](#compare)
  - [Tabs](#tabs)
  - [Search](#search)
  - [Study sessions](#study-sessions)
  - [Journal](#journal)
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
- **Read-aloud**, verse by verse, with the current verse highlighted as it's spoken
- **Peer-to-peer study sessions** with host migration, optional shared markup, and a recap when you leave
- **Strong's Concordance** with tap-a-word Hebrew/Greek lookup, and a true concordance search — every verse using a given original-language word
- **Treasury of Scripture Knowledge** — the classic cross-reference set
- **Nave's Topical Bible** — study by subject rather than by passage
- **AI cross-reference prompts** that work with any AI chat, no API key needed
- **Apologetics practice** — six common objections with response outlines
- **A prayer journal** — requests, an answered-prayer record, and a simple timer (deliberately no streaks)
- **Reading plans** with progress tracking and streaks
- **Verse memorization** with spaced repetition
- **A study outline builder** — your own points interleaved with verses, exportable as text
- **Backup and restore** to a file, covering everything above
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

**Worth doing first:** open **☰ Berea → Translations** and download KJV or WEB. That makes the whole Bible available offline and switches on full-text search. Everything else behind the menu is optional.

### Getting around

The bottom bar holds the five places you'll use daily: **Read, Compare, Search, Study, Journal.** Everything else — downloads, the in-app guide, apologetics, and backup — lives behind **☰ Berea** in the top left, since those are places you visit occasionally rather than every day.

### Reading, marking up, and listening

Tap any verse for its menu:

- **Highlight** in five colours. Highlights are keyed to the verse, so marking John 3:16 marks it in every translation.
- **Write a note.** Notes save on every exit path — colour tap, Close, or tapping the backdrop — so a typed note can't be lost by dismissing the sheet the "wrong" way. A small ✎ marks any verse that has one.
- **Pin as a tab**, or add to an existing tab.
- **Add to memory verses** for spaced-repetition practice (see [Journal](#journal)).
- **Cross-references**, traditional or AI-assisted.

The 🔊 button at the top of the Read view reads the chapter aloud, one verse at a time, highlighting each as it's spoken — uses the browser's built-in speech synthesis, so voice quality depends on your device.

### Compare

Shows one chapter in two translations as facing pages with a spine between them. Choose a translation per page. Highlights and notes appear on both sides.

### Tabs

A tab holds a *set* of passages and displays them side by side. This is what makes connections visible — put Matthew 27:46 beside Psalm 22:1 and you can see Jesus quoting the psalm from the cross. Two tabs ship pre-made as examples.

Tabs sit in the strip above the bottom bar. Tap to open, **+ tab** to create one from the current chapter, × to remove.

Inside an open tab, **+ Add a cross-reference passage** accepts plain references — `Romans 8:38-39`, `ps 22`, `1 cor 13:4-7`, `jn 3:16` all parse. Single-chapter books resolve sensibly too: `2 John 5` means chapter 1, verse 5.

The facing-page look holds for **two** passages. Add a third and the tab switches to a vertical list instead — the book-spread metaphor stops being readable once there's more to swipe through than fits in one glance, and nothing on screen would hint that more passages exist off to the side.

### Search

Four modes:

| Mode | Searches |
|---|---|
| **Verses** | Full text of downloaded/cached translations. Tap to jump, or pin straight to a tab. |
| **Tabs** | Your saved tabs, by name or by any reference inside them. |
| **Topics** | Nave's Topical Bible, once downloaded — by subject rather than wording. |
| **Words** | A true concordance, once a tagged Bible and its word index are built (see [Hebrew and Greek](#hebrew-and-greek)) — search an English word, transliteration, or Strong's number and get *every* verse using that exact original-language word. This is where Strong's earns its keep: one Hebrew word rendered six different ways teaches more than any single definition. |

Search only covers text stored on your device, so downloading a translation makes it substantially more useful.

Jumping to a verse from any result list leaves a **"‹ Back to…"** chip at the top of the reader, so you're never stranded after following a lead — tapping it reopens the exact list you came from, not just a reset search box.

### Study sessions

Tap **Start a Study**, then share the link through any messaging app. Whoever opens it joins immediately — first-time guests are asked for a name right in the app, not via a browser dialog (see the note below on why that distinction matters). The roster of everyone connected shows at the top of the Study tab.

- **Leading** — the leader's navigation moves everyone following along. Anyone can *Take the lead*; anyone can switch off *Follow along* to read independently.
- **Sharing highlights and notes** — off by default. Switch it on and your marks go to everyone else who also has it on, and theirs are saved to your copy. Leave it off to read along and mark up privately. Turning it on mid-study? *Send my existing marks* catches the group up on the current chapter.
- **Sharing an outline** — open it under Journal › Outlines during a session and tap *Share with study group*. It's an explicit, one-shot send rather than continuous auto-sync (an outline is built up over many small edits, unlike a tab which is usually complete the moment it's made); share again after further changes to update everyone else's copy.

It's a full mesh — everyone connects directly to everyone else — so the session continues even if the person who started it closes their tab. If someone new needs to join after that, a surviving peer automatically takes over the "findable" slot. Reopening the same link rejoins. If a join is taking a while, the app now says so plainly rather than sitting silent.

> A guest joining for the first time needs a name, and getting one used to mean calling the browser's `prompt()` from a timer right after the link opened. Mobile Safari (and others) routinely block dialogs that aren't triggered by a direct tap — especially right after page load — which silently killed the whole join with no error shown anywhere. The name prompt is now a real form inside the Study view instead, so it only ever fires from an actual tap.

Conflicts on shared marks are last-write-wins.

**Leaving a study that covered ground** shows a recap — passages visited and tabs pinned, ready to copy. It's built from your own local record, not synced, so each person's recap reflects what they personally had open.

### Journal

The **Journal** tab is for what you bring rather than what you read. Four parts, switched with the strip at the top:

**Prayer** — add a request in a line of text; tap it to add detail, log that you prayed for it, set a category, or mark it answered. Requests you haven't prayed for in a while drift to the top. Answered prayers get their own section with how long you carried each one and room to record what happened. *Pray now* runs a simple timer and logs the minutes.

There are **no streaks on prayer, on purpose.** Streaks suit a daily-habit goal; applied to something devotional they turn it into score-keeping, and a broken streak becomes guilt about praying. The record here is quiet — the warmth is saved for the moment something's answered.

**Plan** — pick a reading plan (Whole Bible in a year, New Testament in 90 days, the Gospels in a month, Psalms in a month, Old Testament in 180 days) and it shows today's assignment, one tap from the reading itself. Chapters are spread as evenly as the day count allows. This is where streaks *do* belong — the streak survives until a full calendar day is missed, so it won't read as "broken" every morning before you've had a chance to read.

**Memory** — verses added from the Read view's menu come up for review on a spaced schedule (a simplified SM-2): sooner after adding, further apart each time you get one right, faster again if you slip. Practice shows the reference first, then reveals the verse with a growing share of words blanked out as your review count rises.

**Outlines** — build a document mixing headings, plain text, teaching points, discussion questions, and verses, in whatever order you'll actually use it: teaching, leading a study, or thinking a passage through. Verse text is captured at the moment a verse is added (by hand or via import), so it won't shift under you later if you switch translations. Tap any block to edit it in place, tap **+** on a block to insert a new one right after it (not just at the end), reorder with the ↑↓ arrows, and copy the whole thing as **text** or as **JSON** when you're ready to use it elsewhere. Discussion questions can carry their own answer or notes — tap *+ Add answer* underneath one, or an AI-generated outline can suggest one directly. In a study session, **Share with study group** sends the outline to everyone connected; sharing again after edits updates their copy.

**⚡ Import from AI**, on the outline list, builds a prompt from a topic ("Emmanuel: God With Us") or from an outline you already have — paste one in from ChatGPT, Claude, notes, wherever. Copy the prompt into any AI, paste its JSON reply back, and it becomes a real, editable outline. The AI supplies structure and its own wording; verse text always comes from the app's own Bible data, never from the AI — so nothing scriptural gets hallucinated or misquoted, and copyrighted translation text never has a way to leak in through an AI's reply.

> AI-generated JSON reliably breaks in a few specific, well-known ways — curly "smart" quotation marks used as the actual JSON delimiters, *and often reused for a quotation nested inside the prose itself* (a common one: `"...means "God with us," establishing..."`, where the AI used the identical curly-quote character for both the delimiter and the in-text quotation, making them structurally impossible to tell apart by character alone), plus a trailing comma before a closing bracket, and an object key left unquoted — all signs of a model drifting toward "JavaScript-ish" instead of strict JSON. Both prompts (this one and the cross-reference one) now explicitly require ASCII-only output with quotes properly escaped, and the paste-back import repairs all of this automatically — alone or in combination — if it happens anyway, including the nested-quote case, by looking at what comes right after each quote to decide whether it's really closing the string or just quoting a phrase within it. If an import still fails, the error message says so directly rather than showing a bare parse error.

All of Journal stays on your device and is included in your backup file.

### Hebrew and Greek

Two separate downloads under **☰ Berea → Hebrew & Greek**:

- **Strong's dictionaries** (Hebrew and Greek) — then search by English word, transliteration, or number: `agape`, `H7225`, `G26`.
- **Tap-a-word text** — a Strong's-tagged KJV or ASV. Once downloaded, the **Strong's** button appears at the top of the Read view. Tagged words get a dotted underline; tap one for lexeme, transliteration, pronunciation, and definition. Words carrying several roots show each entry.

After downloading tagged text, **build the word index** (same screen) to turn on Search › Words — a real concordance, letting you find every verse that uses a given original-language word rather than just looking one up.

Lookups run offline once the dictionaries are downloaded, and fall back to an online lexicon otherwise. The sheet tells you which source it used.

### Cross-references

**Treasury of Scripture Knowledge** — several hundred thousand verse-to-verse links compiled over more than a century, ranked by how many editors flagged each one. Download it, then reach it from any verse's menu. Large download; do it on Wi-Fi.

**AI-assisted** — Berea writes the prompt; you paste it into whatever AI you already use and paste the reply back to import. No account or API key required. The prompt asks for quotations, fulfilments, thematic parallels, and *undesigned coincidences*, and returns structured JSON that the app parses into selectable suggestions. You choose which become a tab. (Same quote-repair as outline import, below, covers this too — malformed AI JSON is a shared problem with a shared fix.)

Optionally you can connect an API key (Claude, OpenAI, or any OpenAI-compatible endpoint) for one-tap lookups instead of copy/paste. The key is stored only in your browser and sent only to that provider.

> Treat AI suggestions as leads to verify, not answers. Check every reference before building on it.

### Apologetics practice

Six common objections — suffering, alleged contradictions, Gospel reliability, Old Testament violence, hell and exclusivity, science — each with the objection stated fairly, a response outline, and the passages behind it. Save any as a tab to work through the verses side by side.

### Backup and restore

Tabs, highlights, notes, prayers, reading-plan progress, memory verses, and outlines all live **only in the browser**. Clearing site data or switching devices loses them, so save a backup file occasionally.

- **Save backup** downloads a dated JSON file.
- **Restore** *merges* rather than replaces — it won't wipe work already on the device. Where both have something for the same verse or tab, the restored file generally wins — with one deliberate exception: reading-plan progress is merged day-by-day, and where both copies have a completion for the same day, the **device you're restoring onto wins**, so an older backup can never erase progress made since.

Backups deliberately exclude downloaded scripture, dictionaries, cross-references, the topic index, and your AI key. Those are large and re-downloadable; the key stays out because backup files get emailed and synced around.

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

- **Storage** — IndexedDB for scripture, dictionaries, cross-references, topics, the concordance index, highlights, notes, prayers, reading-plan progress, memory verses, and outlines; `localStorage` for tabs and preferences. The schema has gone through several versions as features were added; IndexedDB migrates automatically on open, so nothing needs doing by hand.
- **Scripture is not bundled.** Downloads fetch from public repositories and cache locally, which keeps the file editable and the texts updatable.
- **Networking** — PeerJS for WebRTC study sessions. A public signalling service helps browsers find each other; once connected, all session traffic is peer-to-peer.
- **Speech** — the browser's built-in SpeechSynthesis API for read-aloud. No external service, no download.
- **Privacy** — no account, no analytics, no server storing your work.

Some notes for anyone modifying it:

- Verse keys are `Book|Chapter|Verse` throughout — highlights, notes, cross-references, tagged text, and memory verses all share that format.
- Data-source parsers are deliberately defensive. The Strong's tag parser auto-detects between markup conventions; the Nave's CSV loader detects column names and fails with a readable error naming the actual headers rather than importing nothing silently.
- Bulk-import code is batched into chunked IndexedDB transactions to avoid blocking on large datasets. When a write transaction needs a read first (as the reading-plan merge does), the read happens in its own transaction *before* the write loop starts — interleaving an awaited read inside an open write transaction risks the transaction auto-committing early in some browsers, Safari especially.
- Anything that calls `speechSynthesis.speak()` has to do so synchronously within the click handler that triggered it, or Safari/iOS silently drops the request with no error. Read-aloud keeps a small cache of the currently-displayed chapter for exactly this reason, rather than fetching fresh on tap.
- The same class of bug applies to `prompt()`, `alert()`, and `confirm()`: browsers routinely block these when they're not triggered by a direct, synchronous user gesture, especially right after page load. This bit the auto-join flow specifically (a `setTimeout` calling `prompt()` for a guest's name) with a completely silent failure — no error, nothing on screen, the join just never happened. The fix pattern is the same as for speech: never call a browser dialog from a timer or another async callback; use a real in-app form instead, so it's always a genuine tap.
- AI JSON parsing (outline import, cross-reference import) shares one repair pipeline, `parseAiJsonLoose`, rather than each duplicating the same fixes. The hard part isn't converting curly quotes to straight ones — it's that an AI often reuses the *same* curly-quote character for the JSON delimiters AND a nested quotation inside its own prose, so a blind find-and-replace can't tell a real delimiter from quoted content; converting both identically just moves the corruption rather than fixing it. `smartRequote` resolves this structurally instead: whether a quote closes a string is decided by what comes right after it (skipping whitespace) — a JSON-structural character (`: , } ]`) means it's a true closer, anything else means it's nested content and gets escaped rather than treated as the end of the string. Trailing-comma and unquoted-key repairs stack on top of that, so a reply with more than one problem still repairs in a single pass. All of it only ever runs as a fallback after a first parse attempt on the untouched text fails, never up front: every one of these patterns can also appear as legitimate *content* inside JSON that was never broken, so repairing pre-emptively would occasionally turn valid JSON into broken JSON instead of the other way round.
- The concordance is a proper inverted index (Strong's number → every verse using it), built once with a database cursor rather than loading all tagged text into memory, and searched instantly afterward rather than rescanned per query.
- Memorization uses a simplified SM-2 spaced-repetition schedule with an ease-factor floor, so repeated misses can't spiral a card into an unrecoverable state.
- Reading-plan streaks compare **local calendar days**, not raw elapsed hours — a streak survives until a full day is missed, so it doesn't read as broken every morning before you've had a chance to read.
- The backup format has its own version number (currently 3) independent of the database schema version, and grows monotonically as new data types are added — never remove a field from an old format without keeping restore able to read it.
- The in-app how-to (the `HELP` array) mirrors this README. Change behaviour, update both.

---

## Troubleshooting

**Home screen icon not showing (iPhone).** `icon.png` must exist next to `berea.html`, be square (180×180 ideal), and have **no transparency**. If you added the app to your home screen before fixing it, remove and re-add — iOS won't re-check.

**A download button errors out.** These pull from third-party repositories, and file paths do occasionally move. The fetch URL for each source is isolated at the top of its module in the source — search for the resource name to find it. The error toast usually names the cause.

**Tagged text downloaded but tapping words does nothing.** The Library card reports what it found. If it says *"no Strong's tags were found"*, the source text isn't tagged in a format the parser recognises — try the other translation, or check the source URL in `BOLLS_TAGGED`.

**Search › Words is empty even after downloading tagged text.** Two separate steps: downloading the tagged Bible and *building the word index* are different actions, both under **☰ Berea → Hebrew & Greek**. The index has to be built (or rebuilt) once after a tagged download before Words search finds anything.

**Nave's download fails with a column error.** The message names the actual CSV headers it found. Add the relevant one to `TOPIC_COLUMNS` or `ENTRY_COLUMNS` at the top of that module. Note that Nave's has no reference column — citations are scanned out of the `entry` prose by `extractReferences`, so a topic whose entry contains no recognisable citation is skipped by design.

**Cross-references download fails.** `downloadCrossReferences` tries several known mirrors of `cross_references.txt` in turn and reports failure only if all are unreachable. If that happens, add a working URL to `XREF_URLS`.

**Search returns nothing.** Search only covers text stored on your device. Download a translation under ☰ Berea, or read a few chapters first.

**🔊 read-aloud does nothing, or the toast says it's unsupported.** Depends entirely on the browser's SpeechSynthesis support — nearly universal on iOS/Android/desktop Safari, Chrome, and Edge, but can be missing in embedded webviews (an in-app browser inside another app, for instance). Try opening the page in the regular browser app. If it stayed silent with no error at all on an otherwise-supported browser, that was a real bug in an earlier version — `toggleReadAloud` awaited a database read before calling `speak()`, and Safari silently drops speech requests that aren't triggered synchronously by the tap that started them. Fixed by reading from the chapter already on screen instead.

**Pasting an AI's outline or cross-reference JSON fails to import.** Almost always curly "smart" quotation marks, a trailing comma before a closing bracket, or an unquoted object key — all common ways a model drifts toward JavaScript-ish output instead of strict JSON. The trickiest version: the AI reuses the *same* curly-quote character for the JSON delimiters and for a quotation nested inside its own sentence, which the import resolves by looking at what follows each quote (a JSON-structural character means it's a true closer; anything else means it's quoted content) rather than a blind replace. If it still won't import after all that, the error message explains why — and if the pasted text looks visibly cut off partway through (missing a final `]}`), that's a different problem: the AI's reply itself got truncated, and re-copying the complete response is the fix, not a JSON quirk.

**A reading-plan streak looks wrong.** It's calculated from local calendar days, not a rolling 24-hour count, and today doesn't have to be done yet for the streak to still be "alive" — only a full missed day breaks it. If the streak seems off by exactly one, check the device's clock and timezone setting.

**Study session won't connect, or a guest sees nothing after opening the link.** Both devices need internet access for the initial handshake, and corporate or school networks sometimes block WebRTC outright — that's a real limitation no amount of code can work around. If it's not that: the app now shows "Joining CODE…" the instant a join starts and warns after about 12 seconds if no connection ever completed, so a stall is at least visible rather than silent. If a session drops after backgrounding the app, reopening the link rejoins.

**Roster stays empty, or the host never sees a guest join.** Almost always the same root cause as the join-flow fix above — check that both people are on the same code and that neither device lost its connection mid-handshake. The 12-second warning (previous entry) is the first signal something didn't complete.

**Lost tabs, highlights, notes, prayers, plans, memory verses, or outlines.** Browser storage was probably cleared. Restore from a backup file if you have one. If not, save backups going forward — this is the one loss that can't be undone.
