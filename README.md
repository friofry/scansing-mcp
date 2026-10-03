# ScanSing MCP

Turn PDFs and photos of printed sheet music into MusicXML, then pull out parts, transpose them or export MIDI, from Claude, ChatGPT, Cursor or any MCP client.

![ScanSing](https://scansing.app/assets/img/icon-512.png)

ScanSing is a hosted (remote) MCP server. Nothing to install: connect to

```
https://mcp.scansing.app/mcp
```

Sign-in is OAuth (your client opens the ScanSing page; a new email gets 20 free pages), or send an API key from https://scansing.app/account as `Authorization: Bearer <key>`.

## Install

Claude Code:

```bash
claude mcp add --transport http scansing https://mcp.scansing.app/mcp
```

Claude (claude.ai / desktop): Settings → Connectors → Add custom connector → `https://mcp.scansing.app/mcp`.

Cursor / VS Code / other clients (`mcp.json`):

```json
{
  "mcpServers": {
    "scansing": { "url": "https://mcp.scansing.app/mcp" }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `recognize_sheet_music` | Recognise a PDF or image (URL or base64) into MusicXML; spends pages |
| `get_upload_link` | One-time upload link + curl command for a file on your computer |
| `get_recognition` | Status and summary of a recognition |
| `get_musicxml` | MusicXML of a recognition, in chunks |
| `inspect_score` | File type and page count before recognising (free) |
| `get_usage` | Pages used and left this month |
| `describe_score` | Title, composer, key, time, tempo; per part range, clefs, lyrics |
| `extract_part` | MusicXML of one part (e.g. the alto) |
| `transpose_score` | The score or a part in another key |
| `export_midi` | MIDI link, one track per part |
| `get_download_link` | Short-lived link to MusicXML or MIDI to open in a browser or notation app |

Only `recognize_sheet_music` spends pages; every other tool works on the stored result and is free.

Formats: PDF (up to 40 pages), PNG, JPEG, HEIC, TIFF, WebP. Songbooks can be split into one MusicXML per piece.

## Pricing

20 free pages on sign-up. Paid plans from $9/month for 300 pages: https://scansing.app/pricing/

## Links

- Docs: https://scansing.app/mcp/
- REST API: https://scansing.app/api/
- Privacy: https://scansing.app/privacy/#mcp
- MCP Registry: `app.scansing/scansing`
- Site: https://scansing.app

Scores and results are deleted about an hour after recognition and are never used for training.
