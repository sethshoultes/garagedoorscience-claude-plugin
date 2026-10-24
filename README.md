# Garage Door Science for Claude

Skills and a connector that help a homeowner work out what is wrong with a garage door, know what is safe to do themselves and what is a job for a pro, and hand off to a local pro. The answers cite the matching article at [garagedoorscience.com](https://garagedoorscience.com).

## Install

In Claude Code:

```
/plugin install garagedoorscience --marketplace sethshoultes/garagedoorscience-claude-plugin
```

This adds the skills and the Garage Door Science connector (`https://garagedoorscience.com/mcp`, public, no sign-in). In Claude on the web or Desktop, add the connector at that URL under Settings, Connectors.

## What is inside

| Skill | When Claude uses it |
|---|---|
| `diagnose` | The door will not open or close, the opener or lights are dead, the remote only works up close, or it acts up in a power outage |
| `noisy-door` | A grind, rattle, squeak or pop |
| `seasonal-maintenance-checklist` | A safe walk-around and the three-to-six-month pass |
| `stay-safe` | Always on: springs and cables are always a job for a pro, never a step |
| `find-a-pro` | The problem is not a do-it-yourself job, or the homeowner wants someone to come out |

## Safety

Claude never gives steps for springs, cables, bottom brackets or an off-track door. It never tells anyone to open an outlet, a panel or the opener, or to turn off, cover or bypass the safety sensors. If a skill is unsure, it says so and points to a pro.

## Connector

The connector is read-only for homeowners: it looks up diagnoses, reference photos, door styles and typical cost ranges from Garage Door Science. Two tools take a photo or an inspection a homeowner chooses to send. Privacy: https://garagedoorscience.com/privacy

## License

MIT
