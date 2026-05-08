# CycleMatix Privacy Policy

_Last updated: 2026-05-08_

CycleMatix is a single-developer cycling tracker for Android. This document
explains what the app collects, why, and what you can do about it.

## TL;DR

- All your ride data lives **on your phone**. We don't run a server. We don't
  see your rides, your routes, your sensors, your GPS coordinates, or
  anything else recorded by the app.
- The app uses third-party services **only when you explicitly opt in**:
  Mapbox (maps), Strava (import / upload), Google Drive (import / backup).
  Each of those gets only what's needed for that feature.
- You can delete every byte the app stored, on-device, with one tap. There
  is nothing on a server to "request deletion of."

## Who we are

CycleMatix is built and operated by Rok Jenko, a single developer based in
Slovenia, EU. Contact: rok.jenko@hycu.com.

## What CycleMatix collects

| | Where it's stored | When we transmit it |
|---|---|---|
| GPS coordinates during a ride | On your device, in a local SQLite database | Never — unless you tap "Export to Strava" or back up to your own Drive |
| BLE sensor readings (power, HR, cadence) | Same | Same |
| Settings (FTP, weight, paired sensors, app preferences) | On your device, in shared_preferences | Never |
| Strava OAuth token (if you connected Strava) | flutter_secure_storage on your device | Used only when you import / push rides to Strava |
| Google Drive OAuth token | Same | Used only when you import / back up to your own Drive |
| Mapbox API key | Same | Used to fetch map tiles from Mapbox during normal use |

## Third parties

- **Mapbox** — provides map tiles. When you view a map, your approximate
  GPS location is sent to Mapbox's servers to fetch the right tiles. This
  is unavoidable for any map-rendering library.
- **Strava** — only if you connect your account. We use Strava's OAuth
  (the same flow you'd see on any third-party Strava app).
- **Google Drive** — only if you connect your account, for ride imports
  and optional encrypted backups.
- **Sentry** — receives crash reports. We send only the stack trace, app
  version, OS version, and device model. **No GPS, no ride data, no
  personal info.** You can opt out in Settings.

These are the only third parties. There is no analytics, no ad network,
no tracking SDK. We do not sell, share, or transmit your data anywhere
else.

## Permissions

| Permission | Why |
|---|---|
| Fine + background location | Recording GPS during a ride, including with screen off. Stays on the device. |
| Bluetooth scan / connect | Pairing power meters, HR straps, cadence sensors. |
| Foreground service | Keeps GPS recording running while the screen is locked. |
| Notifications | Active-ride status notification (so Android doesn't kill the recorder). |
| Internet | Map tiles, optional Strava / Drive sync, optional Mapbox routing. |

## Your rights

Under GDPR (EU) and CCPA (California):

- **Access** — your data is on your phone. Open the app to see it.
- **Erasure** — Settings → Storage → Delete all my data. Wipes the
  SQLite database, all settings, all OAuth tokens, all offline maps.
  The action is irreversible.
- **Portability** — every ride can be exported as `.fit`, `.gpx`, or
  `.json` from the ride detail screen.
- **No sale** — we don't sell your data. We have no business model that
  would benefit from selling data; CycleMatix is a one-time-purchase app.
- **Contact** — rok.jenko@hycu.com for any data request.

## Children

CycleMatix is not directed at users under 13. We don't knowingly collect
data from children.

## Changes

If this policy changes, the new version will be posted at this URL with
an updated "Last updated" date. Material changes will be announced
in-app.

## Legal basis

Under GDPR Art. 6:
- Legitimate interest (Art. 6.1.f) for crash reporting (Sentry).
- Performance of contract (Art. 6.1.b) for Strava / Drive integration
  when you've connected those services.
- All other processing is local-only and does not constitute "processing"
  under the GDPR's transmission definition.
