# Space Scrap Shooter: Bare Bones

The smallest version of the main game, so the team can each pick a piece to build on.
TypeScript + Konva + Vite.

## Run it

```
npm install
npm run dev      # open the local URL it prints
npm test         # unit tests for the question and answer logic
npm run build    # typecheck + production build
```

## What it does

4 scraps sit on screen, each with a multiplication problem. The first one has a thick outline.
Type its answer (digits, Backspace to fix) and press Enter.

- Right: the ship fires a line at it, and a new scrap takes its place at the back of the line.
- Wrong: the input box border thickens briefly and the input clears.

That is all. Black and white, plain shapes. No waves, health, score, falling, or effects.

## Files

```
src/
  logic/
    questions.ts       makeQuestion() builds a "6 x 7" problem; isCorrect() checks the typed answer
    logic.test.ts      unit tests for questions.ts
  engine/
    GameEngine.ts      Konva drawing, keyboard input, shooting; starts the game at the bottom
```

`index.html` loads `GameEngine.ts` directly and has the `<div id="game">` the game draws into.

## Pieces you could pick up

| Piece | Where to start |
|---|---|
| Falling scraps and a danger line | `GameEngine.ts`: add a `Konva.Animation` that moves each scrap down |
| Waves and difficulty | `GameEngine.ts` `spawnScrap`, `questions.ts` `makeQuestion` |
| Health and game over | new `HealthSystem` in `logic/`, hooked into the engine |
| Score and combo | new `ScoringAndCombo` in `logic/`, called from `shoot()` and `flashWrong()` |
| Other problem types (division, factors) | `questions.ts`, `checkAnswer.ts` |
| Teacher settings (range, speed) | pull the constants at the top of `questions.ts` and `GameEngine.ts` into a config |
| Start and results screens | new screens around `GameEngine` in `main.ts` |
