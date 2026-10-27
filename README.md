# Stream sales demo skills

Reusable AI instructions for researching a SaaS prospect, building a tailored billing demo, and adapting a Stream Canva presentation.

These skills capture the reusable workflow from previous demo projects. They contain no client conversations, credentials, account records, private source decks, or client-specific implementation files.

## What is included

- **[stream-client-demo](skills/stream-client-demo/SKILL.md)** — research the client, choose a credible pricing story, recreate its product experience, connect an authorized sandbox, and prepare the presenter handoff.
- **[stream-client-deck](skills/stream-client-deck/SKILL.md)** — copy an existing Stream deck, personalize native content and screenshots, and verify the saved result.

## Use with your AI

Download this repository and place the two skill folders in your AI tool’s skill directory, or attach the relevant `SKILL.md` and references to the task. In Codex, the user skill directory is `~/.codex/skills/`.

Give the AI the client’s official website, the source presentation, the requested language and the authorized sandbox account. Then ask:

> Use stream-client-demo and stream-client-deck to research this client, build a tailored website demo, and create a separate copy of the presentation. Keep existing work intact. Verify the live customer journey and the saved slides. Keep credentials server-side and label proposed pricing in the presenter notes.

Start with [Stream’s API documentation](https://docs.streampay.sa/) for current integration details. Tool access and sandbox credentials are supplied separately; this repository does not grant access.

## Delivery standard

The client’s product names, terminology and buying journey should be recognizable. Show one relevant customer journey end to end. Keep proposed prices separate from published prices. Verify the real embedded checkout, consumer portal, invoices and any usage meters before describing them as working.

Publishing a demo, making payments, or contacting a prospect requires the user’s authorization for that action.
