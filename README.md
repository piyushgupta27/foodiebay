# foodiebay

An Android app that finds **food trucks near you on a map** — built in **2015** as my take-home for a **HyperTrack** interview. It became my way in: the solution converted into the offer.

I keep it public on purpose. It's early-career work, and that's the point — a marker of where I started and how I thought about engineering a decade ago.

## What it does
Plots San Francisco's mobile food facilities (the public [DataSF permit dataset](https://data.sfgov.org/Permitting/Mobile-Food-Facility-Permit/rqzj-sfat)) on Google Maps, and helps you see what kinds of food trucks are likely near a given spot.

## How it was built (2015)
- **Android / Java**, `minSdk 16` / `targetSdk 23`.
- **Retrofit + Gson** for the DataSF API — clean async networking without boilerplate.
- **Google Maps + maps-utils marker clustering** — the dataset is ~700 facilities packed into a small area, so raw markers were a memory/perf problem; clustering fixed it.
- **Crashlytics (Fabric)** for crash reporting *(note: Fabric has since been sunset by Google)*.
- A splash-screen animation I was fond of — an idea I'd first shipped at Shuttl.

## Looking back — what I'd do differently today
Leaving the original code intact; the gap *is* the story. If I built this now:
- **Architecture** — MVVM + repository and a real state layer, not Activity-driven logic.
- **Language / async** — Kotlin + coroutines/Flow over Java + callbacks.
- **Secrets** — externalized from day one. The original hard-coded its API keys in `build.gradle`; that's fixed here (keys now read from a gitignored `gradle.properties`), and the old values are retired.
- **Testing / CI** — unit + UI tests and a pipeline, neither of which 2015-me wrote.
- **Resilience** — cache the dataset; degrade gracefully offline.

## Status
Not actively maintained — preserved as a historical artifact. Current work: **[piyushgupta.io](https://piyushgupta.io/)**.
