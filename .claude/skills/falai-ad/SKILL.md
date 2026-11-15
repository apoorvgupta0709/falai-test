---
name: falai-ad
description: End-to-end workflow for producing a short product video ad (Instagram Reels / YouTube Shorts, including Amazon affiliate content) with fal.ai for images and video and Sarvam for voiceover. Use when the user wants a product ad, reel, short, promo video, or any stage of one (brief, script, voice, character, environment, key image, direction, final video). Every stage ends with a human approval gate.
---

# falai-ad: product video ad workflow

Seven stages, in order. **Each stage ends with explicit human approval.** Never move to the next stage, or spend money, on an assumption. If the user skips a question (e.g. language), state the assumption, mark it "to confirm", and ask again at the next gate.

**Money rule:** every paid call (fal.ai image or video, Sarvam TTS, Firecrawl scrapes, etc.) and every setting that changes the price (model, resolution, duration, audio, number of outputs, retries) follows `.claude/skills/paid-action-approval/SKILL.md`. Confirm the real price for the exact settings, offer a cheaper option, and wait for a yes. A pricing API's base `unit_price` is not a quote. Wan 3.0 Prime showed "USD 0.05/s" but bills USD 0.28/s at 1080p.

**Writing prices in this skill:** write "USD 0.03", never a dollar sign followed by a digit. Skill arguments replace `$0`, `$1`… with the user's input.

## Project layout and record-keeping

One folder per ad, committed and pushed after every stage:

```
ads/<ad-name>/
  ad-brief.md      # stage status table, every approved decision, review notes, spend log
  product.webp     # the user's product photo
  voice/           # TTS samples and the approved take
  previews/        # character / environment previews
  keyimage/        # key image versions (v1, v2, ...)
  video/           # raw model output and the final cut
```

`ad-brief.md` holds:
- a **stage status table** (✅ approved / ⏳ in review)
- each approved decision in full: brief, script, voice file, character and environment descriptions, key image path and URL, motion prompt, overlays
- **review notes** for every generated asset (✅ / ⚠️ / ❌ per issue)
- a **spend log** table: step | model | settings | quoted | actual

Rejected or failed attempts go in the log too, with a note on whether they may have been charged.

## Showing media to the user

The user may not see inline previews. With every generated image or video:
- send the file with `SendUserFile`
- also give the **direct fal URL**
- give the repo path

## Compliance (affiliate and safety)

- **Affiliate disclosure:** an on-screen "#ad" tag for the whole clip, plus "#ad / affiliate link" in the caption.
- **Call to action:** "Link in bio" or a pinned comment; description links in Shorts and Reels often can't be clicked.
- **No price claims** in the video.
- **Branding:** show the real product as-is. Frame the ad as a creator recommendation, not an official brand ad. No other brands or logos (e.g. a phone maker's logo) in generated images.
- **Riding or vehicle scenes:** helmets on, the driver's hands on the controls. Only a passenger or a bystander holds the product.

---

## 1. Product and reel briefs → approval

- Ask for:
  - the exact product name and model
  - key features to push
  - audience
  - platforms
  - language: English, Hindi or Hinglish
  - length: 5, 10 or 15 s
  - tone
  - product photos (a clean cutout works best)
  - whether they're an authorised seller or affiliate
- List the features you can **see** in the photo and ask the user to confirm them. Never invent specs.
- Propose **3 short briefs** with: hook (first 1–2 s), core message, mood, call to action, format (9:16, length). If the user wants a different angle (e.g. "show a biker and stabilisation"), propose a fresh set of 3–5 briefs.
- Record the **Approved brief**.

## 2. Voice and ad script → approval

**Script**
- About 2–2.5 words per second. A 5 s ad fits about 9–12 words, starting at 0.3 s.
- Put the product name in the line when the user asks for product focus.
- **Spell out digits in product names** ("Osmo Eight P", not "8P") so the TTS reads them correctly.

**Voices**
- Shortlist 2–3 Sarvam `bulbul:v4-flash` personas that fit the tone and language:
  - Ads: `shubh_en_ads`, `simran_en_ads`, `shubh_enhi_ads` (Hinglish)
  - Reels: `sunny_hi_reels`, `ritu_hi_reels`
  - High energy / sports: `ratan_hi_sports`, `ashwin_en_sports_energetic`
- Use `sarvam_code_speakers` for the full list. Hinglish in Roman script works with `target_language_code: en-IN`.
- **Cost:** Sarvam bills per character, and the exact v4-flash rate isn't published. Quote the character count (e.g. 3 × 65 = 195 chars) and get an OK before generating.

**Energy and timing**
- Exclamation marks and a pace of 1.2–1.25 add energy, but they also add pauses after each phrase.
- Fix the length for free with ffmpeg instead of paying for another take:
  - Tighten pauses: `silenceremove=start_periods=1:start_threshold=-40dB:stop_periods=-1:stop_duration=0.12:stop_threshold=-40dB:stop_silence=0.1`
  - Speed up a little without changing pitch: `atempo=1.05–1.1`
- Check duration with `ffprobe`. Measure phrase timings with `silencedetect=n=-35dB:d=0.06`; they're needed for sync in Stage 6.

Send all samples. Record the **approved voice file**, the line, pace and edits.

## 3. Character(s) → variations → approval

- Decide whether a person is needed. Propose **3 concepts**: who they are, look, wardrobe, age, energy, and how they interact with the product.
- Adjust in text first (e.g. "make her jazzy and glamorous": keep it tasteful and keep safety gear on).
- **Previews** (only with a price-approved go-ahead):
  - **Characters only, no props or vehicles**, full-body, plain studio backdrop, helmets off so faces and hair show.
  - **One image per character**, so each is shown in detail.
  - Seedream 4 text-to-image (`fal-ai/bytedance/seedream/v4/text-to-image`, USD 0.03/image) gave clean results. It returns 1152×2048 even for the `portrait_16_9` preset, billed per image.
  - Flux Schnell (USD 0.003/MP) is cheaper but gets hands and props wrong.
- Record the **approved characters** with preview paths and fal URLs; Stage 5 uses them as references.

## 4. Environment → variations → approval

- Propose **3 environments**: setting, light, palette (complementing the product and wardrobe), props (no real brand text), mood.
- Text first; paid previews only with approval.
- Note what AI video can do: keep the action to one clear event (e.g. a single pothole bump). Chaotic or multi-event motion tends to fail.
- Record the **approved environment**.

## 5. Key image (fal.ai) → approval

This becomes the video's first frame: 9:16 at the final framing.

**Pass 1: compose**
- Use a multi-reference edit model with the **product photo + character previews** as references.
- Seedream 4 Edit (`fal-ai/bytedance/seedream/v4/edit`, USD 0.03/image) composes scenes well, but it **did not copy the product faithfully** and left an extra hand.
- Upload the local product photo with `upload_file` (`prepare_upload`), then PUT the bytes. The environment must allow `v3b.fal.media` and `v3.fal.media`.

**Inspect before showing**
- Crop and zoom on the product, hands, faces and any logos.
- Check against the real product photo: shape, colour, parts, materials.
- Count hands and arms per person.
- Check that faces aren't hidden (visors, scarves).
- Look for stray brands.

**Pass 2: targeted fix (do this instead of regenerating)**
- Feed the good image back in with the product photo. List **only** the changes, and ask for everything else to stay the same.
- **Nano Banana 2 Edit** (`fal-ai/nano-banana-2/edit`, USD 0.08/image at 1K, 9:16) fixed what Seedream couldn't: it matched the product exactly and removed an extra hand. Its output was 768×1376, still above 720p vertical.
- If the same model fails at the same problem twice, stop. Offer the user a different model or approach with prices; never keep paying for retries.

Record every version with review notes, and the **approved key image**.

## 6. Director's treatment → variations → approval

Act as a commercial director. Give **2–3 treatments**, each a **single continuous shot from the key image**: image-to-video starts from that frame, and cuts mean paying for extra clips. Each treatment has:
- a shot list with timing that adds up to the length
- **sync points from the measured voice timings** (e.g. "Osmo Eight P!" 0.3–1.1 s)
- camera move and lens feel
- the action, showing the product benefit visually (e.g. bike jolts, gimbal stays level)
- light and grade
- a concise motion prompt that ends with: *"The product's design, colour and shape stay exactly the same; faces and clothes unchanged; the driver keeps both hands on the controls; no new logos or text."*

Ask for the phone or product screen to show the scene (e.g. "the phone screen shows the rider"). State the risk of each treatment; complex multi-event motion is likely to fail. Record the **approved treatment, motion prompt and overlays**.

## 7. Video generation (fal.ai) → approval → final

**Inputs and settings**
- Start frame: the approved key image. Prompt: the approved motion prompt. Length: 5 s (or as approved). Aspect: 9:16.
- Turn the model's own audio **off**. **Drafts are always 480p.**

**Model choice: realistic people**
- **ByteDance Seedance (2.x / 2.5) rejected a photorealistic AI-generated start image with people in it** ("content_policy_violation: may contain likenesses of real people"). Don't use Seedance image-to-video for realistic human characters.
- Never resubmit a rejected input. Fal's Seedance docs say 422 client errors **are charged**, so report it as possibly charged.
- **Wan 3.0 Prime** (`alibaba/wan-3.0-prime/image-to-video`) accepted the same image. It held the product design, and the push-in ended on a clean product hero shot. Its prices, from the model page, per second:

  | Resolution | USD per second |
  |---|---|
  | 480p | 0.068 |
  | 720p | 0.14 |
  | 1080p | 0.28 |

  It outputs 30 fps; at 480p, 9:16 is 480×854.

**Seedance pricing, if used for non-human scenes**
- Tokens = height × width × fps × seconds ÷ 1024, at 24 fps. This was verified against the Seedance 2.0 720p rate of USD 0.3034/s.
- 480p is about 9,700 tokens/s, so 5 s is about 48,500 tokens. Multiply by the per-1,000-token rate from `get_pricing`.

**Running and checking**
- Present 2–3 models with **verified** 480p prices; mark any price you couldn't confirm.
- Submit once with a `submission_key`, then `wait_for_jobs`. Never resubmit to check status.
- Download the result. Inspect a 6-frame contact sheet for product fidelity, hands, faces and the key action.

**Final cut (ffmpeg, free)**
- Voice from 0.3 s: `[1:a]adelay=300|300,apad,atrim=0:<len>,afade=t=out:st=<len-0.2>:d=0.2[a]`
- Overlays with `drawtext` (font `/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf`):
  - "#ad": small, top-left, the whole clip
  - "<Product> · Link in bio": from the "Link in bio" line onward, with a short fade-in. **Keep it clear of the product** in the hero shot.
- Encode: `-c:v libx264 -crf 20 -pix_fmt yuv420p -c:a aac -b:a 160k -movflags +faststart -t <len>`

**Report and finish**
- Report the **actual cost** of every paid step and the running total. Flag any difference from the quote.
- Offer:
  - free fixes (overlay position or wording, voice timing)
  - a 720p final at a verified price (a new generation, so motion will differ)
  - keeping the 480p draft
- Commit the final MP4 and `ad-brief.md`.

---

## Gate checklist (all need a human yes)

1. Brief (and confirmed product features)
2. Voice + script (and the character cost of TTS samples)
3. Character(s), with optional paid previews
4. Environment
5. Key image: model, settings and price; then each fix; then the image itself
6. Director's treatment + motion prompt + overlays
7. Video: model, resolution, duration and price; then the final cut, and any 720p final
