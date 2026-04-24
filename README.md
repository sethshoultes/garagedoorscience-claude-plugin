# Garage Door Science — Claude Code plugin

A Claude Code plugin that ships a `diagnose-garage-door` skill plus an MCP connector config for `garagedoorscience.com`. Once installed, Claude gains eight tools for garage-door diagnostics, reference photos, cost estimation, and partner routing.

## What's inside

- **`.claude-plugin/plugin.json`** — plugin manifest
- **`skills/diagnose-garage-door/SKILL.md`** — instructions for Claude on when and how to use the garagedoorscience.com tools, safety rules, and answer shape
- **`.mcp.json`** — MCP server registration pointing at `https://garagedoorscience.com/mcp` (public tier; no auth)

## Install

### Option 1 — User-level (every project gets the plugin)

```bash
cd ~/.claude/plugins
git clone https://github.com/sethshoultes/garagedoorscience-claude-plugin.git
```

Restart Claude Code (or reload via `/plugin reload` if your version supports it).

### Option 2 — Project-level

```bash
cd your-project
mkdir -p .claude/plugins
git clone https://github.com/sethshoultes/garagedoorscience-claude-plugin.git .claude/plugins/garagedoorscience
```

The plugin is registered for that project only.

### Option 3 — Claude Desktop (Custom Connector UI, no plugin)

If you're using Claude Desktop instead of Claude Code:

1. Open Claude Desktop → Settings → **Connectors**
2. Click **Add Custom Connector**
3. URL: `https://garagedoorscience.com/mcp`
4. Auth: **None** (public tier)

The SKILL.md in this repo becomes reference documentation you can paste into your own system prompt.

## Use

Once installed, ask Claude questions like:

- *"My garage door won't close all the way — what should I check?"*
- *"What does a broken torsion spring look like?"*
- *"Find me a garage-door pro near 84770."*

Claude will invoke the `diagnose-garage-door` skill when the conversation hits those triggers, and call MCP tools as needed.

## Upgrade to pro tier

The public tier is 60 requests/min, 2000/day per IP. For higher limits and top-10 retrieval (vs top-3 public), grab a free `gds_live_` key at [garagedoorscience.com/developers](https://garagedoorscience.com/developers), then edit `.mcp.json`:

```json
{
  "mcpServers": {
    "garagedoorscience": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://garagedoorscience.com/mcp-pro",
        "--header",
        "Authorization: Bearer gds_live_YOUR_KEY_HERE"
      ]
    }
  }
}
```

## Related

- **Platform this calls:** [garagedoorscience.com](https://garagedoorscience.com)
- **Agent docs:** [/brain](https://garagedoorscience.com/brain)
- **Use cases & recipes:** [/developers/use-cases](https://garagedoorscience.com/developers/use-cases)
- **Cookbook repo:** [garagedoorscience-cookbook](https://github.com/sethshoultes/garagedoorscience-cookbook)
- **WordPress plugin:** [wp-garagedoorscience](https://github.com/sethshoultes/wp-garagedoorscience)
- **Essay on the pattern:** [One Registry, Seven Surfaces](https://sethshoultes.com/blog/one-registry-seven-surfaces.html)

## License

MIT.
