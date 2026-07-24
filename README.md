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

## Antigravity MCP Server Setup Steps

THese are the steps that I will show in my first video of this series on how to get the MCP Server connected. First, let's go over some prerequisites.

### What you will need:

- Antigravity 2.0: Make sure to upgrade to 2.0 if you're still running the old version
- Python 3: Required for running the MCP server locally

### Steps: Follow these steps along in my video

1. Login to Google Cloud Console and create a project
2. Setup OAuth Consent Screent
3. Create the credentials for your account that you will use in Antigravity
4. Enable the Google APIs
5. Create a project folder and copy credentials to it
6. Paste this prompt for setting up the MCP Server:

"I have added my Google OAuth client credentials file to this workspace root directory.

Please set up an MCP (Model Context Protocol) connection for Google Workspace using the taylorwilsdon/google_workspace_mcp package.

Walk me through any initial dependencies or local setup, locate my credentials file, and trigger the local OAuth authentication flow so I can authorize the connection."

7. Review the access requets and accept the changes.
