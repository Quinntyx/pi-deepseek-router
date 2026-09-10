# pi-deepseek-router

Route DeepSeek models across configured providers with quota-aware failover.

The Flash routes use DeepSeek V4.1 Flash (`deepseek-flash` on OpenCode Go and
`deepseek/deepseek-v4.1-flash` on OpenRouter). They are exposed as
`deepseek-router/deepseek-v4.1-flash` (200K cap) and
`deepseek-router/deepseek-v4.1-flash-1m`. Delegated OpenCode requests retain Pi's
stable `x-opencode-session` header for routing and prompt-cache affinity.

Served turns are re-stamped with the router's own `provider`/`model` identity on
the way out (`usage`/`cost` are forwarded untouched, so spend is still
attributed to the upstream that served the turn). Pi rebuilds a session's model
from its last assistant entry when resuming or forking it, so without this the
upstream that served a turn would become that session's model: `/fork` (and
`/undo`) would silently switch the user off the router, and the router would no
longer recognise the session model as one of its tiers.

Install as a Pi git package:

```json
"git:git.quinntyx.dev/quinntyx/pi-deepseek-router"
```
