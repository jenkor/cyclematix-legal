---
title: CycleMatix — Data Deletion
---

# CycleMatix — How to delete your data

_Last updated: 2026-06-02_

CycleMatix is a local-first cycling tracker for Android, built by Rok Jenko,
an independent developer based in Slovenia, EU. The app does **not** run a
server. Everything the app records lives on your phone, so deleting your data
is something you do directly in the app — there is nothing on a server for us
to delete.

## TL;DR

- Open **CycleMatix → Settings → Storage → "Delete all my data"**.
- One tap wipes every ride, route, workout, sensor reading and setting from
  your device.
- Uninstalling the app also removes all of its on-device data.
- We hold nothing on a server. There is no account to close.

## Delete everything from your phone

1. Open **CycleMatix**.
2. Go to **Settings**.
3. Open the **Storage** section.
4. Tap **"Delete all my data"** and confirm.

This permanently removes, from your device:

- All recorded rides, including GPS tracks and every per-second sample
  (power, heart rate, cadence, speed, elevation).
- All saved routes, planned routes and workouts.
- Your bike profiles and app settings.
- Any stored Strava and Google sign-in tokens.
- The encrypted-backup passphrase, if you set one.

The deletion is immediate and cannot be undone.

## Optional cloud backups (Google Drive)

If — and only if — you turned on **encrypted Drive backup**, CycleMatix
stored backup files in the hidden _app-data folder_ of **your own** Google
Drive. We never see these files and cannot read them: they are encrypted on
your phone with a passphrase only you hold.

To remove them:

1. In CycleMatix, open **Settings → Cloud backup** and **disconnect**.
   Disconnecting clears the stored passphrase and the Drive sign-in token
   from your phone.
2. To delete the backup files themselves, browse the backups from
   **Settings → Cloud backup → Browse**, or remove the app's data from your
   Google account at
   [myaccount.google.com → Data & privacy → Third-party apps](https://myaccount.google.com/connections).

## What we keep

Nothing. CycleMatix has no server, no analytics database, and no user
accounts. We do not retain any copy of your rides, routes, sensors or
identity. Crash diagnostics (if you have them enabled) are anonymised and
contain no ride data. Once you delete on-device data and disconnect any
optional cloud backup, no CycleMatix-held copy of your data remains, because
none ever existed off your device.

## Contact

Questions about deleting your data, or want to confirm a deletion?
Email **cyclematix@gmail.com** and we'll help.
