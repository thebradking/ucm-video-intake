# UCM Video Intake Chatbot

A self-contained intake tool for University Communications & Marketing at the University of Pittsburgh. Walks clients through a short conversation, then generates a downloadable PDF creative brief.

**No server required. No dependencies. One file.**

---

## What it does

- Asks 10 intake questions conversationally
- Generates a formatted PDF brief matching the UCM Video Pre-Production template
- Checkboxes for project type and audience auto-fill based on answers
- Flags missing fields in red so the client knows what to fill in
- Tells the client to email the completed brief to jvastine@pitt.edu and bradking@pitt.edu

---

## How to deploy on GitHub Pages

1. **Create a new repository** on GitHub (e.g. `ucm-video-intake`)
2. **Upload `index.html`** — drag it into the repo on GitHub, or push via git:
   ```bash
   git init
   git add index.html
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/ucm-video-intake.git
   git push -u origin main
   ```
3. **Enable GitHub Pages:**
   - Go to your repo → Settings → Pages
   - Under "Source", select **Deploy from a branch**
   - Branch: `main` / Folder: `/ (root)`
   - Click Save
4. **Your URL will be:**
   ```
   https://YOUR_USERNAME.github.io/ucm-video-intake/
   ```
   GitHub Pages usually goes live within 1–2 minutes.

---

## How to update

To change the questions, contact emails, or anything else — edit `index.html` and push the change. GitHub Pages redeploys automatically.

Key spots to edit:
- **Questions:** the `QS` array near the top of the `<script>` block
- **Contact emails:** search for `jvastine@pitt.edu` and `bradking@pitt.edu`
- **Phone number:** search for `(412) 624-0000`
- **PDF layout:** the `makePDF()` function

---

## Files

| File | What it is |
|---|---|
| `index.html` | The entire app — chatbot + PDF generator |
| `README.md` | This file |

---

## Notes

- Works in all modern browsers (Chrome, Firefox, Safari, Edge)
- PDF is generated entirely in the browser — no data is sent anywhere
- The Tabler Icons font is loaded from a CDN (jsdelivr) — requires internet access
- Tested on desktop; mobile-friendly but optimized for desktop use
