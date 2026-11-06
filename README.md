# Rhythm Practice Lab

Practice a Web Audio metronome and inspect tap timing against a beat grid.

[![Build and verify](https://github.com/netcodermike/rhythm-practice-lab/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/rhythm-practice-lab/actions/workflows/verify.yml)

**Language:** TypeScript · **Platform:** Windows, macOS, Linux browser · **App type:** Browser metronome and timing accuracy trainer

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- 30–240 BPM metronome
- Lookahead audio scheduling
- Mouse/Space taps
- Mean-absolute and RMS timing error

## Requirements

Node.js 24.12+ and a modern browser; no npm dependencies.

## Quick start

```sh
git clone https://github.com/netcodermike/rhythm-practice-lab.git
cd rhythm-practice-lab
node server.ts
# Open http://127.0.0.1:3030
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Start at 120 BPM, tap Space repeatedly, inspect signed errors, reset taps, and compare at a slower tempo. Stop before changing tempo.

## Architecture, configuration, and data

core.ts validates increasing timestamps and compares each tap with the nearest beat grid anchored at the first tap. Browser AudioContext schedules short oscillator clicks with a 100 ms lookahead/25 ms timer. The first beat is accented every four beats. Up to 64 taps are retained. Stop closes audio; tempo is locked while playing. Tests verify perfect grids, signed drift, and invalid timing. No data is saved.

## Verification

Build with the quick-start command where needed, then run:

```sh
node --test test.ts
```

Manual acceptance: Start at 120 BPM, tap Space repeatedly, inspect signed errors, reset taps, and compare at a slower tempo. Stop before changing tempo. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

Not calibrated for audio/input latency, clinical measurement, or professional timing certification. Tap grid anchors to the first tap rather than the audible metronome start, so fixed phase offsets are not measured. Missed beats can still match the nearest grid. Browser scheduling/tab throttling affects performance. Audio requires user activation.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `core.ts`
- `package.json`
- `server.ts`
- `test.ts`
- `public/index.html`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
