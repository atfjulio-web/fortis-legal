---
title: Fortis IM — Privacy Policy
---

[← Legal & Support index](README.md) · [Support](support.md)

# Fortis IM Privacy Policy

**Last updated:** 10 August 2026

Fortis IM is a private, invite-only, end-to-end encrypted messaging app. This policy
describes exactly what the app and its relay server can and cannot see. It is written
to match what the code actually does — not a generic template.

Contact for privacy questions and abuse reports: **5jx7fcydby@privaterelay.appleid.com**

## The short version

- **No account is required.** You never give us an email, phone number, or real name.
  Rooms with a PIN work with no registration of any kind.
- You *may* optionally register a **username** so people can reach you directly. That is
  the one piece of data we hold that persists between sessions, and you can delete it
  from inside the app at any time. See "Usernames" below.
- Message content is end-to-end encrypted. We cannot read it, and we do not store it.
- Nothing you say is ever readable by us. What we do hold — who is currently in a
  room, and encrypted attachments waiting to be collected — is described below.
- When everyone leaves a room, that conversation ceases to exist entirely.

## What stays on your device

The following are stored locally on your phone and are never transmitted to us:

| Data | Where it's stored | Why |
|---|---|---|
| Your username and avatar | App storage | So you don't re-enter them each launch |
| Theme, privacy, notification and timeout preferences | App storage | Your settings |
| Recently used room PINs | App storage | Convenience when rejoining |
| App Lock PIN (hashed, never the PIN itself) | iOS Keychain / Android Keystore | Local app lock |
| Room encryption keys | Memory only, never written to storage | Decrypting your messages |
| Device identifier (a random ID, see below) | iOS Keychain / Android Keystore | Abuse enforcement |
| Your saved contacts, and any name you gave them | iOS Keychain / Android Keystore | Reaching people without swapping a PIN |
| Your identity key, if you registered a username | iOS Keychain / Android Keystore | Proving the username is yours |

Your **push token** is the one thing in this list that does not stay on the device,
and only if you turn notifications on — see "Push notifications" below.

**Your contact list is never sent to us.** It is not uploaded, backed up, or synced. We
learn that one username asked to talk to another at the moment it happens, and we keep
no record of it — so we cannot reconstruct who knows whom.

**Messages are never stored on your device between sessions.** Leaving a room deletes
its messages and any downloaded attachments from the device.

**None of it is copied into a cloud backup.** Phone operating systems back app data
up automatically unless the app opts out, and a room PIN in a backup is a room PIN
off the phone. Fortis IM opts out on both platforms: on Android it is excluded from
Google's automatic app backup, and on iOS its stored data is marked as excluded from
iCloud and computer backups. The practical consequence is deliberate — reinstalling
Fortis IM gives you a clean app, not your old settings and PINs back.

## What our server can see

Our relay server passes encrypted data between people in a room. While you are in a
room, it necessarily handles:

- **Your username** — sent in plain text so other people in the room can see who is
  talking. Treat it as public to that room.
- **Room membership and presence** — who is currently connected to a room. While a room
  is open this is held in a database so the service can survive a restart without
  ending everyone's conversation. It is deleted when the room empties.
- **Message timing and encrypted size** — the server knows a message passed through and
  roughly how big it was.
- **Your IP address** — unavoidable for any internet connection. It is used to rate-limit
  PIN guessing, and for that purpose only a one-way hash of it is recorded, which expires
  automatically after 60 seconds. We do not keep a log of addresses that connected.
- **System events** — joins, leaves, renames, and screenshot notices.

## What our server can never see

- **The content of your messages.** They are encrypted on your device with a key the
  server never receives and mathematically cannot derive.
- **Attachments**, including their filenames and file types. Photos, videos, voice
  messages and files are encrypted on your device and uploaded directly to storage as
  ciphertext. We hold those encrypted files only long enough for the other people in the
  room to download them, and delete them when the room ends. We have no key for them.
- **Your profile photo**, if you set one. It is encrypted with a key derived from the
  room's PIN — which never leaves your phone — so only people who have the PIN can see it.
- **Your room PIN**, or any encryption key derived from it. The server only ever receives
  a one-way fingerprint of the PIN, which cannot be reversed.

This is a property of the design, not a promise about our conduct: even if our servers
were fully compromised or we were compelled to hand over everything we have, message
content is not among the things we possess.

## What we retain

**Nothing readable, and nothing about your conversations.** There is no message archive
and no backup. Messages are never written down at all — they are passed between the
people in a room and discarded.

Two things do exist while a room is open, and both are deleted when the last person
leaves it:

- **Who is currently in the room** — usernames and connection state, held in a database so
  that a server restart doesn't end everyone's conversation mid-sentence.
- **Encrypted attachments** — held only so the other people in the room can download
  them. They are ciphertext we have no key for, and anything left behind by a crash is
  deleted automatically within a day.
- **A sealed hand-off of the conversation, briefly** — there are two moments when one
  member's phone passes the conversation to another's, and it travels as one encrypted
  bundle we hold just long enough for the other phone to fetch it. It is ciphertext we
  have no key for, and it is deleted with the room like everything else.

  The first is when **someone new joins**. Everyone already in the room is asked, and
  **each person answers only for their own messages** — if three of five agree, the new
  arrival receives those three people's messages and not the other two's. Nobody can
  agree on your behalf.

  The second is when **you come back** after your own phone was asleep or the app was
  minimised. Nobody is asked, because nothing new is being shared: you are given only
  what was said while you already held your place in the room — messages that would
  have arrived on your screen had your phone been awake. It cannot reach back past the
  moment you joined.

The one thing we keep for longer is abuse enforcement. When you report someone, we record:

- A **random device identifier** — generated on first launch, containing no personal
  information and not linked to your identity, contacts, advertising ID, or hardware.
- **Report metadata** — the time, the reason category chosen, the usernames of the person
  reporting and the person reported, and the device identifiers of both. **Never message
  content**, because we do not have it, and never the room involved. Retained so a human
  can review reports; older entries are discarded automatically.

  **A report is also emailed to us**, to the abuse address published on this page and
  shown in the app, so that reports are seen when they arrive rather than whenever
  somebody next looks at a database. The email carries those same fields and nothing
  else — no message content, and not the room. It travels through Amazon's notification
  service and ordinary email, so, like a push notification, it leaves our system; unlike
  a push notification it is addressed to us rather than to you.

If enough different people report the same device, that device is blocked from creating
or joining rooms. These records contain no message data and cannot be used to reconstruct
a conversation. Reinstalling the app generates a new device identifier.

**Short-lived server logs.** Our relay writes operational logs so that faults can be
found, and they are deleted after seven days. They record events rather than content: an
error, a report being filed, or whether a notification we tried to send was accepted or
refused. A notification entry includes the last few characters of the push address it
concerned — not enough to send anything to your device, and there so that two phones can
be told apart while reading a log. No message text, no attachment, no room, and no full
push address appears in any of it.

## Usernames

You pick a username on the home screen, and it is the name rooms show. **Registering
it is optional and a separate, deliberate act** — tapping CLAIM. Until you do, nothing
in this section applies to you: nothing about the name leaves your phone except to the
people in a room you are in, exactly as before.

If you do register one, we store the username itself, the public half of a key your phone
generates to prove the name is yours, and the time it was last proved. We never receive
the private half — it stays in your phone's keychain — which is what lets us verify a
claim we could never make ourselves. We do not store an email, a phone number, or
anything else that identifies you.

- **A username is a name, not a profile.** Nothing is attached to it: no messages, no
  contact list, no history of who you spoke to.
- **Anyone can ask whether a username exists and whether it is currently online.** That is
  what makes a contact list with online indicators work, and a username is meant to be
  shared rather than guessed. If that is not what you want, do not register one.
- **A username you stop using is released after 180 days** and becomes available to
  someone else.
- **Nobody else can use it**, in a room or anywhere else, unless they hold its key.
- **You can release it at any time**, from the home screen.

## Deleting your account

On the home screen, tap **RELEASE** beside your username.

This gives the username up immediately — it becomes available for anyone else to
register — and erases the key that proved it was yours from your phone. Because there is
deliberately no recovery path, this cannot be undone: registering the same name again
later, even from the same phone, produces a new identity, and people who had saved you
will be warned that your key changed.

You can go on using the same name in PIN rooms afterwards. Releasing gives up the
*reservation*, not what you are called.

Your saved contacts, recent room PINs and settings stay on your phone; remove them in the
app, or delete the app to remove everything at once. There is nothing else about you for
us to delete, because there was never anything else to collect.

## Data we do not collect

We do not use analytics, advertising SDKs, crash reporting, or tracking of any kind. We
do not build profiles, and we do not share, sell, or transfer data to third parties.

The single exception is push notifications, and only if you turn them on. See below.

## Permissions the app requests

Each is used only for the stated purpose and only when you actively invoke it:

- **Photos / Camera** — to attach images and videos you choose to send.
- **Microphone** — to record voice messages you choose to send.
- **Media library** — to save an attachment you explicitly choose to keep.
- **Face ID / Touch ID** — to unlock the app when you enable App Lock.
- **Notifications** — see "Push notifications" below. Optional, off unless you turn
  them on.

## Push notifications

Turning notifications on lets us wake your phone when someone invites you to a
conversation, or when there is a new message in a room you have stepped away from.
Along with the abuse-report email described under "What we retain", this is one of
only two parts of Fortis IM that involve anyone outside it, so it is worth being exact
about.

**What a notification contains: nothing.** Every push we send is one of two fixed
sentences — "Someone wants to chat." or "New message." There is no sender, no
username, no room, no message text, and no hidden data field. We could not include
your messages even if we wanted to, because they are encrypted and we cannot read
them; we do not include the rest because a notification is delivered by other
companies and displayed on a locked screen. Open the app to find out who and what.

**What leaves our system.** To reach a closed app we must hand a *push token* — an
opaque address for your device, issued by Apple — to Expo's push service, which
passes it to Apple's Push Notification service. Those two companies therefore learn
that a Fortis IM notification was sent to your device, and when. They learn nothing
about who it was from or what it concerned, because we do not tell them.

**What we store.** Your push token, on your username's record, for as long as
notifications are on. Turning them off in Settings removes it from our server, and
deleting your username removes it with everything else.

**An invite that arrives while your app is closed** is held on our server just long
enough to be delivered — five minutes — and is discarded after that whether or not
it was collected. It is the only record we keep of one person contacting another,
and it exists so that the notification itself does not have to carry it.

If you would rather none of this happened, leave notifications off. Everything else
in the app works exactly the same; you are simply reachable only while it is open.

## Your rights and choices

Because we hold no personal data — and, unless you registered a username, no account:

- **Access/portability** — there is nothing about you for us to export. If you registered
  a username, what we hold about it is listed in full under "Usernames" above.
- **Deletion** — leaving a room deletes the conversation for everyone. A registered
  username can be deleted in the app, as described above. Deleting the app removes all
  local data. Device ban records are the only retained data; you may request review of
  one via the contact address above.
- **Consent** — accepting the in-app terms on first launch is the point of consent; you
  can withdraw it by deleting the app.

## Children

Fortis IM is not directed at children. We do not knowingly collect any information from
children, and because we collect no personal information from anyone — a username is
chosen, not identifying — we have no age-identifying data. Please observe the age rating
shown on the App Store or Google Play.

## Changes

If this policy changes materially, the "last updated" date above will change and the
revised policy will be published at this address before taking effect.

## Contact

**5jx7fcydby@privaterelay.appleid.com**
