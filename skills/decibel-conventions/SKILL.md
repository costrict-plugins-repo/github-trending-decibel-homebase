---
name: decibel-conventions
description: Use when working in any Decibel project — establishes tool priority, directory conventions, and project detection
---

## Tool Priority

| Priority | Source | Examples |
|----------|--------|---------|
| 1 | Decibel MCP tools | sentinel, architect, oracle, learnings, context, corpus |
| 2 | Plugin skills | This skill, verification, domain-specific skills |
| 3 | Built-in tools | Read, Edit, Bash, Grep, Glob |

Always check if a Decibel MCP tool covers the task before falling back. If MCP tools are unavailable, degrade gracefully to built-in tools.

## Project Detection

A directory is a Decibel project if it contains:
- `.decibel/` directory, OR
- `decibel.json` at the root

## `.decibel/` Directory Contract

| Path | Purpose |
|------|---------|
| `.decibel/sentinel/issues/` | Tracked issues (created via sentinel tool) |
| `.decibel/architect/` | Architecture decisions and design records |
| `.decibel/oracle/learnings/` | Extracted learnings and knowledge |
| `.decibel/specs/` | Specifications and requirements |
| `.decibel/principles/` | Branch-specific principles (each branch decides content) |
| `.decibel/manifest.json` | Project capability manifest |

## Capability Manifest

Projects can declare what they expose via `.decibel/manifest.json`:

```json
{
  "projectId": "my-project",
  "domains": ["trading", "defi"],
  "capabilities": ["portfolio-tracking", "risk-analysis"],
  "designSystem": "decibel-core"
}
```

## Package Discovery

- Check for installed plugins before assuming availability
- Degrade gracefully when optional packages are absent
- Never hard-depend on another plugin — use capability discovery

## Integration Hooks

Packages declare optional interactions via capability discovery:
- If sentinel tools available: structure findings as issues
- If architect tools available: reference ADRs in design work
- If oracle tools available: persist learnings after significant work

No hard dependencies. If a tool is missing, skip the integration silently.
