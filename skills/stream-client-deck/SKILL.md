---
name: stream-client-deck
description: Personalize an existing Stream Canva presentation for another client. Create a separate copy, replace client names and official logos in editable content and embedded payer-flow screenshots, update the client website screenshot, and preserve the source deck's design. Use for requests like “make the another client version for another school/client”; not for designing an unrelated deck from scratch.
---

# Stream Client Deck

Produce a separate, saved Canva presentation for the new client, with their identity carried through every relevant slide and payment screenshot. Preserve the source presentation and its approved visual design.

## Establish the source and client

Use the client name, official website, logo and source deck supplied in the current conversation. Ask only for missing essentials: an identifiable client and a usable source deck. A supplied source or newer designer edits take precedence.

Verify the official website and logo. If a supplied site cannot be confirmed as belonging to the target client, ask for the correct identity source while continuing independent work; do not use an unrelated site or guess its logo. Use the user's preferred display spelling, and the official Arabic name when the slides contain Arabic. Record old-name variants and abbreviations from the actual source. A useful brief contains the source Canva URL, old client name, target display name, official website, official logo reference, and any language or scope exceptions.

Do not infer a new client's commercial results, product eligibility, or customer status. Personalization is not authorization to add the prospect to the client-logo grid, alter metrics, or send the presentation.

## Inspect, copy, map

Use the available Canva connector for supported copy/content/media operations, and the browser for visual inspection and editor operations when useful. Follow the current tools' schemas and transaction rules; do not rely on remembered parameters. Read [references/canva-editing.md](references/canva-editing.md) for editor pitfalls and saved-versus-draft checks.

1. Inspect the live source, including thumbnails, editable text, image assets and presenter notes. Identify slides by title and contents, **not fixed page numbers**. The payer journey, reminders, student portal, enrollment/payment link, website/API slide and closing slide may all contain client identity.
2. Copy the entire source unless a narrower scope was requested. Name the copy `Stream × <Client display name>` and retain its new ID/URL. All personalization happens in that copy. Do not recreate the deck from screenshots or flatten editable slides.
3. Re-inspect the copy to resolve its actual page and element IDs. Keep a small local change map: page/title, element or asset, old identity, replacement, original position/size/crop, and verification status. Do not assume copied IDs stay identical.
4. Download or export original image assets at usable resolution through supported tools. A page thumbnail is for inspection, not a replacement for a sharp screenshot asset. Inspect the actual image before editing it.

## Personalize every surface

### Editable text and native logos

Replace client references in headings, invoice sender/merchant labels, portal and enrollment content, website labels, notes and any other relevant native text. Review abbreviation matches in context rather than performing an indiscriminate global replacement. Preserve student names and unrelated organizations unless requested otherwise.

Replace the old institution logo wherever it belongs to the presented client, while retaining Stream branding, payment-provider marks and other organizations' logos. Preserve the official logo's aspect ratio and use its visible artwork bounds to size and center it; bitmap padding can make nominal dimensions misleading. Do not recreate the client's logo from memory.

Keep native text editable and retain the source's font family, weight, size, tracking, line height and alignment. Make only the smallest necessary adjustment when a longer client name would wrap or clip. Carry forward the latest designer changes, not an older default theme.

### Embedded payer and product screenshots

Use the built-in image generation/editing capability for raster screenshot substitutions, with the **original screenshot as the edit target** and the verified official logo as a separate reference. Read the available imagegen skill and [references/image-personalization.md](references/image-personalization.md) before generating. Do not redraw the whole slide, regenerate a phone frame, or return placeholder screens.

Create one edited asset per actual source screen. The source often contains four payer-journey screens plus a reminder screen, but inspect every slide: the relevant screen might be elsewhere or the portal might consist of native Canva components.

Change every visible institution-name occurrence, including WhatsApp sender text, invoice `From` rows, header logos, payment-success screens and wallet merchant labels. Inspect **behind the dimmed Apple Pay sheet** as carefully as the foreground. Preserve amounts, payer details, controls, phone geometry, browser bars and Stream footer unless the user requested those changes.

Insert visually verified outputs into the existing screenshot areas, keeping their phone frames and placements. Confirm crop and aspect ratio in Canva after replacement. Generated text and logos require visual verification; a successful generation response does not establish correctness.

### Actual client website

On the slide titled “We serve you wherever you need,” “Stream, wherever you work,” or an equivalent website/API presentation, replace the old site's image with an **authentic screenshot of the target's official website**.

Open the live site in the browser, let the header and hero finish rendering, and capture a viewport suited to the existing website frame. Prefer a clear frame showing the institution's logo/navigation and recognizable content. Avoid transient menus, loading states and obstructing banners. Preserve the website's actual appearance; do not generate a fictional homepage or use a search thumbnail.

Fit the screenshot into the existing website area, retaining the frame, Stream-side interface and authorized checkout overlay. Update any separate displayed domain. Presenting the website with a Stream overlay is an illustrative integration example, not evidence of a live deployment. If the site cannot be captured after reasonable retries, complete independent edits and report that exact remaining limitation rather than fabricating a screenshot.

## Verify and deliver

- Re-read all editable text, notes and relevant alt text for old client name variants, old domain and old institutional logo references. Review hits in context; leave unrelated client-list content alone.
- Inspect each changed raster at readable resolution and within its slide. Check exact spelling, complete official logo, all repeated merchant names, dimmed wallet background, success receipt and reminder screen. OCR can help find remnants but does not replace visual inspection.
- Compare the copy with the source for page count/order, typography, phones, alignment, crops and untouched content. Confirm logos are not stretched and longer names are not cramped. Preserve the latest source typography and grey backgrounds.
- Save the actual Canva copy, observing any approval required by the current tool. Do not report a draft, generated asset, old JSON snapshot or preview-only transaction as saved. Re-read the final saved copy after the last mutation. Never use another route to evade a denied action.
- Open the new deck in Canva and provide its direct edit link. Mention any unresolved asset or blocked check plainly. Retain final assets and the change map in the task workspace so targeted corrections are possible.

“Done” means a usable **separate Canva deck**, with the new client identity present in native content, all relevant screenshot pixels, and the real website image—not merely a folder of generated images.
