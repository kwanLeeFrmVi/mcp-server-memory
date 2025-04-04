# MCP Server: Memory

[![NPM Version](https://img.shields.io/npm/v/mcp-server-memory.svg)](https://www.npmjs.com/package/mcp-server-memory)
[![Bun Version](https://img.shields.io/badge/bun-v1.2.8-blueviolet)](https://bun.sh)
[![License](https://img.shields.io/npm/l/mcp-server-memory.svg)](LICENSE)

This project is derived from the original [`@modelcontextprotocol/server-memory`](https://www.npmjs.com/package/@modelcontextprotocol/server-memory) package, modified for my specific needs.

An MCP (Model Context Protocol) server providing persistent memory capabilities for AI models through a knowledge graph. This allows models like Claude to retain and recall information across interactions.

## Overview

This server implements the Model Context Protocol and acts as a bridge between an AI model and a persistent knowledge graph stored locally. It allows the model to:

- Create and manage entities (people, places, concepts, etc.).
- Define relationships between entities.
- Store observations or facts associated with entities.
- Search and retrieve information from the knowledge graph.

By default, the knowledge graph is stored in a `knowledge_graph.json` file in the current working directory where the server is run.

## Usage with Claude Desktop

This server is primarily designed to be used with MCP-compatible clients like the Claude Desktop application. You configure it within the client's settings.

**Example `mcpServers` Configuration:**

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "mcp-server-memory"],
      "env": {
        "MEMORY_FILE_PATH": "/path/to/your/custom_memory.json"
      }
    }
  }
}
```

...[rest of existing content remains unchanged...]
