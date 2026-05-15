# Matt

## VS Code MCP Setup

This workspace includes an Etherscan MCP server definition in `.vscode/mcp.json`.

1. Open this workspace in VS Code.
2. When prompted, trust the `etherscan` MCP server.
3. Enter your Etherscan API key when VS Code asks for `etherscan-api-key`.
4. Use `MCP: List Servers` from the Command Palette if you need to start or inspect the server manually.

The API key is requested securely through a VS Code input variable and is not stored in the repository.

## User Profile MCP Config

If you want to use the same Etherscan MCP server across multiple workspaces, add this to your user-profile `mcp.json` instead of keeping it only in this repository:

```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "etherscan-api-key",
      "description": "Etherscan API key",
      "password": true
    }
  ],
  "servers": {
    "etherscan": {
      "type": "http",
      "url": "https://mcp.etherscan.io/mcp",
      "headers": {
        "Authorization": "Bearer ${input:etherscan-api-key}"
      }
    }
  }
}
```

Open the user-profile config with `MCP: Open User Configuration` from the Command Palette.
