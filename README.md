# BrowserCat MCP Server

[![smithery badge](https://smithery.ai/badge/@browsercat/browsercat-mcp-server)](https://smithery.ai/server/@browsercat/browsercat-mcp-server)

A Model Context Protocol server that provides browser automation capabilities using BrowserCat's cloud browser service. This server enables LLMs to interact with web pages, take screenshots, and execute JavaScript in a real browser environment without needing to install browsers locally.

## Components

### Tools

- **browsercat_navigate**
    - Navigate to any URL in the browser
    - Input: `url` (string)
- **browsercat_screenshot**
    - Capture screenshots of the entire page or specific elements
    - Inputs:
        - `name` (string, required): Name for the screenshot
        - `selector` (string, optional): CSS selector for element to screenshot
        - `width` (number, optional, default: 800): Screenshot width
        - `height` (number, optional, default: 600): Screenshot height
- **browsercat_click**
    - Click elements on the page
    - Input: `selector` (string): CSS selector for element to click
- **browsercat_hover**
    - Hover elements on the page
    - Input: `selector` (string): CSS selector for element to hover
- **browsercat_fill**
    - Fill out input fields
    - Inputs:
        - `selector` (string): CSS selector for input field
        - `value` (string): Value to fill
- **browsercat_select**
    - Select an option from a dropdown menu
    - Inputs:
        - `selector` (string): CSS selector for select element
        - `value` (string): Value to select
- **browsercat_evaluate**
    - Execute JavaScript in the browser console
    - Input: `script` (string): JavaScript code to execute

### Resources

The server provides access to two types of resources:

1. **Console Logs** (`console://logs`)
    - Browser console output in text format
    - Includes all console messages from the browser
2. **Screenshots** (`screenshot://<name>`)
    - PNG images of captured screenshots
    - Accessible via the screenshot name specified during capture

## Key Features

- Cloud-based browser automation
- No local browser installation required
- Console log monitoring
- Screenshot capabilities
- JavaScript execution
- Basic web interaction (navigation, clicking, form filling)

## Configuration to use BrowserCat MCP Server

### Environment Variables

The BrowserCat MCP server requires the following environment variable:

- `BROWSERCAT_API_KEY`: Your BrowserCat API key (required). You can get one for free at https://browsercat.xyz/mcp.

### NPX Configuration

```json
{
  "mcpServers": {
    "browsercat": {
      "command": "npx",
      "args": ["-y", "@browsercatco/mcp-server"],
      "env": {
        "BROWSERCAT_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License. For more details, please see the LICENSE file in the project repository.
