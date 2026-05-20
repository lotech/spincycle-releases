# SpinCycle

A native macOS Swift app that converts video files as well as allowing to create seamless looping videos.

## How looping works

1. **Trim** — Removes the first N seconds of the input (default 4s) to cut encoding noise
2. **Split** — Calculates a cut point at N% of the remaining duration (default 5%) and splits the video into Part A (start→cut) and Part B (cut→end)
3. **Reassemble** — Joins as B+A with a crossfade at the seam (default 1s) using FFmpeg's `xfade` filter
4. **Encode** — Outputs using the selected codec with configurable quality

The result is a video that loops seamlessly — the end fades into the beginning.

## Features

- Drag-and-drop interface for single or batch video files
- Configurable settings: trim start, cut percentage, crossfade duration, CRF quality
- **Match Source** toggle — re-encodes using the same codec as the input file
- Multiple output codecs: H.264, HEVC, ProRes (LT / 422 / 4444), HAP (+ Alpha, Q), DXV
- Automatic fallback to H.264 if the chosen codec fails
- Output alongside source files by default, or pick a custom output folder
- Per-file progress bar during encoding

## Requirements

- macOS 14.0 (Sonoma) or later
