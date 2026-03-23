# Connecting MCP Clients to a Drupal Site

> Research compiled 2026-03-23 from official Drupal.org project pages, drupalmcp.io docs, and community guides.

## The Module Landscape

There are **two main Drupal modules** for turning a Drupal site into an MCP server. They are currently merging:

| Module | Project URL | Status |
|--------|------------|--------|
| **Model Context Protocol (drupal/mcp)** | https://www.drupal.org/project/mcp | Stable (v1.2.3, Nov 2025). 368 sites. Recommended. |
| **MCP Server (drupal/mcp_server)** | https://www.drupal.org/project/mcp_server | Built on Tool API. Being merged into drupal/mcp. |

The drupal.org/project/mcp page states: "This module is currently in the process of merging with the MCP Server module." The recommendation is to use `drupal/mcp` as the primary module.

Other related modules:
- **drupal/mcp_client** -- Lets Drupal connect TO external MCP servers (the reverse direction).
- **drupal/mcp_tools** -- Separate project for exposing Drupal tools via MCP using Tool API.

---

## 1. Installation

```bash
# Install the module
composer require 'drupal/mcp:^1.2'

# Enable core module
drush en mcp -y

# Optional submodules
drush en mcp_extra       # Exposes AI module function call actions
drush en mcp_dev_tools   # Controlled Drush command access via MCP
```

If using DDEV, prefix with `ddev`:
```bash
ddev composer require 'drupal/mcp:^1.2'
ddev drush en mcp -y
```

Drupal version support: **^10 || ^11**

---

## 2. Drupal-Side Configuration

1. Go to **`/admin/config/mcp`** (under Web Services) to configure:
   - Enable/disable authentication (token-based or credentials)
   - Enable/disable plugins
   - Select which content types to expose (opt-in by default)
   - Configure user permissions for MCP access

2. Grant the **"Use MCP server"** permission to the appropriate role.

3. Create a **dedicated Drupal user** for MCP access (do not use UID 1 in production).

4. If using the MCP Server module, tool configuration is at **`/admin/config/services/mcp-server/tools`**.

---

## 3. MCP Endpoint URL

The HTTP endpoint exposed by the module:

```
https://your-drupal-site.com/_mcp
```

This endpoint accepts POST requests carrying JSON-RPC messages and can return streaming SSE responses. This is the "Streamable HTTP" transport.

---

## 4. Two Connection Approaches

### Approach A: Docker/Binary STDIO Proxy (Recommended for Claude Desktop)

This uses a TypeScript-based intermediary (`mcp-server-drupal`) that communicates with your Drupal site's HTTP API and exposes STDIO to the local MCP client. This is the most common approach for Claude Desktop since it requires STDIO-based servers.

**Docker image:** `ghcr.io/omedia/mcp-server-drupal:latest`
**Binary releases:** https://github.com/Omedia/mcp-server-drupal/releases

### Approach B: Direct HTTP (Streamable HTTP Transport)

For clients that support Streamable HTTP transport (not STDIO), connect directly to `https://your-site.com/_mcp`. No intermediary binary needed. This is simpler and ideal for remote Drupal sites.

### Approach C: Drush STDIO (MCP Server module)

The MCP Server module (`drupal/mcp_server`) provides a Drush command for STDIO transport:

```bash
vendor/bin/drush mcp:server
```

---

## 5. Client Configuration

### Claude Desktop

Config file location:
- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%/Claude/claude_desktop_config.json`

#### Option 1: Docker (most common)

```json
{
  "mcpServers": {
    "drupal": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "-e", "DRUPAL_AUTH_USER",
        "-e", "DRUPAL_AUTH_PASSWORD",
        "--network=host",
        "ghcr.io/omedia/mcp-server-drupal:latest",
        "--drupal-url=https://mysite.ddev.site",
        "--unsafe-net"
      ],
      "env": {
        "DRUPAL_AUTH_USER": "mcp_user",
        "DRUPAL_AUTH_PASSWORD": "secure_password_here"
      }
    }
  }
}
```

Notes:
- Replace `https://mysite.ddev.site` with your actual Drupal URL.
- `--network=host` is needed for local DDEV sites.
- `--unsafe-net` is needed for self-signed certificates.
- The user must have the "Use MCP server" permission in Drupal.

#### Option 2: Binary (no Docker)

Download the binary from https://github.com/Omedia/mcp-server-drupal/releases, make it executable, then:

```json
{
  "mcpServers": {
    "drupal": {
      "command": "/path/to/mcp-server-drupal",
      "args": ["--drupalBaseUrl", "https://your-drupal-site.com"],
      "env": {}
    }
  }
}
```

#### Option 3: Drush STDIO (MCP Server module)

```json
{
  "mcpServers": {
    "drupal": {
      "command": "vendor/bin/drush",
      "args": ["mcp:server"],
      "cwd": "/path/to/your/drupal/site"
    }
  }
}
```

### Claude Code (CLI)

```bash
claude mcp add --scope project mcp-server-drupal docker \
  -e DRUPAL_AUTH_USER=mcp_user \
  -e DRUPAL_AUTH_PASSWORD=secure_password_here \
  -- run -i --rm \
  -e DRUPAL_AUTH_USER \
  -e DRUPAL_AUTH_PASSWORD \
  --network=host \
  ghcr.io/omedia/mcp-server-drupal:latest \
  --drupal-url=https://mysite.ddev.site \
  --unsafe-net
```

### Cursor

Cursor uses the same configuration format as Claude Desktop. Add the same JSON configuration block to Cursor's MCP settings. The config location in Cursor is typically accessible via Settings > MCP.

### MCP Tools Module (Alternative)

If using `drupal/mcp_tools` instead, the Drush command is different:

```bash
drush mcp-tools:serve --quiet --uid=1 --scope=read,write
```

---

## 6. Is There an npx Command?

**No.** There is no `npx` command for the Drupal MCP server. The options are:
1. **Docker image:** `ghcr.io/omedia/mcp-server-drupal:latest`
2. **Pre-built binary:** Download from GitHub releases
3. **Direct HTTP:** Connect to `/_mcp` endpoint (no intermediary needed)
4. **Drush command:** `drush mcp:server` (MCP Server module)

---

## 7. Quick Start Summary

The fastest path to get Claude Desktop talking to a Drupal site:

```bash
# 1. Install and enable
composer require 'drupal/mcp:^1.2'
drush en mcp -y

# 2. Grant permission to a user
# Go to /admin/people/permissions and grant "Use MCP server"

# 3. Configure content types to expose
# Go to /admin/config/mcp

# 4. Add to Claude Desktop config (macOS)
# Edit ~/Library/Application Support/Claude/claude_desktop_config.json
# Add the Docker-based mcpServers config shown above

# 5. Restart Claude Desktop
```

---

## Sources

- https://www.drupal.org/project/mcp
- https://www.drupal.org/project/mcp_server
- https://www.drupal.org/project/mcp_tools
- https://drupalmcp.io/en/
- https://drupalmcp.io/en/mcp-server/connect-to-llms/
- https://drupalmcp.io/en/mcp-server/setup-configure/
- https://mcp-77a54f.pages.drupalcode.org/quick-start/setup/
- https://opensenselabs.com/blog/mcp-server
- https://bonnici.co.nz/blog/drupal-mcp-server-ai-integration
- https://github.com/Omedia/mcp-server-drupal
