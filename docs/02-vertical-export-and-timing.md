# 9:16 export, beat placement and safe zones

Generated clips usually come out as a vertical MP4 without sound (so you can add the trending track inside TikTok or Reels and get attributed to that sound). These are the numbers for turning that file into a post that does not lose quality or hide the payoff behind UI.

## 1. Frame sizes

| Platform | Canvas | Notes |
|---|---|---|
| TikTok | 1080 × 1920 (9:16) | 720 × 1280 is accepted and displayed full-screen |
| Instagram Reels | 1080 × 1920 (9:16) | Grid preview crops to 3:4 (1080 × 1440) from the centre |
| YouTube Shorts | 1080 × 1920 (9:16) | Up to 3 minutes; vertical or square |

A 720p vertical clip is 720 × 1280. Upload it as-is. Upscaling to 1080 × 1920 in an editor does not add detail; it only raises bitrate. If your editor exports at 1080 × 1920 anyway, that is fine — just do not stack several re-encodes.

## 2. Safe zones on a 1080 × 1920 canvas

Platform UI covers parts of the frame. The exact overlay changes with app versions, so treat these as conservative margins:

| Region | Approx. pixels | Covered by |
|---|---|---|
| Top | 0–~220 px | status bar, "Following / For You", search |
| Bottom | ~1500–1920 px (bottom ~20%) | caption, username, music ticker |
| Right | ~950–1080 px (right ~12%) | like / comment / share / sound column |
| Reels grid | outside the centre 1080 × 1440 | cropped in profile grid |

Keep captions and anything you want read inside roughly **x 60–940, y 260–1480**. For 720 × 1280 multiply by 2/3 (x 40–627, y 173–987).

## 3. Placing the beat

A 15-second zombie couple clip follows a fixed story: standoff → the turned partner leaps → turns back mid-leap → embrace → cut to a happy memory. The emotional peak is the turn back and the memory cut, not the first second.

Beat maths for lining up a song:

```
seconds per beat  = 60 / BPM
beats in N seconds = N × BPM / 60
bars (4/4)        = beats / 4
```

| BPM | Seconds per beat | Beats in 15 s | Bars in 15 s |
|---|---|---|---|
| 70 | 0.857 | 17.5 | 4.4 |
| 80 | 0.750 | 20 | 5 |
| 90 | 0.667 | 22.5 | 5.6 |
| 100 | 0.600 | 25 | 6.25 |
| 120 | 0.500 | 30 | 7.5 |

Slow, sad trending tracks are usually 60–90 BPM, so the whole clip is only 4–6 bars. Practical method:

1. Scrub the clip and note the second where the face turns back and where the memory cut happens.
2. In the app's sound editor, slide the song start (do not trim the video) so the song's drop or key line lands on that moment.
3. Leave the memory ending intact; it is the payoff that gets rewatches.

## 4. Export settings if you edit outside the app

If you add text or the song in a desktop editor before uploading:

| Setting | Value |
|---|---|
| Container | MP4 |
| Video codec | H.264 High profile (HEVC is accepted, H.264 is safest) |
| Resolution | same as source (720 × 1280) or 1080 × 1920 |
| Frame rate | same as source; do not convert 24 → 30 or 30 → 60 |
| Bitrate | 8–12 Mbps for 720p, 12–20 Mbps for 1080p (VBR) |
| Keyframe interval | 1–2 s |
| Audio | AAC-LC, 44.1 or 48 kHz, 128–320 kbps, stereo |
| Colour | Rec.709, 8-bit SDR |

ffmpeg example (add a song and burn nothing in):

```bash
ffmpeg -i clip.mp4 -i song.m4a -map 0:v -map 1:a \
  -c:v libx264 -profile:v high -crf 18 -preset slow -pix_fmt yuv420p \
  -c:a aac -b:a 192k -shortest -movflags +faststart out.mp4
```

Or keep the video stream untouched and only add audio:

```bash
ffmpeg -i clip.mp4 -i song.m4a -map 0:v -map 1:a -c:v copy -c:a aac -b:a 192k -shortest -movflags +faststart out.mp4
```

## 5. Upload hygiene

- Upload the downloaded MP4 itself, not a screen recording (screen recording re-encodes, adds UI and often drops frames).
- If you use the platform's in-app sound for attribution, upload the silent clip and add the sound in the app.
- Check the first frame: it becomes the default cover on some platforms. Pick a cover where both faces are visible.
