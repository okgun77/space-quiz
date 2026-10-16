# Copilot instructions

## Project
Single-file Korean-language space quiz web app: everything (CSS, HTML, JS) lives in `index.html`. There is no build step, package manager, tests, or linter — open the file in a browser (or serve the folder with any static server) to run it. Not a git repository.

## Architecture
- `<script>` at the bottom of `index.html` holds all logic: a `questions` array (`{category, question, answers[4], correct (index), explanation}`), module-level state (`current`, `correctCount`, `answered`, `countFrame`), and `get(id)` as the `getElementById` shortcut.
- Flow: `renderQuestion()` → `selectAnswer(i)` (locks answers, shows feedback, updates score/progress) → `#next` click → `showResults()` after the last question; `#restart` resets state and DOM by hand.
- Screens are toggled with the `hidden` attribute (`#question-screen` / `#result-screen`).

## Conventions
- **Question count and scoring are hard-coded to 10 questions × 10 points.** `showResults`, `restart`, the `0 / 10` progress text, the `<aside>` "10개의 질문" copy, and the `correctCount === 10` / `* 10` percent/score math all assume this. If you add or remove questions, update all of those (and the initial HTML progress `max`/text).
- UI text is Korean with a friendly "~요" tone; keep new copy consistent. File must stay UTF-8 (`lang="ko"`); in PowerShell, read/write with explicit UTF-8 to avoid mojibake.
- DOM is built with `createElement`/`textContent` (no user-content `innerHTML` except the static next-button label); keep it that way.
- Accessibility is deliberate: focus moves to the question heading (`renderQuestion(true)`) and to `#next` after answering, results are announced via the `#announcement` `aria-live` region, and the score count-up animation is skipped under `prefers-reduced-motion`. Preserve these when changing flow.
- Styling uses CSS custom properties in `:root` (dark theme; `color-scheme: dark`).
