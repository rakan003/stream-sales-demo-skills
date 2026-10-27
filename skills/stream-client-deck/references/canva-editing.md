# Canva editing and delivery notes

Use purpose-built Canva tools where they fit, and native editor controls for precise layout or typography where needed. Tool availability and schemas vary; discover them in the active session. Follow current tool constraints and approval requirements. An old transaction ID, asset ID or element ID is not reusable authority for a new run.

## Copy, draft and saved state

- Copy first and retain the new design ID. Distinguish the live source, target copy and editing transaction.
- For transaction edits, retain the returned page map/transaction ID, perform the requested operations, review changed-page previews, and commit when authorized. If a current tool specifically requires post-preview approval, follow it. Discard unused read-only transactions explicitly.
- Avoid native edits to a design while an outstanding transaction could overwrite them. Finish or cancel that transaction first.
- After native edits, check Canva's saved indicator and re-read the resulting page. Do not equate an uploaded asset with a replaced asset on the slide.

## Native editor pitfalls observed in this workflow

- Identify actual rendered elements. Some accessibility “image” entries are navigation clones and do not select the visible image. Verify the selection toolbar or bounding box before copy, delete or formatting.
- A transparent image can intercept a title click. Select the intended object through **Position → Layers** instead of moving or deleting the covering object.
- In some numeric controls, automation's `fill()` appended digits instead of replacing them. Click the field, select all with the platform shortcut, type the complete value and confirm. Read back actual geometry afterward.
- **Lock aspect ratio before scaling an image.** Changing width and height separately while unlocked can resize the frame but leave the interior bitmap at its old size. Check the frame and visible artwork after scaling.
- Preserve visible artwork center/baseline, not just bitmap edges. Official logos can have large transparent or solid margins. Keep neighboring logos and captions fixed unless the requested change needs them moved.
- Replacing an image may alter its crop, fill transform or layering. Inspect the new screen within the phone rather than checking only the asset preview.
- Native text edits can resize boxes or reflow grouped captions. Compare the group's other members before and after.
- Do not paste blindly: confirm the intended object was copied and the destination page is active. If paste fails after deletion, restore the deleted object before another approach.

When an observed DOM selector or control label stops matching, inspect the current UI; do not hard-code old selectors or invent app internals. Browser automation should operate through documented tools and visible page/editor state.

## Preserve design roles

Client-name substitution should retain the current source's text style. Native Canva supports more precise font variants and tracking than some connector operations. Do not flatten Semibold into Bold or change font family to make a generic API operation fit.

Phone screenshots should replace their content image only. Keep phone frames, dimensions, position, border weight and shared alignment between slides. Keep other Stream graphics, partner logos, statistics, section dividers and page numbers as currently approved.
