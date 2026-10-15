# Memory Game: Project Context

## What this project is

Memory Game is a small, self-contained browser game based on the classic matching-pairs game, also known as Concentration. Players reveal two cards at a time and try to find every matching pair on the board.

## What the name stands for

"Memory Game" describes the experience directly: players use observation and short-term memory to remember where symbols are hidden and match them with as few turns as possible. The name is not presented as an acronym.

## Purpose

The project offers a quick, approachable game that exercises visual recall and concentration. It is also an example of building a complete interactive experience with standard browser technologies, without requiring a framework, account, server, or external dependency.

## How it works

- Choose a 4x4 board with 8 pairs or a 6x6 board with 18 pairs.
- Reveal cards using a mouse or keyboard. Each turn consists of revealing two cards.
- Matching cards stay revealed; non-matching cards turn back over after a brief pause.
- The game tracks moves and elapsed time and awards a three-star rating based on the number of moves.
- Completing a board shows a results dialog and saves the score in the browser's local storage.
- The best-scores list displays up to five saved results, ordered by move count.

## Who it is for

The game is intended for anyone looking for a short casual puzzle, including players on phones and computers. Keyboard interaction and accessibility attributes support play beyond mouse-only input.

## Technology and structure

The game is implemented in a single `memory-game.html` file using plain HTML, CSS, and JavaScript. CSS Grid creates the responsive board, and JavaScript handles shuffling, card state, timing, scoring, and persistence. There are no external libraries or build steps.

`README.md` explains the features and how to run the game. Open `memory-game.html` directly in a browser, or serve the repository with a local HTTP server.

## Product principles

- Keep the rules immediately understandable.
- Make a new game easy to start and replay.
- Provide feedback through visible moves, time, and rating.
- Support both pointer and keyboard interaction.
- Keep the experience lightweight and self-contained.

## Current scope

This repository is a focused game, not an online multiplayer service or a user-account system. Scores are stored only in the current browser's local storage; they are not synchronized across devices or shared between users.