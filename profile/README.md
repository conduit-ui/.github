# Conduit

> **Production-grade GitHub API connectors with 100% test coverage**

[![Sentinel Certified](https://img.shields.io/badge/Sentinel-Certified-brightgreen?style=flat-square)](https://github.com/synapse-sentinel/gate)

## What is Conduit?

Conduit is an ecosystem of PHP packages for GitHub API integration. Each package is:

- **100% test coverage** - Every line tested
- **Sentinel Certified** - Automated quality gates enforce standards
- **Type-safe** - Full PHP 8.2+ type coverage
- **Production-ready** - Used in real applications

## Ecosystem

| Package | Purpose | Status |
|---------|---------|--------|
| [connector](https://github.com/conduit-ui/connector) | HTTP transport layer with typed exceptions | [![Sentinel](https://img.shields.io/github/actions/workflow/status/conduit-ui/connector/gate.yml?label=Sentinel&style=flat-square)](https://github.com/conduit-ui/connector/actions/workflows/gate.yml) |
| [issue](https://github.com/conduit-ui/issue) | Issue management (CRUD, labels, assignees, milestones) | [![Sentinel](https://img.shields.io/github/actions/workflow/status/conduit-ui/issue/gate.yml?label=Sentinel&style=flat-square)](https://github.com/conduit-ui/issue/actions/workflows/gate.yml) |
| [pr](https://github.com/conduit-ui/pr) | Pull request operations (review, merge, query) | [![Sentinel](https://img.shields.io/github/actions/workflow/status/conduit-ui/pr/gate.yml?label=Sentinel&style=flat-square)](https://github.com/conduit-ui/pr/actions/workflows/gate.yml) |
| [repo](https://github.com/conduit-ui/repo) | Repository management | Coming soon |
| [action](https://github.com/conduit-ui/action) | GitHub Actions integration | Coming soon |
| [commit](https://github.com/conduit-ui/commit) | Commit operations | Coming soon |

## Quality Standards

Every package in the Conduit ecosystem passes **Synapse Sentinel** certification:

```
✓ Tests & Coverage (100% threshold)
✓ Security Audit (no vulnerabilities)
✓ Pest Syntax (describe/it blocks)
✓ Static Analysis (PHPStan level 8)
```

PRs automatically merge when certification passes. No exceptions.

## Installation

```bash
# Core connector (required)
composer require conduit-ui/connector

# Add packages as needed
composer require conduit-ui/issue
composer require conduit-ui/pr
```

## Quick Start

```php
use ConduitUI\Connector\Connector;
use ConduitUI\Issue\IssuesService;

// Initialize
$connector = new Connector(env('GITHUB_TOKEN'));
$issues = new IssuesService($connector);

// Use
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

- **connector**: Authentication, rate limiting, typed exceptions
- **Domain packages**: Clean APIs for specific GitHub resources
- **Saloon**: Battle-tested HTTP client underneath

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

For enterprise support: jordan@partridge.rocks

## License

MIT
