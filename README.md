# ytmp3 — MP3 → MP4 (black card) for YouTube

I love YouTube to share and archive projects. However, sometimes my projects are audio only, but YouTube is still by far the best way to store them and share them with anyone. It's just the most accessible.

But how do you turn those MP3 files into MP4 so YouTube will take them? You could open a video editor and render everything… and that’s just annoying.

So I made a shell script you can run and boom: transform any MP3 into an MP4 with a black screen and centered text.

**Happy YouTube-ing!!!**

---

## What it does

- Creates a **1080p black video** with your **title** centered (and an optional **subtitle**).
- Encodes **fast**: hardware H.264 on Mac (VideoToolbox), or ultrafast x264 fallback.
- Optimized: renders the text **once** to a PNG, then loops it (way faster than drawing every frame).
- Output is YouTube-friendly: H.264/AAC, yuv420p, `+faststart`.

## Requirements

- `ffmpeg`  
  - macOS (Homebrew): `brew install ffmpeg`
  - Linux: use your package manager or static build

## Install

### Quick local install (no sudo)

```bash
mkdir -p "$HOME/bin"
curl -fsSL https://raw.githubusercontent.com/jdcampolargo/ytmp3/main/ytmp3 -o "$HOME/bin/ytmp3"
chmod +x "$HOME/bin/ytmp3"
# add to PATH if needed
case ":$PATH:" in *":$HOME/bin:"*) ;; *) echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc; export PATH="$HOME/bin:$PATH";; esac
```

Prefer another location? Drop it in /usr/local/bin or /opt/homebrew/bin (may require sudo).

### Usage
```
ytmp3 "audio.mp3" "Title"
ytmp3 "audio.mp3" "Title" "Optional subtitle"
ytmp3 "audio.mp3" "Title" "Subtitle" "MyVideo.mp4"  # custom output name
```

### Why is it fast?

	•	Renders text once to a PNG and loops it.
