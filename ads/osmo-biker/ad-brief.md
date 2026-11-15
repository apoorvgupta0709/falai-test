# Ad brief: Osmo Mobile 8P, "Pillion Cinematographer"

Workflow: `.claude/skills/falai-ad/SKILL.md`

| Stage | Status |
|---|---|
| 1. Brief | ✅ Approved |
| 2. Voice + script | ✅ Approved |
| 3. Character(s) | ✅ Approved (Seedream previews locked) |
| 4. Environment | ✅ Approved |
| 5. Key image | ⏳ In review |
| 6. Director's treatment | — |
| 7. Video | — |

## Product
- **Name:** DJI Osmo Mobile 8P (user-supplied name; specs not independently verified)
- **Photo:** `product.webp` (clean cutout: gimbal with phone, detachable screen remote, tracking module with fill light)
- **Purpose:** Amazon affiliate content
- **Audience:** vloggers, travellers (biker / road-trip angle)
- **Platforms:** Instagram Reels + YouTube Shorts (9:16)
- **Key feature to show:** stabilisation, no blur

## Approved brief: E, "Pillion Cinematographer"
- **Hook (0–2 s):** the pillion rider swings the gimbal out sideways and the frame glides alongside the rider like a film tracking shot.
- **Core message:** anyone on the back seat becomes a pro camera operator.
- **Mood:** cinematic, golden hour, friendship and road-trip energy.
- **Call to action:** "Apne riding buddy ko DOP bana do. Link in bio."
- **Length:** 5 seconds, 9:16.
- **To confirm:** motorbike (assumed). Language: Hinglish (accepted).

## Stage 2: script and voice (approved)
- **✅ Final voice:** `voice/ratan_hi_sports_tight.wav`: Ratan (`ratan_hi_sports`, bulbul:v4-flash), pace 1.2, pauses tightened to ~0.1 s, 4.22 s.
- **Final line:** "Osmo Eight P! Kahin bhi, kaise bhi... bilkul stable! Link in bio!"
- **Script:** "Osmo Eight P. Kahin bhi, kaise bhi... bilkul stable. Link in bio." ("Eight" spelled out so the voice says it correctly)
- **Energetic take (pending approval):** `voice/sunny_hi_reels_energetic_final.wav` (4.43 s): Sunny, line with "!", pace 1.25, pauses tightened to ~0.1 s and sped up 8% with ffmpeg. Raw take: `voice/sunny_hi_reels_energetic.wav` (5.36 s).
- **Sports candidates (pending):** `voice/ratan_hi_sports_tight.wav` (4.22 s), `voice/ashwin_en_sports_energetic_tight.wav` (4.32 s): same line, pace 1.2, pauses tightened (raw takes alongside).
- **Earlier candidates (male):** `voice/shubh_enhi_ads.wav` (3.63 s), `voice/sunny_hi_reels.wav` (3.80 s), both bulbul:v4-flash, pace 1.1

## Stage 3: characters (approved): Concept 2, "Road-Trip Couple"
- **Who:** couple, late 20s, travel creators.
- **Rider:** male, grey touring jacket, full-face helmet, both hands on the bars, classic cruiser-style motorbike (no real brand logos).
- **Pillion:** female creator, red riding jacket, open-face helmet with sunglasses, big smile; holds the Osmo 8P out to the side, filming the rider and the view.
- **Product moment:** close-up of her hand on the gimbal; the remote's screen shows a steady shot.
- **Look:** B, "Rugged Tourers" (pending sign-off after preview). Rider: about 30, heavy stubble, charcoal-grey adventure jacket with reflective strips, grey neck buff, scuffed black full-face helmet, visor up. Pillion: about 28, red-and-black textile jacket, black open-face helmet, wraparound sunglasses, curly hair.
- **Preview:** `previews/character-lookB-schnell.jpg` (Flux Schnell, seed 549141296). Artifacts: the pillion has a third hand, and the gimbal looks like a bare phone.
- **Revised pillion ("jazzy"):** about 26, glamorous, fitted cropped red leather biker jacket with silver zips open over a black top, black high-waist jeans, glossy red open-face helmet, long wavy hair, oversized mirrored gold sunglasses, red lipstick, gold hoops, playful smile. Preview: `previews/character-lookB-jazzy-schnell.jpg` (seed 1690421495).
- **User note:** must show a bumpy Indian road (taken forward to Stage 4).

## Character previews: Seedream 4 (no props, studio)
- Rider: `previews/character-rider-seedream4.jpg` (seed 1218036513)
- Pillion: `previews/character-pillion-seedream4.jpg` (seed 1531317186)
- Side-by-side: `previews/characters-side-by-side.jpg`
- Output was 1152×2048 even though the `portrait_16_9` preset was requested (billed per image).

## Stage 4: environment (approved): Option 3, "Himalayan Broken Stretch"
- **Setting:** high mountain gravel road with rocks and washed-out, bumpy broken sections; snow peaks, prayer flags, a small stream crossing.
- **Light:** late afternoon, crisp sun, deep blue sky.
- **Palette:** cool blues and browns with bright prayer-flag colours; the red jacket and red helmet pop.
- **Props:** prayer flags, stone cairns, a BRO-style road sign (no real brand text).

## Model choices (user)
- **Stage 5 key image:** Seedream 4 Edit (`fal-ai/bytedance/seedream/v4/edit`), USD 0.03/image per fal pricing API (re-verify on model page before generating).
- **Stage 7 video:** Seedance family (exact endpoint + 480p draft price to be confirmed at Stage 7).

## Compliance notes
- Safety: the rider rides with both hands and a helmet; only the pillion holds the gimbal.
- Affiliate disclosure (#ad / affiliate link) goes in the caption, plus an optional on-screen tag.
- CTA points to link in bio / pinned comment. No price claims.
- Show the product as-is; framed as a creator recommendation, not an official DJI ad.

## Spend log
| Step | Model | Settings | Quoted | Actual |
|---|---|---|---|---|
| Voice samples | Sarvam bulbul:v4-flash | 2 × 65 chars | ~150 chars approved (rate unconfirmed) | 130 chars |
| Energetic re-take | Sarvam bulbul:v4-flash | 1 × 65 chars, pace 1.25 | ~65 chars quoted | 65 chars |
| Sports voice samples | Sarvam bulbul:v4-flash | 2 × 65 chars, pace 1.2 | ~130 chars quoted | 130 chars |
| Character preview, Look B | fal-ai/flux/schnell | 1 × 576×1024 (rounds up to 1 MP) | USD 0.003 | USD 0.003 (per docs rate; not yet seen on dashboard) |
| Character preview, Look B jazzy | fal-ai/flux/schnell | 1 × 576×1024 (rounds up to 1 MP) | USD 0.003 | USD 0.003 (per docs rate) |
| Character previews (rider + pillion) | fal-ai/bytedance/seedream/v4/text-to-image | 2 × portrait_16_9 (returned 1152×2048) | USD 0.06 | USD 0.06 (per-image rate; not yet seen on dashboard) |
