# n0t3.zt

Ephemeral encrypted notepad. Runs in the browser. Leaves no trace.

---

## what it is

A single `.html` file. No server. No database. No localStorage. Everything lives in RAM — when you close the tab, it's gone.

## features

**writing**
- Adjustable page width (30–95%)
- Three typefaces: Fira Code · Garamond · Roboto
- Typewriter mode (cursor stays vertically centered)
- Invert colors

**timers**
- Writing timer — set a duration; freeze, erase, or notify on expiry
- Session timer — tracks elapsed time from first keypress; type `finalizar` to end
- Sprint — set a word goal; freeze or continue on completion
- Pomodoro — configurable work/break durations, cycle count, long break interval

**stats** (live, bottom bar)
- Words · Characters · Characters without spaces · Lines · Paragraphs · Bytes · Reading time · WPM (30s window)
- Selection mode: select any text to see stats for that fragment only

**export**
- `.txt` with SHA-256 cryptographic signature + timestamp
- `.cryptpad` — AES-256-GCM encrypted, password-protected
- Import both formats

---

## use

Download `n0t3.zt.html`. Open it in any modern browser. Write.

No installation. No dependencies. No network requests except loading Google Fonts.

---

## encryption

Export encrypted uses [AES-256-GCM](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto) via the browser's native Web Crypto API. Key derivation via PBKDF2 (150,000 iterations, SHA-256). Salt and IV are randomly generated per export. The password never leaves your machine.

## cryptographic signature

Every `.txt` export appends a block containing a SHA-256 hash of the content + timestamp. This serves as a lightweight proof of existence — useful for dated notes, journals, or anything where timing matters.

```
────────────────────────────────────────────────────────────
n0t3.zt · FIRMA CRIPTOGRÁFICA
Timestamp : 2026-02-24T18:43:21.000Z
SHA-256   : a3f9c2d1e8b7...
Verificar : sha256( contenido_literal + "|" + timestamp )
────────────────────────────────────────────────────────────
```

---

## keyboard shortcuts

| action | shortcut |
|---|---|
| Invert colors | `Ctrl+I` |
| Typewriter mode | `Ctrl+T` |
| Export .txt | `Ctrl+S` |
| Copy all | `Ctrl+Shift+C` |
| Erase all | `Ctrl+Shift+X` |
| Timer | `Ctrl+Shift+T` |
| Sprint | `Ctrl+Shift+P` |
| Session | `Ctrl+Shift+E` |
| Pomodoro | `Ctrl+Shift+O` |
| Shortcuts panel | `Ctrl+Shift+H` |

---

## privacy

Nothing is stored. Nothing is sent. Closing the tab destroys everything. The browser will ask for confirmation if you try to close with unsaved text.

---

MIT
