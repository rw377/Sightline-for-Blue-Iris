# Changelog

All notable changes to Sightline for Blue Iris. Released versions match what **Settings → About** shows; a version ending in `-dev` is a work-in-progress copy from `main`.

## 0.15.0 — 2026-10-24

- **Auto alert filters.** A new choice in **Settings → Alert filters**: **Auto** shows All, the filters you always want (switch them on under Always show, for example People and Vehicles), then the detections your cameras have seen most in the last 3 weeks. Person counts as People and car / truck / bus as Vehicles; other labels get their own button (Dogs, UPS, Amazon…). Show as many as fit across the screen (Fit screen, up to 5) or an exact number (1–8). The counts are kept in this browser and refreshed every few hours in the background. **Choose** is the hand-picked list as before. Brand-new visitors start on Auto; everyone else keeps their own list until they switch.
- The label scan in Alert filters now covers the last 3 weeks (was 14 days).
- **Smooth mode for the alert preview panel.** Settings → Interface → Alert preview panel is now **Standard / Smooth / Off**. Standard (the default) is the slideshow of stills, like UI3. Smooth plays the alert as real video from its recording file, sped up so it lasts about 6 seconds (2×–8×, shown in the corner), 3 times. Blue Iris has to decode and encode it for each preview, so it's best on a capable server. One stream at a time; it pauses while the player is open; an alert that can't be played falls back to the slideshow.
- **Go to any date and time in the player.** A calendar button after 48h opens quick choices (Last hour, This morning, Last night, Yesterday, This time yesterday, This time last week) or a month calendar with from / to times (a range can run past midnight). Days with no recordings for the camera are greyed out and can't be picked; days with alerts get a dot (one coarse timeline request per month viewed). The timeline then shows exactly that window and plays from its start, however far back. Times not yet recorded are refused.

## 0.14.0 — 2026-10-21

- **Step frame by frame with `,` and `.`**, like UI3. Pauses, then shows the frame one frame interval back or forward, using the camera's frame rate in Blue Iris. From live, `,` pauses on the frame shown and steps back.
- **Flag or protect alerts, like UI3.** A new button in the player (or right-click an alert in the list, long-press on Android) opens Flagged and Protected switches. Flagged marks an alert to come back to; Protected stops Blue Iris deleting it in its clean-up. It uses the same Blue Iris command as UI3 and changes only those flags, so UI3 and Blue Iris show the change too. Flagged and protected alerts get small icons in the list. New **Flagged** alert filter (turn it on under Settings → Alert filters). Clear message if the Blue Iris user isn't allowed to change alerts.
- **Phones: download, flag and protect share one "⋯" button** in the player, so the camera name keeps its room in the top bar.
- **Alert preview panel on computers.** With a mouse and a window at least 900 px wide, pointing at an alert plays it in a large panel beside the list as a flip-book of 8 frames spread across the alert, with each frame's time, the AI labels, camera, date and length. Frames load one at a time and only for the alert you stop on; the last few previews are kept. Click the picture to open the alert. **Settings → Interface → Alert preview panel** turns it off. Phones are unchanged.
- **Server status and System log** in a new **Settings → Server** section, like UI3's. Server status shows CPU (and GPU, as Blue Iris reports it), memory, recordings against their allowed space, total frame rate and bitrate, uptime, web connections, warnings (tap to open the log) and profile, refreshed every 2 seconds while open; disk usage per disk drawn as UI3 does (recordings, allocated free, other files, free) with a note when Blue Iris is over its allocation; and each camera's frame rate, bitrate and how far back its recordings go ("Footage kept"; worked out from one long timeline request per camera, at most every 10 minutes, ignoring old clips kept after a gap of more than 2 days). The System log is Blue Iris's own log, newest first, with level icons, repeat counts, filters (All / Warnings & errors / Info) and search. Clear message if Blue Iris keeps the log to admin users.
- **Back button on phones closes popups** (Settings, Server status, the log, the alert popup and so on) and then the player, instead of leaving Sightline.
- **Sightline logo next to the server name** at the top left. The logo is now the blue ring and white center without the red dot, everywhere (header, browser tab, home-screen icon, About).
- **Live video in the camera tiles.** The Live grid now shows moving video instead of snapshots refreshed every 1.5 seconds. Sightline plays one stream of the whole Blue Iris group (the picture UI3's group view shows) and each tile draws its own camera's part of it, so the grid keeps Sightline's order, sizes and labels. It uses one connection however many cameras are in the group, and the stream's size follows the grid's width (720p to 1440p tier). Motion boxes still work on live tiles. Turn it off in **Settings → Live view → Live video in camera tiles** to go back to snapshots, which use less data. Tiles fall back to snapshots by themselves for a group without a Blue Iris layout, a camera that isn't in the group's picture, or a browser that can't play the stream. The grid stream pauses while the player is open or the page is in the background, and switches straight to the new group's stream when you change groups.
- **Copy diagnostics** in Settings → About: a short report for bug reports (Sightline and Blue Iris versions, browser, screen, video support, camera and group counts, live-tile state, recording file types seen, settings and the last few errors). It includes no camera names, user name, password or server address.
- **Issue forms on GitHub** for bug reports (asking whether the problem also happens in UI3, plus the diagnostics) and feature requests.
- **Zoom the timeline in and out of time, like UI3.** Scroll the mouse wheel over the timeline (or pinch a trackpad) to zoom around the moment under the pointer; Shift + wheel or a sideways swipe moves along. On a phone, pinch with two fingers on the timeline. The span can be anything from 30 seconds to 7 days; the 2m to 48h buttons still jump to their spans. In live view, "now" stays at the right edge. Dragging with one finger or the mouse still moves the playhead.

## 0.13.0 — 2026-10-19

- **Sharper video, matching UI3.** Sightline now asks Blue Iris for video the way UI3 does: a size plus UI3's quality and bitrate settings for that size. Before, Blue Iris fell back to its web server defaults, which looked softer and took longer to sharpen after movement. **Auto** picks the size from the pixels the player covers, with a margin: a full-screen browser on a computer gets the camera's full picture (for example 2560×1440 at up to 4 Mbps on a 4MP camera, the same as UI3's 4MP setting), while a phone held upright gets 720p at up to 1 Mbps. Fixed choices (480p to 4K) use UI3's settings for that size. The quality menu shows the data rate for each choice and the live rate being received. Viewing on a computer away from home can now use more data than before.
- **Click or tap the video, like UI3.** On a recording it pauses or resumes; on a live camera it closes the player and goes back to where you opened it (usually the camera grid). Double-click still switches between fit and fill. When the controls float over the video on a touch screen (phone sideways or full screen), a tap still shows or hides them.
- **Download alerts as MP4.** A download button in the player (when watching an alert) asks Blue Iris to export just that alert, follows its progress and saves the file with a readable name. Options, remembered per browser: **Re-encode to H.264** (default; plays smoothly in any player) with a choice of Blue Iris encoder profile (export 0-3) and the camera's text and graphic overlay (on by default), or **Original recording** (fastest, nothing lost, but some players show it choppy); include audio (on by default). Clear messages if the Blue Iris user isn't allowed to export or the export fails.
- **Choose the start and end of a download.** In the download sheet, pick **Choose start and end**: a bar above the timeline shows the range (starting from the whole alert), highlighted on the timeline with blue handles you can drag, plus **Set start** / **Set end** buttons that use the playhead. Tap a time to jump to it. Up to 15 minutes, and not before the alert's recording file starts.
- **Alerts play from their recording file**, as UI3's Clips list does. Fixed: on some cameras, alerts played zoomed into the top-left corner of the picture. Blue Iris's timeline stream of those alerts came out cropped; the recording file plays correctly. Before and after the alert, or once its file ends, playback carries on from the timeline.
- Fixed: a "Not BVR" picture could show on some alerts. Still frames are only read from recording files that support it, and every still frame now asks Blue Iris for both a width and a height (as UI3 does).
- Fixed: switching an alert's timeline to a longer span (for example 15m to 24h) could leave the timeline blank until you clicked it. While playing, Sightline kept trying to scroll a timeline that was already at the present, which cancelled the request for its motion and AI markings.
- If a recording changes picture size part-way through (for example sub stream to main stream), the player now restarts at the new size instead of stalling.
- **Links in Settings → About** to the project page, What’s new (Releases) and Report a problem (Issues) on GitHub. They open in a new tab only when tapped; Sightline still never contacts anything but your Blue Iris server by itself.

## 0.12.0 — 2026-10-18

- **Hidden and disabled cameras are left out.** Cameras marked Hidden in Blue Iris, and disabled cameras, no longer appear in the Live grid, the alert list, alert-label counts or the camera picker. New setting: **Settings → Live view → Show hidden cameras** (off by default). Disabled cameras are never shown.
- **Combine alert filters.** A click or tap still shows just that filter. **Shift + click**, **Ctrl + click** (⌘ + click on Mac) or a **long-press** on touch screens adds or removes a filter, so you can show, for example, Dogs + People together (alerts matching any selected filter). Tap All to clear.
- **PTZ controls.** For cameras Blue Iris marks as PTZ, a new button in the player (live view) opens a pad: hold an arrow, a diagonal or + / − to move or zoom, and let go to stop. **Home** sends the camera to its home position, or to a preset named "Home" if there is one. **Presets** lists every saved preset by name. Sends the same commands as UI3, plus an explicit stop as a backstop; the camera is stopped on release, sliding off the button, leaving the page, closing the player, switching camera, after 30 s of holding, and retried for up to 30 s if Blue Iris can't be reached.
- **Full screen.** New button in the player and in the main header (camera grid), plus the `F` key on desktop. In full screen, the player's controls float over the picture and fade out after a few seconds; move the mouse or tap to bring them back. Hidden on browsers without full-screen support (iPhone Safari).
- **Bigger video on desktop.** On wider screens the player's controls now fit in one row: timeline span on the left, play controls in the middle, speed and LIVE on the right, with a slimmer timeline. At 1280×800 the video grows from 1006×566 to 1116×628. Phones keep the two-row layout.
- Fixed: in full screen on a phone held upright, the play controls ran off the left edge of the screen. They now use the same two rows as the normal phone view.
- README: Blue Iris 6 listed as supported (reported working by a user).

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
