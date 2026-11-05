# Build Android APK for Regain Clone

## Configuration Files Created

| File | Purpose |
|------|---------|
| `app.json` | Expo config with Android permissions (accessibility, overlay, usage stats) |
| `eas.json` | EAS Build profiles for development/preview/production APKs |
| `package.json` | Dependencies including expo-accessibility-service, expo-overlay |

## Quick Start (5 minutes)

### 1. Install EAS CLI
```bash
npm install -g eas-cli
eas login
```

### 2. Create Expo Project
```bash
eas project:init
```

### 3. Build Preview APK
```bash
eas build --platform android --profile preview
```

### 4. Download APK
After build completes (~5-10 min), you'll get a link like:
```
https://expo.dev/accounts/your-account/projects/regain-clone/builds/abc123/artifacts/regain-clone.apk
```

## Android Permissions Included

The APK will request these permissions at runtime:
- **BIND_ACCESSIBILITY_SERVICE** - Detect YouTube Shorts/Reels/TikTok
- **SYSTEM_ALERT_WINDOW** - Floating focus bubble overlay
- **PACKAGE_USAGE_STATS** - Track daily app usage
- **FOREGROUND_SERVICE** - Persistent timer notification
- **RECEIVE_BOOT_COMPLETED** - Restart services on reboot
- **POST_NOTIFICATIONS** - Motivational guilt-trip notifications

## What's in the APK

| Screen | Feature |
|--------|---------|
| Home | Dashboard, quick stats, start focus CTA |
| Focus Timer | 25-min Pomodoro with circular progress, pause/resume/break |
| Block | Toggle Instagram, YouTube Shorts, TikTok + custom domains |
| Stats | Weekly usage charts (placeholder data) |
| Profile | Settings, daily reset time config |

## Important Notes

1. **Accessibility Service**: After installing the APK, user must manually enable:
   `Settings → Accessibility → Regain Clone → Allow`

2. **Overlay Permission**: Must grant "Display over other apps" for floating bubble

3. **Usage Stats**: Must grant "App usage access" for tracking

4. **iOS Limitations**: True overlay blocking not possible on iOS (Apple restriction)

## For Production Release

```bash
eas build --platform android --profile production
eas submit --platform android
```

Requires Google Play Console service account key.