# CTF Challenge Project

A group project for building a single, self-contained Capture the Flag (CTF) challenge as a runnable `.html` file.
Built by a team of 6, informed by prior analysis of [picoCTF](https://picoctf.org) and [TryHackMe](https://tryhackme.com).

---

## Team Roles

| Person | Role |
|--------|------|
| Person 1 | UI/HTML structure & file owner |
| Person 2 | Core puzzle logic (JavaScript) |
| Person 3 | Flag encoding & answer validation |
| Person 4 | Challenge text, hints & flavor content |
| Person 5 | Gamification & feedback elements |
| Person 6 | Playtesting & QA |

---

## Project Goal

Design and code one original CTF problem in the style of platforms studied during the research phase.

- Deliverable: one working `src/ctf_challenge.html` file
- The file must be runnable by opening it locally in a browser — no server required
- The flag must not be readable in plain text in the source code

---

## Folder Structure

```
ctf-project/
├── README.md               <- You are here
├── src/
│   └── ctf_challenge.html  <- Final deliverable (main file)
├── docs/
│   ├── concept_brief.md    <- Day 1: agreed problem concept & flag format
│   ├── design_notes.md     <- UI decisions and layout notes
│   └── flag_spec.md        <- Flag string, encoding method, validation logic
├── assets/
│   └── (any images, icons, or external files used in the challenge)
├── testing/
│   ├── playtest_log.md     <- Person 6's blind playtest notes
│   └── bug_tracker.md      <- Known bugs and fix status
└── notes/
    ├── tryhackme_analysis.md   <- Summary of TryHackMe weaknesses
    └── picoctf_analysis.md     <- Summary of picoCTF strengths
```

---

## 14-Day Sprint Plan

### Week 1 — Build foundations

**Day 1 — Kickoff (All members)**
- [ ] Hold group meeting: present and vote on 3–4 challenge concept ideas
- [ ] Agree on problem category (e.g. cipher, web exploitation, steganography, logic puzzle)
- [ ] Define the flag format (e.g. `FLAG{your_text_here}`)
- [ ] Person 1 creates the GitHub repo and shares access with the team
- [ ] Write up the agreed concept in `docs/concept_brief.md`

**Day 2 — Parallel starts (Person 1 + Person 2)**
- [ ] Person 1: create the base `src/ctf_challenge.html` with page skeleton (title, description area, hint toggle, input field, submit button)
- [ ] Person 1: apply base CSS — clean card layout, readable font, consistent color scheme (reference picoCTF's clean design)
- [ ] Person 2: begin drafting the puzzle mechanic in a scratch JS file or `<script>` block
- [ ] Person 2 + Person 3: agree on the exact flag string and where it lives in the code

**Day 3 — Puzzle logic (Person 2 + Person 3)**
- [ ] Person 2: implement the core puzzle mechanic fully in JavaScript
- [ ] Person 3: encode or hash the flag so it is not readable in plain source (e.g. SHA-256 comparison, XOR, reversed split string)
- [ ] Person 3: write the submission handler — correct flag shows success message, wrong flag shows generic error
- [ ] Document the encoding method in `docs/flag_spec.md`

**Day 4 — Integration (Person 1 + Person 2)**
- [ ] Person 1: integrate Person 2's puzzle logic into the main HTML file
- [ ] Person 1: integrate Person 3's flag validation into the submission handler
- [ ] Verify the full flow works end-to-end: puzzle → player solves → enters flag → success/fail message

**Day 5 — End of Week 1 checkpoint (All members)**
- [ ] All members do a quick test run of the current file
- [ ] Confirm: puzzle is solvable, flag check works, no JS errors in console
- [ ] Identify anything missing or broken before Week 2
- [ ] Update `testing/bug_tracker.md` with any known issues

---

### Week 2 — Polish, test, and submit

**Day 8 — Challenge text and hints (Person 4)**
- [ ] Write the challenge description — enough context, not too much
- [ ] Write 3 tiered hints (Hint 1 = nudge, Hint 2 = direction, Hint 3 = near-spoiler)
- [ ] Add hints behind a "Show Hint" toggle button in the HTML
- [ ] Review language for clarity — avoid TryHackMe's noted problem of "too much or too little info"

**Day 9 — Gamification (Person 5)**
- [ ] Add attempt counter (tracks how many times the player has submitted)
- [ ] Add point/score display that decrements with each wrong attempt (optional)
- [ ] Add animated success state on correct flag submission (e.g. banner, confetti, color change)
- [ ] Add a "Solved" badge or visual that appears on success
- [ ] Keep all effects lightweight — they must not distract from the puzzle

**Day 10 — Merge everything (Person 1)**
- [ ] Merge Person 4's text and hints into the HTML file
- [ ] Merge Person 5's gamification elements
- [ ] Verify the full file still works after all additions
- [ ] Pass the complete file to Person 6 for playtesting

**Day 11 — Blind playtest (Person 6)**
- [ ] Open `src/ctf_challenge.html` with no prior explanation from the builders
- [ ] Attempt to solve the challenge from scratch
- [ ] Record in `testing/playtest_log.md`:
  - [ ] Was the challenge solvable?
  - [ ] Was it too easy or too hard?
  - [ ] Were the hints helpful and well-timed?
  - [ ] Did the flag submission work correctly?
  - [ ] Any confusing wording, broken UI, or JS errors?
- [ ] Add all issues to `testing/bug_tracker.md`

**Day 12 — Bug fixes (Person 1 + Person 2)**
- [ ] Work through every item in `testing/bug_tracker.md`
- [ ] Fix all blocking bugs; flag anything cosmetic as low priority
- [ ] Run a second quick test after fixes

**Day 13 — Final review checklist (All members)**
- [ ] File opens correctly as a standalone `.html` in Chrome, Firefox, or Edge
- [ ] No external dependencies that could break (no CDN links, no relative file paths)
- [ ] Flag is NOT readable in plain text anywhere in the source
- [ ] All text is readable and buttons are accessible
- [ ] Layout holds on a standard laptop screen
- [ ] Hints are visible and work correctly
- [ ] Success and failure states both display properly
- [ ] No console errors on load or on submission

**Day 14 — Submission**
- [ ] Final version saved as `src/ctf_challenge.html`
- [ ] README updated with any last changes
- [ ] Submit to instructor

---

## File Ownership

- `src/ctf_challenge.html` is owned by **Person 1**. All changes go through Person 1.
- When contributing code, name your file with your initials and a version number (e.g. `puzzle_logic_p2_v2.js`) and hand it off to Person 1 for merging.
- Never push directly to the main branch without checking with Person 1.

---

## Challenge Category Options (Day 1 Vote)

If the group has not decided yet, here are five categories that work well in a single `.html` file:

1. **Hidden source flag** — Flag embedded as an HTML comment or invisible element; player must view page source
2. **Caesar / Vigenere cipher** — Encoded message displayed on screen; player decodes and submits the plaintext
3. **Base64 + ROT13 chain** — Flag is double-encoded; player must decode in two steps
4. **Hidden color steganography** — Text hidden using `color: #000001` on a black background or similar
5. **JS logic puzzle** — Player must figure out what input satisfies a visible JavaScript condition

---

## Resources

- [picoCTF](https://picoctf.org) — reference platform (clean UI, good hint structure)
- [TryHackMe](https://tryhackme.com) — reference platform (see `notes/tryhackme_analysis.md` for weaknesses to avoid)
- [CyberChef](https://gchq.github.io/CyberChef/) — useful for encoding/decoding during development
- [SHA-256 in JavaScript](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/digest) — for flag hashing reference
