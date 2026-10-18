# Changelog

All notable changes to Sightline for Blue Iris. The version shown in **Settings → About** matches the newest entry here.

## 0.12.0 — 2026-10-17

- **Hidden and disabled cameras are left out.** Cameras marked Hidden in Blue Iris, and disabled cameras, no longer appear in the Live grid, the alert list, alert-label counts or the camera picker. New setting: **Settings → Live view → Show hidden cameras** (off by default). Disabled cameras are never shown.
- **Combine alert filters.** Tapping a filter button now adds or removes it, so you can show, for example, Dogs + People together (alerts matching any selected filter). Tap All to clear.
- **Full screen.** New button in the player and in the main header (camera grid), plus the `F` key on desktop. In full screen, the player's controls float over the picture and fade out after a few seconds; move the mouse or tap to bring them back. Hidden on browsers without full-screen support (iPhone Safari).

## 0.11.3 — 2026-10-17

- **"Stay signed in" is now off by default.** New users choose it with the checkbox on the sign-in screen, or later in Settings. Anyone who already has it turned on keeps it.

## 0.11.2 — 2026-10-17

Pre-release review fixes.

- Fixed: for new users, the Alerts filter buttons could change on a later visit, from the basic set (All, People, Vehicles, Animals) to a longer set. The starting set is now saved on first load.
- Hardened: alert thumbnail addresses only accept plain recording IDs.
- README: corrected the date-range and browser-testing details.

## 0.11.1 — 2026-10-17

- Licensed under the **GNU GPL v3.0 or later**. Added the LICENSE file, a copyright and license notice at the top of `sightline.htm`, and a license note in Settings → About.

## 0.11.0 — 2026-10-17

- Player timeline: new **48h** zoom level next to 24h.
- On the 24h and 48h views, the midnight tick shows the day (for example "Sat") instead of "12a", so you can tell the days apart.

## 0.10.0 — 2026-10-17

- Renamed to **Sightline for Blue Iris**. Files are now `sightline.htm`, `sightline-jmuxer.min.js`, `sightline.json` and `sightline-icon-*.png`. Open the page at `/sightline.htm`.
- Settings carry over from earlier versions served by the same Blue Iris server.

## 0.9.0 — 2026-10-17

First versioned build (previously "Cameras", served as `simple.htm`).

- **Live view:** auto-fitting camera grid with tile sizes, Blue Iris groups as buttons, drag-to-reorder, motion and trigger highlights colored by AI result, AI labels on tiles, optional motion boxes on tiles.
- **Alerts:** People / Vehicles / Animals filters plus any AI label, built from a 14-day scan of your alerts or typed in; date and time ranges; camera and group filter.
- **Player:** live and recorded H.264 video with audio, scrubbable timeline with alert markers, timeline zoom from 2 minutes to 24 hours, previous / next alert, speed control, swipe between cameras, digital zoom up to 8x with pan, quality picker, volume slider, motion boxes with 1-10 sensitivity.
- **Settings:** grouped into Live view, Interface and Account; choose which groups and alert filters appear; color legend; About screen with version info.
- **Sign-in:** stays signed in through Blue Iris session timeouts and network drops.
