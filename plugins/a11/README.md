# A11 plugin for coding agents

A11 is a backend for apps built with the `@a11code/sdk` package: end-user
sign-in, files, structured data, key-value storage, AI, email, scheduled jobs,
location and hosting. This plugin helps your coding agent build on it
correctly. It works in Claude Code and Codex.

## What it adds

One skill, `a11`. It tells the agent to read the A11 Cookbook before it writes
A11 code, and how to reach it: the `read_cookbook` tool of the A11 MCP server,
or the `a11` CLI.

## Before you start

1. Create a project and an API key at https://app.a11.tech.
2. Install the A11 CLI (instructions: https://a11.tech/#agents).
3. Run `a11 init` in your project folder. It saves the project's key to
   `.a11/.env` (and your system keychain). In Claude Code it also registers the
   A11 MCP server; in Codex the agent reads the Cookbook with the `a11` CLI.
   Each project has its own key, so the plugin asks for none.

## What it runs, reads and sends

**The plugin itself:** one Markdown skill. It runs no commands, starts no
servers, reads no files, stores nothing and collects no personal data.

**What the skill asks the agent to do:** read the A11 Cookbook with tools you
set up separately: the `a11` CLI (`a11 cookbook <topic>`), or the A11 MCP
server's `read_cookbook` tool, which `a11 init` registers for Claude Code.

| | |
|---|---|
| Sent to | `https://api.a11.tech` (A11's own API), and nowhere else |
| What each request carries | The Cookbook topic name (and section, if any), your A11 project API key (from `A11_API_KEY`, your project's `.a11/.env`, or your system keychain), and from the CLI its name and version |
| Never sent | Your code, files, conversation, or any personal data |
| What comes back | The topic's text. The skill tells the agent not to copy it into your project |

## Install

Claude Code:

```bash
claude plugin marketplace add a11-tech/a11-agent
claude plugin install a11@a11-tech
```

Codex:

```bash
codex plugin marketplace add a11-tech/a11-agent
```

then open `/plugins` in Codex and install **A11**.

## Support

support@a11.tech, or https://a11.tech.

## License

See [LICENSE](LICENSE).
