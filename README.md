# Ring event listener watchdog (test build)

Temporary test build of Home Assistant's built-in Ring integration for
[home-assistant/core#157764](https://github.com/home-assistant/core/issues/157764)
(doorbell and motion events silently stop until the integration is reloaded).

It overrides the built-in `ring` integration with the Home Assistant 2026.10.1
version plus:

- a watchdog that restarts the Ring event listener when it stops, marks event
  entities unavailable meanwhile, and raises a repair issue if it keeps failing
  ([branch](https://github.com/mogarber/ha-core/tree/ring-listener-watchdog));
- `ring-doorbell` built from
  [mogarber/python-ring-doorbell@test/listener-health](https://github.com/mogarber/python-ring-doorbell/tree/test/listener-health),
  which combines
  [python-ring-doorbell#559](https://github.com/python-ring-doorbell/python-ring-doorbell/pull/559)
  with [python-ring-doorbell#555](https://github.com/python-ring-doorbell/python-ring-doorbell/pull/555)
  and [python-ring-doorbell#556](https://github.com/python-ring-doorbell/python-ring-doorbell/pull/556).

This is for testing only. Remove it from HACS and restart to go back to the
built-in integration; the existing Ring config entry is reused either way.
