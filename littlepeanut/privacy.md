---
layout: default
title: Little Peanut Privacy Policy
---

# Little Peanut Privacy Policy

**Effective:** November 8, 2026 · **Developer:** Ronnie Simonelli

Little Peanut is a baby tracker for iPhone: feeds, sleep, diapers, pumping and tummy time,
shared between the caregivers of one household through iCloud. This policy explains what
the app stores, where it goes, and what never leaves your phone. The short version: there
is no account, no analytics, no advertising, and no server of ours that keeps your data.

## What the app stores

Everything in the app is entered by you or another caregiver in your household:

- **Your baby:** name, birthday and the time zone of the birth, and an optional photo.
- **Caregivers:** each caregiver's name and optional photo, and the identifier iCloud
  gives their account so the app can tell caregivers apart.
- **Entries:** each feed, sleep, diaper, pump and tummy time, with its times, amounts,
  sides, kind and any note you type.
- **Settings:** the household's preferences (units, night hours, feeding style, which
  rings show) and each caregiver's own display preferences.
- **Timer tokens:** while a timer runs as a Live Activity, each phone in the household
  records the token Apple issued for that activity, so the other phones' timers can be
  kept in step (see "Live timers" below).

Little Peanut does not ask for your location, contacts, calendar, microphone or health
data, and never reads your photo library: a profile photo is chosen with the system's
photo picker, which hands the app only the picture you pick.

## Where it lives: your iCloud

The household's data is stored in iCloud, in the CloudKit database of the caregiver who
created the household, under Apple's account and privacy terms. Other caregivers join
through an iCloud share, the same mechanism Notes and Reminders use, and see the whole
household: every entry, profile and setting. A copy stays on each caregiver's phone so the
app works offline and syncs when it can.

We cannot see any of it. Apple hosts the data; the developer has no server that holds a
copy, no way to read your household, and no key to it. Apple's handling of iCloud data is
described in [Apple's privacy policy](https://www.apple.com/legal/privacy/).

Device-local preferences (for example the theme you picked) are kept on that phone only.
The Today widget and the Lock Screen timer read a small snapshot of today's figures that
the app writes on the same phone.

## Live timers: what passes through the relay

When a caregiver starts, changes or stops a timer, the household's other phones update
their Lock Screen timer within seconds. Apple's push service delivers those updates, and
sending a push needs a signing key that cannot ship inside an app. So the phone making the
change sends the update to a small relay service run by the developer (a Cloudflare
Worker), which checks that the request comes from a genuine Apple device running Little
Peanut (Apple's DeviceCheck), signs the update and hands it to Apple's push service.

What the relay handles, in transit only: the update's content (the baby's name, the
timer's start and end times, amounts and sides), the push tokens and channel identifier of
the phones it is addressed to, and the DeviceCheck token. It **stores none of it**. It keeps
no database, writes no payloads, tokens or identifiers to its logs (the logs count requests
and record Apple's status codes, nothing else), and forgets each request as soon as it is
forwarded. Cloudflare, which runs the relay, sees each request's IP address to limit
abuse, under [Cloudflare's privacy policy](https://www.cloudflare.com/privacypolicy/);
the relay does not record it.

The relay is a convenience, not a requirement: if it is unreachable, timers still update
through iCloud, just more slowly. Everything else in the app works without it.

## Siri, widgets and Live Activities

Logging with Siri ("Start a nap in Little Peanut") runs on your phone through Apple's App
Intents; what you say to Siri is handled by Apple under its terms. Widgets and the Lock
Screen timer are drawn on your phone from the snapshot above.

## Exports and backups

You can export your history as a CSV file, share a PDF summary for the pediatrician, and
save a backup file of the whole household (including photos). Each of these is created on
your phone and goes only where you send it, through the share sheet or the file picker. A
backup can be restored on a new phone from the welcome screen.

## What we don't do

- No account, sign-up or password.
- No analytics, usage tracking, advertising or advertising identifiers.
- No third-party SDKs; the app talks only to Apple's services and the relay above.
- No selling or sharing of data with anyone.

If you have turned on "Share With App Developers" in your iPhone's analytics settings,
Apple may share crash reports with the developer. They contain no household data. That
setting is yours, in Settings ▸ Privacy & Security ▸ Analytics & Improvements.

## Deleting your data

Entries, babies and caregiver details can be edited or deleted in the app; a deletion syncs
to every caregiver's phone. To remove the household entirely, delete the app's data from
iCloud (Settings ▸ your name ▸ iCloud ▸ Manage Account Storage ▸ Little Peanut) and delete
the app. A caregiver who leaves the iCloud share stops seeing the household; the owner can
stop sharing it at any time. Deleting the app from a phone alone does not delete the
household from iCloud.

## Children

Little Peanut is made for parents and caregivers, not for children, and does not knowingly
collect anything from a child. The information about a baby is entered by their caregivers
and stays in those caregivers' iCloud.

## Changes

If this policy changes, the new version will be posted at the same address with a new
effective date, and the app's What's New page will say so when the change matters.

## Contact

Questions about privacy: ronnie.simonelli@gmail.com.
