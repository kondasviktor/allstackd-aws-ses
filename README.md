# AllStackd — email for your AWS AI agents

**Product site:** [https://allstackd.com](https://allstackd.com)

Give each of your AI agents its own inbox inside **your** AWS account. Mail arrives through Amazon SES into your S3 bucket, your agent reads it and drafts replies, and **nothing is sent until a person approves it.** SES health monitoring is free.

> This repository is a public landing page for discoverability. It is **not** the AllStackd product and contains **no source code**, APIs or CloudFormation templates. The product is proprietary. The documentation on the site is the source of truth.

## How it works

```
Sender ──► Amazon SES (your account) ──► S3 (your bucket) ──► AllStackd (metadata only)
                                                                    │
Agent (Claude, ChatGPT, Cursor, Grok, your own) ◄── MCP / REST ─────┤
                                                                    ▼
                       Draft ──► policy checks ──► person approves ──► SES (your account) ──► Recipient
```

- **Your AWS account.** Receiving, storage and sending run in your SES and S3. AWS bills them to you.
- **Metadata only.** AllStackd stores addresses, timestamps and thread structure. Message bodies and attachments are read on demand from your bucket and never stored by AllStackd.
- **Human approval.** Every reply waits for a person by default. Agents can draft and request a send; they can never approve, change a policy or turn off the kill switch.
- **Guardrails on the server.** Replies only to people already in the thread, a recipient cap, no BCC or attachments, daily and per-thread limits, secret scanners, loop protection, a reputation breaker and an organization kill switch.
- **No access keys.** You connect with a reviewable CloudFormation role and an External ID.

## Who it is for

- Teams running AI agents on AWS that need to receive and answer email under guardrails
- Founders who want a support or ops inbox an agent can triage and draft for
- Builders using Claude, ChatGPT, Cursor, Grok, Strands or AgentCore with their own SES

Not for cold email, purchased lists, bulk marketing or people without an AWS account.

## Plans

Free: 3 inboxes, 1,000 messages a month, SES health monitoring. Builder and Team add inboxes, volume, auto-send to allowlisted recipients, custom policies and audit. See [allstackd.com](https://allstackd.com) for current pricing.

## Developer surfaces

| Surface | What it is |
|---|---|
| **MCP (OAuth)** | `https://allstackd.com/mcp` for Claude, ChatGPT and other clients where a person signs in |
| **MCP (agent key)** | `https://allstackd.com/api/mcp` with `Authorization: Bearer as_…`, limited to chosen inboxes |
| **REST API** | `/api/v1` with an OpenAPI description and a TypeScript client |
| **Webhooks** | Signed events such as `message.received` and `draft.pending_approval`, IDs and metadata only |

## Agent plugin

Connector pack (MIT, no product source): [github.com/kondasviktor/allstackd-plugin](https://github.com/kondasviktor/allstackd-plugin). It includes the `allstackd-agent-mail` and `allstackd-inbox-triage` skills and configuration for Claude, ChatGPT, Cursor, Grok, Muse, Antigravity, AgentCore and Strands.

| Client | Status |
|--------|--------|
| **Claude** | Listed in the Connectors directory (community) |
| **Cursor** | Listed on cursor.directory |
| **Grok Build** | Submitted ([marketplace PR](https://github.com/xai-org/plugin-marketplace/pull/1069)); manual MCP install works |
| **ChatGPT** | Works as a custom connector; directory submission parked |
| **Antigravity CLI** | Path install from the plugin repo |

## Start here

| | |
|---|---|
| Product | [https://allstackd.com](https://allstackd.com) |
| Docs | [https://allstackd.com/docs](https://allstackd.com/docs) |
| Guides (Strands, AgentCore, DIY SES, approval, prompt injection) | [https://allstackd.com/guides](https://allstackd.com/guides) |
| Security | [https://allstackd.com/security](https://allstackd.com/security) |
| Sign up (free, no card) | [https://allstackd.com/sign-up](https://allstackd.com/sign-up) |
| Support | support@allstackd.com |

## Keywords

AI agents · agent email · inbox · human-in-the-loop · Amazon SES · AWS · MCP · Claude · ChatGPT · Cursor · Grok · AgentCore · Strands

## License

AllStackd the product is proprietary. This repository holds marketing copy only and does not grant rights to the SaaS, API or any implementation. See [https://allstackd.com/terms](https://allstackd.com/terms).
