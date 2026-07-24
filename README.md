# Rekounts speech models

This repository is the **model distribution host** for [Rekounts](https://github.com/rekreatedigital/rekounts) — free, open-source, privacy-first voice dictation for Windows. There is no code here: the [release assets](https://github.com/rekreatedigital/rekounts-models/releases) are the speech-model files the app downloads on first use.

## Whose models are these?

Not ours, and we don't claim otherwise:

- The models are **[Whisper](https://github.com/openai/whisper)**, created and released by **OpenAI** under the MIT license.
- The files served here are **[Systran's faster-whisper conversions](https://github.com/SYSTRAN/faster-whisper)** of those models to the CTranslate2 format, also MIT-licensed.

Both licenses permit redistribution; the required notices ship as `LICENSE-MODELS.txt` alongside every release, and in the app repo at [docs/model-license.md](https://github.com/rekreatedigital/rekounts/blob/master/docs/model-license.md).

## Why does this repo exist?

So the app never has to contact any third-party host at runtime. Rekounts downloads a model **once**, from here, and verifies every file against a SHA-256 hash pinned in [the app's source](https://github.com/rekreatedigital/rekounts/blob/master/rekounts/models.py) before using it — a corrupted or tampered download is rejected. After that one download the app is fully offline.

Assets are published with [`scripts/publish_models.py`](https://github.com/rekreatedigital/rekounts/blob/master/scripts/publish_models.py), which fetches the upstream files, verifies them against the same manifest, and uploads them here.

| Model | Size | Notes |
| --- | --- | --- |
| `base` | ~148 MB | Fastest on any CPU |
| `small` | ~486 MB | The app's default |
| `medium` | ~1.5 GB | Most accurate offered |

## Questions or issues?

Please use the **[app repository](https://github.com/rekreatedigital/rekounts/issues)** — this repo only hosts files.
