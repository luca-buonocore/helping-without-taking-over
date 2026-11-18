# Helping without taking over

A 3–5 minute serious game. You manage Alex across three connected scenes and decide how to help: take over, support, or step back. Then replay with another approach and compare.

## Run it
Open `index.html` in a browser. No build, no dependencies, no network.

Saved runs use `localStorage`. Some browsers block it for files opened with `file://`; the game still works, but runs are not kept after a reload. To test persistence, serve the folder:

```
python -m http.server 8765
```

and open http://localhost:8765.

## How it works
- **State is only the list of choices** (plus the current scene and phase). Every meter is recomputed from that list, so replay, restart and reload cannot drift out of sync.
- **Four meters**: Result quality, Relationship with Alex, Your time, Alex's ownership. The first three change immediately. Ownership changes one scene later ("Since last time…"), because the cost of taking over is delayed in real life.
- **Branching**: scene 2 opens differently depending on scene 1. Scene 3 reads the pattern of the first two choices (Alex is dependent, owning or withdrawn) and changes Alex's lines, reactions and effects.
- **No style always wins.** Each option is the best move somewhere and costly elsewhere:
  - Scene 1: coaching builds ownership but costs quality and goodwill the night before a client meeting; taking over does the opposite.
  - Scene 2: only the manager can remove the blocker, so taking over is right; coaching here is wasted homework, and refusing leaves Alex stuck.
  - Scene 3: with an Alex who already owns their work, coaching feels like micromanagement and stepping back is best; with a withdrawn Alex, coaching repairs the relationship.
- **Situations stay fixed on purpose**: what changes between runs is Alex (how problems reach you, what Alex says, how they react), so runs can be compared like for like.
- **End screen**: an epilogue six months later, a comparison with the previous run, and a step-by-step timeline.
- **Restart** discards the current run and keeps completed runs.

## Shortcuts
- Fixed text and hand-tuned numbers; no AI model at runtime.
- One Alex, one storyline, three options per scene.
- Replay is whole-run only (no "retry this scene").

## Files
- `index.html` — the whole app
