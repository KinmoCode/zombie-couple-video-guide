# Matching two separate photos

Two solo photos become one scene. The model has to place both people in the same space, under the same light, seen by the same camera. Every difference between the two inputs is something it has to guess, and faces are where wrong guesses show.

## 1. Shot size and face resolution

What matters is **pixels across the face**, not the file's megapixels.

| Source | Typical face height in pixels |
|---|---|
| Front-camera selfie, 12 MP, arm's length | 1,200–1,800 px |
| Rear camera, 12 MP, person at 2 m, head-and-shoulders | 900–1,400 px |
| Rear camera, 12 MP, full body at 4 m | 250–400 px |
| One face cropped from a 10-person group photo | often 100–200 px |
| Photo saved from a messaging app (re-compressed, ~1600 px long edge) | 300–600 px |

Rules of thumb:

- Aim for **≥ 300 px** chin-to-hairline in each input. Below ~150 px, likeness is mostly invented.
- Make the face occupy a **similar share of the frame** in both photos — around 30–45% of the image height works well for head-and-shoulders crops.
- Crop, do not upscale. Cropping a wide photo down to head-and-shoulders keeps its real face pixels; a 4× "AI upscale" adds texture that the video model then animates as if it were real detail.
- Keep the long edge ≥ 1024 px after cropping if you can, but face pixels win over total pixels.

## 2. Camera height and angle

- **Eye level for both.** A selfie held above the head (looking down) shortens the chin and enlarges the forehead; a photo from below enlarges the jaw and nostrils. Mixed, they read as two different cameras.
- **Face turned ≤ ~30°.** Three-quarter views are fine. Near-profile views give the model half a face for a clip where the head turns toward the camera.
- **Head tilt under ~15°.** Strong tilts get "straightened" and the face is redrawn.

## 3. Lens distance (perspective)

Perspective is set by camera **distance**, not by zoom. At arm's length (0.4–0.6 m), the nose is proportionally ~10–30% closer to the lens than the ears, so it renders larger and the ears recede. At 1.5–3 m, the difference is a few percent.

- Best: both photos taken by someone else from **1.5–3 m**, or with the phone's **2×/3× lens** from a step back.
- Acceptable: **both** selfies. The distortion at least matches.
- Worst: one close selfie + one portrait from 2 m. One face will look wider and rounder than the other in the shared scene.

## 4. Light

| Property | What to match | How to check |
|---|---|---|
| Direction | Brighter side of the face on the same side in both, or both frontal | Cover one half of the face with your thumb, compare brightness |
| Softness | Both soft (shade, overcast, window) or both hard (direct sun) | Hard light = sharp-edged nose shadow |
| Colour temperature | Similar skin tone | Put the two photos side by side on the same screen |
| Exposure | No clipped highlights on forehead / cheeks | Phone editor "highlights" warning, or zoom to 100% |

Approximate colour temperatures you will meet in phone photos:

| Light | Approx. Kelvin | Skin looks |
|---|---|---|
| Household tungsten / warm LED bulb | 2700–3000 K | orange |
| Golden hour sun | 3000–4000 K | warm |
| Midday sun | 5000–5500 K | neutral |
| Overcast sky | 6000–7000 K | slightly cool |
| Open shade, blue sky | 7000–10000 K | blue |

Phone cameras auto white-balance, so the file is usually closer to neutral than the table, but a bulb-lit evening photo next to a shade photo still differs clearly. Correct one with the warmth/temperature slider until skin tones match before uploading. Do not use colour filters to do it.

Avoid: midday top light (black eye sockets — the zombie gets empty eyes, then the "turn back" looks like someone else), strong backlight (dark, noisy face), coloured party lights.

## 5. Expression, hair, clothes

- Neutral or a small closed-mouth smile. Big laughs make teeth and lips hard to keep stable through the snarl-and-back transition.
- Hair away from the eyes. Fringe over the eyes is often redrawn.
- Clothes usually carry over (torn and dusty on the zombie). Plain clothes survive better than large logos or text, which get warped.

## 6. Pets as the one who turns

- Photograph at the pet's eye level, head filling a good part of the frame, eyes open.
- Daylight. Warm indoor light shifts fur colour, and the model may "correct" it into a different coat.
- Avoid photos from above (mostly forehead and back) — the leap toward the camera needs a frontal face.
- Long-haired pets: a photo where the eyes are visible matters more than sharpness of the fur.

## 7. Pre-upload checklist

1. One person (or pet) per photo; group shots cropped to one face and saved as a new file.
2. Face ≥ 300 px tall in both; similar share of the frame.
3. Both at eye level, both from a similar distance.
4. Face angle ≤ 30°, nothing covering it, no beauty filter.
5. Same light side and softness; skin tones matched.
6. Neutral face or small smile.
