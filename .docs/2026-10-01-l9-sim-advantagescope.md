# 2026-10-01: L9Drive24OpMode in the simulator, watched in AdvantageScope

The run is `ftc-claude/ftc31459-26-27-biobuzz` on `solutions-03` at `13bfea1`. The frames and the
flight log are in `scratch/l9-sim-capture/`, which is gitignored.

## Build gate (watched)
- `./gradlew :TeamCode:assembleDebug`: BUILD SUCCESSFUL.
- `./gradlew :TeamCode:test`: 19 classes, 183 tests, 0 failures (read from the XML).
- `./gradlew :TeamCode:testLessons`: 66 tests, 0 failures.

## What worked
- **Command:** `./gradlew :TeamCode:simRun --args="lessons.L9Drive24OpMode"`. The name is the class
  path under `org.firstinspires.ftc.teamcode`. A bare `L9Drive24OpMode` gives
  `simRun: no OpMode called "L9Drive24OpMode"...`. Note that this branch's SIM.md still shows the
  older bare-name form.
- **Connect live:** start AdvantageScope first and choose **File → Connect to Simulator →
  NetworkTables 4**. The title reads `127.0.0.1 (Searching)` until simRun starts, and then it shows
  16 fields under `sim`.
- **Field:** in the 2D Field tab, the **Field** drop-down has a separate **FTC Fields** group. Pick
  **2026-2027 Field**. AdvantageScope shows an "Experimental Feature" notice for FTC fields; click
  **OK**.
- **Pose:** drag `sim/Pose` (live) or `Robot/Pose` (log) onto the **Poses** panel. Drag
  `Robot/Path` there too, then click its icon and choose **Trajectory** to draw the planned line.
- **The robot finishes its drive in about 1 s.** Live, it had already reached `HOLD` before the
  field was set up. A log replay is better for capture.
- **Log replay:** stop simRun with Ctrl-C (SIGINT), which closes the WPILOG and prints
  `Flight logs: <dir>`. Open the file with `open -a AdvantageScope <file>.wpilog`; it opens in a
  new window. Click the timeline to scrub.
- **Line graph:** drag `Robot/Pose/translation/x` and `y` onto **Left Axis**. Scroll vertically
  over the graph to zoom and horizontally to pan.
- **Driving AdvantageScope:** it's Electron, so accessibility doesn't expose its contents.
  Peekaboo can capture the window, but clicks and drags have to go by screen coordinate
  (`cliclick`).

## What the log shows (read with wpiutil's DataLogReader)
- x goes from 1.5621 m to 0.9525 m: **23.999 in** of travel. y stays at 0 m and heading at π rad.
- It overshoots 0.537 in at 0.810 s and is within 1 mm of its final position from 1.119 s.
- `Robot/Path` has 21 points while `Mode` is `FOLLOW`, and no values once it is `HOLD`.

## Observations, not fixed
- simRun ran on Gradle's own JetBrains JDK 17 (`~/.gradle/jdks/jetbrains_s_r_o_-17-...`), not on
  Oracle 17.0.12. The project's toolchain resolver picks it.
