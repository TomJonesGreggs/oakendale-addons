# Oakendale add-ons

Config-only variants of upstream [homeassistant-ai/ha-mcp](https://github.com/homeassistant-ai/ha-mcp) add-ons, so a second
instance can run alongside the main one under its own slug. Purpose: give the Oakendale planner agent (#185) its own
MCP server whose Tool Security Policies fence its writes to the eight `agent_writable` helpers.

| Folder | Slug | Source |
|---|---|---|
| `ha_mcp_agent/` | `ha_mcp_agent` | upstream `homeassistant-addon-dev/config.yaml`, image-based (pulls the published dev image) |
| `ha_mcp_webhook_proxy_agent/` | `ha_mcp_webhook_proxy_agent` | verbatim copy of upstream `homeassistant-addon-webhook-proxy/` (built locally; upstream has no published image) |

## Keeping in step with upstream
`ha_mcp_agent/config.yaml` must track upstream dev's `version:` and `image:` lines. The proxy folder is a copy; re-copy it
when upstream's proxy version moves. Nothing here holds secrets: `secret_path` and OAuth creds live in the add-on options in HA.

Add to HA: Settings → Add-ons → Add-on Store → ⋮ → Repositories → `https://github.com/TomJonesGreggs/oakendale-addons`.
