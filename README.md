# Tenzies

A dice-rolling puzzle game built with React. Roll ten dice and hold the ones you want to keep between rolls — the goal is to get all ten dice to show the same number in as few rolls as possible. Built as a learning project to practice array state, conditional logic, and accessibility basics.

## Tech Stack

- **React** (via Vite)
- **Plain CSS**
- **nanoid** — for generating unique IDs for each die
- **react-confetti** — celebration animation on winning

## How to Play

1. Click "Roll" to roll all ten dice
2. Click any die to "hold" it and lock in its current value
3. Keep rolling — held dice won't change, others will re-roll
4. Win by getting all ten dice to hold the same number

## Features

- **Die component** — a single die button that shows its value and changes color when held
- **Game logic**:
  - Generates 10 dice with random values on load
  - Rolling only re-rolls the dice that aren't held
  - Clicking a die toggles whether it's held
  - Automatically detects when the game is won (all dice held and matching)
- **Win celebration** — a confetti animation plays across the screen when you win, and the button automatically changes to "New Game"
- **Accessibility features**:
  - `aria-pressed` and a descriptive `aria-label` on each die so screen readers announce its value and held state
  - An `aria-live` region that announces "Congratulations! You won!" to screen reader users when the game is won
  - The "New Game" button is automatically focused when the game is won, so keyboard users can immediately start again

## Project Structure

```
src/
├── App.jsx
├── app.css
├── index.jsx
├── index.html
└── components/
    └── Die.jsx
```

## What This Project Practices

- **Managing an array of objects in state** — dice are stored as an array of `{ value, isHeld, id }` objects, updated immutably with `.map()`
- **Generating unique keys with a library** — using `nanoid` instead of array index, so React can correctly track each die even as values change
- **Derived state / computed values** — `gameWon` isn't stored in state; it's calculated on every render from the current `dice` array
- **`useEffect` for side effects tied to state changes** — focusing the button automatically whenever `gameWon` becomes true
- **`useRef` for direct DOM access** — used to grab a reference to the button so it can be focused programmatically
- **Conditional rendering** — showing confetti and swapping button text only when the game is won
- **Accessibility (a11y) fundamentals** — using ARIA attributes and a live region so the game is usable with a screen reader, not just visually

## Status

Actively being built as part of a structured React learning path — more features and refinements to come.