# A11 for coding agents

The A11 plugin for **Claude Code** and **Codex**. It helps your coding agent
build on [A11](https://a11.tech), the backend for apps built with the
`@a11code/sdk` package: end-user sign-in, files, structured data, key-value
storage, AI, email, scheduled jobs, location and hosting.

It adds one skill, which tells the agent to read the A11 Cookbook before it
writes A11 code. It runs nothing itself: [plugins/a11/README.md](plugins/a11/README.md).

## Before you start

Create a project and an API key at https://app.a11.tech, install the A11 CLI
(instructions: https://a11.tech/#agents), then run `a11 init` in your project
folder. It saves the project's key, and in Claude Code registers the A11 MCP
server.

## Install

Claude Code:

```bash
claude plugin marketplace add a11-tech/a11-agent
claude plugin install a11tech@a11-tech
```

Codex:

```bash
codex plugin marketplace add a11-tech/a11-agent
```

then open `/plugins` in Codex and install **A11**.

## Support

support@a11.tech

## Maintainers

This repository is published from A11's own source, so pull requests here
are not merged. Report problems to support@a11.tech.
