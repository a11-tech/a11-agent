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

Nothing. The plugin is one Markdown skill. It runs no commands, starts no
servers, reads no files and sends no data. The agent follows it with the tools
you have set up: the `a11` CLI and the A11 MCP server, which send requests to
`https://api.a11.tech` with your project's key.

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
