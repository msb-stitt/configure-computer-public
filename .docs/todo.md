# TODO

Running task list. `[x]` = done, `[ ]` = pending, `[~]` = in progress or partial.

## Machine setup
- [x] GUI automation for screenshots (Peekaboo, cliclick, Ghostty permissions) — 2026-10-01
- [x] Install git (Homebrew 2.56.0) and set the global identity "Mike S.B. Stitt" — 2026-10-01
- [x] Make `configure-computer` a git repo, with `.docs/` and `install-media/` — 2026-10-01
- [x] Stop the screen from auto-locking (Lock Screen set to Never; screen saver idleTime 0). See [settings-log.md](settings-log.md) — 2026-10-01

## FTC / robotics dev environment
- [x] Research the FTC Android Studio setup and review the four reference repos ([ftc-dev-environment.md](ftc-dev-environment.md)) — 2026-10-01
- [x] Oracle JDK 17.0.12 (the last version downloadable without an Oracle login), with JAVA_HOME in ~/.zprofile — 2026-10-01
- [x] Android Studio Quail 4 (2026.1.4 Patch 1) — 2026-10-01
- [x] Android SDK: cmdline-tools, platform-tools, android-30, android-34, build-tools 35.0.0; ANDROID_HOME in ~/.zprofile — 2026-10-01
- [x] Android Studio first-run wizard (Standard; it also added the emulator) — 2026-10-01
- [x] Clone FtcRobotController v12.0 to ~/projects. `./gradlew assembleDebug` passes with JDK 17 — 2026-10-01
- [x] Open FtcRobotController in Android Studio and set Gradle JDK = Oracle 17.0.12. Gradle sync passes; AGP upgrade prompt declined — 2026-10-01
- [x] REV Hardware Client 2 v1.4.2 — 2026-10-01
- [x] Launch REV Hardware Client 2 for the first time: the first launch hung and Mike force-quit it; the relaunch works and shows "No Hardware Detected" — 2026-10-01
- [ ] Check REV Hardware Client 2 with a Control Hub over USB and over Wi-Fi (needs hardware). If Wi-Fi discovery fails, check Local Network permissions (see settings-log 07:01)
- [x] AdvantageKit: it's a Gradle library (FRC only) with nothing to install on the machine, and none of the reference repos use it. The FTC community port is PsiKit — 2026-10-01
- [x] AdvantageScope 26.0.2 (log viewer) — 2026-10-01
- [x] uv 0.12.21 — 2026-10-01
- [x] Python 3.14.7 (through uv, set as default). Note: python.org has 3.14.8; uv will pick it up when python-build-standalone ships it — 2026-10-01
- [x] PyCharm 2026.2.3, unified free tier (Community Edition is discontinued; see [pycharm-community-edition.md](pycharm-community-edition.md)) — 2026-10-01
- [x] Launch PyCharm for the first time: Mike accepted the JetBrains User Agreement and allowed local network access — 2026-10-01
- [x] ninja 1.13.2 (brew) — 2026-10-01
- [x] Clone the reference repos to ~/projects and check that they build — 2026-10-01
  - ftc31459-26-27-biobuzz: `:TeamCode:assembleDebug` passes
  - corbelsflightlog: `./gradlew build` passes
  - spiresRobot2026: `uv sync` and `uv run robotpy test` pass (12 passed)
  - stick-e-bot: `uv sync`, `playwright install chromium`, and `ninja check` pass (37 readability notes above grade 8, informational only)

## Reference repos in `scratch/`
- [x] Install GitHub CLI `gh` 2.102.0 — 2026-10-01
- [x] Mike signed in with `gh auth login` as msb-stitt — 2026-10-01
- [x] Clone `msb-stitt/ftc-claude` into `scratch/` with a local branch for each of its 3 remote branches, switch to the newest (`student-motors-plan`), move `corbelsflightlog` into it, move `ftc31459-26-27-biobuzz` into it renamed to `ftc31459-26-27-biobuz` (the name its `.gitignore`, README and constitution use), and read its constitution — 2026-10-01
- [ ] Evaluate whether these are the right things to do to spiresRobot2026 (details: [2026-10-01-spires-replay-findings.md](2026-10-01-spires-replay-findings.md)):
  - The replay command in CLAUDE.md doesn't match the tests. It gives `robotpy test .\tests\replay_test.py::test_log_and_replay_step3 -- --runreplay`. No branch defines `--runreplay`, and `step3` only exists on `2026-03-30-debugging-test` and `2026-03-31-debugging-test-bus-error`. On every other branch the replay is `step1` then `step2`, and both pass in the full run.
  - The replay test fails when run on its own. `robotpy test -- tests/replay_test.py` gives 2 passed and 2 errors. `step2` can't set up because "A SparkMax instance has already been created with this device ID: 2" (`wrappers/wrapperedSparkFlex.py:42`). The full suite doesn't hit this. It looks related to this branch's goal of making the pyfrc tests more robust, but I haven't investigated further.
- [x] Fork `ftc31459-26-27-biobuzz`, `corbelsflightlog` and `stick-e-bot` from MikeStitt into msb-stitt, public, every branch matching its parent. Clones now push only to msb-stitt; `upstream` (MikeStitt) and `spires` (spiresfrc9106) are fetch-only — 2026-10-01
- [x] ftc-claude: subproject folder renamed `ftc31459-26-27-biobuzz`, and constitution 1.2.0 (commit as Mike S.B. Stitt; two-z name) on branch `biobuzz-rename`, pushed to msb-stitt/ftc-claude at `95ca285` — 2026-10-01
- [x] Onshape: `stickbot-cylinder-test` (owner msb stitt) built over REST with stick-e-bot's tooling, 100 mm × 100 mm, driven by `#diameter` and `#height`; version `cylinder 100 mm x 100 mm` `d8afe22d042190584f6aacbd` — 2026-10-01
- [ ] stick-e-bot: Mike to move or share the old Onshape documents to msb@stitt.cc (`access.onshape.msb_account` on branch `onshape-msb-account`, pushed to msb-stitt/stick-e-bot at `187df8d`)
- [x] biobuzz: SIM.md's AdvantageScope menu path and replay paragraph, `f852306` on `lessons-03` and carried as `8e2310d` to `solutions-03`, pushed to msb-stitt/ftc31459-26-27-biobuzz — 2026-10-01
- [x] biobuzz: the 14 `lessons-03` commits carried to `solutions-03` (Temurin pin, CI, SIM.md, README, guide), gate 181/0 and lessons 66/0, pushed to msb-stitt at `2a390b0` — 2026-10-01
- [x] biobuzz: `lessons-04` (from `lessons-03`, `f852306`) and `solutions-04` (from `solutions-03`, `2a390b0`) created; MikeStitt's `-03` merged in (already up to date); build and gate green on both, lessons 66/0 on solutions-04 and 54 of 66 failing by design on lessons-04; pushed to msb-stitt — 2026-10-01
- [x] biobuzz: MikeStitt's `lessons-no-serial` and `solutions-no-serial` (one commit each, "Accept a gamepad that reports no serial number.") merged into `lessons-04` (`ec16cda`) and `solutions-04` (`48bd7d8`); gate 183/0 on both, lessons 66/0 on solutions-04, 54 of 66 failing by design on lessons-04; pushed to msb-stitt — 2026-10-01
- [x] Deleted the first-morning clones in ~/projects (corbelsflightlog, ftc31459-26-27-biobuzz, FtcRobotController, spiresRobot2026, stick-e-bot). They were clean, with no unpushed work, and still pointed at MikeStitt/spiresfrc9106. The live clones are under scratch/ — 2026-10-02
- [x] Deleted scratch/biobuzz-solutions-03. It was clean, with no unpushed work; its job is covered by scratch/ftc-claude/ftc31459-26-27-biobuzz — 2026-10-02

## Project organization
- [x] Moved scratch/spiresRobot2026 into scratch/ftc-claude/spiresRobot2026. It was clean, with no unpushed work, on `2026-03-20-Try-MoreRobustPyfrcTest` — 2026-10-02
- [ ] Decide: fork spiresRobot2026 to msb-stitt and repoint its remotes (`origin` = msb-stitt; `spiresfrc9106` fetch-only)? Its CLAUDE.md bars Claude from git state changes, so this needs Mike's explicit go-ahead
- [x] spiresRobot2026 added to ftc-claude's constitution (1.3.0) under that contract including its CLAUDE.md, with its four CI gates; conflicts go to ftc-claude's open-work.md (first one: `contract.spires.git_state`). On branch `newcomputer01`, `bdf0d94`, pushed to msb-stitt/ftc-claude — 2026-10-02
- [x] ftc-claude `.gitignore` ignores `/spiresRobot2026` (`b2b474e` on `newcomputer01`) — 2026-10-02
- [ ] Mike: rebuild spiresRobot2026's venv after the moves (uv bakes in absolute paths): `cd ~/projects/ftc-claude/spiresRobot2026 && rm -rf .venv && uv sync`
- [x] Moved scratch/ftc-claude and scratch/stick-e-bot up to ~/projects/ftc-claude and ~/projects/stick-e-bot. Rebuilt stick-e-bot's `.venv` (`uv sync`) and corbelsflightlog's logcheck `.venv` (7 tests OK), and stopped the Gradle daemon. Older entries name the scratch/ paths as they were at the time — 2026-10-02
- [ ] Decide: is configure-computer a third operating point with its own `.claude/rules/constitution.md` and `active-plan.md`?
- [ ] Decide: where the project-organization log lives (ftc-claude, configure-computer, or split). No layout document: remotes and live branches come from git and the plans (Derive, don't maintain)
- [ ] Decide: pin corbelsflightlog's daemon JVM to Temurin 17 (`./gradlew updateDaemonJvm --jvm-version=17 --jvm-vendor=adoptium`) on a feature branch
- [ ] Correct stale todo lines: the FtcRobotController lines (that clone is deleted), and the ftc-claude clone line's one-z `biobuz`
- [x] Created private `msb-stitt/configure-computer` on GitHub as `origin`; pushed `main` at
  `d17df0a` — 2026-10-14
