# Conduit

**GitHub automation that actually works.**

Composable PHP packages built for AI agents. Each package is a single verb: `issue`, `pr`, `commit`, `repo`, `action`. Chain them together to build autonomous GitHub workflows that don't break.

## The Ecosystem

| Package | What It Does | Install |
|---------|--------------|---------|
| [connector](https://github.com/conduit-ui/connector) | HTTP foundation layer (Saloon) | `composer require conduit-ui/connector` |
| [issue](https://github.com/conduit-ui/issue) | Create, update, close issues | `composer require conduit-ui/issue` |
| [pr](https://github.com/conduit-ui/pr) | Manage pull requests | `composer require conduit-ui/pr` |
| [commit](https://github.com/conduit-ui/commit) | Work with commit history | `composer require conduit-ui/commit` |
| [repo](https://github.com/conduit-ui/repo) | Repository governance | `composer require conduit-ui/repo` |
| [action](https://github.com/conduit-ui/action) | Trigger GitHub Actions | `composer require conduit-ui/action` |
| [review](https://github.com/conduit-ui/review) | Code review automation | `composer require conduit-ui/review` |
| [know](https://github.com/conduit-ui/know) | Agent domain knowledge | `composer require conduit-ui/know` |

## Quick Start

```php
use ConduitUi\GitHubConnector\Connector;
use ConduitUi\Issue\IssueResource;

// Connect
$connector = new Connector(token: 'ghp_...');

// Create issue
$issue = new IssueResource($connector);
$issue->create('owner/repo', [
    'title' => 'Bug found by agent',
    'body' => 'Details...',
    'labels' => ['bug', 'agent-created']
]);
```

Each package is:
- **Minimal** - One responsibility
- **Composable** - Mix and match
- **Type-safe** - Full PHP 8.2+ typing
- **Tested** - Pest coverage

## Built for Agents

Human developers use GitHub's UI. AI agents need programmatic interfaces.

Conduit gives agents structured, deterministic access to GitHub. Same input, same output. No surprises.

Perfect for:
- Autonomous issue triaging
- Automated PR workflows
- Repository governance bots
- GitHub Actions orchestration
- Code review automation

## Architecture

```
┌─────────────┐
│  Your Agent │
└──────┬──────┘
       │
       ↓
┌─────────────────────────────────────┐
│  Conduit Packages (issue/pr/etc)    │
└──────────────┬──────────────────────┘
               │
               ↓
       ┌──────────────┐
       │  Connector   │  ← Saloon HTTP
       └──────┬───────┘
              │
              ↓
      ┌──────────────┐
      │  GitHub API  │
      └──────────────┘
```

## Philosophy

- **Singular**: One word, one purpose
- **Deterministic**: Predictable behavior
- **Agent-first**: Built for automation
- **No magic**: Explicit over implicit

## Support

Open issues on package repos. PRs welcome.

For enterprise support or custom packages: jordan@partridge.rocks

---

*Part of [THE SHIT](https://github.com/the-shit) - Developer tools that don't suck.*
