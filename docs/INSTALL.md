# Installation Guide

This guide walks you through installing SEO Toolkit skills into Claude Desktop.

## Prerequisites

- [Claude Desktop](https://claude.ai/download) installed
- Terminal access (Terminal on macOS, PowerShell on Windows)
- (Optional but recommended) MCP servers configured — see [MCP-SETUP.md](MCP-SETUP.md)

## Quick Install

### macOS

```bash
# Clone the repository
git clone https://github.com/ibangtam/seo-toolkit.git
cd seo-toolkit

# Copy all skills
cp -r skills/* ~/Library/Application\ Support/Claude/skills/

# Or copy individual skills
cp -r skills/outline-content ~/Library/Application\ Support/Claude/skills/
```

### Windows (PowerShell)

```powershell
# Clone the repository
git clone https://github.com/ibangtam/seo-toolkit.git
cd seo-toolkit

# Copy all skills
Copy-Item -Recurse skills\* $env:APPDATA\Claude\skills\

# Or copy individual skills
Copy-Item -Recurse skills\outline-content $env:APPDATA\Claude\skills\
```

### Linux

```bash
# Clone the repository
git clone https://github.com/ibangtam/seo-toolkit.git
cd seo-toolkit

# Copy all skills
cp -r skills/* ~/.config/Claude/skills/
```

## Verify Installation

1. Quit and reopen Claude Desktop
2. Start a new conversation
3. Trigger a skill — for example, type: `"create an SEO outline for the keyword digital marketing"`
4. Claude should recognize the trigger and load the skill

## Verify Skills Are Loaded

In a Claude Desktop conversation, you can ask:

```
What skills do you have available?
```

Claude will list installed skills including those from this toolkit.

## Skill Directory Locations

| OS | Path |
|---|---|
| macOS | `~/Library/Application Support/Claude/skills/` |
| Windows | `%APPDATA%\Claude\skills\` |
| Linux | `~/.config/Claude/skills/` |

## Updating Skills

To pull the latest version of skills:

```bash
cd seo-toolkit
git pull

# macOS
cp -r skills/* ~/Library/Application\ Support/Claude/skills/

# Windows
Copy-Item -Recurse -Force skills\* $env:APPDATA\Claude\skills\
```

Restart Claude Desktop after updating.

## Uninstalling a Skill

Simply delete the skill folder from the skills directory:

```bash
# macOS example
rm -rf ~/Library/Application\ Support/Claude/skills/outline-content
```

Restart Claude Desktop.

## Troubleshooting

### Skill doesn't trigger

- Verify the folder is in the correct skills directory
- Make sure `SKILL.md` is at the root of the skill folder (not nested)
- Restart Claude Desktop fully (Quit, then reopen)
- Check that your trigger phrase matches what's in the skill's description

### MCP tools not working

- See [MCP-SETUP.md](MCP-SETUP.md) for MCP server configuration
- The skills will fall back to `web_search` / `web_fetch` if MCPs aren't available

### Permission denied errors

On macOS, make sure Claude Desktop has permission to read the skills directory. Check System Settings → Privacy & Security → Files and Folders.

## Still Stuck?

Open a [Discussion](../../discussions) with your OS and error details.
