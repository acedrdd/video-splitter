<p align="center"><img src="logo.svg" width="112" alt="Video Splitter logo"></p>

# Video Splitter

Cut a long video into equal-length clips, right in your browser or on your phone. Nothing is uploaded: your video never leaves your device.

Splitting is lossless (no re-encoding), so it is fast and keeps full quality. It uses a small built-in MP4/MOV cutter written in plain JavaScript (no ffmpeg, no downloads), which copies the video and audio samples between keyframes without re-encoding. The Auto clip tab finds standout moments from the audio (pauses and energy) and cuts them the same way.

## Features

- Split a video into clips of any length (quick buttons for 10, 13, 15, 20 and 30 minutes)
- Live film-strip preview showing where each cut will land
- Automatically merges a tiny leftover last clip into the clip before it
- Download each clip on its own, or all at once
- Light and dark mode with a toggle button
- Works as a website (GitHub Pages) and as an Android APK
- The APK works offline and saves clips to `Documents/VideoSplitter`

## Use it

**Website:** open your GitHub Pages link, choose a video, set the clip length, and tap **Split video**.

**Android APK:** open the **Actions** tab, open the latest run, and download `VideoSplitter-apk` from **Artifacts**. Unzip it and install `app-debug.apk`. Android will ask you to allow installs from unknown sources, because this is a debug build.

## Set up your own copy

1. Fork or copy this repo to your GitHub account.
2. Go to **Settings > Pages** and set the source to **GitHub Actions**.
3. Push to `main`, or run the workflow by hand from the **Actions** tab.
4. When the run finishes, the website is live and the APK is under **Artifacts**.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole app (page, styles and logic) |
| `package.json` | Pulls in Capacitor |
| `capacitor.config.json` | Android app settings |
| `.github/workflows/build.yml` | Builds the site, deploys Pages, and builds the APK |

## Limits

- Cuts snap to the nearest keyframe, so clips can be off by a second or two.
- Works with MP4 and MOV videos (what phones record). Other formats such as MKV or WebM are not supported; for those use ffmpeg in Termux or on a computer:

```
ffmpeg -i input.mp4 -c copy -f segment -segment_time 1200 -reset_timestamps 1 clip_%03d.mp4
```

- The APK is a debug build, not signed for the Play Store.

## Built with

[Capacitor](https://capacitorjs.com), and GitHub Actions.
