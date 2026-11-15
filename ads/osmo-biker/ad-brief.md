# Ad brief: Osmo Mobile 8P, "Pillion Cinematographer"

Workflow: `.claude/skills/falai-ad/SKILL.md`

| Stage | Status |
|---|---|
| 1. Brief | ✅ Approved |
| 2. Voice + script | ✅ Approved |
| 3. Character(s) | ✅ Approved (Seedream previews locked) |
| 4. Environment | ✅ Approved |
| 5. Key image | ✅ Approved (v3) |
| 6. Director's treatment | ✅ Approved (Treatment 1) |
| 7. Video | ⏳ 480p draft in review |

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

## Stage 5: key image
- **v1:** `keyimage/key-v1-seedream4edit.jpg` (Seedream 4 Edit, seed 886229388, 1152×2048). Refs: product photo, rider preview, pillion preview.
  - ✅ Environment, pillion look, red helmet, rider's hands on bars, front wheel over potholes, dust.
  - ❌ Gimbal is generic (thin black stick); doesn't match Osmo 8P. ❌ Pillion has 3 hands (gimbal hand plus both hands on his shoulders). ❌ Rider's face hidden (goggle visor down, buff over mouth).
- **v2 (targeted fix):** `keyimage/key-v2-seedream4edit-fix.jpg` (Seedream 4 Edit, seed 416658939). Refs: v1, product photo.
  - ✅ Rider's visor up, buff down, bearded face visible. ✅ Rest of scene preserved.
  - ⚠️ Gimbal closer (grey handle, folding silver arm, phone clamp, light) but not faithful: thin silver arm, light on top instead of a tracking module under the phone, handle not the thick dark-grey Osmo grip.
  - ❌ Pillion still has 3 hands.
- **v3 (Nano Banana 2 Edit fix):** `keyimage/key-v3-nanobanana2-fix.jpg` (768×1376, 1K, 9:16). Refs: v2, product photo.
  - ✅ Gimbal matches Osmo 8P: dark-grey handle with logo, angled arm, silver joint, phone clamp, tracking module under phone. ✅ Pillion has 2 hands. ✅ Rider's face visible. ✅ Scene preserved.
  - ⚠️ Phone screen shows the tennis image from the product photo, not the rider. ⚠️ Lower resolution (768×1376), still above 720p vertical.

## Stage 6: director's treatment (approved): Treatment 1, "Glide Alongside"
- 0–1.2 s: low tracking shot in front of the bike; she raises the gimbal ("Osmo Eight P!" 0.3–1.1 s)
- 1.2–2.4 s: front wheel drops into a pothole, dust, riders jolt; gimbal head and phone stay level ("Kahin bhi, kaise bhi…" 1.3–2.3 s)
- 2.4–3.8 s: slow push-in to the gimbal; phone screen shows a steady shot of the rider ("bilkul stable!" 2.5–3.6 s)
- 3.8–5 s: product-hero framing, prayer flags, snow peaks ("Link in bio!" 3.8–4.5 s)
- **Motion prompt:** Smooth low tracking shot moving backward in front of the motorbike as it rides toward camera on a rocky Himalayan gravel road. At about 1 second the front wheel drops into a pothole: dust and gravel kick up, suspension compresses, both riders jolt. The woman's raised arm bounces, but the smartphone gimbal head and phone stay perfectly level and steady, stabilised. The camera then slowly pushes in toward the gimbal; the phone screen shows a steady video of the rider. Prayer flags flutter, she laughs, he smiles. The rider keeps both hands on the handlebars. The gimbal's design, colour and shape stay exactly the same; faces and clothes unchanged; no new logos or text.
- **Overlays (ffmpeg, free; defaults, user can change):** "#ad" for the whole clip; "Osmo 8P · Link in bio" from 3.8 s.

## Stage 7: video
- **Attempt 1:** Seedance 2.5 Flash i2v, 480p, 5 s, audio off, start frame key v3. **Declined by the model's safety system** (content_policy_violation on `image_url`: "may contain likenesses of real people"). No video produced. Request ID 01a1e0ec-420c-7283-a1e1-b1eace298c1e.
- **Attempt 2 (draft):** Wan 3.0 Prime i2v, 480p (480×854, 30 fps), 5 s, 9:16, audio off, seed 275635521. Raw: `video/raw-wan30prime-480p.mp4`.
  - ✅ Bike approaches and kicks up dust over the broken road; push-in ends on a product hero shot; gimbal design held (handle, arm, joint, clamp, tracking module); phone screen shows the couple; faces and outfits consistent.
  - ⚠️ The pothole jolt is mild (more dust than bounce).
- **Draft cut:** `video/osmo-biker-ad-draft-480p.mp4`: Ratan voiceover from 0.3 s, "#ad" top-left throughout, "Osmo 8P · Link in bio" from 3.8 s (ffmpeg, free).

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
| Key image v1 | fal-ai/bytedance/seedream/v4/edit | 1 × portrait_16_9 (1152×2048), 3 refs | USD 0.03 | USD 0.03 (per-image rate; not yet seen on dashboard) |
| Key image v2 (fix) | fal-ai/bytedance/seedream/v4/edit | 1 × portrait_16_9, 2 refs | USD 0.03 | USD 0.03 (per-image rate) |
| Key image v3 (fix) | fal-ai/nano-banana-2/edit | 1 × 1K, 9:16, 2 refs | USD 0.08 | USD 0.08 (per-image rate; not yet seen on dashboard) |
| Video attempt 1 (declined) | bytedance/seedance-2.5/flash/image-to-video | 480p, 5 s | ≈ USD 0.68 | No output. Possibly charged: fal's Seedance 1.0 docs say 422 client errors are charged; check dashboard |
| Video draft (Wan 3.0 Prime) | alibaba/wan-3.0-prime/image-to-video | 480p, 5 s, audio off | USD 0.34 (USD 0.068/s per model page) | USD 0.34 expected; confirm on dashboard |
