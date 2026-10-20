---
name: decibel-verification
description: Use when about to claim work is complete in a Decibel project — verify before asserting done
---

## Before Claiming Done

1. **Run tests** — execute the project's test suite, confirm passing output
2. **Check build** — run the build command, confirm zero errors
3. **Verify actual output** — show the passing output, don't just say "it works"

## With Sentinel Available

- Run `sentinel` to check for open issues related to current work
- Confirm no regressions introduced
- If new issues found, address or explicitly note them

## Without Sentinel (Degraded Mode)

- Still verify via tests and build
- Log that sentinel check was skipped: "Note: sentinel unavailable, verified via tests/build only"

## Core Rule

**Evidence before assertions.** Show the terminal output. Paste the passing test count. Include the build log snippet. Never claim completion without proof.
