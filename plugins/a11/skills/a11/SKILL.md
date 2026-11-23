---
name: a11
description: Build on A11, the backend-as-a-service for apps that call the @a11code/sdk package. Use when the project has an .a11/ folder, an A11_API_KEY, imports @a11code/sdk, calls api.a11.tech, or the developer asks to add auth, file storage, data, AI, email, scheduled jobs, location or hosting with A11. Tells you how to read the A11 Cookbook, which holds the patterns to follow, before writing A11 code.
---

# A11

A11 is the backend for apps built with the `@a11code/sdk` package: end-user
sign-in, files, structured data, key-value storage, AI, email, scheduled jobs,
location and hosting. How to build each of these correctly lives in the
**A11 Cookbook**, which A11 serves one topic at a time with the developer's
A11 API key. This skill only tells you how to reach it.

## 1. Read the Cookbook before you write A11 code

Use the first route that works:

1. **The `a11` MCP server.** Call its `read_cookbook` tool with no arguments
   to list the topics, then with `topic: "cookbook"` for the entry point.
   Follow what it says, and read the topic for a task before writing its code.
2. **The `a11` CLI.** `a11 cookbook` lists the topics, `a11 cookbook cookbook`
   prints the entry point, and `a11 cookbook <topic> --section <heading>`
   prints one section of a large topic.

Rules:

- Read the matching topic first. Do not write `a11.*` calls from memory: the
  Cookbook names behaviours that fail silently.
- Prefer an MCP tool over prose when the Cookbook names one for the task.
- Never copy Cookbook text into the project (files, comments, docs, commits).
  Read it again when you need it.

## 2. When neither route works

| What you see | What to do |
|---|---|
| `a11: command not found` and no `read_cookbook` tool | Ask the developer to install the CLI with the command below, then run `a11 init` in the project folder |
| A key error, or a 401 from either route | The developer gets a key at https://app.a11.tech and runs `a11 init` in the project folder. It saves the key to `.a11/.env` and the system keychain |
| The CLI works but `read_cookbook` is missing | Use the CLI route. The MCP server starts with the agent, so it appears after a restart |

The CLI install command:

```bash
curl -sSfL https://cli.a11.tech/install.sh | sh
```

## 3. The API key

- Each A11 project has its own key, and `a11 init` stores it per project.
- Never ask the developer to paste the key into chat, and never write it into
  source code, a commit, or browser code. The Cookbook's `setup` topic shows
  where it goes for each framework.
