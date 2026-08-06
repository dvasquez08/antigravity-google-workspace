# Welcome to my Antigravity Google Workspace Repository

This is a growing collection of Google Workspaace workflows for Antigravity. This is where all of the demo files from my YouTUbe videos will be stored. This repo documents the journey of building an AI-Powered assistant, connected to your Google tools.

Whether you're just experimenting, or putting these workflows to your own use, I hope you find these helpful and make your life easier!

This will be part of a YouTube series which you can follow along with as this grows.

## What You Will Find Here

I will outline the steps here on how I got Antigravity setup, how the MCP server was setup. When you follow along with the videos, instead of manually typing some of the text from the videos, you can just copy and paste from here to make it easier.

This is just starting up, so more information will be added here as it grows, and as I make more videos.

If you have any questions, let me know on any of my socials.

[X](https://x.com/Dave53v) | [Instagram](https://www.instagram.com/david.vasq1/) | [YouTube](https://www.youtube.com/@davtekio)

For business inquiries: dvasquez@davtek.io

## Table of Contents

- [Antigravity MCP Server Setup Steps](#antigravity-mcp-server-setup-steps)
- [Inbox Cleanup and Notion MCP Server Connection](#inbox-cleanup-and-notion-mcp-server-connection)

## Antigravity MCP Server Setup Steps

THese are the steps that I will show in my first video of this series on how to get the MCP Server connected. First, let's go over some prerequisites.

### What you will need:

- Antigravity 2.0: Make sure to upgrade to 2.0 if you're still running the old version
- Python 3: Required for running the MCP server locally

Linux (Ubuntu/Mint):

```bash
sudo apt update && sudo apt install python3 -y
```

Windows/Mac: [Python Download](https://www.python.org/downloads/)

### Steps: Follow these steps along in my Episode 1 video.

1. Login to Google Cloud Console and create a project
2. Setup OAuth Consent Screen
3. Create the credentials for your account that you will use in Antigravity
4. Enable the Google APIs
5. Create a project folder and copy credentials to it
6. Paste this prompt for setting up the MCP Server:

"I have added my Google OAuth client credentials file to this workspace root directory.

Please set up an MCP (Model Context Protocol) connection for Google Workspace using the taylorwilsdon/google_workspace_mcp package.

Walk me through any initial dependencies or local setup, locate my credentials file, and trigger the local OAuth authentication flow so I can authorize the connection."

7. Review the access request and accept the changes.

## Inbox Cleanup and Notion MCP Server Connection

Follow along here for episode 2, where I add two additional workflows and connect my agent with Notion, so it works alongside Google Workspace MCP Server.

### Steps: You can follow along here and use the prompts here that I used in my video:

1. Create two new files inside the workflows directory, call them "inbox-cleanup.md" and "meeting-prep.md"
2. Grab the contents from the templates here in this repo, also inside the workflows folder. Paste them into your new files.
3. Test the inbox cleanup workflow by entering in the following prompt:

"Please read inbox-cleanup.md and cleanup my inbox as per the instructions in that markdown file, remember to only touch unread messages."

4. Go to the [Notions Connection page]("https://app.notion.com/developers/connections") and sign in with your Notion account.
5. Choose "Access Token," give your connection a name, and click "Create Token."
6. On the next page, copy your token. Create a new file in the root of your project and call it ".env" and add the following line:

NOTION_TOKEN="YOUR NOTION TOKEN HERE"

7. Back to antigravity, setup your Notion MCP server by entering this single prompt:

"I have added my Notion Integration Secret as NOTION_TOKEN inside the .env file in this workspace root directory.

Please set up the Notion MCP server for this project. Use the official @notionhq/notion-mcp-server package (via npx -y @notionhq/notion-mcp-server).

Read NOTION_TOKEN from the local .env file and update my MCP server configuration file so that both Google Workspace and Notion run side-by-side as available tool sources."

8. Test your meeting prep workflow by entering the following prompt below:

"Read the meeting-prep.md markdown file, and help me prepare for today's meetings, as per the instructions in that file.
