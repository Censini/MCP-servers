# GitHub MCP Server Troubleshooting Guide

This guide provides solutions to common issues you might encounter when setting up or using the GitHub MCP server.

## Installation Issues

### "Command not found" when running npm commands

**Problem**: When running npm commands, you get an error like "'npm' is not recognized as an internal or external command".

**Solution**:
1. Make sure Node.js is installed properly. Download and install from [nodejs.org](https://nodejs.org/).
2. Check if Node.js is in your PATH by running `node --version` in a new terminal.
3. If needed, add Node.js to your PATH environment variable.

### Error installing the GitHub MCP server package

**Problem**: You encounter errors when trying to install the package globally.

**Solution**:
1. Try running the command with administrator privileges (Run PowerShell or Command Prompt as Administrator).
2. Check your npm configuration with `npm config list`.
3. Try clearing the npm cache with `npm cache clean --force` and then reinstall.

## Configuration Issues

### MCP server not connecting

**Problem**: The GitHub MCP server is not connecting after configuration.

**Solution**:
1. Double-check the path to the server in your configuration file. Make sure it points to the correct location where the package is installed.
2. Verify that the server name in the configuration matches exactly: `github.com/modelcontextprotocol/servers/tree/main/src/github`.
3. Make sure you've restarted Claude Desktop or VSCode after making configuration changes.
4. Check that your GitHub Personal Access Token is valid and has the necessary permissions.

### "Not connected" error when using MCP tools

**Problem**: When trying to use GitHub MCP tools, you get a "Not connected" error.

**Solution**:
1. Make sure the MCP server is properly configured in the settings file.
2. Try running the GitHub MCP server manually to see if there are any errors:
   ```powershell
   node "C:\Users\YourUsername\AppData\Roaming\npm\node_modules\@modelcontextprotocol\server-github\dist\index.js"
   ```
3. Check if the GITHUB_PERSONAL_ACCESS_TOKEN environment variable is set correctly in your configuration.

## GitHub API Issues

### Authentication errors

**Problem**: You get authentication errors when trying to use GitHub MCP tools.

**Solution**:
1. Verify that your GitHub Personal Access Token is valid and hasn't expired.
2. Check that your token has the necessary scopes (e.g., `repo` for full repository access).
3. Generate a new token if needed and update your configuration.

### Rate limiting

**Problem**: You encounter rate limiting errors when making many requests to the GitHub API.

**Solution**:
1. The GitHub API has rate limits for authenticated users. Check your current rate limit status by asking Claude to use the GitHub API to check rate limits.
2. Space out your requests or wait until the rate limit resets.

## Other Issues

### Claude doesn't use the GitHub MCP tools

**Problem**: Claude doesn't seem to be using the GitHub MCP tools even though they're configured.

**Solution**:
1. Make sure you're asking Claude to perform tasks that would require the GitHub MCP tools.
2. Be specific in your requests, mentioning GitHub explicitly.
3. If Claude suggests using other methods (like curl or direct API calls), remind it that it has access to the GitHub MCP server.

### Error: "spawn npx ENOENT"

**Problem**: When trying to run the GitHub MCP server, you get an error like "Error: spawn npx ENOENT".

**Solution**:
1. This error indicates that the `npx` command is not found in the PATH.
2. Instead of using npx, modify your configuration to use the full path to the installed package:
   ```json
   "command": "node",
   "args": [
     "C:\\Users\\YourUsername\\AppData\\Roaming\\npm\\node_modules\\@modelcontextprotocol\\server-github\\dist\\index.js"
   ]
   ```

## Getting Help

If you continue to experience issues that aren't covered in this guide:

1. Check the [GitHub MCP server documentation](https://github.com/modelcontextprotocol/servers/tree/main/src/github) for updates.
2. Look for similar issues in the GitHub repository's issue tracker.
3. Ask Claude for help troubleshooting specific error messages you're encountering.
