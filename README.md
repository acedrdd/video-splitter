# Video Splitter

Cut a long video into equal-length clips, right in your browser or on your phone. Nothing is uploaded: your video never leaves your device.

Splitting is lossless (no re-encoding), so it is fast and keeps full quality. It runs [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) locally, using the same `-c copy` segment method as the ffmpeg command line.

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
| `package.json` | Pulls in ffmpeg.wasm and Capacitor |
| `capacitor.config.json` | Android app settings |
| `.github/workflows/build.yml` | Builds the site, deploys Pages, and builds the APK |

## Limits

- Cuts snap to the nearest keyframe, so clips can be off by a second or two.
- The video is loaded into memory, so files over about 1 GB may fail, especially on phones. For very large files, use ffmpeg in Termux or on a computer:

```
ffmpeg -i input.mp4 -c copy -f segment -segment_time 1200 -reset_timestamps 1 clip_%03d.mp4
```

- The APK is a debug build, not signed for the Play Store.

## Built with

[ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm), [Capacitor](https://capacitorjs.com), and GitHub Actions.
