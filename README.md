# Trail·Time — GPX Timestamp Viewer

A single-page tool for figuring out when you were at a specific point during a recorded activity, using the timestamps embedded in a GPX track (e.g. exported from Strava).

Runs entirely in your browser. No account, no install, no data leaves your machine except requests for map tiles.

## Using it

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. Drag a `.gpx` file onto the drop zone, or click it to browse.
3. Your track appears on the map, with:
   * a green dot at the start
   * an orange dot at the end
4. Click anywhere on the trail line — it snaps to the nearest recorded GPS point and shows:
   * the exact time and date you were there
   * distance covered so far
   * elevation climbed so far
   * elapsed time since the start
5. Or drag the scrubber at the bottom of the sidebar to move through the track point-by-point instead of clicking.

## Requirements for your GPX file

* Must contain `<trkpt>` elements with `lat`/`lon` attributes (standard for any GPS-recorded track, including Strava exports).
* Timestamps require a `<time>` tag on each point. Most devices/apps record this on every point, but some only log it periodically — if a point shows "no timestamp," that's a gap in the original recording, not a bug in the viewer.
* Elevation figures require an `<ele>` tag; if absent, elevation fields are simply omitted.

## Getting a GPX from Strava

Strava → open the activity → the "···" (more options) menu → Export GPX.

## Notes

* "Climbed so far" is total climb (sum of all uphill segments), not net elevation change — so it will keep increasing even on a rolling or out-and-back trail.
* The map uses OpenStreetMap tiles, so an internet connection is needed to see the map background, but all GPX parsing and timestamp lookup works fully offline.
