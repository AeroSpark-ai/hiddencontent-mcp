# HiddenContent — MCP server downloads

**Check a document for hidden text before your agent reads it.**

A document can carry text a person will never see — white on white, sub-readable
font sizes, content positioned off the page, text underneath an image, invisible
codepoints. A model reading that document sees all of it. This MCP server checks
a file first and tells your agent what a human would actually see.

Works on PDF, DOCX, XLSX, PPTX, RTF, HTML, email and the legacy Office formats.

## Install

**Claude Desktop — double-click**

Download `hiddencontent.mcpb` from [the latest
release](https://github.com/AeroSpark-ai/hiddencontent-mcp/releases/latest) and
open it. Claude Desktop installs it from the Extensions tab and asks for your
API token.

**Everything else — npm**

```json
{
  "mcpServers": {
    "hiddencontent": {
      "command": "npx",
      "args": ["-y", "@hiddencontent/mcp"],
      "env": { "HCS_API_TOKEN": "your-token" }
    }
  }
}
```

That snippet is the same for Claude Code and Cursor.

## You need an API token

Get one at [hiddencontent.ai](https://hiddencontent.ai). The server will not
start without one and says so plainly rather than failing quietly.

| Variable | | |
|---|---|---|
| `HCS_API_TOKEN` | required | your API token |
| `HCS_URL` | optional | defaults to the hosted API; set it to point at a self-hosted instance |
| `HCS_CAPABILITIES` | optional | comma-separated list of what your agent can actually do, e.g. `send_email,make_payment`. Some checks only evaluate against what you declare |

## About this repository

**It holds downloads, not source.** The engine that does the detection is
closed-source and lives elsewhere; this repository exists because the MCP
registry distributes bundles from GitHub releases and there has to be a public
place to put one.

The bundle ships no detection rules — no thresholds, no patterns — deliberately.
A published detection signature is something an attacker writes around, so the
server calls the API and the rules stay server-side.

- npm: [`@hiddencontent/mcp`](https://www.npmjs.com/package/@hiddencontent/mcp)
- MCP registry: `ai.hiddencontent/mcp`
- Licence: MIT

## Support

[hiddencontent.ai](https://hiddencontent.ai) · support@aerospark.ai
