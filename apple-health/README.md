# Apple Health → Gevety

Apple Health has no server-side API, so Gevety receives your Apple Health data
from an app on your iPhone that pushes it on a schedule. The supported sender is
**Health Auto Export** by HealthyApps.

## What you need

- An iPhone with the Health app (an Apple Watch adds heart rate, HRV, sleep and workouts).
- [Health Auto Export on the App Store](https://apps.apple.com/app/id1115567069).
  The **Premium** plan is required for the REST API automation that sends data
  in the background. It has a 7-day trial and a lifetime purchase option.
- A Gevety account at [gevety.com](https://gevety.com).

## Set it up (about five minutes)

1. In Gevety go to **Profile → Sources → Apple Health** and press **Connect Apple Health**.
   Gevety shows two values once: a **receiver URL** and an **Authorization header**.
   Copy both. If you lose them, press **Issue a new key** to get a fresh pair.
2. Open Health Auto Export → **Automations** → add a **REST API** automation.
3. Paste the receiver URL, add the header exactly as shown (`Authorization: Bearer …`),
   and choose **JSON** as the format.
4. Turn **Batch Requests** on and set the date range to **Since Last Sync**.
5. Pick the metrics and workouts you want to share (steps, resting heart rate, HRV,
   sleep, weight, workouts are the ones Gevety uses today), then run the automation once.
6. Back in Gevety, the Apple Health page shows "synced just now" when the first
   delivery lands. After that, the app keeps sending on its own schedule.

## What Gevety does with it

- Daily metrics (steps, resting heart rate, HRV, respiratory rate, blood oxygen,
  weight, body fat) are stored per day under the Apple Health source.
- Sleep nights are stored with their stages.
- Workouts appear in Activities. If you also log strength sessions in Hevy, the
  Apple Watch session becomes the primary record and Hevy's sets are merged into it.

## Troubleshooting

- **"synced" never appears**: open the automation's run history in Health Auto
  Export. A `401` means the header no longer matches the key Gevety holds; press
  **Issue a new key** in Gevety and paste the new header. A `413` means a very
  large first export; keep **Batch Requests** on.
- **Nothing to send yet**: Health Auto Export only sends what Apple Health has;
  make sure the watch has synced to the phone.
- **Changed phones?** Reinstall the app and paste the same two values again, or
  issue a new key.

Gevety shows Apple Health data as text only and never uses the Apple logo, in
line with Apple's guidelines. Health Auto Export is an independent app; Gevety
is not affiliated with HealthyApps or Apple.
