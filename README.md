# AllStackd — Amazon SES operations

**Product site:** [https://allstackd.com](https://allstackd.com)

AllStackd is an Amazon SES operations layer for founders, studios, agencies, and freelance developers who run more than one product, AWS account, or region.

Monitor every Amazon SES account, region, and domain from one workspace. Keep delivery in your AWS account. Use AllStackd’s durable API when you need transactional sending.

> This repository is a public landing page for discoverability. It is **not** the AllStackd product and contains **no source code**, APIs, SDKs, or CloudFormation templates. The product is proprietary and closed-source. Specs and examples live on the site docs so they stay in sync with production.

## What it does

- **Observe** — See SES identities, DKIM, sandbox status, quotas, and reputation without routing email through AllStackd.
- **Control** — Add a durable, policy-enforced sending layer project by project while keeping delivery in your AWS account.
- **Your AWS role** — Connect with a reviewable CloudFormation stack. No long-lived access keys.
- **Your SES account** — Delivery stays in AWS. AWS bills the sends.

## Who it is for

- Founders and studios tracking identities, quotas, sandbox state, and reputation across products
- Agencies separating client AWS access and catching health issues before campaigns or releases
- Freelance developers keeping each client’s SES account apart
- SaaS teams watching quotas, bounces, and domain health for transactional mail

## Developer surfaces

These are hosted by AllStackd (account + API key required). This repo does not ship client libraries or OpenAPI files — use the docs as the source of truth.

| Surface | What it is | Where to read |
|---|---|---|
| **REST API** | Transactional send (`POST /api/v1/emails`), message status, templates, scoped API keys, signed webhooks | [Docs](https://allstackd.com/docs) |
| **TypeScript SDK** | Thin client helpers for send, status, and template CRUD (copy from docs into your app) | [Docs — TypeScript SDK](https://allstackd.com/docs) |
| **MCP (beta)** | Agent tools over `https://allstackd.com/api/mcp` with the same Bearer API key (projects, domains, templates, usage, send) | [Docs — MCP beta](https://allstackd.com/docs) |

Typical Control-mode path: connect AWS via CloudFormation → verify a sender domain → leave the SES sandbox if needed → queue sends with an idempotency key → poll status or receive signed delivery events.

## Start here

| | |
|---|---|
| Product | [https://allstackd.com](https://allstackd.com) |
| Docs (AWS connection & API) | [https://allstackd.com/docs](https://allstackd.com/docs) |
| 14-day trial | [https://allstackd.com/sign-up](https://allstackd.com/sign-up) |
| Support | support@allstackd.com |

No card required for the trial. Founder-assisted setup is available.

## Keywords

Amazon SES · AWS · CloudFormation · transactional email · multi-account SES · SES reputation · DKIM · SES sandbox · REST API · TypeScript SDK · MCP · email webhooks

## License

AllStackd the product is proprietary. This repository holds marketing copy only and does not grant rights to the SaaS, API, or any implementation. See [https://allstackd.com/terms](https://allstackd.com/terms).
