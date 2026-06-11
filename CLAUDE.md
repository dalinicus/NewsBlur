# NewsBlur — Kubernetes Fork

This is a personal fork of [samuelclay/NewsBlur](https://github.com/samuelclay/NewsBlur).
The goal of this fork is to make NewsBlur self-hostable on Kubernetes, deployed via a Helm chart
in the [glados-config](https://github.com/dalinicus/glados-config) repo.

The upstream codebase assumes a docker-compose environment with fixed container hostnames (e.g.
`newsblur_db_redis`, `newsblur_db_mongo`). This fork patches those assumptions so services
read connection info from environment variables, compatible with standard Kubernetes service names.

## Changelog

All changes made in this fork should be documented here so there is a single place to understand
what diverges from upstream.

| File | Change |
|------|--------|
| `CLAUDE.md` | Added (this file) — K8s fork context and changelog |
| `AGENTS.md` | Kept as-is (upstream content) |
| `node/unread_counts.coffee` + `.js` | Redis host/port now read from `REDIS_HOST` / `REDIS_PORT` env vars (fallback: `newsblur-db-redis` / docker-mode port) |
| `node/favicons.coffee` + `.js` | Mongo host now reads from `MONGODB_HOST` env var (fallback: `newsblur-db-mongo`) |

## Outstanding tasks

See [tasks/k8s-compatibility.md](tasks/k8s-compatibility.md) for work that needs to be done
across conversations.

## Upstream development guidelines

The original upstream development guidelines (docker-compose workflow, Android/iOS, code style,
etc.) are in [AGENTS.md](AGENTS.md).
