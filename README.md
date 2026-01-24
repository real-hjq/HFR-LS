# HFR-LS: High Frame Rate Live Streaming Dataset

## 📖 Overview

**HFR-LS (High Frame Rate Live Streaming Dataset)** is a large-scale
subjective video quality dataset designed to study the perceptual
trade-offs between **compression strength and frame rate under
bitrate-constrained live streaming scenarios**.

This dataset accompanies the paper:

> **Subjective Evaluation of Frame Rate in Bitrate-Constrained Live
> Streaming**\
> Jiaqi He, Zhengfang Duanmu, Kede Ma\
> *IEEE International Conference on Acoustics, Speech, and Signal
> Processing (ICASSP), 2026*

HFR-LS provides high-quality source videos and systematically encoded
representations at multiple bitrates and frame rates, together with
**subjective Difference Mean Opinion Scores (DMOS)** collected under
standardized viewing conditions.

------------------------------------------------------------------------

## 🖼️ Dataset Preview

Sample frames from the HFR-LS dataset (corresponding to Fig.1 in the
paper):

![Sample frames from HFR-LS](assets/HFR-LS_samples.png)

This figure illustrates diverse content covering: 
- Camera motion and static scenes
- Low to high spatial complexity
- Low to high temporal activity

------------------------------------------------------------------------

## 🎬 Source Content

-   **32 high-quality source sequences**
-   Originally captured at **120 fps**
-   Converted to **1920×1080, YUV 4:2:0, 8-bit**
-   Duration: **5 seconds per clip**
-   Content sources:
    -   22 from **BVI-HFR**
    -   5 from **UVG**
    -   5 from **LIVE-YT-HFR**

Content diversity is characterized using **Spatial Information (SI)**
and **Temporal Information (TI)** according to ITU-T P.910.

------------------------------------------------------------------------

## ⚙️ Encoded Representations

Each source video is encoded using **H.264 (x264)** at fixed 1080p
resolution under realistic live-streaming constraints.

-   **Target Bitrates:** 5, 7, 10, 15 Mbps
-   **Frame Rates:** 30, 60, 120 fps
-   **Total Representations per Source:** 12
-   **Total Processed Videos:** 32 × 12 = **384 clips**

### Encoding Ladder

  Bitrate   Frame Rates
  --------- -------------------
  5 Mbps    30 / 60 / 120 fps
  7 Mbps    30 / 60 / 120 fps
  10 Mbps   30 / 60 / 120 fps
  15 Mbps   30 / 60 / 120 fps

### FFmpeg Encoding Command

``` bash
ffmpeg -f rawvideo -s:v 1920x1080 -r 120 -pix_fmt yuv420p -i input.yuv        -r <fps> -c:v libx264 -preset fast -tune zerolatency        -b:v <bitrate> -an output.mp4
```

Frame rate down-conversion is performed via frame dropping.

------------------------------------------------------------------------

## 👥 Subjective Study

-   **Protocol:** Single-stimulus with hidden reference
-   **Scale:** Continuous quality scale \[0--100\]
-   **Participants:** 30 naïve subjects (after outlier removal: 26
    valid)
-   **Display:** 120 Hz calibrated monitor (ITU-R BT.500 compliant)
-   **Viewing distance:** \~1.5H

### Subjective Scores

-   **MOS** collected for each video
-   **DMOS** computed relative to corresponding reference
-   DMOS range: **0 -- 47**
-   Mean DMOS: **8.57**
-   Inter-subject consistency: **PLCC ≈ 0.91**

All subjective scores are provided with the dataset.

------------------------------------------------------------------------

## 📊 Key Findings Enabled by HFR-LS

-   Frame rate significantly affects perceived quality under fixed
    bitrate.
-   Strong interaction between **bitrate × frame rate × content**.
-   Higher frame rates may degrade spatial quality at insufficient
    bitrate.
-   Existing VQA models struggle with varying frame rate conditions.

------------------------------------------------------------------------

## 📂 Dataset Structure

    HFR-LS/
    ├── source_videos/
    ├── encoded_videos/
    │   ├── 5Mbps_30fps/
    │   ├── 5Mbps_60fps/
    │   ├── ...
    ├── subjective_scores/
    │   ├── MOS.csv
    │   ├── DMOS.csv
    │   └── subject_raw_scores.csv
    ├── metadata/
    │   ├── SI_TI.csv
    │   └── content_info.csv
    └── assets/
        └── HFR-LS_samples.png

------------------------------------------------------------------------

## 📥 Download

Dataset available at:

Test videos: [Google Drive](https://drive.google.com/file/d/13FkO-KrlbtRxYOyHj5UxsKv6CvP9PBis/view?usp=sharing)
    
Reference videos: [Google Drive](https://drive.google.com/file/d/1KEj2mgn0RyfQrnstTyR_Pf34SB89kfuS/view?usp=drive_link)
    
------------------------------------------------------------------------

## 📚 Citation

``` bibtex
@inproceedings{He2026HFRLS,
  title={Subjective Evaluation of Frame Rate in Bitrate-Constrained Live Streaming},
  author={He, Jiaqi and Duanmu, Zhengfang and Ma, Kede},
  booktitle={IEEE International Conference on Acoustics, Speech, and Signal Processing (ICASSP)},
  year={2026}
}
```

------------------------------------------------------------------------

## 📧 Contact

**Jiaqi He**\
Department of Computer Science, City University of Hong Kong\
Email: jiaqhe5-c@my.cityu.edu.hk

------------------------------------------------------------------------

## 🏁 License

This dataset is released for **research purposes only**.\
Please refer to the LICENSE file for detailed usage terms.
