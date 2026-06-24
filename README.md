# UCM Video Intake Chatbot

A self-contained intake tool for University Communications & Marketing at the University of Pittsburgh. Walks clients through a short conversation and generates a downloadable, editable PDF creative brief.

**No server. No dependencies. One HTML file.**

---

## What it does

1. Asks 17 questions — one at a time, one field each
2. Collects interview subjects in a loop (name → contact → key point → repeat until done)
3. Generates a formatted, two-page PDF matching the UCM Video Pre-Production Brief template
4. Flags any unanswered fields in red as `[MISSING]`
5. Tells the client to email the completed brief to Jim and Brad

---

## The questions (in order)

**Getting Started**
1. Name and department
2. Email and phone number

**Project Details**
3. Preferred shoot date
4. Due date for finished video
5. Existing files to share (logos, scripts, b-roll)
6. Project type (numbered choice: 1–6)
7. Audience (numbered choices: 1–8, select all that apply)

**Distribution**
8. Where the video will live (channels)
9. Expected length

**The Video**
10. Project description (3–5 sentences)
11. Key messages (one sentence each)

**Interview Subjects** *(loops until client says "done")*
12. Subject name
13. Subject contact info
14. What they should speak to
→ "Is there another subject?" — repeats 12–14 for each additional person

**Creative Direction**
15. Visual style and tone
16. What this video SHOULD be
17. What this video should NOT be

---

## How to deploy on GitHub Pages

1. **Upload `index.html`** to your repo (drag into GitHub, or push via git):
   ```bash
   git add index.html
   git commit -m "Update chatbot"
   git push
   ```
2. Go to **Settings → Pages**
3. Source: **Deploy from a branch** → Branch: `main` / Folder: `/ (root)` → Save
4. Wait about 60 seconds. Your URL:
   ```
   https://YOUR_USERNAME.github.io/REPO-NAME/
   ```

To update: edit `index.html`, commit, push. GitHub Pages redeploys automatically.

---

## Key things to edit

| What to change | Where in `index.html` |
|---|---|
| Questions | The `QS` array near the top of the `<script>` block |
| Contact emails | Search for `jvastine@pitt.edu` and `bradking@pitt.edu` |
| Phone number | Search for `(412) 624-0000` |
| Project type options | The `TYPE_MAP` object |
| Audience options | The `AUD_LABELS` array |
| PDF layout and styling | The `makePDF()` function |

---

## How the subject loop works

Interview subjects use a separate mini state machine (independent from the main question flow) with four steps:

```
ask_name → ask_contact → ask_point → ask_more
                                         │
                          name typed ────┘  (loops back to ask_contact)
                          "done" typed ───→  continues to next section
```

This means there's no limit on how many subjects can be added, and it can't loop incorrectly.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — chatbot + PDF engine |
| `README.md` | This file |

---

## Notes

- Works in all modern browsers (Chrome, Firefox, Safari, Edge)
- PDF is generated entirely in the browser — no data is sent anywhere until the client emails it
- The Tabler Icons font loads from jsDelivr CDN — requires an internet connection
- Optimized for desktop; functional on mobile
- The PDF is editable in Adobe Acrobat and most PDF viewers
