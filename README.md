# HiddenContent — MCP server downloads

**Detects hidden text in PDF, Word, Excel, PowerPoint, RTF and HTML files that a person can’t see but an AI reads: white-on-white text, tiny fonts, off-page text, invisible Unicode, hidden layers.**

Run it before your agent reads a document. It checks the file itself, tells your
agent what a person would actually see, and shows you each hidden passage, where
it sits and the trick behind it. It also reads email (.eml), plain text and the
older Office formats (.doc, .xls, .ppt).

- [Every technique it detects, one page each](https://hiddencontent.ai/techniques/)
- [Real cases: hidden text read by AI, in the wild](https://hiddencontent.ai/in-the-wild/)
- [How-to guides: checking a PDF, a Word file, a résumé and more](https://hiddencontent.ai/guides/)

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
