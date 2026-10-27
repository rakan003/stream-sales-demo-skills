---
name: stream-saas-demo
description: Build a tailored SaaS demo website with two coherent Stream billing stories — recurring subscribe-and-manage and usage-based consumption-to-billing. Use for technical B2B SaaS prospects, recognizable client products, a clean Link-like checkout, real sandbox checkout/portal and matched merchant records. Not for school payment demos or production migrations.
---

# Stream SaaS demo website

Make a credible product experience that feels like the prospect’s own site, with a recurring-subscription story and a UBB story the presenter can follow into Stream. Read [AGENTS.md](../../AGENTS.md) for routing. If slides are requested, also read [stream-saas-deck](../stream-saas-deck/SKILL.md).

## Research before implementation

Inspect the current official website, pricing, product pages and any authorized portal. Capture product names exactly, the buyer and user, navigation, terminology, typography, assets and normal customer workflow. Inspect the existing demo’s source and live state before reusing it.

Build a short product map: what each product does, who pays, the commercial unit, current or proposed pricing, and the evidence. Choose products that make sense for the two stories. Do not force token/credit billing onto a service with no defensible consumption unit, or copy another client’s tiers and rates.

For AI or rewards products, separate provider cost, customer price, platform fees and pass-through value. A reward’s face value is not the SaaS platform’s fee revenue. Label proposed commercial terms in the private guide, rather than cluttering the payer UI.

## Make the site recognizable

Recreate the client’s actual visual system and key product shell. Preserve company versus product identity and multi-product navigation. Use official logos and real assets. Default to English unless the user requests otherwise.

Keep the homepage about the business. Put plans and pricing on a dedicated route. Add a discreet bottom-left Stories control exposing the two journeys and reset. The payer should not see engineering notes, provider IDs or lengthy demo disclaimers.

## Story 1 — recurring subscribe and manage

The intended journey is:

1. Client marketing site → Pricing.
2. Choose an appropriate base plan and any supported seats/add-ons. Show the selected items and total as choices change.
3. Identify the business/customer account. If the service requires KYC/KYB or operational approval, show approval before monetization or make the approval handoff explicit.
4. Open the real Stream checkout inside a clean, focused dialog. Aim for the clarity of Link: recognizable merchant, concise order summary, one clear total and the payment action. Keep payer identity discreet and use the client’s visual treatment where the provider permits it.
5. Verify payment server-side. Land in the same customer account’s Billing view.
6. Manage subscription opens the real Stream consumer portal as a separate user action. Show the supported plan, quantity, add-on and card actions, with invoices/payments accessible from Billing.
7. Demonstrate one meaningful change and its actual proration/invoice result. The client’s application applies access/entitlement changes from the agreed integration.

Keep the same account and selection throughout. Closing and reopening the dialog must work. Lock background scrolling and give the iframe one scrolling owner. Fit the order summary, seats and add-ons comfortably rather than shrinking text.

## Story 2 — usage to a bill

Choose a real client product whose value can be metered. Define the mapping explicitly:

`customer action → event → billable unit → rate → Stream product/meter → subscription → customer → billing period`

Show a small, intelligible set of usage meters with quantity, unit, rate, billing period and current charge. Connect them to the intended sandbox subscriptions. Use the same units and totals on the product screen and in Stream so the presenter can compare them directly.

Seed deterministic activity once when useful. A fake action button is not required. If product activity is simulated but usage records are real sandbox records, explain that in the presenter guide. Do not describe generated screenshots or frontend-only arithmetic as a connected UBB flow.

Pure UBB, included allowances, thresholds, credits, graduated tiers, volume pricing and hybrid commitments are different models. Implement the model the environment actually supports. Keep unimplemented options as proposals. If an on-demand invoice bills a usage snapshot, track covered quantity ranges and prevent duplicate billing; do not claim it closes the native metered cycle.

## Use the right sandbox

Read [billing invariants](../stream-client-demo/references/billing-invariants.md) before reusing code or configuring billing. Verify the authorized merchant, admin, API, checkout and portal origins independently. Confirm the intended organization with a read-only lookup before writes. Never inherit another client’s IDs, keys, seed records, tax identity or deployment binding.

Use the current [Stream docs](https://docs.streampay.sa/), including [embedded checkout](https://docs.streampay.sa/embedded-checkout), [consumer portal](https://docs.streampay.sa/customer-portal), [webhooks](https://docs.streampay.sa/webhooks), [testing cards](https://docs.streampay.sa/testing-cards) and [MCP](https://docs.streampay.sa/mcp-server). Re-check supported fields and behavior; this skill is not an API specification.

Keep keys in server runtime secrets. Reconcile existing resources before creating them and use durable idempotency keys for setup and usage events. Keep the fixed UBB account separate from resettable inbound sessions. Authorize invoices, subscriptions and portal sessions against the current customer.

Respect cross-origin iframe boundaries. Treat callbacks as refresh signals, then verify the owned payment server-side. Validate provider message origins and narrow authentication destinations. Do not infer success from a redirect, token activation or an accepted request.

## Reset, invoices and handoff

Reset returns the recurring story to clean pricing and rotates only the local demo session; it should not create new provider records or erase past sandbox subscriptions. Make the presenter’s reset repeatable without touching other clients.

Use Stream’s issued invoice PDF by default. If the user requests a custom invoice, derive it from the actual issued record, preserve the financial values and inspect the rendered result. Verify a real download, including customer ownership and paid status.

Keep a private manifest with the website routes, recurring story, UBB story, presenter guide, copied deck if requested, sandbox record links and verification outcomes. Never store credentials in it. The guide should give a 3–6 step walkthrough per story, matching merchant record, reset instructions and actual limitations.

## Verify before delivery

Check the live recurring flow, payment return, portal, invoices, UBB meter/period/quantity agreement and repeat-request behavior. Verify session isolation, reset, correct organization and duplicate prevention. Use meaningful tests for those boundaries and inspect the real UI at desktop and narrow mobile widths.

Follow the hosting platform’s workflow when publication is requested. Preserve access restrictions unless the user changes them. Check a requested public demo without a signed-in session. Return working links and the specific Stream record to compare for UBB; deployment success alone is not proof the journey works.
