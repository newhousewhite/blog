# 'Getting Started with Codex' Summary
source: https://www.youtube.com/watch?v=px7XlbYgk7I

1. Agent.md
common sections:
- project overview and structure
- build and test commands
- helpful CLI tools and MCP servers
- workflow for implemeting a feature
- pointers to other task-specific guidance for the agent

2. Config.toml
- usd to configure codex
- located at ~/.codex/config.toml

default model ,reasoning depth, approval mode, MCP servers, ...

3. approval_mode and sandbox_mode

4. prompting examples
- provide clear code pointers with @mention
- include verification steps
- customize how codes does its work (reference specific commits, log failures, ask it to follow a PR message template in Agent.md)
- start with small tasks -> larger ones
- paste the full tack trace when debugging
- try open-ended prompts

5. codex starter task examples
- explaining a codebase
- expanding test coverage
- bug fixing
- refactoring across many files

6. CLI & IDE tips
- @filename
- //TODO
- Diagram (Dataflow): command is "provide me a clean Mermaid sequence diagram for this codebase"
- Websearch is disabled by default.
  - enabling it:
`codex --enable web_search_requeset "Add a small 'Latest News' footer box that links to a current article about Next.js 15. Include a date and source."`
  - change to default true through config.toml
- Add a custom `/command`
  - in codex CLI: create `~/.codex/prompts/add-texts.md` for `add-tests` example with your standard ask:, like 
    "Generate unit tests for the touched files.  Use the project's existing test runner and conventions. Keep diffs minimal and runnable locally."
    Then, `codex resume`, then run it by typing `/add-tests`

7. MCP configuration
- codex support MCP over both STDUIO and streamable HTTP.
  - generate front-end designs based mocks using the Figma MCP server
  - Update a ticket status using the Jira MCP
  - Implement 3rd party API callouts using the Context7 MCP server
  - Diagnose production issues using the Datadog MCP server
  - Understand feature flag functionality using the Statsig MCP server
- running command:
  - `codex mcp add <mcp name> /usr/bin/env npx -y mcp-remote@0.1.13 https://codex-102.vercel.app/mcp --transport http`
- context7: MCP for the latest documentations

8. code review
- `/review`

9. Building workflows with Codex & Agents SDK:
- use codex as an MCP server that can be calld as a tool by an agent
- control context and handoffs b/w agents
- create agents designed for specific tasks: frontend, backend, test implementaiton
- more examples in the OpenAI Cookbook: https://cookbook.openai.com/topic/codex

10. Auto-Fix Failing CI
- trigger codex based on CI failures
- codex checks out its own branch and works to fix the failures
- result: a PR that passes tests

11. Auto-label issues
- use codex to categorize issues when creating them.  based on a series of predefined labels
- update issues with the relevant label

12. Resources (QR code in the youtube)
- codex doc: developers.openai.com/codex
- codex cookbooks: cookbook.openai.com/topic/codex
- codex changelog: developers.openai.com/codex/changelog/
- Admins:
  - enterprise Admin Guide
  - Codex Security Guide
  - Rate Card

