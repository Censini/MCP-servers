# GitHub MCP Server Installation Guide

This guide provides detailed instructions for installing and configuring the GitHub MCP server on Windows for use with Claude Desktop or Cline.

## Prerequisites

- Windows operating system
- Node.js and npm installed
- GitHub account with a Personal Access Token (PAT)
- Claude Desktop or Cline installed

## Installation Steps

### Step 1: Create Directory Structure

```powershell
# Create the MCP directory in Documents folder
mkdir -p "$env:USERPROFILE\Documents\Claude\MCP"
```

### Step 2: Install GitHub MCP Server Package

```powershell
# Install the GitHub MCP server package globally
npm install -g @modelcontextprotocol/server-github
```

### Step 3: Create GitHub Personal Access Token

1. Go to [GitHub Settings > Developer settings > Personal access tokens](https://github.com/settings/tokens)
2. Click "Generate new token" (classic)
3. Give it a descriptive name like "Claude GitHub MCP"
4. Select the `repo` scope for full repository access (or `public_repo` for public repositories only)
5. Click "Generate token"
6. Copy the generated token (you'll need it in the next step)

### Step 4: Configure Claude Desktop or Cline

#### For Claude Desktop:

1. Locate the Claude Desktop configuration file:
   ```
   %APPDATA%\Claude\claude_desktop_config.json
   ```
   (Typically: C:\Users\YourUsername\AppData\Roaming\Claude\claude_desktop_config.json)

2. Edit the file to add the GitHub MCP server configuration (see example in `claude_desktop_config.json`)

#### For Cline (VSCode Extension):

1. Locate the Cline MCP settings file:
   ```
   %APPDATA%\Code\User\globalStorage\saoudrizwan.claude-dev\settings\cline_mcp_settings.json
   ```
   (Typically: C:\Users\YourUsername\AppData\Roaming\Code\User\globalStorage\saoudrizwan.claude-dev\settings\cline_mcp_settings.json)

2. Edit the file to add the GitHub MCP server configuration:
   ```json
   {
     "mcpServers": {
       "github.com/modelcontextprotocol/servers/tree/main/src/github": {
         "command": "node",
         "args": [
           "C:\\Users\\YourUsername\\AppData\\Roaming\\npm\\node_modules\\@modelcontextprotocol\\server-github\\dist\\index.js"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "your-github-token-here"
         },
         "disabled": false,
         "autoApprove": []
       }
     }
   }
   ```

3. Replace:
   - `YourUsername` with your Windows username
   - `your-github-token-here` with the GitHub Personal Access Token you created

### Step 5: Restart Claude Desktop or VSCode

1. Close Claude Desktop or VSCode completely
2. Reopen the application

### Step 6: Verify Installation

1. Ask Claude a question that uses the GitHub MCP server, such as:
   ```
   Search for repositories related to "modelcontextprotocol" on GitHub
   ```

2. Claude should use the GitHub MCP server to search for repositories and display the results.
