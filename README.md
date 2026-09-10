# pi-deepseek-router

Route DeepSeek models across configured providers with quota-aware failover.

The Flash routes use DeepSeek V4.1 Flash (`deepseek-flash` on OpenCode Go and
`deepseek/deepseek-v4.1-flash` on OpenRouter). They are exposed as
`deepseek-router/deepseek-v4.1-flash` (200K cap) and
`deepseek-router/deepseek-v4.1-flash-1m`. Delegated OpenCode requests retain Pi's
stable `x-opencode-session` header for routing and prompt-cache affinity.

Install as a Pi git package:

```json
"git:git.quinntyx.dev/quinntyx/pi-deepseek-router"
```
