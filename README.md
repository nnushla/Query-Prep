# QUERY/PREP — SQL Interview Trainer

A browser-based SQL interview prep tool built for data engineering and analytics job seekers.

**[Live Demo →](https://nnushla.github.io/Query-Prep/)**

## Features
- **Roadmap** — 20 concepts across Beginner → Data Engineering, each with syntax, runnable examples, and the common interview mistake
- **Playground** — Live SQLite database running in-browser via WebAssembly. Write and run real SQL, no backend needed
- **Practice Problems** — 12 graded problems from basic filtering to window functions and deduplication
- **Flashcards** — Spaced-repetition style cards weighted toward weak topics
- **Mock Interview** — Timed 15-minute session with multiple choice + live query rounds
- **Question Bank** — Curated answers to the questions interviewers actually ask
- **Dashboard** — Tracks progress across concepts, problems, and mock scores

## Tech Stack
- Vanilla HTML, CSS, JavaScript — zero dependencies, zero build step
- [sql.js](https://github.com/sql-js/sql.js/) — SQLite compiled to WebAssembly, runs entirely client-side
- Deployed via GitHub Pages

## Running locally
Just open `index.html` in a browser. No install required.
