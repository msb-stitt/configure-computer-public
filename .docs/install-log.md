# Install log

The running record of what was installed on this Mac and when. Times are local (EDT). Newest entries are at the bottom.

| Date / time | Item | Version | Method / source | Location | Notes |
|---|---|---|---|---|---|
| (pre-existing) | Homebrew | 7.0.7 | already installed | /opt/homebrew | |
| (pre-existing) | Xcode Command Line Tools (Apple git 2.54.0) | — | already installed | /Library/Developer/CommandLineTools | |
| (pre-existing) | Python 3.9.6 (system) | 3.9.6 | macOS built-in | /usr/bin/python3 | do not use for projects |
| 2026-10-01 ~05:58 | Peekaboo | 4.5.0 | `brew install steipete/tap/peekaboo` | /opt/homebrew/bin/peekaboo | GUI automation/screenshots; see [mac-gui-automation.md](mac-gui-automation.md) |
| 2026-10-01 ~05:58 | cliclick | (brew) | `brew install cliclick` | /opt/homebrew/bin/cliclick | mouse/keyboard CLI |
| 2026-10-01 06:21 | git | 2.56.0 | `brew install git` | /opt/homebrew/bin/git | global user "Mike S.B. Stitt" <OLD@EMAIL.ADDRESS>, default branch `main` |
| 2026-10-01 06:22 | uv / uvx | 0.12.21 | standalone installer `https://astral.sh/uv/install.sh` (saved as `install-media/uv-installer.sh`, sha256 `0722d6c4…36c3`) | ~/.local/bin/uv | update with `uv self update` |
| 2026-10-01 06:22 | Python (CPython) | 3.14.7 | `uv python install 3.14 --default` (python-build-standalone 20260929; archive saved in install-media, sha256 `44b4716f…f4f9`) | ~/.local/share/uv/python/, links in ~/.local/bin | `python`, `python3`, and `python3.14` all point here. ~/.local/bin comes before /usr/bin on PATH |
| 2026-10-01 06:23 | Oracle JDK 17 | 17.0.12 (build 17.0.12+8-LTS-286) | `https://download.oracle.com/java/17/archive/jdk-17.0.12_macos-aarch64_bin.tar.gz` (sha256 `d8866b36…a34c`, verified) extracted, no sudo | ~/Library/Java/JavaVirtualMachines/jdk-17.0.12.jdk | Last Oracle 17 release under the free NFTC license; 17.0.13+ needs an Oracle account. `JAVA_HOME` set in ~/.zprofile with `/usr/libexec/java_home -v 17` |
| 2026-10-01 06:24 | REV Hardware Client 2 | 1.4.2 | `https://rhc2.revrobotics.com/download/rev-hardware-client-1.4.2-mac-aarch64.zip` (sha256 `fbd3b961…b2c8`) | /Applications/REV Hardware Client 2.app | Notarized, REV Robotics LLC (3MTSGT5M96) |
| 2026-10-01 06:24 | PyCharm (unified; free tier replaces Community Edition) | 2026.2.3 | `https://download.jetbrains.com/python/pycharm-2026.2.3-aarch64.dmg` (sha256 verified against the .sha256 file) | /Applications/PyCharm.app | CE was discontinued after 2025.2.x. See [pycharm-community-edition.md](pycharm-community-edition.md) |
| 2026-10-01 06:25 | Android Studio Quail 4, 2026.1.4 Patch 1 | 2026.1.4.8 | `https://edgedl.me.gvt1.com/android/studio/install/2026.1.4.8/android-studio-quail4-patch1-mac_arm.dmg` (sha256 `1a339330…c066`) | /Applications/Android Studio.app | Notarized, Google LLC. First-run wizard not done yet. Set the Gradle JDK to 17 |
| 2026-10-01 06:25 | AdvantageScope | 26.0.2 | `https://github.com/Mechanical-Advantage/AdvantageScope/releases/download/v26.0.2/advantagescope-mac-arm64-v26.0.2.dmg` (sha256 `01022c3e…5434`) | /Applications/AdvantageScope.app | Log viewer for AdvantageKit, corbelsflightlog, and PyKit logs |
| 2026-10-01 06:26 | Android SDK command-line tools | 21.0 (build 15641748) | `https://dl.google.com/android/repository/commandlinetools-mac-15641748_latest.zip` (sha1 `b62a5d8c…6df`, verified against repository2-3.xml) | ~/Library/Android/sdk/cmdline-tools/latest | SDK licenses accepted with `sdkmanager --licenses` |
| 2026-10-01 06:26 | Android SDK packages | platform-tools 37.0.1, platforms;android-30, platforms;android-34, build-tools;35.0.0 | `sdkmanager` | ~/Library/Android/sdk | `ANDROID_HOME` and PATH set in ~/.zprofile |
| 2026-10-01 06:27 | ninja | 1.13.2 | `brew install ninja` | /opt/homebrew/bin/ninja | used by the stick-e-bot and biobuzz book builds |
| 2026-10-01 06:27 | Git clones | FtcRobotController v12.0, ftc31459-26-27-biobuzz, corbelsflightlog, stick-e-bot, spiresRobot2026 | `git clone` | ~/projects/ | `uv sync` run for spiresRobot2026 and stick-e-bot |
| 2026-10-01 06:37 | Android Studio first-run wizard | — | GUI (driven by Peekaboo): declined usage stats, chose Standard, used the existing SDK at ~/Library/Android/sdk | — | The wizard also installed **Android Emulator 37.1.11** (376 MB) into ~/Library/Android/sdk/emulator |
| 2026-10-01 12:55 | GitHub CLI (gh) | 2.102.0 | `brew install gh`. The bottle is saved as `install-media/gh--2.102.0.arm64_tahoe.bottle.tar.gz` (sha256 `c2ca0cdf…9ad8`) | /opt/homebrew/bin/gh | Not signed in yet. Mike runs `gh auth login`; that change goes in settings-log.md |
