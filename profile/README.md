# Conduit

> **GitHub API connectors that work exactly as documented. No surprises. No exceptions.**

[![Sentinel Certified](https://img.shields.io/badge/Sentinel-Certified-brightgreen?style=flat-square)](https://github.com/synapse-sentinel/gate)

## The Standard

Every certified Conduit package:
- **Works as documented** - No hidden behaviors or edge cases
- **100% test coverage** - Every line proven correct
- **Fails fast** - Typed exceptions, not silent errors
- **Auto-verified** - PRs merge only when Sentinel certifies

Packages without the Sentinel badge are in active development.

## Ecosystem

| Package | Purpose | Status |
|---------|---------|--------|
| [connector](https://github.com/conduit-ui/connector) | HTTP transport, typed exceptions | [![Sentinel](https://img.shields.io/github/actions/workflow/status/conduit-ui/connector/gate.yml?label=Sentinel&style=flat-square)](https://github.com/conduit-ui/connector/actions/workflows/gate.yml) |
| [issue](https://github.com/conduit-ui/issue) | Issue CRUD, labels, milestones | [![Sentinel](https://img.shields.io/github/actions/workflow/status/conduit-ui/issue/gate.yml?label=Sentinel&style=flat-square)](https://github.com/conduit-ui/issue/actions/workflows/gate.yml) |
| [pr](https://github.com/conduit-ui/pr) | PR review, merge, query | [![Sentinel](https://img.shields.io/github/actions/workflow/status/conduit-ui/pr/gate.yml?label=Sentinel&style=flat-square)](https://github.com/conduit-ui/pr/actions/workflows/gate.yml) |
| [repo](https://github.com/conduit-ui/repo) | Repository management | ![Building](https://img.shields.io/badge/status-building-yellow?style=flat-square) |
| [commit](https://github.com/conduit-ui/commit) | Commit operations | ![Planned](https://img.shields.io/badge/status-planned-lightgrey?style=flat-square) |
| [action](https://github.com/conduit-ui/action) | GitHub Actions integration | ![Planned](https://img.shields.io/badge/status-planned-lightgrey?style=flat-square) |

## Quality Gates

Every package passes **Synapse Sentinel** certification:

```
✓ Tests & Coverage (100% threshold)
✓ Security Audit (no vulnerabilities)
✓ Pest Syntax (describe/it blocks)
✓ Static Analysis (PHPStan level 8)
```

PRs auto-merge when certification passes. No exceptions.

## Quick Start

```bash
composer require conduit-ui/connector conduit-ui/issue
```

```php
use ConduitUI\Connector\Connector;
use ConduitUI\Issue\IssuesService;

$connector = new Connector(env('GITHUB_TOKEN'));
$issues = new IssuesService($connector);

// Every method works exactly as documented
$issue = $issues->get('owner', 'repo', 123);
$issues->addLabels('owner', 'repo', 123, ['bug', 'priority-high']);
$issues->close('owner', 'repo', 123);
```

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Your Application                   │
├─────────────────────────────────────────────────────┤
│  issue   │   pr    │   repo   │  action  │  commit  │
├─────────────────────────────────────────────────────┤
│                    connector                         │
├─────────────────────────────────────────────────────┤
│                  Saloon HTTP Client                  │
└─────────────────────────────────────────────────────┘
```

## Requirements

- PHP 8.2+
- GitHub personal access token

## Contributing

1. Fork the relevant package
2. Write tests first (100% coverage required)
3. Implement your changes
4. PR auto-merges when Sentinel certifies

## Support

Open issues on package repos. PRs welcome.

Enterprise support: jordan@partridge.rocks

## License

MIT
