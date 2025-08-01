# Contributing to @zilliz/code-context-mcp

Thanks for your interest in contributing to the Code Context MCP server!

> 📖 **First time contributing?** Please read the [main contributing guide](../../CONTRIBUTING.md) first for general setup and workflow.

## MCP Server Development

This guide covers development specific to the MCP server.

### Quick Commands
```bash
# Build MCP server
pnpm build:mcp

# Watch mode for development
pnpm dev:mcp

# Start server
pnpm start

# Run with environment variables
pnpm start:with-env
```

### Required Environment Variables
See [README.md](./README.md#prepare-environment-variables) for required environment variables.

## Running the MCP Server

1. Build the server:
   ```bash
   pnpm build
   ```
2. Run with MCP client or directly:
   ```bash
   pnpm start
   ```
3. Use the tools:
   - `index_codebase` - Index a sample codebase
   - `search_code` - Search for code snippets
   - `clear_index` - Clear the index

## Making Changes

1. Create a new branch for your feature/fix
2. Edit `src/index.ts` - Main MCP server implementation  
3. Verify with MCP clients (Claude Desktop, etc.)
4. Follow commit guidelines in the [main guide](../../CONTRIBUTING.md)

## MCP Protocol

- Follow [MCP specification](https://modelcontextprotocol.io/)
- Use stdio transport for compatibility
- Handle errors gracefully with proper MCP responses
- Redirect logs to stderr (not stdout)

## Guidelines

- Keep tool interfaces simple and intuitive
- Provide clear error messages
- Validate all user inputs
- Use TypeScript for type safety

## Working with MCP Clients

### Cursor/Claude Desktop Development Mode Configuration
You can use the following configuration to configure the MCP server with a development mode.
```json
{
  "mcpServers": {
    "code-context-local": {
      "command": "node",
      "args": ["PATH_TO_CODECONTEXT/packages/mcp/dist/index.js"],
      "env": {
        "OPENAI_API_KEY": "sk-your-openai-api-key",
        "MILVUS_TOKEN": "your-zilliz-cloud-api-key"
      }
    }
  }
}
```

### Claude Code Development Mode Configuration
```bash
claude mcp add code-context -e OPENAI_API_KEY=sk-your-openai-api-key -e MILVUS_TOKEN=your-zilliz-cloud-api-key -- node PATH_TO_CODECONTEXT/packages/mcp/dist/index.js
```
And then you can start Claude Code with `claude --debug` to see the MCP server logs.

### Manual Usage
Use all three MCP tools:
- `index_codebase` - Index sample repositories
- `search_code` - Search with various queries  
- `clear_index` - Clear and re-index

## Questions?

- **General questions**: See [main contributing guide](../../CONTRIBUTING.md)
- **MCP-specific issues**: Open an issue with the `mcp` label 