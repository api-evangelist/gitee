# Gitee (gitee)

Gitee (码云) is a major China-based Git hosting and DevOps platform operated by OSChina / Shenzhen Oschina (开源中国). It provides code hosting, pull requests, issue tracking, gists, organizations, and enterprise DevOps workflows for millions of developers and repositories. Gitee exposes a documented REST API v5 covering repositories, issues, pull requests, users, organizations, gists, enterprises, webhooks, and search.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/gitee/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/gitee/refs/heads/main/apis.yml)

## Access Model (Honest Summary)

- **Real, live, documented API.** The Gitee Open API v5 is a REST API over HTTPS with base URL `https://gitee.com/api/v5` and a live Swagger 2.0 definition at [`https://gitee.com/api/v5/swagger`](https://gitee.com/api/v5/swagger) (machine-readable JSON at `https://gitee.com/api/v5/swagger_doc.json`, observed as Gitee Open API version 5.4.92 on 2026-07-12). The full spec declares **175 paths / 264 operations**.
- **Verified live.** `GET https://gitee.com/api/v5/repos/oschina/git-osc` returned HTTP 200 with real repository JSON and an `X-RateLimit-Limit: 60` header; `GET /api/v5/emojis` returned HTTP 200.
- **Authentication.** A **personal access token** sent as the `access_token` query parameter (present on 236 of 264 operations) or as an `Authorization: Bearer <token>` header, **or OAuth2** (authorize at `https://gitee.com/oauth/authorize`, token at `https://gitee.com/oauth/token`; scopes include `user_info`, `projects`, `pull_requests`, `issues`, `notes`, `keys`, `hook`, `groups`, `gists`, `enterprises`, `emails`). Public reads work unauthenticated at a lower rate limit.
- **Pricing.** A **free personal tier** (public/private repos, pull requests, issues, gists, API access) plus **paid Gitee Enterprise Edition** (企业版) sold per seat per year in CNY across Free, Standard (标准版, from ~299 CNY/user/year with seat minimums), and Premium (尊享版) packages. The API itself carries no per-call fee - it is governed by rate limits.
- **China-based platform.** Gitee is operated from mainland China (`gitee.com`), is ICP-registered, and serves Chinese-language documentation and responses. Expect cross-border latency and account for data-residency considerations if consuming from outside China.
- **No WebSocket.** Gitee's public API is REST plus outbound repository **WebHooks** (HTTP callbacks). No WebSocket (`wss://`) or SSE endpoint is documented - see `review.yml`.

## Tags

- Code Hosting
- Git
- Git Hosting
- Version Control
- Repositories
- Pull Requests
- Issue Tracking
- DevOps
- Open Source
- China

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

The catalog groups the Gitee v5 surface into seven APIs. All share base URL `https://gitee.com/api/v5`. The curated OpenAPI (`openapi/gitee-openapi.yml`) captures a representative subset (~30 operations) of the authoritative 264-operation spec.

### Gitee Repositories API

Create and manage repositories and their contents - branches, tags, commits, contents, forks, collaborators, branch protection, and file blobs and trees. The largest surface of the Gitee v5 API.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Repositories, Code Hosting, Git

### Gitee Issues API

Track work with issues - list, create, and update issues for a repository or organization, manage issue comments, labels, and milestones, and inspect the pull requests linked to an issue.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Issues, Issue Tracking, Labels

### Gitee Pull Requests API

Propose and review code changes - list, create, and update pull requests, read their commits and changed files, check merge status, merge or test a pull request, and assign reviewers and testers.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Pull Requests, Code Review, Merge

### Gitee Users and Organizations API

Read and manage the authenticated user's profile, SSH public keys, namespaces, followers and following, plus organizations and their members and membership.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Users, Organizations, Members

### Gitee Gists API

Manage code snippets (gists) - list, create, read, update, and delete gists, star and unstar them, browse their commit history, and manage gist comments.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Gists, Snippets, Code Sharing

### Gitee Enterprises API

Enterprise DevOps surface for Gitee Enterprise Edition - list the authenticated user's enterprises, read an enterprise, manage enterprise members and invitations, and work with weekly reports and their comments.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Enterprises, DevOps, Teams

### Gitee Webhooks API

Configure repository WebHooks that Gitee posts events to over outbound HTTP - list, create, read, update, and delete a repository's webhooks and send a test delivery. These are server-to-endpoint HTTP callbacks, not a WebSocket API.

- **Human URL:** [https://gitee.com/api/v5/swagger](https://gitee.com/api/v5/swagger)
- **Base URL:** `https://gitee.com/api/v5`
- **Tags:** Webhooks, Events, Automation

## Properties

- [OpenAPI](openapi/gitee-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/gitee.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/gitee.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/gitee-domain-security.yml)
- [Authentication](authentication/gitee-authentication.yml)
- [Website](https://gitee.com)
- [Documentation](https://gitee.com/api/v5/swagger)
- [Sign Up](https://gitee.com/signup)
- [OAuth](https://gitee.com/api/v5/oauth_doc)
- [Plans](plans/gitee-plans-pricing.yml)
- [Rate Limits](rate-limits/gitee-rate-limits.yml)
- [Fin Ops](finops/gitee-finops.yml)
- [LinkedIn](https://www.linkedin.com/company/gitee)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
