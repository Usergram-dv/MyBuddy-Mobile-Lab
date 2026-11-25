# My Buddy — Mobile Lab

This repository contains the **separate Android Mobile Benchmark Lab** extracted from My Buddy V6.3. It is not the full My Buddy PWA/Personal AI Agent.

## What is built here
- Android Kotlin app for importing compatible local model files and running on-device benchmark cases.
- Versioned Hindi/Hinglish, planning, tool-intent, coding, hallucination, memory and speed/RAM benchmark suites.
- Python benchmark validation and comparison tools.
- GitHub Actions workflow that builds a debug APK and runs the benchmark-kit unit tests.

## Important limitations
- The APK is a diagnostic/benchmark prototype. It is not the full My Buddy assistant or a general-purpose Android automation agent.
- No AI model weights are bundled. Models are imported manually by the user.
- No network, microphone, camera, contacts or broad storage permission is declared by the Android app.
- The GitHub Actions APK is an unsigned debug build; it is not a Play Store release.
- Physical-device behavior, especially on Realme 8, must be tested separately.

## Source archive
To keep this public repository small and avoid committing generated checkpoints or personal workspace logs, the reviewed Mobile Lab source is stored as split ZIP parts under `source-v6.3/`. The workflow concatenates and verifies the archive, then extracts it into `V5_Mobile_Lab/` for the build.

## Build
Open **Actions → Build My Buddy Mobile Lab** and run the workflow, or push changes to the build branch. On success, download the `mybuddy-mobile-lab-debug-apk` artifact from the workflow run.

## Local commands
From the extracted `V5_Mobile_Lab/` directory:

```bash
python -m unittest discover -s benchmark_kit/tests -v
gradle --no-daemon :app:assembleDebug
```

## Source status
The source archive is derived from the V6.3 Mobile Lab folder. The full My Buddy PWA and research workspace are intentionally not included in this public repository.
