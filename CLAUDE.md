# 4-Bit Adder / Subtractor (CLAUDE.md)

## What this is
- A **showcase repo for a class lab**, not an app: Lab 2 of ECE 2705 (Digital Design I Lab), UVU, Fall 2026.
- The whole product is `README.md` plus images. It shows a 4-bit adder and a 4-bit two's-complement subtractor, designed in NI Multisim and built on a breadboard (74LS83 adder, 74LS04 inverters, 8-position DIP switch, 5 LEDs).
- Audience: anyone who opens the GitHub repo page (portfolio). Tim is the author.
- **No live site.** GitHub Pages is not enabled (the Pages API returns 404, checked 2026-10-16). The repo page itself is the "site": https://github.com/TimothyHadfield/4-bit-adder-subtractor

## File map
- `README.md`: the showcase page (how it works, Multisim screenshots, breadboard photos, parts, credits).
- `docs/multisim/adder-1..4.png`: Multisim adder schematic, 4 simulated switch settings.
- `docs/multisim/subtractor-1..3.png`: Multisim subtractor schematic, 3 simulated switch settings.
- `docs/photos/hero.jpg` + `breadboard-84xx.jpg`: breadboard photos (already resized to 1050-1400 px).
- `progress.md`: handoff notes.
- There is no code, no build, no tests, no package.json.

## How to run / check it
- Nothing to run. To preview, open `README.md` in VS Code's Markdown preview, or view the repo on GitHub after pushing.
- Check that every image path in the README exists (a short Python regex over `![alt](path)` works).
- **Logic check:** model the 74LS83 as `S = A + B + C0` (4-bit sum, carry-out = bit 4) and run all 256 (A, B) pairs. The adder is `C0 = 0`. The subtractor is `B` inverted on all 4 bits with `C0 = 1`. Read switch states and LEDs from the screenshots to compare (DIP knob up = 1; LED with red arrows = lit = 1; LED order is Cout, S3, S2, S1, S0).

## How it deploys
- Push to `main` on GitHub. The README renders on the repo page. No Pages, no CI.

## Traps
- **The subtractor schematic in `docs/multisim/subtractor-*.png` does not match the README's method.** It has only 3 inverters on B (B0 goes straight to the chip) and the carry-in C0 is tied to ground, not 1. That gives the right answer only when B0 = 1 (128 of 256 inputs wrong). `subtractor-3.png` (7 - 8) shows 0 1101 instead of 0 1111. Found in the 2026-10-16 sweep and reported to Tim. The images are screenshots of his graded lab work: don't edit, replace or caption them without his say.
- `docs/photos/breadboard-8477.jpg` is in the repo but not used in the README (left alone; Tim's call).
- The circuit has no overflow indicator. Signed overflow happens in 64 of 256 additions and 64 of 256 subtractions. That's how the lab is designed, not a bug.
- The README text, captions and layout are Tim's wording. Fix facts only with his OK.
- The repo is public: no emails, account ids or other people's names.

## Standing instructions
- Tim's global rules in `~/.claude/CLAUDE.md` apply. There are no project-specific quotes from Tim yet.
