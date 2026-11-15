---
name: falai-ad
description: End-to-end workflow for producing a short product video ad (Instagram Reels / YouTube Shorts) with fal.ai for images and video and Sarvam for voiceover. Use when the user wants a product ad, reel, short, promo video, or any stage of one (brief, script, voice, character, environment, key image, direction, final video). Every stage ends with a human approval gate.
---

# falai-ad: product video ad workflow

Seven stages, in order. **Each stage ends with explicit human approval.** Never move to the next stage, or spend money, on an assumption. Keep all approved decisions in a running `ad-brief.md` in the project (product, brief, script, voice, character, environment, image, direction, final video) so later stages and later sessions can build on them.

**Money rule:** every paid call (fal.ai image or video, Sarvam TTS, paid scraping, etc.) and every setting that changes the price (model, resolution, duration, audio, number of outputs, retries) follows `.claude/skills/paid-action-approval/SKILL.md`: confirm the real price for the exact settings, offer a cheaper option, and wait for a yes. A pricing API's base `unit_price` is not a quote. Wan 3.0 Prime showed "$0.05/s" but bills $0.28/s at 1080p.

---

## 1. Product and reel briefs → approval

- Ask for the product: name, what it is, its key features or USP, target audience, platform (Instagram Reels / YouTube Shorts), language (English / Hindi / Hinglish), length (e.g. 5, 10 or 15 s), tone, and any product photos.
- Propose **3 short briefs**, each with: hook (first 1–2 s), core message, mood or tone, call to action, format (9:16 vertical, length).
- Wait for the user to pick or edit one. Record it as **Approved brief**.

## 2. Voice and ad script → approval

- Write the script to fit the approved length. Speech runs at roughly 2.3–2.8 words per second; leave about 0.3 s of silence at the start and end.
- Shortlist 3 voices that fit the language and tone. Sarvam `bulbul:v4-flash` ad personas work well: `shubh_en_ads`, `simran_en_ads`, `shubh_enhi_ads` (Hinglish), `ishita_hi_ads`, `sunny_hi_reels`, and others. On `bulbul:v3`: `priya`, `kabir`, `shreya`. Use `sarvam_code_speakers` for the full list.
- Short TTS samples cost a little. State that and get an OK, then generate them and send all of them to the user.
- Tune the length with `pace` (about 0.9–1.4) or small script edits. Check the duration with Python's `wave` module or `ffprobe`.
- Wait for approval of **voice + script**. Record both and the sample file path.

## 3. Character(s) → variations → approval

- Decide whether the ad needs a person or mascot at all (product-only can be the right call). Propose **3 character concepts**: who they are, look, wardrobe, age range, energy, and how they interact with the product.
- Describe them in text first (free). Only generate preview images after a price-approved go-ahead.
- Wait for the user to pick or edit. Record the **Approved character(s)**.

## 4. Environment → variations → approval

- Propose **3 environment concepts**: setting, lighting, colour palette (complementing the product), props, time of day, and the mood they set.
- Same rule: text first, paid previews only with approval.
- Wait for approval. Record the **Approved environment**.

## 5. Key image (fal.ai) → approval

- Combine product + character + environment into one key image or first frame, in the final aspect ratio (9:16 for Reels/Shorts).
- Model choice: use fal `recommend_model` (image-edit / reference-based generation when the real product photo must be preserved). Then **check the model page's price for the exact settings**, show the options (e.g. resolution, number of images) with confirmed prices, and get approval.
- Upload local images with `upload_file` (`prepare_upload`), then PUT the bytes. The environment must allow `v3b.fal.media` and `v3.fal.media`.
- Inspect the result against the real product: shape, colour, logo, material. Show it to the user; regenerate only with fresh approval of the cost.
- Wait for approval of the **key image**. Record its URL and local path.

## 6. Director's treatment → variations → approval

Act as a professional commercial director. Give **2–3 treatments**, each with:

- A shot list with timing that adds up to the approved length (e.g. 0–1.5 s hook, 1.5–4 s feature reveal, 4–5 s product hero + CTA).
- Camera: shot size, angle, movement (slow push-in, orbit, 360° spin, dolly, static), and lens feel.
- Subject and product action, and how the character interacts with the product.
- Lighting, colour grade, pacing and transitions.
- Sync points: which voiceover words land on which shot.
- The resulting video-model motion prompt (concise, specific, with "product design, colour and shape stay exactly the same").

Wait for approval of the **treatment and the final motion prompt**.

## 7. Video generation (fal.ai) → approval → final

- Inputs: the approved key image (start frame, plus an end frame or references if the model supports them), the approved motion prompt, length, and aspect ratio.
- Model choice: `recommend_model` (`image-to-video` or `reference-to-video`). Turn off the model's own audio when we add the Sarvam voiceover. For 2–3 suitable models, look up **real prices for the exact resolution and duration on each model page**. Present them with a cheaper option (720p is usually right for Reels/Shorts drafts; 1080p only if chosen), and wait for a yes.
- Submit once with a `submission_key`, then `wait_for_jobs`. Never resubmit to check status.
- Download the result, inspect a frame contact sheet for product fidelity, and show the user.
- Add the approved voiceover locally with ffmpeg (free):
  `ffmpeg -i video.mp4 -i voice.wav -filter_complex "[1:a]adelay=300|300,apad,atrim=0:<len>,afade=t=out:st=<len-0.2>:d=0.2[a]" -map 0:v -map "[a]" -c:v libx264 -crf 20 -pix_fmt yuv420p -c:a aac -b:a 160k -movflags +faststart -t <len> final.mp4`
  Optional: background music at a low level (about -20 dB under the voice). Generating music is a paid step and needs approval.
- Report the **actual cost** of every paid step. Flag any difference from the quote.
- Commit the final MP4 and `ad-brief.md`.

---

## Gate checklist (all need a human yes)

1. Brief
2. Voice + script (and the cost of TTS samples)
3. Character(s)
4. Environment
5. Key image: model, settings and price; then the image itself
6. Director's treatment + motion prompt
7. Video: model, resolution, duration and price; then the final cut
