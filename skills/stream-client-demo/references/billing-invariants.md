# Billing invariants

Read before connecting a new client account, cloning a demo, or changing billing behavior. These are observed failure boundaries, not fixed API schemas. Verify current endpoints and payloads in authenticated documentation.

## Separate each client and environment

After normal merchant signup or reuse of the user's existing account, perform a read-only authenticated account lookup before billing writes. Confirm the intended organization and the nonproduction environment using the API base URL, account identity, and current documentation. A flag named `sandbox` by itself may not describe the environment reliably. Do not assume a generic Stream connector uses the new key the user supplied.

Treat the chosen nonproduction environment mapping as a lock. Record the merchant app and admin panel separately; their origins may differ when authorized or verified as parts of the same setup. Resolve the API, checkout and consumer-portal origins independently from current documentation or authenticated behavior, and record them with the expected organization ID. Do not infer an API origin from the app hostname. A missing endpoint, failed login or inaccessible account is a blocker for that operation, not a reason to try production or an unrelated demo host. Establish the mapping before billing writes; never inherit it from copied code.

Prefer ordinary merchant signup and reuse the authorized existing account. Use internal admin creation only when requested and working. Keep internal account contacts separate from the client’s public details. Follow the current tool policy for credentials; never store passwords or API keys in notes or skill files.

When adapting a previous demo, inventory and replace:

- Runtime API key, organization ID, expected account allowlist, catalog/product maps, and any consumer or subscription IDs.
- Imported seed modules, embedded operation records, local databases/migrations with data, invoice ranges, payment links, portal session URLs, and cached responses.
- Browser cookie/storage names, workspace namespaces, event IDs, invoice descriptions, metadata tags, and persistent operation keys.
- Project/site IDs, database bindings, Git remote, deployment credentials, domains, redirect URLs, and archive contents.
- Previous client logos, fonts/assets whose reuse is inappropriate, names, URLs, pricing, public pages, presenter notes, and tests that silently assert the old account.

Copy reusable source deliberately. Do not carry `.git`, `.env*`, runtime state, build output, or live seeds into a new client project. Preserve the prior demo. Store each new client's resources under a distinct namespace and verify the new deployment does not expose old records.

Use an intended-organization check before provider operations. Keep secrets server-side and redact them in logs/errors. Provider IDs needed by the browser may be ordinary identifiers, but authorization must still come from the session and server ownership checks, never from a supplied ID alone.

## Configure the signed-up account

Use the current merchant UI and documentation; field names and supported options can change. Configure the requested account before provisioning demo billing:

1. Read the signed-in organization without changes and record its ID, display name and environment mapping. Confirm it is the account the user intended.
2. Set English and Arabic display names from official client sources. Keep a verified brand name distinct from the incorporated legal name; do not invent a legal suffix. Configure the official logo, supported invoice header, brand colors, website/contact URL and verified public contacts. Keep internal sandbox contacts separate from public client details.
3. Fill only verified address fields. Use a verified VAT registration number, or a sandbox placeholder only when the user explicitly authorizes it; record that placeholder as non-real in the manifest and presenter notes. A VAT rate is separate from registration identity. Do not fabricate missing legal/tax details or copy them from another demo.
4. Configure supported consumer-portal branding, language and customer actions, plus the intended product group/catalog selection when available. Verify the effective settings and eligibility instead of assuming that a saved toggle enables a feature for every subscription type.
5. Create or reuse API access through the merchant UI under the current browser policy. Copy the full credential supplied for the `X-API-Key` header into the approved server runtime secret mechanism. Distinguish a key ID or displayed raw key from the actual header value: use the UI's current instructions or authenticated documentation for any required format; never guess or substitute one for another. Verify it with a read-only lookup of the expected organization, without logging the credential.
6. Save, reload and read back the company, branding, tax and portal settings. Verify a representative checkout, portal and native invoice when those records exist. Record actual results, unavailable fields and any authorized sandbox placeholders; do not record passwords or API credentials.

## Idempotent staging setup

Maintain a durable operation ledger with a stable operation key, payload fingerprint, state, and remote resource ID. Where practical, serialize operations per workspace with a bounded lock. Persist the intent before a remote create.

For a customer, product, subscription, usage event, or invoice:

1. Reuse a completed operation with the same payload.
2. Search/reconcile the remote account using stable external metadata before creating.
3. Reject a reused key with a different payload.
4. After a timeout or unknown response, reconcile the same intent. Do not issue a fresh key to escape uncertainty.
5. If reconciliation cannot establish whether the write committed, leave the operation pending and surface the specific blocker. Do not create a duplicate or keep blind retries running.

Verify product type, currency, interval, quantity rules, unit rate, and actual VAT configuration. Do not copy an earlier demo's exemption just to make totals match. Coordinate product and subscription creation under one owner to avoid two workers provisioning the same catalog.

A usage event has a stable source-event ID. Replaying it must not increment the meter again. Read the resulting meter and current period from Stream after recording; an accepted request alone does not establish the quantity displayed by the provider.

## Self-serve session and reset

Use a server-controlled session identity, such as a validated opaque UUID in an HttpOnly, Secure, SameSite cookie. Map it to the current inbound workspace/customer. A random cookie is suitable for an owner-private demonstration, not a substitute for real end-user authentication on a public multi-user product.

The initial empty view and reset should not create provider resources. Reset rotates the local inbound session and returns to clean pricing. Earlier customers/subscriptions remain in staging but disappear from this journey. Explain that behavior to the presenter. Do not cancel/delete old subscriptions or imply that reset erased provider records.

Keep the fixed UBB account separate from resettable inbound sessions. Filter invoice lists and subscription/portal lookups by the current customer. Old sessions must not see the new session's records or vice versa.

Within a session, reuse the same checkout request. If a paid active subscription already exists, direct the user to Billing rather than creating another one. When choices change, retire only the obsolete unpaid link owned by that session if the API supports it. Never affect another session's links or subscriptions.

## Embedded payment and portal

Create portal sessions for the current customer and, where supported, the intended subscription. Use current supported language/theme settings and short-lived session URLs. Do not expose merchant credentials to the iframe.

Treat iframe callbacks/redirects as a prompt to refresh, not proof of payment. Validate message origin and shape when consuming postMessage events, then verify the owned invoice's status on the server. Update Billing from the verified snapshot. Keep confirmation reads lightweight: unrelated catalog validation and invoice-link resolution should not delay the paid customer reaching Billing. If a trusted return signal arrives during an older status request, perform a fresh follow-up rather than losing the signal. Poll only while payment is pending and make reload/close/reopen safe.

Handle a currently verified processor-verification/3DS handoff emitted by the trusted Stream iframe. Require the message's `source` to equal the active iframe's `contentWindow`, its `origin` to match the exact verified Stream origin, and its shape to match the current provider contract. Parse the destination as a URL and allow only the confirmed HTTPS processor origin and narrow transaction-authentication path. Keep initial checkout and portal URLs restricted to the authorized staging origins; this handoff is not a general external-redirect allowlist. Do not silently discard a valid handoff or leave the payer's button spinning. Follow the supported verification flow, or show a recoverable error for an unsupported destination, then verify the owned payment server-side on return.

Processor routes can differ from a documentation example. Inspect the actual handoff from the authorized sandbox checkout and confirm its purpose with current official documentation. Restrict it to the verified HTTPS origin and narrow authentication path. Never permit an arbitrary path prefix. Redact query/authentication tokens from diagnostics. Reaching an authentication route is not proof of payment.

Confirm the current processor route and event contract before implementing a handoff. Token activation, authorization and a paid invoice are separate states. Verify the owned payment server-side.

A full-page fallback may be necessary when the provider refuses embedding. Report that constraint rather than bypassing frame policy or presenting a fake embedded success screen.

## Pure UBB and invoices

Maintain an explicit mapping: product feature → billable event → unit → rate → Stream product → metered subscription → customer → period. Show those same units in the UI. Do not mix videos, seconds, images, API calls, emails, credits, or currency without an explained conversion.

Use provider readings for quantities and period boundaries. Read prices/tax from the configured product; derived UI arithmetic must reconcile to provider invoice totals. Distinguish gross from net consistently. Avoid hard-coded screenshots or frontend totals that diverge after refresh.

Determine whether the environment generates a native cycle invoice. If the demo instead creates an on-demand invoice for a usage snapshot, record covered quantity ranges per meter/period and reuse the invoice for that snapshot. Do not bill the same range twice. Do not describe snapshot payment as closing or settling the native metered cycle, and do not allow a later cycle charge to be presented as already paid. Document the actual lifecycle in the guide.

If staging cannot display metered subscriptions in its consumer portal or cannot combine add-ons with meters, preserve the working UBB view and disclose that limit in presenter notes. Use the recurring story to demonstrate seats/add-ons; do not fabricate portal support.

## Invoice downloads

Default to **only Stream's issued PDF**, without a custom cover or appended pages. An explicit request for a custom downloadable invoice overrides this presentation default. Preserve the same ownership/payment checks below and derive the custom document from the actual issued invoice: number, dates, legal details, currency, line items, discounts/proration, net, VAT and paid total. Never copy another demo's tax identity, invent a regulatory QR code or imply that typography establishes ZATCA compliance.

When the user supplies an earlier invoice as a design reference, inspect its code and rendered output, reuse its visual treatment where appropriate, and replace all client data. Match the new brand's font hierarchy, spacing and page balance. Compare the rendered pages side by side: logo and title must not collide, numeric columns must align, and the main total should be prominent without overpowering the table. Preserve real financial values even when shortening display labels. Make the download return the requested document by itself; do not combine it with a second document unless asked. Inspect the rendered PDF and reconcile it to the provider record. Retain access to the original issued record for traceability, and describe the custom PDF's status accurately in the private guide.

Verify branding colors in the original issued PDF, not only the settings preview. A secondary invoice color may control body text; a pale brand accent can make totals and tax details unreadable. Choose a contrasting text-safe value when that is how the provider uses it, save and reload the setting, then download and visually inspect the refreshed native PDF before calling the correction verified.

The server should:

1. Resolve the current workspace/customer and verify the invoice belongs to that customer and expected organization.
2. Confirm payment completion and select the successful payment associated with that invoice.
3. Resolve the current supported provider PDF endpoint. A previous implementation used a consumer-portal invoice/payment route; do not assume that route or storage bucket is permanent.
4. Validate the returned HTTPS storage URL against the verified provider destination, refuse unexpected redirects, and fetch without forwarding the Stream API key to storage.
5. Enforce a bounded response size, PDF MIME type, and `%PDF-` signature. Return native bytes for a native download, or the verified custom render when requested, with private/no-store attachment headers.

Check invalid/cross-session invoice IDs, unpaid status, unexpected storage hosts, bad payloads, and cross-site requests. Verify a real download locally: compare native bytes to the provider result where possible, and reconcile custom document values plus visual rendering to the issued record. The presence of a QR code or tax fields in staging is not a ZATCA compliance certification.
