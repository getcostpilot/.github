<div align="center">
  <img src="https://raw.githubusercontent.com/getcostpilot/.github/main/profile/costpilot-logo.svg" alt="Costpilot" width="72" height="72">
  <h1>Costpilot</h1>
  <p><strong>AI cost per feature, not per invoice.</strong></p>
  <p>
    <a href="https://demo.getcostpilot.io"><strong>Live demo</strong></a> ·
    <a href="https://getcostpilot.io"><strong>Website</strong></a> ·
    <a href="https://docs.getcostpilot.io"><strong>Documentation</strong></a>
  </p>
</div>

Your provider's invoice tells you what AI coding assistants cost in total. It
does not tell you which feature the money went into. Costpilot pins every
token to the issue that caused it and rolls it up per epic, project,
developer and model, so you know what a feature really costs and get warned
before a budget runs over.

**[Try the live demo](https://demo.getcostpilot.io)**: the real dashboard on
sample data, no signup.

## What you get

- **Cost per feature**: spend per issue, rolled up to epics and projects,
  with trends against the previous period.
- **Automatic attribution**: the issue key on the developer's git branch
  decides where the cost lands. No manual tagging.
- **Names, types and status from your tracker**: with Jira connected, issues
  carry their title, type, status and hierarchy. Filter spend by bugs, open
  work or a whole epic.
- **Budgets with alerts**: for the whole organisation, a project, a feature,
  a developer or a model. Notifications in the app, by e-mail, to Slack or a
  webhook.
- **API prices and what you actually pay**: subscriptions and API keys side
  by side, per person and period.
- **Self-hosted**: one service with SQLite on a volume. Your telemetry stays
  with you.

## How it works

```
AI coding agent ──► usage via OpenTelemetry ───┐
                                               │
git branch ──► issue key via the agent hook ───┼──► Costpilot ──► cost per issue, epic,
                                               │                  project, developer, model
Issue tracker ──► title, type, status, epic ───┘
```

1. Your **coding agent** exports tokens, model and cost via OpenTelemetry.
2. The **Costpilot Agent**, installed once per developer machine, reads the
   issue key from the git branch and reports it with every prompt.
3. Your **issue tracker** adds what the key stands for: title, type, status
   and the epic it belongs to.
4. The **Costpilot server** joins all three and prices the calls; the
   **dashboard** shows the result per project, issue, developer and model.

Cost is attributed the moment it happens, from the branch alone. The tracker
adds names, status and hierarchy on top.

## Works with

| Coding agents | Issue trackers |
|---|---|
| Claude Code | **Jira Cloud**: synced with titles, types, status and hierarchy |
| Gemini CLI | **Azure DevOps, GitHub, GitLab**: cost per issue through the key on the branch; sync on the roadmap |
| Codex CLI | |

## Get started

1. **Run the server**: locally, or on Railway, Fly.io or Docker.
2. **Install the agent** on each developer machine: one command turns on
   telemetry export and installs the hook.
3. **Work on a branch** that carries an issue key, such as
   `feature/PROJ-123-login`. Cost for every prompt shows up under `PROJ-123`.

Step by step: [Getting started](https://docs.getcostpilot.io/getting-started/).

## Repositories

| Repository | What it is |
|---|---|
| [core](https://github.com/getcostpilot/core) | Server and dashboard: ingestion, attribution, budgets, tracker connection, documentation sources |
| [agent](https://github.com/getcostpilot/agent) | Developer-side setup: telemetry export and the branch-to-issue hook for each coding agent |

## Get in touch

- A demo with your own numbers, or a question: [getcostpilot.io](https://getcostpilot.io)
- Bugs and ideas: [issues in the core repository](https://github.com/getcostpilot/core/issues)
