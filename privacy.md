# CycleMatix Privacy Policy

_Last updated: 2026-05-08_

CycleMatix is a single-developer cycling tracker for Android. This document
explains what the app collects, why, and what you can do about it.

## TL;DR

- All your ride data lives **on your phone**. We don't run a server. We
  don't see your rides, your routes, your sensors, your GPS coordinates,
  or anything else recorded by the app.
- The app uses third-party services **only when you explicitly opt in**:
  Mapbox (maps), Strava (import / upload), Google Drive (import / encrypted
  backup). Each of those gets only what's needed for that feature.
- We do not run any analytics. We do not run any crash-reporting. There
  is no advertising SDK in the app.
- You can delete every byte the app stored, on-device, with one tap.
  There is nothing on a server to "request deletion of."

## Who we are

CycleMatix is built and operated by Rok Jenko, an independent developer
based in Slovenia, EU. Contact: jenkocoban@gmail.com. This email is also
the single point of contact under Article 12 of Regulation (EU) 2022/2065
(the Digital Services Act).

## What CycleMatix collects

| Data | Purpose | Legal basis (GDPR Art. 6) | Where it lives | Recipients | Retention |
|---|---|---|---|---|---|
| GPS coordinates during a ride | Record the ride | Contract — Art. 6(1)(b) | On your device, local SQLite DB + JSON blobs | None unless you export | Until you delete it |
| BLE sensor readings (power, HR, cadence) | Record the ride | Contract — Art. 6(1)(b) | Same | None unless you export | Until you delete it |
| Settings (FTP, weight, units, paired sensor IDs, theme, preferences) | Run the app | Contract — Art. 6(1)(b) | shared_preferences on your device | None | Until you delete it |
| Trial state (timestamp of first ride, ride count, extension flag) | Decide whether you're inside the free-trial window | Contract — Art. 6(1)(b) | shared_preferences | None | Wiped by Settings → Delete all my data |
| Approximate location for map tile fetches | Render the map you're looking at | Contract — Art. 6(1)(b) | Sent to Mapbox per render | Mapbox Inc. (US) | Mapbox's logs (see their policy) |
| Strava OAuth token | Push / import rides if you connect Strava | Consent — Art. 6(1)(a) | flutter_secure_storage (Android Keystore) | Strava Inc. (US) when you sync | Until you disconnect or wipe |
| Google Drive OAuth token | Backup / import via your own Drive | Consent — Art. 6(1)(a) | flutter_secure_storage (Android Keystore) | Google LLC (US) when you sync | Until you disconnect or wipe |
| Mapbox API key (yours, if you switched to BYO) | Authenticate map requests against your account | Contract — Art. 6(1)(b) | flutter_secure_storage | Mapbox (US) on each tile fetch | Until you replace or wipe it |
| Purchase token / order ID | Verify your one-time purchase / restore | Contract — Art. 6(1)(b) | Google Play Billing | Google LLC | Per Google Play retention |

We do not perform automated decision-making or profiling under GDPR
Art. 22.

## What CycleMatix does **not** collect

CycleMatix does not collect: your name, email address, phone number,
contacts, calendar, photos, audio, SMS, web browsing history, installed
apps, advertising ID, or any cross-app behavioural signal. There is no
analytics SDK in the app, and currently no crash-reporting SDK
either — if that ever changes, this policy will say so before the
change ships.

## Third parties

Each of these is reached **only when you use the relevant feature**.
Disconnect any of them at any time in Settings → Integrations.

- **Mapbox** — provides map tiles. Each tile your viewport touches is
  requested from Mapbox's servers. That request necessarily reveals the
  rough area you're looking at (roughly street-block resolution) plus
  your IP address, on Mapbox's timing. Mapbox's own retention policy
  applies; see https://www.mapbox.com/legal/privacy.

  **During your free trial**, those tile requests are billed against
  the developer's shared Mapbox account, which is rate-limited to
  5,000 tiles per device per month. Once that cap is hit (or the
  global free tier is exhausted) the app falls back to OpenStreetMap
  raster tiles. After purchase, a one-time prompt offers to add your
  own Mapbox key — once you do, the developer's account stops seeing
  your requests entirely.

- **Strava** — only if you connect your account. We use Strava's OAuth
  (the same flow you'd see on any third-party Strava app). The token
  stays on your device until you disconnect.

- **Google Drive** — only if you connect your account, for ride imports
  and optional encrypted backups. We use Drive's `appdata` scope for
  backups (a hidden folder visible only to this app, not to your normal
  Drive view).

- **Google Play Billing** — handles your one-time purchase. Google
  passes us back a purchase token / order ID we use to verify and
  restore your entitlement.

These are the only third parties. We do not sell, share, or transmit
your data anywhere else.

## Data categories (Google Play taxonomy)

For Google Play's Data Safety form, the data CycleMatix handles maps to:

| Play category | Data type | Collected? | Shared? | Optional? |
|---|---|---|---|---|
| Location → Precise location | GPS during a ride | On device | Only on user-initiated export to Strava / Drive | Required for ride recording |
| Health and fitness → Fitness info | Heart rate, power, cadence, distance, routes, elevation | On device | Only on user-initiated export | Optional (no sensors paired = no readings) |
| Files and docs | User-imported `.fit` / `.gpx` / `.tcx` files | On device | No | Optional |
| Financial info → Purchase history | Purchase token / order ID | Yes | Google Play (essential service) | Required for paid entitlement |
| App activity, app info & performance | — | **Not collected** | — | — |
| Personal info, messages, photos, audio, contacts, calendar, web browsing, advertising ID, device IDs | — | **Not collected** | — | — |

## Transfers outside the EU

Mapbox, Strava, and Google process data in the United States. Transfers
rely on:

- the **EU–US Data Privacy Framework** adequacy decision
  (Commission Decision (EU) 2023/1795) where the recipient is
  DPF-certified, and
- **Standard Contractual Clauses** (Commission Decision (EU) 2021/914)
  otherwise.

You can ask for the relevant clauses or certification status by emailing
jenkocoban@gmail.com.

## Permissions

| Permission | Why |
|---|---|
| Fine + background location | Recording GPS during a ride. Background access is used **only** while a ride is actively recording, so the recording continues when the screen is off, when you switch to a music app, or when the phone is in your jersey pocket. The recording stops the moment you tap Stop. Location stays on the device unless you explicitly export the ride. |
| Bluetooth scan / connect | Pairing power meters, HR straps, cadence sensors. |
| Foreground service | Keeps GPS recording running while the screen is locked. |
| Notifications | Active-ride status notification (so Android doesn't kill the recorder). |
| Internet | Map tiles, optional Strava / Drive sync, Mapbox routing. |

## Security

- **In transit:** every network request (Mapbox, Strava, Google Drive,
  Google Play Billing) goes over HTTPS / TLS.
- **At rest on device:** OAuth tokens for Strava and Google Drive, and
  your BYO Mapbox key if you set one, are stored in
  `flutter_secure_storage`, which on Android maps to the Android Keystore
  (hardware-backed where the device supports it). The ride database
  (SQLite) and exported files inherit Android's app-sandbox isolation —
  readable only by the CycleMatix process, only while the device is
  unlocked.
- **No server.** We operate no backend, so there is no server-side data
  to breach.

## What's in a Drive backup

If you turn on encrypted Drive backup, exactly this is uploaded:

- the SQLite ride database (rides, splits, climbs, computed metrics,
  routes, workouts), and
- your `shared_preferences` (settings, FTP/HR zones, paired sensor IDs,
  trial state).

The backup is encrypted on your device **before upload** with AES-256-GCM.
The encryption key is derived from your passphrase via PBKDF2-HMAC-SHA256,
200,000 iterations, with a 16-byte random salt per backup and a 12-byte
random nonce per backup. The passphrase never leaves your device. The
minimum passphrase length is 8 characters; you decide a strong one.

OAuth tokens, your BYO Mapbox key, and your purchase flag are **not**
included in the backup — they're device-specific and are re-collected
on a fresh install. If you lose your passphrase, the backup is
unrecoverable: we cannot help, because we do not have the key.

If a backup leaks (Drive breach, account compromise), the attacker holds
a ciphertext blob. Without your passphrase, recovering ride data
requires brute-forcing PBKDF2 at 200k iterations per guess against a
256-bit AES-GCM key — not feasible against a strong passphrase.

## What happens if your phone is stolen

Ride data on the device sits inside the Android app sandbox and benefits
from Android's full-disk encryption, which is on by default on modern
Android and tied to your screen lock. OAuth tokens and any BYO Mapbox key
sit in the Android Keystore, hardware-backed on most devices. An attacker
who unlocks your phone can see your rides; an attacker who has the device
locked cannot.

We do not offer remote wipe — there is no server to issue the command
from. Use Android's Find My Device for that.

## Your rights

Under the GDPR you have the right to access, rectify, erase, restrict,
port, and object to processing of your personal data, and to withdraw
any consent you've given.

- **Access** — your data is on your phone. Open the app to see it.
- **Erasure** — Settings → Storage → "Delete all my data". Wipes:
  the SQLite database, every JSON ride blob in the app's documents
  folder, all shared_preferences (settings + trial state), all
  flutter_secure_storage entries (Strava token, Drive token, BYO
  Mapbox key, purchase flag), all Mapbox offline tile regions and
  style packs. The action is immediate and irreversible. Activities
  you previously pushed to Strava remain on Strava — manage those at
  strava.com. Drive backups you previously uploaded remain in your
  Drive — delete them in your Drive's "Apps with access" view.
- **Portability** — every ride can be exported as `.fit`, `.gpx`, or
  `.json` from the ride detail screen. Settings, FTP history, paired
  sensor IDs, and trial state are not currently exportable as a
  standalone bundle; an encrypted Drive backup contains all of it and
  can be restored to a fresh install. Email jenkocoban@gmail.com if
  you need a different format.
- **Withdraw consent** — disconnect Strava / Drive in Settings →
  Integrations.
- **No sale** — we don't sell your data. CycleMatix is a one-time
  purchase; selling data wouldn't fit the model.
- **Complaint** — you can lodge a complaint with the Slovenian
  Information Commissioner (Informacijski pooblaščenec, Dunajska 22,
  1000 Ljubljana, gp.ip@ip-rs.si, https://www.ip-rs.si) or with the
  supervisory authority in your EU/EEA country of residence.
- **Contact** — jenkocoban@gmail.com.

## Accounts

CycleMatix does not create user accounts. There is no sign-up, no
username, no password. Strava and Google Drive OAuth tokens authenticate
you to **those third-party services** — CycleMatix never sees your
Strava or Google credentials. To revoke access: Settings →
Integrations → Disconnect, or revoke directly in your Strava /
Google account settings.

## Children

CycleMatix is not directed at children, but cycling is a children's
activity and we know minors will install it. We don't ask for age,
don't gate by age, and don't collect anything that would identify a user
as a minor. Under GDPR Art. 8 we don't knowingly process personal data
of users below the digital-consent age in their country (16 by default;
15 in Slovenia under ZVOP-2 Art. 6(3); lower where national law sets a
lower threshold, down to 13).

If you are a parent and want your child's local data wiped, the in-app
erasure flow does that without contacting us. If you want us to confirm
we hold nothing on a server about your child: we don't, because we
don't run a server.

## Changes

If this policy changes, the new version is posted at this URL with an
updated "Last updated" date. Material changes will be announced in-app.
