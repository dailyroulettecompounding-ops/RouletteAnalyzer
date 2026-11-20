# Roulette Analyzer (Android)

An open-source, offline-first Android app for analysing manually entered European roulette results (single zero, 0–36).

## Features
- Manual number entry with 0–36 keypad
- Persistent local spin history using Android SharedPreferences
- Undo latest spin and clear history
- Custom two-column strategy:
  - Requires at least six recorded results
  - Compares the newest spin's column with the 6th previous spin's column (the oldest result in the six-spin window)
  - If the two eligible columns differ, both are displayed as the next-spin selection
  - If they are equal, the app waits and recalculates after the next spin
  - Zero in either comparison position produces WAIT; the rule recalculates after the next result
  - Each new spin settles the previously active prediction as hit/miss before recalculating
- Hot/cold number frequency rankings
- European wheel neighbours of latest result
- Red/black/green and odd/even counts
- Dozens, columns and streets
- Split-bet analysis using adjacent numbers on the standard 3-column betting layout
- Prediction performance tracking
- CSV export via Android share sheet

## Build APK
1. Install Android Studio (Hedgehog or newer) and Android SDK Platform 35.
2. Open this project folder in Android Studio.
3. Let Gradle sync complete.
4. Select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. Debug APK output: `app/build/outputs/apk/debug/app-debug.apk`.

Command line (with Android SDK and Gradle installed):
```bash
gradle assembleDebug
```

## Open-source license
MIT. See `LICENSE`.

## Notes and limitations
- No network permission or server is required.
- Data is stored locally on the device. Clearing app data/uninstalling removes it.
- Frequency and pattern analysis describes historical observations only. Roulette spins are independent; this app does not guarantee or establish future outcomes.
- The two-column strategy is implemented as specified; zero is treated as a non-column and causes WAIT when it occupies either comparison position.
