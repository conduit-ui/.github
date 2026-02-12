# Conduit

**Agent-native GitHub automation built on PHP.**

Typed Saloon connectors, Laravel Zero CLIs, and AI-powered workflows. Built for autonomous agents that need deterministic, testable access to GitHub.

## Architecture

```
┌─────────────────────────────────────────┐
│  Agents (triage-agent, agentctl, etc.)  │
└──────────────┬──────────────────────────┘
               │
       ┌───────┴────────┐
       │   CLI Layer     │  ← Laravel Zero
       │  issue-cli      │
       │  pr-cli         │
       │  commit-cli     │
       └───────┬─────────┘
               │
       ┌───────┴────────┐
       │  Domain Layer   │  ← Typed resources
       │  issue / pr     │
       │  commit / repo  │
       └───────┬─────────┘
               │
       ┌───────┴────────┐
       │  Connector      │  ← Saloon HTTP
       └───────┬─────────┘
               │
       ┌───────┴────────┐
       │  GitHub API     │
       └────────────────┘
```

## Packages

### API Foundation
| Package | Description |
|---------|-------------|
| [connector](https://github.com/conduit-ui/connector) | Saloon-based GitHub API client |
| [contracts](https://github.com/conduit-ui/contracts) | Shared value objects and interfaces |

### Domain Layer
| Package | Description |
|---------|-------------|
| [issue](https://github.com/conduit-ui/issue) | GitHub issue management |
| [pr](https://github.com/conduit-ui/pr) | Pull request management |
| [commit](https://github.com/conduit-ui/commit) | Commit history and management |
| [repo](https://github.com/conduit-ui/repo) | Repository governance |

### CLI Tools
| Package | Description |
|---------|-------------|
| [issue-cli](https://github.com/conduit-ui/issue-cli) | Issue management CLI |
| [pr-cli](https://github.com/conduit-ui/pr-cli) | PR management CLI |
| [commit-cli](https://github.com/conduit-ui/commit-cli) | Commit management CLI |

### Knowledge & Intelligence
| Package | Description |
|---------|-------------|
| [knowledge](https://github.com/conduit-ui/knowledge) | AI-powered knowledge base with semantic search and Qdrant |
| [know-plugin](https://github.com/conduit-ui/know-plugin) | Claude Code plugin for knowledge capture |
| [qdrant-tools](https://github.com/conduit-ui/qdrant-tools) | CLI tools for Qdrant vector database |

### Infrastructure
| Package | Description |
|---------|-------------|
| [monitor](https://github.com/conduit-ui/monitor) | System health monitoring |
| [cloudflare](https://github.com/conduit-ui/cloudflare) | Cloudflare tunnel and DNS management |
| [marketplace](https://github.com/conduit-ui/marketplace) | Claude Code plugins marketplace |

## Stack

- **PHP 8.2+** with full type coverage
- **Saloon** for HTTP client foundation
- **Laravel Zero** for CLI applications
- **Pest** for BDD-style testing
- **Prism** for AI integration (Ollama, OpenRouter)

## Philosophy

- **Agent-first**: Built for automation, not humans clicking buttons
- **Layered**: Connector → Domain → CLI. Use any layer directly
- **Typed**: Saloon requests/responses, not string parsing
- **Testable**: MockClient, Prism::fake(), Http::fake() — no real API calls in tests
