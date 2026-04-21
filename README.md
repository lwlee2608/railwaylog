# railwaylog

A drop-in replacement for `railway logs` that fixes two problems with the official CLI.

## Problems with `railway logs`

1. **Log stream gets cut off.** `railway logs` is meant to follow logs like `tail -f`, but the stream frequently drops and stops emitting new lines without exiting or reconnecting.
2. **`railway logs | humanlog` doesn't work.** Piping the output into [humanlog](https://github.com/humanlogio/humanlog) (or other log formatters) produces no useful output, so structured logs can't be reformatted for readability.

## What this does

`railwaylog` streams logs from Railway directly and:

- Reconnects automatically when the stream drops, so following logs stays reliable.
- Emits output in a form that pipes cleanly into `humanlog` and other log processors.
