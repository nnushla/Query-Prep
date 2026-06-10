# Query-Prep

- Built by Claude Code

# Query/Prep — SQL Interview Trainer

An interactive, single-page web app for learning SQL and preparing for data analytics / data engineering interviews. It runs a **real SQLite database entirely in your browser** — every query you write actually executes, including joins, CTEs, and window functions.

**🔗 Live demo:** [nnushla.github.io/Query-Prep](https://nnushla.github.io/Query-Prep/)

No installation, no signup, no backend. Open the page and start querying.

---

## Features

| Section | What it does |
|---|---|
| 📚 **Roadmap** | 23 concept pages across four levels (Beginner → Intermediate → Advanced → Data Engineering). Each one covers a plain-language explanation, syntax, a runnable example, and the common mistake interviewers watch for. |
| ▶️ **Playground** | A live SQL editor backed by an in-browser SQLite database with four sample tables. Includes a schema reference panel, preset sample queries, error messages, and `Cmd/Ctrl + Enter` to run. |
| ⌗ **Practice** | 12 problems (easy → hard) with progressive hints. Your query is auto-graded by comparing its result set against the expected output — not by string-matching your SQL. |
| ❓ **Question bank** | ~20 frequently asked interview questions (WHERE vs HAVING, join pitfalls, dedup strategies, star vs snowflake, incremental loads) with concise answers you can say out loud. |
| ⇄ **Flashcards** | Flip cards for rapid review. Cards you mark as "shaky" resurface first. |
| ◷ **Mock interview** | A 15-minute timed simulation: 8 multiple-choice concept questions + 3 live query-writing tasks, scored with a readiness verdict. |
| ▦ **Dashboard** | Tracks concepts read, problems solved, and mock scores, and surfaces your weakest topics — rendered as a SQL result table, naturally. |

## The practice database

Queries run against a small company dataset designed to exercise every interview pattern:

```
employees(id, name, department, salary, hire_date, manager_id)   -- self-joins, rankings
customers(customer_id, name, city)                                -- includes customers with no orders
orders(order_id, customer_id, employee_id, amount, order_date)    -- joins, aggregations, running totals
raw_signups(signup_id, email, plan, created_at)                   -- contains duplicates, on purpose
```

`manager_id` enables the classic employee→manager self-join, two customers have zero orders (for LEFT JOIN anti-join practice), and `raw_signups` is intentionally dirty so you can practice the `ROW_NUMBER()` deduplication pattern.

## How it works

- **One file.** The entire app — markup, styles, data, and logic — lives in a single `index.html`. No build step, no framework.
- **Real SQL execution** via [sql.js](https://github.com/sql-js/sql.js) (SQLite compiled to WebAssembly), loaded from a CDN. Your queries never leave the browser.
- **Honest auto-grading.** Each practice problem stores a reference solution. Both your query and the solution run against a freshly reset database, and the result sets are compared (order-insensitive unless the problem requires ordering). Aliases and formatting differences don't matter — correct results do.
- **Zero dependencies to install.** Fonts and sql.js are fetched from CDNs at runtime; everything else is vanilla HTML/CSS/JavaScript.

## Topics covered

SELECT · WHERE · ORDER BY / LIMIT · DISTINCT · aggregate functions · GROUP BY · HAVING · CASE WHEN · string & date functions · INNER / LEFT / RIGHT / FULL joins · self joins · subqueries · CTEs · window functions · ROW_NUMBER / RANK / DENSE_RANK · set operations · deduplication · top-N per group · running totals · NULL handling · star vs snowflake schemas · ETL, incremental loads & data-quality checks

## Running locally

```bash
git clone https://github.com/nnushla/Query-Prep.git
cd Query-Prep
# any static server works, e.g.:
python3 -m http.server 8000
```

Then open `http://localhost:8000`. (Opening the file directly via `file://` may block the WebAssembly fetch in some browsers, so a local server is recommended.)

## Known limitations

- The **AI tutor** tab depends on an API integration that only functions when the app runs inside the environment it was originally built in; on the public site, tutor messages will not get a response. All other features are fully client-side and work everywhere.
- **Progress persistence** uses a storage API from that same environment, so on the public site your progress resets on reload. The rest of the app is unaffected.
- The SQL dialect is **SQLite**, so a few functions are spelled differently than in Postgres/MySQL/Snowflake (`strftime` instead of `DATE_TRUNC`, `||` for concatenation). The concepts transfer one-to-one.

## Built with

HTML · CSS · JavaScript · [sql.js](https://github.com/sql-js/sql.js) (SQLite + WebAssembly) · IBM Plex Mono, Space Grotesk & Inter via Google Fonts

Initial version built with the help of Claude (Anthropic).

## License

MIT — use it, fork it, prep with it. If it helps you land the job, a ⭐ would make my day.
