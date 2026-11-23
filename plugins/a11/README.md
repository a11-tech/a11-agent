# A11 plugin for coding agents

A11 is a backend for apps built with the `@a11code/sdk` package: end-user
sign-in, files, structured data, key-value storage, AI, email, scheduled jobs,
location and hosting. This plugin helps your coding agent build on it
correctly. It works in Claude Code and Codex.

## What it adds

| Part | What it does |
|---|---|
| `a11` skill | Tells the agent to read the A11 Cookbook before it writes A11 code, and how to reach it (the MCP tool, or the `a11` CLI) |
| `a11` MCP server | Runs `npx -y @a11code/mcp@0.26.1` on your machine: typed tools for data, files, auth, AI, scaffolds and `read_cookbook` |

## Before you start

1. Create a project and an API key at https://app.a11.tech.
2. Install the A11 CLI and set up your project folder:

   ```bash
   curl -sSfL https://cli.a11.tech/install.sh | sh
   a11 init
   ```

   `a11 init` saves the project's key to `.a11/.env` (and your system keychain).
   Each project has its own key, so the plugin asks for none.

## What it runs, reads and sends

Everything the plugin does, so you can check it:

- **Runs:** `npx -y @a11code/mcp@0.26.1`, downloaded from the npm registry the
  first time. It runs on your machine, alongside your agent, and only while the
  agent is open.
- **Reads:** your A11 API key, from the `A11_API_KEY` environment variable if it
  is set, otherwise from `.a11/.env` in the project folder.
- **Sends:** requests to the A11 API at `https://api.a11.tech`, authenticated
  with that key, and only when the agent calls one of its tools. Cookbook topics
  are read the same way and are never written to disk.
- **Writes:** files in your project, only when the agent calls a scaffold tool
  (for example `define_collection` writes `.a11/collections/<name>.json`).
- **Does not:** collect telemetry, run hooks, or change your agent's settings.

The skill itself is a Markdown file. It runs nothing.

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

`a11 init` also registers the A11 MCP server in the project's own agent
config. With the plugin installed you only need one: run `a11 mcp uninstall`
in the project folder, or use `a11 init --no-mcp` in new folders.

## Support

support@a11.tech, or https://a11.tech.

## License

See [LICENSE](LICENSE).
