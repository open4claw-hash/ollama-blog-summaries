# Ollama Blog Summaries

Summaries of recent Ollama blog posts covering new features, models, and integrations.

## Blogs Covered

| Date | Title |
|------|-------|
| Feb 1, 2026 | OpenClaw |
| Jan 23, 2026 | ollama launch |
| Jan 20, 2026 | Image Generation (Experimental) |
| Jan 16, 2026 | Claude Code with Anthropic API Compatibility |
| Jan 15, 2026 | OpenAI Codex with Ollama |
| Oct 29, 2025 | OpenAI gpt-oss-safeguard |
| Oct 28, 2025 | MiniMax M2 |
| Oct 13, 2025 | NVIDIA DGX Spark |

## Browser Agent Implementation

This documentation covers how the browser automation was set up using OpenClaw's Chrome extension relay.

### Prerequisites

- OpenClaw installed and running
- Google Chrome browser
- WSL2 (for Windows users)

### Steps

#### 1. Install the Chrome Extension

The OpenClaw browser extension allows remote control of Chrome tabs.

**Location:** `~/.openclaw/browser/chrome-extension`

**For Windows users:**
The extension path in WSL translates to:
```
C:\Users\pratibhak\.clawdbot\browser\chrome-extension
```

Or copy to an accessible location:
```
C:\Users\pratibhak\Downloads\chrome-extension
```

#### 2. Load Extension in Chrome

1. Open Chrome and navigate to `chrome://extensions`
2. Enable **Developer mode** (toggle in top-right)
3. Click **Load unpacked**
4. Select the extension folder
5. Click the OpenClaw extension icon in the toolbar to pin it

#### 3. Connect a Tab

1. Open the desired website in Chrome
2. Click the OpenClaw extension icon
3. The badge should show "ON" when connected

#### 4. Use OpenClaw Browser Tools

Once connected, you can:

- **Navigate:** `browser.action = "navigate"`, `targetUrl = "https://..."`
- **Get snapshot:** `browser.action = "snapshot"` - returns page content as accessible tree
- **Click:** `browser.action = "act"`, `request = {"kind": "click", "ref": "e1"}`
- **Type:** `browser.action = "act"`, `request = {"kind": "type", "text": "hello"}`
- **Press keys:** `browser.action = "act"`, `request = {"kind": "press", "key": "End"}`

### Example Code

```javascript
// Connect to Chrome tab
await browser({
  action: "tabs",
  profile: "chrome",
  target: "host"
});

// Navigate to a page
await browser({
  action: "navigate",
  profile: "chrome",
  target: "host",
  targetId: "TAB_ID",
  targetUrl: "https://ollama.com/blog"
});

// Get page content
await browser({
  action: "snapshot",
  profile: "chrome",
  target: "host",
  targetId: "TAB_ID"
});

// Click an element
await browser({
  action: "act",
  profile: "chrome",
  target: "host",
  targetId: "TAB_ID",
  request: {
    kind: "click",
    ref: "e124" // element reference from snapshot
  }
});
```

### Troubleshooting

- **No tab connected:** Click the OpenClaw extension icon on a tab until badge shows ON
- **Extension not found:** Copy from `~/.openclaw/browser/chrome-extension` to a Windows-accessible path
- **Service not running:** Run `openclaw gateway restart`

### Resources

- [OpenClaw Docs](https://docs.openclaw.ai)
- [Chrome Extension Setup](https://docs.openclaw.ai/tools/chrome-extension)
