---
name: stream-client-demo
description: Research a prospective Stream client and build a faithful branded billing demonstration with connected self-serve and usage-based stories, plus requested presenter notes, Notion research, or Canva adaptation. Use for client-specific Stream demos or adapting an existing one; not for unrelated site builds or production billing migrations.
---

# Stream client demo

Make a client-specific experience that a presenter can walk through coherently: recognizable product, believable commercial model, real Stream staging records, and a clear connection between the customer's screen and the merchant's Stream screen.

The user's current scope and preferences take precedence over the defaults below. An existing demo is an implementation reference, not evidence of another client's products or prices. This skill does not itself authorize publication, payment, messages, or changes to unrelated accounts.

For an explicitly requested full package, track the site and both stories, presenter guide, Notion brief, Canva adaptation, and any requested public links in a small project manifest. Record only authorized deliverables, their current URLs, verification status and remaining work; keep the package open until each is verified or a specific blocker is reported. See the manifest guidance in [research-and-presenter.md](references/research-and-presenter.md).

## Establish the story before building

1. Inspect the client's current public site and, when the user provides access, its actual product portal. Record product names, intended buyers, purchase flow, brand assets, and any published pricing or consumption units. Inspect the existing demo's source and live state before reusing it.
2. Distinguish **verified client facts**, **a proposed commercial model**, and **features actually available in the connected Stream environment**. Keep source links with the facts. Do not turn unsupported assumptions into site copy, a slide, or a merchant product description presented as the client's actual offering.
3. Test the UBB fit: what customer action creates value, what event is measured, what unit is billed, and who pays? A unit must have an intelligible relationship to the service. Do not force “credits” onto a business that has no coherent credit model. For a rewards business, separate reward face value or prefunded balances from platform/processing fees; a reward issuance is not automatically fee revenue.
4. Choose the strongest narrow story. Existing self-serve is not itself a reason to switch providers. Explain the incremental value: a clearer consumer portal, seats/add-ons where relevant, measured consumption, or billing across existing products. If UBB has weak evidence, present it as a proposal and explain the fit before implementing it as a demo.

For requested company research, competitors, Notion, or Canva work, read [research-and-presenter.md](references/research-and-presenter.md). Those are optional deliverables, not automatic side effects of invoking this skill.

## Shape the two journeys

**Story one — subscribe and manage.** Start on the client's marketing site, go to a dedicated pricing page, choose a plan and relevant seats/add-ons, identify the business account, and open embedded checkout. On server-confirmed payment, land in that account's Billing view; opening the management portal stays a separate user action. Manage subscription opens the real consumer portal in a dialog over Billing. Invoices & payments includes paid-invoice downloads: Stream's issued PDF by default, or a custom PDF when explicitly requested, following the invoice rules in [billing-invariants.md](references/billing-invariants.md). Keep a repeatable reset accessible to the presenter.

Use the client's published tiers when available. Otherwise make the proposed tiers and assumptions clear in presenter notes. Do not copy Starter/Growth/Scale, three tiers, per-seat prices, or add-ons merely because they appeared in a previous demo. Enterprise/contact-sales is appropriate only when the client's model supports it.

**Story two — consumption to billing.** Use the actual product where consumption makes sense. Show a small set of understandable meters with quantity, unit, rate, current amount, and billing period. Connect each to a real Stream metered subscription in the intended staging account. The presenter must be able to show the same customer, meter, period, and quantity in Stream. Seed deterministic activity once if useful; a fake generation/action button is unnecessary unless requested. Distinguish simulated product activity from real recorded staging usage in the guide.

Show pure UBB when that is what the environment supports. Describe tiered pricing, minimum commitments, hybrid plans, or agent/MCP monetization only as future or proposed possibilities unless verified and implemented. Never simulate their execution while claiming they are connected.

## Match the product and preserve continuity

- Use the available REA/recreation skill for design inspection and CUA for authenticated browser inspection. Capture typography, spacing, navigation, assets, selected states, and real workflows. A logo and palette alone are not a faithful replica. Read the selected tool/skill instructions before using it.
- Keep company and product identities distinct. A narrow product may anchor the working billing story, but the marketing site, pricing overview, merchant invoice and general consumer-portal slides should represent the company. For a multi-product client, acknowledge the verified portfolio and use a contact-sales path where pricing or checkout is not established; do not relabel the entire business as the selected demo product.
- Default to English throughout the interface, customer language, product names, checkout, and portal unless the user asks otherwise. Prefer restrained black primary payment controls unless the inspected brand or user calls for another treatment. Use the client's actual identity; avoid repeated Stream logos and decorative “demo/test” copy.
- Keep marketing pages focused. Put plan cards on Pricing rather than inserting a large subscription pitch into the homepage. Put a discreet **Stories** control at bottom left that reveals the two journeys and reset; keep presenter controls distinct from the payer's main actions.
- Preserve the business account and selected items from setup through checkout to Billing. Keep the payment summary focused on the merchant, purchase and total; do not add a prominent fictional payer avatar/name block unless requested. Keep one consistent account shell/sidebar within a product. When stories genuinely span different client products, preserve their real shells while keeping account terminology and billing behavior consistent; do not invent a unified portal that the client does not have.
- Give seat selection, add-ons, and the order summary enough room to read. Show totals as choices change. Use proportionate dialogs that fit the viewport. Lock the background while a portal/payment dialog is open; choose one scrolling owner and eliminate outer-plus-iframe double scrollbars. Do not shrink text to make a crowded form fit.
- Embed real Stream checkout and portal in the account flow. Avoid routine full-page redirects. Respect cross-origin iframe boundaries: configure supported branding/language, and do not claim arbitrary internal DOM restyling. Handle verified completion so closing or returning updates the same Billing page.
- A displayed Visa ending **1010** is an optional presentation fixture only when requested. Never collect real card details, claim tokenization, or imply that a fixture is a real stored payment method. Keep its scope clear in the presenter guide.

## Connect the correct account safely

Before reusing code or making Stream changes, read [billing-invariants.md](references/billing-invariants.md). It covers account isolation, idempotent writes, reset, invoice ownership, and metering/invoicing boundaries.

Default to a nonproduction environment, use the normal merchant signup flow and reuse an account already created for the task. Follow the current tool policy for credentials; never save passwords.

Verify and record the merchant, admin, API, checkout and portal origins independently from current documentation or authenticated behavior. Do not infer an API origin from the app hostname or switch to production to bypass a failure.


Read current authenticated Stream docs and inspect the target account's actual behavior. Follow the signup-first configuration checklist in [billing-invariants.md](references/billing-invariants.md#configure-the-signed-up-account): verify identity, bilingual display names, branding, verified address/tax details, portal settings and API access, then reload and read back. Configure only the authorized client account. Keep API keys in server runtime secrets; never frontend source, browser storage, screenshots, deployment archives, presenter notes, or skill files. Reconcile existing resources before creating them.

## Verify and deliver

Follow the deployment platform's skill when publishing. Preserve the existing site's access/sharing setting unless the user changes it. An explicit request for a public demo authorizes public access for that demo: configure it and verify the published URL without a signed-in session. Keep private research, mailbox material and credentials outside public assets; public access does not authorize sharing unrelated resources. A new client's demo gets its own project and account state rather than overwriting the previous client's site.

Verify the meaningful boundaries: correct account, repeat requests without duplicates, session isolation and reset, ownership of invoices, server-confirmed payment, and agreement between UI and Stream meters. Use targeted automated tests for billing boundaries and browser checks for the actual journeys. Do not create repeated payments or subscriptions just to rerun a visual check.

At the intended desktop size and a narrow mobile size, inspect the real checkout, portal dialog, invoices, and story controls. Check overflow, readability, focus/close behavior, payment return, and selected seats/add-ons. Verify an actual downloaded Stream PDF; a button click alone is not proof. After publishing, check the live routes and at least the changed flow rather than relying on deployment success alone.

Deliver working links, a short walkthrough, reset instructions, and the exact merchant tab/record to compare during UBB. When requested, make the Notion brief a concise meeting document with **Project links first**, plain-English research, practical speaking lines, and a compact local-file handoff for the next agent. Follow [research-and-presenter.md](references/research-and-presenter.md) for the complete link inventory, research structure, local paths and readback checks; always link the saved Notion brief in the final handoff. Say what is verified, proposed, simulated or still unknown, and keep detailed operational records in a collapsed appendix. Do not claim live delivery until the published behavior has been checked.
