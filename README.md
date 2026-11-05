<p align="center"><img src="logo.svg" width="128" alt="Video Splitter logo"></p>

<h1 align="center">Video Splitter</h1>

<p align="center">Cut long videos into clips, by length or automatically.<br>Free, private, and it runs entirely on your device.</p>

---

## What it does

**Quick split** cuts a video into equal clips. Pick a length, check the preview, tap **Split video**.

**Auto clip** finds the standout moments in a long video for you. It listens for natural pauses, builds 20 to 60 second candidates that start and end on a pause, scores them by energy and delivery, and cuts the best ones.

Nothing is uploaded. No account, no API key, no ads.

## Features

- Split into clips of any length, with quick buttons for 10, 13, 15, 20 and 30 minutes
- Live film-strip preview that shows where each cut will land
- Merges a tiny leftover last clip into the clip before it (you choose how short counts as tiny)
- Auto clip: finds up to 15 standout moments by itself
- Lossless cuts: no re-encoding, so it is instant and keeps full quality
- Download clips one by one, or all at once
- Side menu (the burger button) with separate pages for Quick split, Auto clip and Downloads
- Downloads page: every clip you cut is listed one by one as it is made, with filters, totals and a live progress card, and the history is kept between visits
- Android app: each clip is saved automatically as it is cut, and a notification shows what is being cut or saved
- Light and dark mode
- Works as a website and as an Android app
- The Android app works offline and saves clips to `Documents/VideoSplitter`

## How to use it

1. Open the site or the app and choose a video.
2. **Quick split:** set the clip length and tap **Split video**.
3. **Auto clip:** switch to the **Auto clip** tab and tap **Find and cut clips**.
4. Download the clips you want.

**Android app:** open the **Actions** tab, open the latest run, and download `VideoSplitter-apk` from **Artifacts**. Unzip it and install `app-debug.apk`. Android will ask you to allow installs from unknown sources, because this is a debug build.

## Good to know

- Works with **MP4 and MOV** videos, which is what phones record. MKV and WebM are not supported.
- Cuts snap to the nearest keyframe, so a clip can start or end a second or two away from the exact time.
- Auto clip chooses moments by how the audio sounds (pauses, energy, delivery), not by what is said. Treat its picks as a good first guess and check them.
- For other formats, ffmpeg does the same job on a computer or in Termux:

```
ffmpeg -i input.mkv -c copy -f segment -segment_time 1200 -reset_timestamps 1 clip_%03d.mkv
```

## Set up your own copy

1. Fork or copy this repo to your GitHub account.
2. Go to **Settings > Pages** and set the source to **GitHub Actions**.
3. Push to `main`, or run the workflow by hand from the **Actions** tab.
4. When the run finishes, the website is live and the APK is under **Artifacts**.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole app: page, styles and logic |
| `logo.svg` | The logo |
| `package.json` | Pulls in Capacitor and its Filesystem and Local Notifications plugins |
| `capacitor.config.json` | Android app settings |
| `.github/workflows/build.yml` | Builds the site, deploys Pages, and builds the APK |

## Built with

[Capacitor](https://capacitorjs.com) and GitHub Actions.
