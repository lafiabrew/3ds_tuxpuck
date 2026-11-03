# TuxPuck for Nintendo 3DS

**WIP — implementation lane assigned; not a playable/released/device-tested app yet.**

Genuine TuxPuck adaptation: compact air hockey with native stylus/buttons, real engine/session and restart.

Part of [lafiabrew](https://github.com/lafiabrew). UniqueId `0x0D3FE`, ProductCode `CTR-P-TUXP`. Each app is a separate repository. Native logging reuses the reviewed journal with per-app integration tests; media/replays are new immutable files, not replacements of user saves. No private capture/upload by default.

## Build status and source license
`make journal-check` is a real shared-runtime signal only. Current `make test`, `make 3ds` and `make verify-3ds` deliberately fail until the lane implements actual behavior and artifacts. Passing the smoke is not a completed app.

New original code/runtime scaffold is MIT. Actual engine code and assets must retain their separately checked upstream licenses; no game data is bundled by this scaffold.

## Required first-release gate
```sh
make test && python3 -m unittest discover -s tests -p test_contract.py -v && make 3ds && make verify-3ds && git diff --check
```

Engine proof additionally requires `python3 tests/verify_engine.py`, including a compiled ARM launcher-negative control and real upstream object/map/symbol provenance.

See [scope](specs/app.md), [operational instructions](AGENTS.md), [shared safety](specs/CONSTITUTION.md), and [plan](IMPLEMENTATION_PLAN.md). All current status is WIP until verified; no 3DS hardware claims from host models.
