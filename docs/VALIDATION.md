# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux browser.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
node --test test.ts
node --check server.ts
```

## Manual acceptance

Start at 120 BPM, tap Space repeatedly, inspect signed errors, reset taps, and compare at a slower tempo. Stop before changing tempo. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.

## Observed CI result

Passed: [target-platform build/check](https://github.com/netcodermike/rhythm-practice-lab/actions/runs/42206108035). Source commit: `2fdbcc5bca53382d1e4b5734ae33ce5d9113e126`. Later documentation-only changes do not alter the tested implementation. The reproducible commands above identify test scope; native GUI/audio/permissions are not implied by compilation.
