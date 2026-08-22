# Conduit

**Agent-native GitHub automation built on PHP.**

Typed Saloon connectors, Laravel packages, Laravel Zero CLIs, and a knowledge store. Built for autonomous agents that need deterministic, testable access to GitHub and the rest of the house.

Install from Packagist:

```bash
composer require conduit-ui/connector
```

## Architecture

```
┌─────────────────────────────────────────┐
│  Agents                                 │
└──────────────┬──────────────────────────┘
               │
       ┌───────┴────────┐
       │   CLI Layer     │  Laravel Zero 13 (PHP ^8.3)
       │  issue-cli      │
       │  pr-cli         │
       │  monitor / cf   │
       └───────┬─────────┘
               │
       ┌───────┴────────┐
       │  Domain Layer   │  Laravel 13 libraries
       │  issue / pr     │
       │  commit / repo  │
       │  email/calendar │
       └───────┴─────────┘
               │
       ┌───────┴────────┐
       │  Connector      │  Saloon 4 → GitHub API
       └────────────────┘

  knowledge  →  Qdrant (store / search / remember)
  foundry    →  scaffold Laravel microservices
  mattermost →  bots, slash commands, streaming replies
```

## Packages

Composer names are `conduit-ui/<repo>` unless noted.

### API foundation

| Package | Description |
|---------|-------------|
| [connector](https://github.com/conduit-ui/connector) | Saloon GitHub API client (`^1.1`) |
| [contracts](https://github.com/conduit-ui/contracts) | Shared value objects and interfaces (`^0.2`) |
| [core](https://github.com/conduit-ui/core) | Component interfaces and storage (`^0.1`) |

### GitHub domain

| Package | Description |
|---------|-------------|
| [issue](https://github.com/conduit-ui/issue) | Issue management (`^1.0@RC`) |
| [pr](https://github.com/conduit-ui/pr) | Pull request management (`^1.0`) |
| [commit](https://github.com/conduit-ui/commit) | Commit history (`^0.1`) |
| [repo](https://github.com/conduit-ui/repo) | Repository governance (`^0.4`) |

### Other domain

| Package | Description |
|---------|-------------|
| [email](https://github.com/conduit-ui/email) | Provider-agnostic email client — Gmail first |
| [calendar](https://github.com/conduit-ui/calendar) | Provider-agnostic calendar — Google Calendar first |
| [mattermost](https://github.com/conduit-ui/mattermost) | Mattermost bots, WebSocket, slash commands |

### CLIs

| Package | Description |
|---------|-------------|
| [issue-cli](https://github.com/conduit-ui/issue-cli) | Issue CLI (`issue`) |
| [pr-cli](https://github.com/conduit-ui/pr-cli) | PR CLI (`pr`) |
| [monitor](https://github.com/conduit-ui/monitor) | Heartbeat / health checks (`monitor`) |
| [cloudflare](https://github.com/conduit-ui/cloudflare) | Tunnels, DNS, zones (`cf`) |
| [qdrant-tools](https://github.com/conduit-ui/qdrant-tools) | Qdrant export / import / sync (`qdrant`) |

### Knowledge

| Package | Description |
|---------|-------------|
| [knowledge](https://github.com/conduit-ui/knowledge) | Knowledge base with semantic search (`^3.0`) |
| [know-plugin](https://github.com/conduit-ui/know-plugin) | Claude Code plugin for capture / retrieve |

### Scaffolding & plugins

| Package | Description |
|---------|-------------|
| [foundry](https://github.com/conduit-ui/foundry) | Manifest-driven Laravel microservice scaffolder |
| [marketplace](https://github.com/conduit-ui/marketplace) | Claude Code plugins marketplace |

`commit-cli` and `whisper` are empty remotes — not shipped. Archived duplicates (`conduit`, `know`, `issues`, `prs`, …) stay archived.

## Stack

- **PHP ^8.2** libraries, **PHP ^8.3** Laravel Zero CLIs
- **Laravel 13** / **Laravel Zero 13**
- **Saloon 4** for HTTP
- **Pest** for tests
- **Qdrant** for knowledge search

## Philosophy

- **Agent-first**: Built for automation, not humans clicking buttons
- **Layered**: Connector → Domain → CLI. Use any layer directly
- **Typed**: Saloon requests/responses, not string parsing
- **Testable**: MockClient, Prism::fake(), Http::fake() — no real API calls in tests
