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

## Set it up on your iPhone (one minute)

1. On your iPhone, open [gevety.com](https://gevety.com) in Safari, go to
   **Profile → Sources → Apple Health** and press **Connect Apple Health**.
2. Tap **Add health metrics automation**. Health Auto Export opens with a
   "Gevety health metrics" automation already filled in (receiver URL, header,
   JSON, Since Last Sync, batching, hourly). Save it.
3. Go back to Gevety and tap **Add workouts automation**; save that one too.
4. That is it. Each automation runs on its own: the first run sends your whole
   workout history and the last week of daily metrics, one small request at a
   time, so it takes a few minutes. Gevety's Apple Health page shows "synced
   just now" once the first delivery lands. Afterwards the app sends new data
   every hour while your phone is unlocked (see the note on background sending
   below).

Tip: in the health metrics automation, trim **Select Health Metrics** to the
ones you use (steps, resting heart rate, HRV, sleep, weight, respiratory rate,
blood oxygen); the app runs faster with fewer metrics. Workouts you also record
in Strava, Garmin or Hevy are merged into one record, not shown twice.

## Set it up by hand (about five minutes)

Use this on a desktop browser, or if the one-tap links do not open the app.

1. In Gevety go to **Profile → Sources → Apple Health** and press **Connect Apple Health**.
   Gevety shows three values once: a **receiver URL**, a **header key**
   (`Authorization`) and a **header value** (`Bearer …`). Copy all three. If you
   lose them, press **Issue a new key** to get a fresh set.
2. Open Health Auto Export → **Automations** → add a **REST API** automation.
3. Paste the receiver URL and choose **JSON** as the format.
4. Scroll to **HTTP Headers** and tap **Add Headers**. The app shows two fields
   per header: put the header key (`Authorization`) in the **left** field and
   the header value (`Bearer …`) in the **right** field. Do not paste
   `Authorization: Bearer …` as one line into either field: the app ignores a
   header whose value is empty, and Gevety then sees no header at all.
5. Turn **Batch Requests** on and set the date range to **Since Last Sync**.
6. Pick the metrics and workouts you want to share (steps, resting heart rate, HRV,
   sleep, weight, workouts are the ones Gevety uses today), tap **Update** to
   save, then run **Manual Export** from inside the automation.
7. Back in Gevety, the Apple Health page shows "synced just now" when the first
   delivery lands. After that, the app keeps sending on its own schedule while
   the phone is unlocked.

## What Gevety does with it

- Daily metrics (steps, resting heart rate, HRV, respiratory rate, blood oxygen,
  weight, body fat) are stored per day under the Apple Health source.
- Sleep nights are stored with their stages.
- Workouts appear in Activities. If you also log strength sessions in Hevy, the
  Apple Watch session becomes the primary record and Hevy's sets are merged into it.

## Troubleshooting

- **"synced" never appears**: open **Activity Logs** for the automation in
  Health Auto Export. A `401` means Gevety saw no header or a header that does
  not match the key it holds: check that the header is entered as a separate key
  and value (step 4), or press **Issue a new key** in Gevety and paste the new
  value. A `413` means a very large first export; keep **Batch Requests** on.
- **The automation never runs on its own**: background sends need the
  **Premium** plan, and the app only runs automations while the phone is
  unlocked.
- **Nothing to send yet**: Health Auto Export only sends what Apple Health has;
  make sure the watch has synced to the phone.
- **Changed phones?** Reinstall the app and paste the same two values again, or
  issue a new key.

Gevety shows Apple Health data as text only and never uses the Apple logo, in
line with Apple's guidelines. Health Auto Export is an independent app; Gevety
is not affiliated with HealthyApps or Apple.
