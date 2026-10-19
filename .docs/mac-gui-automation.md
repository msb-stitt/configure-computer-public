# Mac GUI automation (for screenshots in how-to lessons)

- Ghostty has the **Screen & System Audio Recording** and **Accessibility** permissions (granted 2026-10-01).
- Tools: Peekaboo (`peekaboo`), cliclick, and the built-in `screencapture` and `osascript`.
- Always pass `--no-remote` to peekaboo. Its Bridge daemon doesn't have Accessibility; the local runtime uses Ghostty's permissions.
- Start apps with `open -a <App>`, because `peekaboo app launch` refuses cold launches.
- Click by label with a fresh snapshot each time:
  ```sh
  SNAP=$(peekaboo see --app Calculator --no-remote --json | python3 -c 'import json,sys;d=json.load(sys.stdin);d=d.get("data",d);print(d.get("snapshot_id") or d.get("snapshotId"))')
  peekaboo click "7" --app Calculator --snapshot "$SNAP" --no-remote
  ```
- Window-only screenshot for a lesson: `peekaboo see --app X --retina --no-elements --path out.png`
- Labeled element map: `peekaboo see --app X --annotate --path out.png`
- If the Mac locks, `peekaboo see` fails with "Screen capture is unavailable while the macOS GUI session is locked". To prevent this, turn off auto-lock and screen saver in System Settings → Lock Screen.
- When an app has more than one window (for example Android Studio's Welcome window), pass `--window-title "<title>"`.
- When Claude needs Mike to act, it runs `open -a Ghostty` to bring the terminal to the front.
- Moving windows around is safe for Peekaboo clicks by label, because each click takes a fresh snapshot. Coordinate clicks (`cliclick c:x,y`, used for Android Studio's unlabeled dialog buttons and for macOS permission prompts) are not safe: they use positions from a screenshot taken seconds earlier. Typed text goes to whichever window has focus.
- Screen coordinates are points, so divide the screenshot pixels by 2 (Retina). The 3024×1964 capture maps to 1512×982 points.
