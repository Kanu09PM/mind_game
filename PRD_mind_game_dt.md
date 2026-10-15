# Product Requirements Document: Dark Theme for Memory Game

## Document information

- Product: Memory Game
- Feature: Optional dark theme
- Status: Ready for implementation
- Scope: `memory-game.html` in this repository

## Summary

Add an optional dark color theme to the existing browser-based memory game. Players can switch between the current light appearance and a dark appearance without interrupting a game. The selected theme should be remembered when browser storage is available, while preserving all existing gameplay, accessibility, and score behavior.

## Problem

The game currently has only a light appearance. Players who prefer a darker interface or play in dim environments have no way to adjust the display. The theme feature should provide that choice without changing the rules or adding setup friction.

## Goals

- Give players a clear, accessible way to switch between light and dark themes.
- Apply the chosen theme immediately without reloading or restarting the game.
- Remember the choice between visits when browser storage is available.
- Keep the current light theme as the default for first-time players.
- Preserve gameplay, saved scores, responsive layout, and keyboard interaction.

## Non-goals

- Redesigning the game or changing its visual layout beyond the theme control and theme colors.
- Automatically following the operating system theme in this release.
- Adding accounts, cross-device preference sync, or new score behavior.
- Changing grid sizes, card symbols, scoring rules, or game mechanics.
- Adding libraries, a build system, or a server requirement.

## Target users

- Players who prefer a dark interface or play in low-light settings.
- Players who need clear contrast and consistent focus indicators.
- Existing players who expect the current game and score behavior to remain unchanged.

## User stories

- As a player, I can switch to dark theme so the game is comfortable to view in a dim environment.
- As a player, I can switch back to light theme at any time.
- As a returning player, I see my last selected theme when I reopen the game, when browser storage permits.
- As a keyboard user, I can find, understand, and operate the theme control without a mouse.
- As a player in an active game, I can change the theme without losing my cards, moves, timer, or progress.

## Requirements

### Theme control

1. Provide a clearly named theme toggle in the existing game interface. It must be available before, during, and after a game.
2. The control must expose its current state to assistive technology, have a visible keyboard focus indicator, and work with standard keyboard activation.
3. The control's visible label and accessible state must make the available action or current theme unambiguous.
4. Switching themes must update the interface immediately without a page reload, a new game, or a change in game state.

### Theme appearance

1. The light theme must retain the current appearance as closely as practical.
2. The dark theme must use coordinated colors for the page background, primary text, statistics area, grid-size controls, card faces and backs, score list, completion dialog, and interactive states.
3. Text, controls, focus indicators, and meaningful card states must remain distinguishable in both themes. Meet WCAG 2.1 AA contrast targets where applicable: 4.5:1 for normal text and 3:1 for large text and essential interface graphics.
4. Hover, active, focus, disabled, and matched states must remain visually clear in both themes.
5. Theme changes must not alter card dimensions, board layout, animations, or responsive behavior.

### Preference persistence

1. On a first visit, or when no valid preference exists, use the current light theme.
2. Save the selected theme under a theme-specific storage key that is separate from the existing `memoryGameScores` data.
3. On later visits, restore the saved theme when browser storage is available.
4. If reading or writing the theme preference fails, keep the game usable and use the current in-memory selection; do not block game startup.
5. Changing the theme must never clear, rewrite, reorder, or otherwise affect saved scores.

### Compatibility and regression protection

1. The 4x4 and 6x6 boards must continue to initialize and play as they do now.
2. Card matching, mismatch timing, move counting, timer, star rating, win dialog, replay, and score ranking must remain unchanged.
3. Mouse and keyboard card interaction must continue to work.
4. The game must continue to run as a standalone HTML file in a modern browser, with no external dependencies or build step.
5. The layout must remain usable on narrow mobile screens and desktop screens.

## UX behavior

- Place the theme control in the existing header or another persistent, clearly discoverable area without crowding the game statistics or grid controls.
- Use concise text that identifies the theme action/state; do not rely on color alone to communicate it.
- Switching themes while a mismatch is waiting to turn over must not cancel or restart that timeout.
- Switching themes while the completion dialog is open must update the dialog and the underlying page consistently.

## Acceptance criteria

- A fresh browser profile opens in light theme and the existing interface remains recognizable.
- The player can switch to dark theme and back using both mouse and keyboard.
- The selected theme is applied immediately; moves, cards, timer, rating, and current board remain unchanged.
- The selected theme is restored after reload when local storage is available.
- Missing, invalid, or inaccessible theme storage does not prevent the game from starting or being played.
- The existing score key and saved score list remain intact after changing themes, completing a game, and reopening it.
- Theme colors cover the board, game controls, statistics, best scores, and completion dialog, with readable text and visible focus states in both themes.
- The 4x4 and 6x6 games remain playable at mobile and desktop widths.
- No external dependency or build step is introduced.

## Verification checklist

1. Clear only the theme preference and reload: confirm light theme is used; do not clear game scores.
2. Switch themes and verify immediate appearance without resetting a game in progress.
3. Reload after each theme selection and confirm persistence.
4. Play and finish one game in each theme; verify moves, timer, rating, matching, dialog, replay, and saved scores.
5. Repeat card and theme control interactions using keyboard only.
6. Test both board sizes at narrow and wide viewport widths.
7. Simulate unavailable or malformed theme preference data and confirm the game remains usable.
8. Check contrast and focus visibility for both themes.

## Release criteria

The feature is ready when all acceptance criteria pass and no gameplay, score persistence, accessibility, or responsive-layout regression is observed. Keep the existing light theme as the fallback if theme preference persistence is unavailable.