# Crorstle

A polished, browser-based Wordle-style daily puzzle with a dark theme, micro-animations, and O(m) trie-based word validation. Zero build steps required to run. Live at https://roogard.github.io/crorstle

Single game mode only. The old Beginner/Normal toggle is gone and the mode is never shown in the UI.

## Daily Answer

- Puzzle number counts up from 1 starting 2026-11-16, and seeds a mulberry32 PRNG
- 90% of days the answer is the full six letter CRORST and the secret 6th letter is in play
- 10% of days the answer is one of the 360 five letter arrangements of C, O, R, R, S, T from CUSTOM_WORDS, with strict Wordle rules (five letter guesses, exact match to win)
- Share text reads "Crorstle N x/6" plus the site URL

## File Structure

- `index.html` - Game UI and React application logic
- `src/css/style.css` - Custom styling, Google Font Inter, and core animations
- `src/js/trie-engine.js` - High-performance TrieEngine validation class
- `src/js/dictionary.js` - Precompiled answers pool and allowed guesses trie data

## Features

- 6x5 grid of tiles
- Daily word selection deterministic by day-of-year + year
- Letter evaluation: green (correct), yellow (wrong position), gray (absent)
- Duplicate letter handling: exact matches first, then yellows up to remaining count
- Tile flip animation on guess submission
- Bounce animation on win
- Row shake + toast on invalid word
- On-screen QWERTY keyboard with state coloring
- Stats modal: games played, win %, streaks, guess distribution
- Share to clipboard with emoji grid
- Help/info modal with "How to Play" examples
- Game state and stats persisted in localStorage, keyed by date and mode

## Tech Stack

- React 18 + Babel standalone via CDN (no local npm install required)
- Vanilla CSS + HSL design system + HFR/responsive flex grid
- Google Font Inter for premium typography
- @rahulmrx/game-ready-dictionary integration (TrieEngine)

## Constraints

- No em dashes in comments or text
- Keep code clean and modularized
- Signature at bottom-right: "Created by Roogard" in 11px, #565656
- All allowed guesses validated via O(m) TrieEngine structure
