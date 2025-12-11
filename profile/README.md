# Conduit

**Agent verbs for GitHub.**

What does an agent do?

| Package | Verb | Agent Does |
|---------|------|------------|
| [connector](https://github.com/conduit-ui/connector) | connect | HTTP transport layer |
| [issue](https://github.com/conduit-ui/issue) | issue | Work on issues |
| [pr](https://github.com/conduit-ui/pr) | pr | Create/manage PRs |
| [commit](https://github.com/conduit-ui/commit) | commit | Make commits |
| [repo](https://github.com/conduit-ui/repo) | repo | Manage repositories |
| [action](https://github.com/conduit-ui/action) | action | Trigger workflows |
| [review](https://github.com/conduit-ui/review) | review | Review code |

## Install

```bash
composer require conduit-ui/connector
composer require conduit-ui/issue
composer require conduit-ui/pr
```

## Philosophy

- **Singular**: One word, one purpose
- **Deterministic**: Same input → same output
- **Minimal**: No unnecessary abstractions
- **Agent-first**: Built for AI automation

---

*Part of [THE SHIT](https://github.com/the-shit) ecosystem*
