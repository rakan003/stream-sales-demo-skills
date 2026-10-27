# Screenshot personalization

## Source-first editing

Work from the existing screen asset at its original aspect ratio. Use the image tool's currently supported reference-image mechanism; inspect local inputs first. Include the official logo as a reference and identify each input's role explicitly. Use one edit per distinct screen so exact changes remain reviewable.

Typical surfaces to inspect:

| Screen | Client-specific areas |
|---|---|
| WhatsApp invoice | Business/sender identity when applicable, invoice “From,” institution name within message, institutional logo if present |
| Invoice and payment plan | Top institution logo/name, “From” row, merchant references in invoice details |
| Wallet/payment | Institution header and name under the dimming layer; invoice sender; wallet “Pay …” merchant label |
| Payment confirmed | Header/logo, “From” row, receipt identity; preserve download action and Stream footer |
| Reminder | Client name/logo inside the message or invoice card, not Stream's sender branding |
| Portal, enrollment or other screen | Institution identity wherever rendered; determine whether native text or embedded image first |

Do not assume only one occurrence in a screen.

## Reusable edit prompt

Fill in only details observed in the target image:

```text
Use case: text-localization and precise-object-edit
Asset type: screenshot inside an existing Stream presentation phone mockup
Input 1: original screenshot, the edit target
Input 2: verified official client logo, the identity reference

Replace every occurrence of "<old client name / observed variant>" with
exactly "<new display name>" at these observed locations:
<list the header, From row, message, wallet merchant label, etc.>
Replace the old institution logo at <observed locations> with the complete
official logo from Input 2, preserving its proportions and all components.

Keep the original screen composition, portrait aspect ratio and full viewport.
Preserve Stream branding, payer name, amounts, dates, card details, UI controls,
status icons, browser bars and payment-provider marks exactly as shown.
Do not add a phone frame, crop the screen, invent UI, change other wording,
or redraw the layout. Match the existing text size, weight and spacing.
If the replacement name is longer, fit it naturally without covering nearby UI.
```

For a wallet overlay, add:

```text
Update the client identity in BOTH the wallet sheet and the dimmed page behind
it. Preserve the original darkening, overlay opacity, layering and payment
controls. The institution logo under the overlay must still be the complete
new official logo, not the old logo and not a partial new emblem.
```

For corrections, identify a single observed defect and preserve the rest. Reinspect after each correction. After repeated failed corrections to the same detail, use an available exact native logo placement for that detail when appropriate, or report the limitation; do not silently accept wrong identity or endlessly regenerate the entire screen. Such a placement must be deliberate, correctly layered and visually seamless, not a cover-up that hides unfinished content.

## Official logo fidelity

Use official vector or high-resolution artwork where possible. Website SVGs sometimes animate from zero opacity or scale and can appear blank when imported. If encountered, preserve the official paths/colors while rendering or freezing the final visible state; do not substitute a guessed emblem.

Check the logo's full silhouette, text, rules and secondary colors. This is an example of what to verify, not a universal six-column-logo requirement.

Keep source and final assets separately. An asset record should include original filename, source slide/element, target name, official logo provenance, final filename, prompt used and visual-QA result. Never store expiring signed URLs as the sole reusable source.

## Final visual checks

Check the native slide and a readable image view. Is every target name exact? Does the full official logo match the reference? Are the foreground and dimmed background correct? Are receipt actions and original UI intact? Does the screenshot fit the same phone without a new bezel or double frame?

Generated output pixel dimensions may differ from the source. Verify composition, aspect ratio and in-frame crop rather than assuming matching dimensions. Do not claim pixel-identical preservation: unchanged layout and business content must be inspected, and minor raster rendering differences are possible.
