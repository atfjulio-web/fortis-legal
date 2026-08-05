---
title: Fortis — Privacy Policy
---

[← Legal & Support index](README.md) · [Support](support.md)

# Fortis Privacy Policy

**Last updated:** 4 August 2026

Fortis is a private, invite-only, end-to-end encrypted messaging app. This policy
describes exactly what the app and its relay server can and cannot see. It is written
to match what the code actually does — not a generic template.

Contact for privacy questions and abuse reports: **5jx7fcydby@privaterelay.appleid.com**

## The short version

- We have no accounts. You never give us an email, phone number, or name.
- Message content is end-to-end encrypted. We cannot read it, and we do not store it.
- Nothing you say is written to a database or a disk anywhere on our servers.
- When everyone leaves a room, that conversation ceases to exist entirely.

## What stays on your device

The following are stored locally on your phone and are never transmitted to us:

| Data | Where it's stored | Why |
|---|---|---|
| Your alias and avatar | App storage | So you don't re-enter them each launch |
| Theme, privacy, notification and timeout preferences | App storage | Your settings |
| Recently used room PINs | App storage | Convenience when rejoining |
| App Lock PIN (hashed, never the PIN itself) | iOS Keychain / Android Keystore | Local app lock |
| Room encryption keys | Memory only, never written to storage | Decrypting your messages |
| Device identifier (a random ID, see below) | iOS Keychain / Android Keystore | Abuse enforcement |

**Messages are never stored on your device between sessions.** Leaving a room deletes
its messages and any downloaded attachments from the device.

## What our server can see

Our relay server passes encrypted data between people in a room. While you are in a
room, it necessarily handles:

- **Your alias and avatar** — sent in plain text so other people in the room can see who
  is talking. Treat your alias as public to that room.
- **Room membership and presence** — who is currently connected to a room.
- **Message timing and encrypted size** — the server knows a message passed through and
  roughly how big it was.
- **Your IP address** — unavoidable for any internet connection; used transiently for
  rate limiting to prevent PIN guessing. Not logged to disk or retained.
- **System events** — joins, leaves, renames, and screenshot notices.

## What our server can never see

- **The content of your messages.** They are encrypted on your device with a key the
  server never receives and mathematically cannot derive.
- **Attachments**, including their filenames and file types.
- **Your room PIN**, or any encryption key derived from it. The server only ever receives
  a one-way fingerprint of the PIN, which cannot be reversed.

This is a property of the design, not a promise about our conduct: even if our servers
were fully compromised or we were compelled to hand over everything we have, message
content is not among the things we possess.

## What we retain

**Nothing about your conversations.** Rooms exist only in server memory and are deleted
the moment the last person leaves. There is no database, no message archive, and no
backup.

The single exception is abuse enforcement. When you report someone, we record:

- A **random device identifier** — generated on first launch, containing no personal
  information and not linked to your identity, contacts, advertising ID, or hardware.
- **Report metadata** — the time, the reason category chosen, the aliases of the person
  reporting and the person reported, and the device identifiers of both. **Never message
  content**, because we do not have it, and never the room involved. Retained so a human
  can review reports; older entries are discarded automatically.

If enough different people report the same device, that device is blocked from creating
or joining rooms. These records contain no message data and cannot be used to reconstruct
a conversation. Reinstalling the app generates a new device identifier.

## Data we do not collect

We do not use analytics, advertising SDKs, crash reporting, or tracking of any kind. We
do not build profiles, and we do not share, sell, or transfer data to third parties —
there is no third party in this system.

## Permissions the app requests

Each is used only for the stated purpose and only when you actively invoke it:

- **Photos / Camera** — to attach images and videos you choose to send.
- **Microphone** — to record voice messages you choose to send.
- **Media library** — to save an attachment you explicitly choose to keep.
- **Face ID / Touch ID** — to unlock the app when you enable App Lock.
- **Notifications** — local reminders only, generated on your device. We have no push
  notification server and cannot send you anything.

## Your rights and choices

Because we hold no account and no personal data:

- **Access/portability** — there is nothing about you for us to export.
- **Deletion** — leaving a room deletes the conversation for everyone. Deleting the app
  removes all local data. Device ban records are the only retained data; you may request
  review of one via the contact address above.
- **Consent** — accepting the in-app terms on first launch is the point of consent; you
  can withdraw it by deleting the app.

## Children

Fortis is not directed at children. We do not knowingly collect any information from
children, and because we collect no personal information from anyone, we have no
age-identifying data. Please observe the age rating shown on the App Store.

## Changes

If this policy changes materially, the "last updated" date above will change and the
revised policy will be published at this address before taking effect.

## Contact

**5jx7fcydby@privaterelay.appleid.com**
