# My Buddy — Mobile Lab

This repository is the **separate Android on-device benchmark app** extracted from My Buddy V6.3. It is not the full My Buddy PWA/Personal AI Agent.

## Scope
- Kotlin Android benchmark app for importing compatible local model files.
- Hindi/Hinglish, tool-intent, multi-step planning, coding, hallucination, in-conversation memory and speed/RAM suites.
- Python dataset validation, scoring and comparison tools.
- GitHub Actions debug APK build.

## Important limitations
- This is a diagnostic/benchmark prototype, not the full My Buddy assistant or an Android automation agent.
- Model weights are not bundled; import them manually from their upstream source.
- Tool-call benchmark entries validate proposed JSON only. They do not execute shell, browser, file or phone actions.
- The debug APK is unsigned and is not a Play Store release.
- Realme 8 compatibility, model inference, memory use and thermal stability require physical-device testing.

## Add the source package once
The source package is intentionally separate from the larger private My Buddy workspace. Download the small source archive `mybuddy_mobile_lab_source.zip` from the ChatGPT conversation, then upload it to this repository at:

`source-v6.3/mybuddy_mobile_lab_source.zip`

Create the `source-v6.3` folder when uploading. Do not upload the 47 MB full V6.3 workspace here; this public repository is only for the standalone benchmark lab. The archive contains source and benchmark datasets, not model weights or signing secrets.

## Build the APK
After the source archive is committed:
1. Open **Actions**.
2. Select **Build My Buddy Mobile Lab**.
3. Press **Run workflow** on branch `build/v6.3-mobile-lab`.
4. Download the `mybuddy-mobile-lab-debug-apk` artifact when the workflow succeeds.

The workflow verifies the archive, runs the Python benchmark tests and dataset validator, then runs `gradle :app:assembleDebug`. A failed build is not reported as an APK.

## Local commands
From the extracted archive directory:

```bash
python -m unittest discover -s benchmark_kit/tests -v
python benchmark_kit/validate.py validate
gradle --no-daemon :app:assembleDebug
```

The full PWA, Node gateway, own-model training workspace and private notes are intentionally excluded from this public repository.
