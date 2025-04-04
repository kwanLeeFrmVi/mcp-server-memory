# MCP Server: Memory

[![NPM Version](https://img.shields.io/npm/v/mcp-server-memory.svg)](https://www.npmjs.com/package/mcp-server-memory)
[![Bun Version](https://img.shields.io/badge/bun-v1.2.8-blueviolet)](https://bun.sh)
[![License](https://img.shields.io/npm/l/mcp-server-memory.svg)](LICENSE)

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

### Configuration: Memory File Path

- **`MEMORY_FILE_PATH` (Environment Variable):** As shown in the example above, you can use this environment variable within the `env` block of your client configuration to specify a custom path for the knowledge graph file. If omitted, it defaults to `knowledge_graph.json` in the directory where the client application runs the server command.

## Standalone Installation & Usage

While typically run via a client like Claude Desktop, you can also run the server directly.

The easiest way is using `npx` (or `bunx`), which downloads and runs the package without a global installation:

```bash
# Using npx
npx mcp-server-memory

# Using bunx
bunx mcp-server-memory
```

This will start the server, listening for MCP connections via standard input/output (stdio) and using the default `knowledge_graph.json` path.

To use a custom memory path when running standalone:

```bash
MEMORY_FILE_PATH=/path/to/your/custom_memory.json npx mcp-server-memory
```

Alternatively, you can install it globally:

```bash
npm install -g mcp-server-memory
# or
bun install -g mcp-server-memory
```

Then run it directly:

```bash
# Default path
mcp-server-memory

# Custom path
MEMORY_FILE_PATH=/path/to/your/custom_memory.json mcp-server-memory
```

## Features (MCP Tools)

This server provides the following tools accessible via the MCP client:

- **`create_entities`**: Create multiple new entities in the knowledge graph.
- **`create_relations`**: Create multiple new relations between entities. Relations should be in active voice.
- **`add_observations`**: Add new observations (facts) to existing entities.
- **`delete_entities`**: Delete multiple entities and their associated relations.
- **`delete_observations`**: Delete specific observations from entities.
- **`delete_relations`**: Delete multiple relations between entities.
- **`read_graph`**: Read the entire knowledge graph.
- **`search_nodes`**: Search for nodes (entities) based on a query matching names, types, or observation content.
- **`open_nodes`**: Retrieve specific nodes by their names.

## Development

If you want to contribute or run the server from the source code:

### Prerequisites

- [Bun](https://bun.sh) or [Node.js](https://nodejs.org/) with npm

### Setup

```bash
# Clone the repository (if you haven't already)
# git clone https://github.com/kwanLeeFrmVi/mcp-server-memory.git
# cd mcp-server-memory

# Install dependencies
bun install
# or
npm install
```

### Building

Compile the TypeScript code:

```bash
bun run build
# or
npm run build
```

### Running Locally

```bash
bun run start
# or
npm run start
# or directly
bun run dist/index.js
```

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](LICENSE)
