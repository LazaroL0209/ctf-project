# Flag Specification

_Completed by Lazaro and Person 3 on Days 2–3. Keep this file private — do not share the plain-text flag publicly._

---

## Flag string

**Plain-text flag:** withheld from the repo; validation uses the encoded value in `src/ctf_challenge.html`

**Flag format:** `FLAG{_______________}`

---

## Encoding method

**Method chosen:** (e.g. SHA-256 hash comparison, XOR with key, base64 + reverse, split array)

**Reason for choosing this method:**

---

## How validation works

Describe the submission handler logic step by step:

1. The player solves the three-dial lock in the puzzle area.
2. The submission handler hashes the entered flag with SHA-256.
3. The hash is compared against the stored digest and success/failure is shown.

---

## Code notes

_Any important notes about how the encoding is implemented in the HTML file — so Person 1 can integrate it correctly._

The lock uses a simple JavaScript state machine for the dials, and the flag is
verified with `crypto.subtle.digest('SHA-256', ...)` so the plain-text answer
is never embedded in the source.

---

## Things to verify before submission

- [ ] The plain-text flag is NOT visible anywhere in the HTML source
- [ ] The encoded value in the source cannot be trivially reversed by a casual viewer
- [ ] The correct flag triggers the success state
- [ ] An incorrect flag triggers the error state with no revealing hints
- [ ] The flag check is case-sensitive (or intentionally case-insensitive — document which)
