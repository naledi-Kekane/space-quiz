# Copilot instructions

## Project shape

This is a self-contained, client-side space quiz. `index.html` is the whole application: markup, responsive styles, light/dark theme variables, and the quiz controller are all inline. Open the file directly in a browser; there is no build step, package manager, server, or external dependency.

The quiz content lives in the `questions` array in the inline script. Each question carries its category, prompt, answer choices, zero-based correct-answer index, and explanatory fact. `renderQuestion()` reflects the current question into the DOM; `chooseAnswer()` locks the response, updates the score and feedback; `showResults()` selects the end-of-quiz reaction and enables the high-score celebration for 8 or more points. Keep changes aligned across this data, these transitions, and their existing DOM elements.

## Commands and checks

There are no configured build, lint, or automated test commands. For a browser check, open `index.html` directly and exercise the answer, feedback, progress, score, results, and restart flows. Check both `prefers-color-scheme` variants and keyboard operation when changing presentation or interaction code.

## Codebase conventions

- Keep the app dependency-free and self-contained in `index.html`; avoid introducing tooling or external assets for features that can use native HTML, CSS, and JavaScript.
- Use the existing CSS custom properties in `:root` for shared colors, with corresponding values in `@media (prefers-color-scheme: dark)`. The quiz panel's instrument/grid treatment and page star field are CSS backgrounds and pseudo-elements; preserve their stacking and pointer-event behavior when adjusting layout.
- Quiz content is data-driven from `questions`. Answer choice order is significant because `correct` is a zero-based array index; feedback facts are shown immediately after selection.
- Preserve accessible native button interaction, progress-bar ARIA values, live feedback/score announcements, visible keyboard focus, and explicit focus movement between questions and results. Honor `prefers-reduced-motion` for animations.
- Keep results thresholds consistent: the celebration styling activates at 8/10, while the emoji/title/copy tiers are selected in `showResults()`.
