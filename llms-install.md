# Installing ScanSing MCP (for Cline and other agents)

ScanSing is a hosted remote MCP server. There is nothing to clone, build or run locally.

1. Ask the user for a ScanSing API key (it starts with `omr_`). They can get one at https://api.scansing.app/account: signing in with a new email comes with 20 free pages.
2. Add the server to the MCP settings (for Cline: `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "scansing": {
      "type": "streamableHttp",
      "url": "https://mcp.scansing.app/mcp",
      "headers": {
        "Authorization": "Bearer omr_YOUR_KEY"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

3. Check it works: call `get_usage`. It returns the pages used and left this month and spends nothing.
4. Try a recognition: `recognize_sheet_music` with `url` set to a PDF or image of printed sheet music, e.g. `https://scansing.app/assets/scores/hosanna.pdf`.

A local file cannot be read by the remote server: call `get_upload_link` and run the `curl` command it returns.
Clients that support MCP OAuth can leave out the `headers` block and sign in in the browser instead.
