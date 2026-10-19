# FTC / robotics dev environment on this Mac

Research done 2026-10-01 for the 2026-27 season (BIOBUZZ).

## Versions
- **FTC SDK:** FtcRobotController **v12.0** (released 2026-09-12). Gradle 9.1.0, AGP 8.13.2, compileSdk 30, minSdk 24, targetSdk 28, Java 1.8 source/target.
  - Requires **Android Studio Narwhal 3 Feature Drop or later**. Installed: Quail 4 (2026.1.4 Patch 1).
  - **Do not accept Android Studio's prompts to upgrade or downgrade AGP or Gradle.**
- **Java:** the FTC docs say Android Studio's bundled JDK (JBR 21) is incompatible with the FtcRobotController workspace, so use **JDK 17**. In Studio, open Settings → Build, Execution, Deployment → Build Tools → Gradle and set **Gradle JDK** to the Oracle 17.0.12 JDK in `~/Library/Java/JavaVirtualMachines/jdk-17.0.12.jdk`.
- **Docs:** https://ftc-docs.firstinspires.org/en/latest/programming_resources/android_studio_java/install/install.html

## AdvantageKit
- AdvantageKit (Team 6328, Littleton Robotics) is FRC/WPILib only. It's a Gradle library dependency, not something you install on the machine. There is no official FTC port.
- A community FTC port is **PsiKit**: https://github.com/PsiLynx/PsiKit (`maven { url 'https://repo.dairy.foundation/releases' }`, `org.psilynx.psikit:core` and `:ftc`).
- **None of the reference repos use AdvantageKit or PsiKit:**
  - biobuzz logs with `corbelsflightlog`, a WPILOG writer.
  - spiresRobot2026 uses `pykit`, a Python AdvantageKit-style logger.
- All of them produce logs for **AdvantageScope**, which is installed.

## Reference repos (cloned to ~/projects)
| Repo | What | Toolchain | Build / test |
|---|---|---|---|
| ftc31459-26-27-biobuzz | FTC team code (Java) | Gradle **8.14.3** (held back because Sloth hot-reload breaks on Gradle 9), AGP 8.13.2, TeamCode compileSdk 34, JDK 17 | `./gradlew :TeamCode:assembleDebug`, `test`, `testLessons`, `simRun` (sends to AdvantageScope through NT4). Book: `ninja book` (sphinx in `book/.venv`). See README, PANELS.md, SIM.md. "Deploy Sloth" run configurations need setting up by hand |
| corbelsflightlog | FTC library: WPILOG logging for AdvantageScope | Gradle 8.14.3, daemon JVM 17 (foojay), `:ftc` module is an Android lib (compileSdk 34) | `./gradlew build`; published on JitPack |
| stick-e-bot | Onshape CAD course (Python) | Python ≥3.12, uv, ninja | `uv sync`, `uv run playwright install chromium`, `ninja check` |
| spiresRobot2026 | FRC robot (Python/RobotPy) | Python **3.14.\***, uv, robotpy 2026.2.2 | `uv sync`, `uv run robotpy sync`, `uv run robotpy test`, `uv run robotpy sim` |
