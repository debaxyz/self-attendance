# Self Attendance – React Native (Expo)

Exact design port of the original HTML Self Attendance app to **React Native + Expo**, supporting **Android** and **Web**. Design (colors, claymorphism, fonts, layout) is preserved as closely as possible.

## Features (same as original)

- Live clock + status (Not checked in / Checked in / Done / Leave)
- Day shift (9 AM – 6 PM) / Night shift (9 PM – 6 AM)
- Check in / Check out / Mark leave
- Late detection (30 min grace)
- Monthly stats: Present, Late, Leave, Hours, Day/Night shifts, Weekly off, Overtime
- Interactive calendar – tap any day to set Shift / OT / Leave / WO / Clear
- Recent days log
- Light / Dark theme toggle
- Data persisted with AsyncStorage (same key as original)

## Quick start

```bash
cd self-attendance
npm install
npx expo start
```

Then:

- Press `w` for **Web**
- Press `a` for **Android** emulator / device (or scan QR with Expo Go)

### Requirements

- Node.js 18+
- For Android: Android Studio / Expo Go app
- For Web: modern browser

## Project structure

- `App.tsx` – entire app (UI + logic)
- `app.json` – Expo config
- Uses `@expo-google-fonts/nunito` + `@expo-google-fonts/baloo-2`
- `@react-native-async-storage/async-storage` for persistence

## Notes

- Claymorphism shadows are approximated with React Native `elevation` / `shadow*` props (exact multi-layer inset shadows of CSS are limited on native).
- Fonts load asynchronously; a short “Loading…” screen appears until ready.
- Web uses the same codebase via `react-native-web`.

Design was intentionally left unchanged from the provided HTML.

## Build Android APK

### Recommended: EAS Build (cloud)

1. Install EAS CLI (once):
   ```bash
   npm install -g eas-cli
   ```

2. Login to your Expo account (free):
   ```bash
   eas login
   ```

3. Configure the project (first time only):
   ```bash
   eas build:configure
   ```

4. Build an APK (preview profile produces a downloadable APK):
   ```bash
   eas build -p android --profile preview
   ```

5. After the build finishes, download the `.apk` from the link shown in the terminal or from https://expo.dev.

**Notes**
- The `preview` profile in `eas.json` is set to produce an **APK** (not AAB).
- You need an Expo account (free tier is enough for personal builds).
- First build may take 10–20 minutes.
- Add a proper app icon later (`assets/icon.png` 1024×1024) and adaptive icon for better results.

### Local build (advanced)

If you have Android Studio + SDK installed:

```bash
npx expo prebuild
npx expo run:android --variant release
```

Or with EAS local:

```bash
eas build -p android --profile preview --local
```

(Requires Docker or proper Android build environment.)
