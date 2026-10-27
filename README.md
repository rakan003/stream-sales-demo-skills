# Stream GTM skills

**For agents: read [AGENTS.md](AGENTS.md) first.** It routes the request to the right skill. The two SaaS skills are the starting point for SaaS work; the general skills support other sectors and reusable implementation details.

| What you need | Use this skill |
| --- | --- |
| SaaS slides tailored to a prospect | [stream-saas-deck](skills/stream-saas-deck/SKILL.md) |
| SaaS website with recurring and UBB stories | [stream-saas-demo](skills/stream-saas-demo/SKILL.md) |
| Both the website and slides | Read both SaaS skills and keep one shared product/pricing manifest. |
| General client demo outside SaaS | [stream-client-demo](skills/stream-client-demo/SKILL.md) |
| Adapt a school or other non-SaaS deck | [stream-client-deck](skills/stream-client-deck/SKILL.md) |

## Give this repo to your AI

> Read AGENTS.md in this repository and select the right skills. Research [client website], make a tailored SaaS demo with recurring subscribe-and-manage and usage-based billing stories, and create a separate copy of [source Canva deck]. Use appropriate client products and pricing units, a clean Link-like embedded checkout, the real Stream sandbox portal and matching merchant records. Keep the source work intact and verify the website and saved slides.

Supply the client website, source deck, requested language and authorized sandbox separately. For a deck-only or website-only request, say so; the agent should not create extra deliverables.

The SaaS website skill covers both customer journeys, billing continuity, appropriate products, KYC/KYB handoffs, idempotent sandbox setup, reset, invoices and presenter notes. The SaaS deck skill covers the source copy, client-specific narrative, native Canva content, screenshots and saved-deck verification.

## Installation

Download the repository and place the desired folders from `skills/` in your AI tool’s skill directory. Codex uses `~/.codex/skills/`. You can also attach the relevant SKILL.md and its linked references directly to the task. Keep linked supporting folders available.

Use the [current Stream documentation](https://docs.streampay.sa/) for API details. This repository contains reusable instructions, not credentials, client conversations, private decks or account records. It does not grant access to Stream, Canva or a hosting provider.
