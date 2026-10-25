# Excalidraw diagrams skill for OpenClaw

An OpenClaw skill that turns a short description of boxes and connections into an Excalidraw drawing: an Obsidian Excalidraw note (`.excalidraw.md`) or a `.excalidraw` file for excalidraw.com.

Language models are bad at writing Excalidraw JSON by hand. They misplace labels, leave arrows unbound and produce overlapping shapes. This skill has the agent write a small spec instead, and a deterministic Python script does the layout, text and arrow bindings, IDs and file wrapper. A second script validates the result.

## Install

From ClawHub: `openclaw skills install @ricardodpalmeida/excalidraw-diagrams`. Or copy this folder into your workspace `skills/` directory. Needs Python 3.9 or newer and nothing else.

## Try it

```bash
python3 scripts/build_diagram.py --spec examples/ci-pipeline.json --out ci-pipeline.excalidraw
python3 scripts/validate.py ci-pipeline.excalidraw
```

Open the file on excalidraw.com, or use a `.excalidraw.md` name and open it in Obsidian with the Excalidraw plugin. The spec format is documented in `SKILL.md`.

## Files

- `SKILL.md` holds the agent instructions and the spec format.
- `scripts/build_diagram.py` builds the drawing. It never overwrites a file without `--force` and makes no network calls.
- `scripts/validate.py` checks structure, two-way bindings, fonts and overlaps.
- `references/excalidraw-format.md` documents the file format for hand edits.
- `examples/` has sample specs; `tests/` runs with `python3 -m unittest discover -s tests`.

## License

MIT-0, as published on ClawHub.
