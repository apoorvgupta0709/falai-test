---
name: paid-action-approval
description: Required before ANY action or decision that costs the user money or has commercial implications — paid AI generation (fal.ai, Sarvam, OpenArt, Firecrawl, Apify, etc.), choosing a model/resolution/duration/quality tier, retries or variations, buying credits, or anything billed per use. Get a verified price and explicit approval first.
---

# Paid action approval

The user must explicitly approve every decision that spends money or changes what they will be charged. This covers more than "should I run it": the settings that drive cost need approval too.

## When this applies

- Any paid generation or API call: image, video, audio, TTS, 3D, LLM, scraping or search credits.
- Choosing the **model, resolution, duration, quality tier, audio on/off, number of outputs, or upscaling**. These change the price, so each one is a commercial decision.
- Retries, variations, re-renders, "one more try", batch jobs.
- Anything that buys credits, subscribes, or changes billing or accounts.
- Paid lookups made on the side, such as Firecrawl scrapes. Say they cost credits before running them.

Free, local work (ffmpeg, file edits, git) needs no approval.

## Before asking: verify the real price

1. A pricing API's base `unit_price` is **not** a quote. Rates often vary by resolution, duration, audio or quality. (Lesson learned: Wan 3.0 Prime showed "USD 0.05/second", but 1080p actually bills USD 0.28/s, so a 5s clip cost **USD 1.40**, not the USD 0.25 that was quoted.)
2. Check the model's own pricing page or docs for the **exact settings** you plan to use (resolution, duration, audio, etc.).
3. If the price for those settings can't be confirmed, say so plainly and give a range or the worst case. Never present an unverified number as the cost.

## How to ask

Present, then wait for an explicit "yes" before spending:

- What will run (model / endpoint) and why.
- The exact settings that affect cost.
- **Verified total cost** for those settings, with the source (e.g. the model page).
- At least one cheaper option when there is one (e.g. 720p or 480p, a shorter clip, a cheaper model), with its price.
- Default to the cheapest setting. **Drafts and previews are always 480p** (or the model's lowest tier). Go higher only for an approved final, and only if the user picks it.

An earlier approval covers only that exact job. A new job, a retry, or changed settings needs a new approval.

## After spending

Report what actually ran and its cost. If the billed amount differs from the quote, say so and explain why.
