# 2026-10-01: spiresRobot2026 replay-test findings

Found while checking the clone in `scratch/spiresRobot2026`, branch
`2026-03-20-Try-MoreRobustPyfrcTest` (the newest branch with a human commit). `uv sync` was run by Mike, as CLAUDE.md
requires. Nothing in the repo was changed.

## Baseline: everything CLAUDE.md lists passes
- `.venv/bin/robotpy test`: 12 passed, including `replay_test.py::test_log_and_replay_step1` and `step2`.
- `.venv/bin/ruff check`: all checks passed.
- `.venv/bin/ruff format --check --diff`: 145 files already formatted.
- `.venv/bin/mypy .`: no issues in 145 source files.

## Finding: the replay command in CLAUDE.md doesn't match the tests
- CLAUDE.md gives `robotpy test .\tests\replay_test.py::test_log_and_replay_step3 -- --runreplay`.
- Run as `.venv/bin/robotpy test tests/replay_test.py::test_log_and_replay_step3 -- --runreplay`, it gives
  `robotpy: error: unrecognized arguments: --runreplay` (exit 4). `robotpy test` takes pytest arguments only after `--`.
- `git grep` across all remote branches finds no `runreplay` under `tests/` on any branch. `test_log_and_replay_step3` exists
  only on `2026-03-30-debugging-test` and `2026-03-31-debugging-test-bus-error`.

## Finding: the replay test file fails when run on its own
- `.venv/bin/robotpy test -- tests/replay_test.py -v` gives 2 passed and 2 errors.
- The error is at the setup of `test_log_and_replay_step2`:
  `RuntimeError: A SparkMax instance has already been created with this device ID: 2` (`wrappers/wrapperedSparkFlex.py:42`).
- The full suite doesn't hit this error. Not investigated further.
