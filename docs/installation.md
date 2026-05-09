# Installation Guide

## Platform Support

**Windows 10/11 — tested and confirmed.**

Mac is untested. The author does not own a Mac. The server may work in principle — it is a .NET 10 application and the Idea Museum protocol is platform-agnostic — but no installation has been verified on Mac hardware. If you successfully get it running on Mac, please share your steps in [Discussions](https://github.com/swiftiansolutions/divergentdecisions-mcp/discussions) so others can benefit.

---

## What You Are Installing

The DivergentDecisions MCP server is a background process that Claude Desktop communicates with over the Model Context Protocol. It gives Claude structured read and write access to your idea museum — a folder on your machine where your catalogue cards, topics, and tangent crates live.

You will create two folders:

- **Your museum folder** — where your intellectual work lives (a git repository)
- **Your server folder** — where the executable lives, kept deliberately separate from git

Keeping them separate means your git history stays clean. Only your catalogue cards and museum structure are committed — not the server binary.

---

## Step 1 — Choose Your Museum Name

Your museum name is the name of your idea collection. It can reflect what you are exploring — `ProductStrategy`, `ResearchMuseum`, `CareerNotes` — or you can use the generic defaults. You will use this name for both folders.

**Default names used throughout this guide:**

| Folder | Default name |
|---|---|
| Museum (your work, git repo) | `IdeaMuseum` |
| Server (the executable) | `IdeaMuseumMCP` |

---

## Step 2 — Create Your Folders

Choose a parent location and create two sibling folders. Example using the defaults:

```
C:\Users\YourName\Documents\Museums\IdeaMuseum\
C:\Users\YourName\Documents\Museums\IdeaMuseumMCP\
```

The folders can be anywhere you like — OneDrive, a local drive, a network location. The museum folder works with whatever sync or version control tool you already use.

---

## Step 3 — Download the Binary

1. Go to the [Releases](https://github.com/swiftiansolutions/divergentdecisions-mcp/releases) page
2. Download the latest release zip
3. Extract `DivergentDecisionsMCP.API.exe` into your server folder (`IdeaMuseumMCP`)

Your server folder should now contain:

```
IdeaMuseumMCP\
  DivergentDecisionsMCP.API.exe
  LICENSE.md
  BETA.md
```

---

## Step 4 — Configure Claude Desktop

Open your Claude Desktop configuration file in any text editor (Notepad works fine):

```
%APPDATA%\Claude\claude_desktop_config.json
```

If the file does not exist, create it. Add the following, replacing the paths with your actual folder locations:

```json
{
  "mcpServers": {
    "DivergentDecisions": {
      "command": "C:\\Users\\YourName\\Documents\\Museums\\IdeaMuseumMCP\\DivergentDecisionsMCP.API.exe",
      "args": [],
      "env": {
        "Museum__RepositoryPath": "C:\\Users\\YourName\\Documents\\Museums\\IdeaMuseum"
      }
    }
  }
}
```

**Path format note:** JSON requires backslashes to be doubled (`\\`) on Windows.

**`Museum__RepositoryPath` note:** The double underscore is how .NET reads nested configuration settings. It is not a typo — type it exactly as shown.

If your `claude_desktop_config.json` already has an `mcpServers` section with other servers, add the `DivergentDecisions` entry inside the existing `mcpServers` object rather than creating a second one.

---

## Step 5 — Restart Claude Desktop

Fully quit Claude Desktop (check the system tray — it runs in the background) and relaunch it. The DivergentDecisions tools will appear in your Claude session.

To confirm the server is connected, start a new conversation and ask Claude: *"What MCP tools do you have available?"* You should see the DivergentDecisions tools listed.

---

## Step 6 — Initialise Git in Your Museum Folder

```bash
cd C:\Users\YourName\Documents\Museums\IdeaMuseum
git init
git commit --allow-empty -m "Initial museum"
```

This creates the git repository that serves as your verification mechanism — your "git diff is your confidence signal" when the server writes catalogue cards on Claude's behalf.

See [banking-posture.md](banking-posture.md) for why git is the recommended approach and what your options are if you prefer not to use git.

---

## Step 7 — First Session

See [first-session.md](first-session.md) for a walkthrough of your first bootstrap and SIP.

---

## Troubleshooting

**Claude does not show DivergentDecisions tools**
- Confirm Claude Desktop was fully quit and relaunched (not just a new conversation)
- Check the JSON in `claude_desktop_config.json` is valid — a missing comma or mismatched brace will prevent it loading
- Confirm the path to the exe is correct and the exe exists at that location
- Check Claude Desktop logs for MCP errors (Help → Show Logs on Windows)

**"Museum__RepositoryPath not set" or similar error**
- The `env` section in the config must be present with the correct key
- Double-check the double underscore: `Museum__RepositoryPath`

**Permission error on the exe**
- Right-click the exe → Properties → Unblock (Windows may block executables downloaded from the internet)
