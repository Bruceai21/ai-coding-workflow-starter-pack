# AGENTS.md - Home-lab dashboard example

## Project purpose

This is a LAN-only dashboard for monitoring a home-lab or personal ops workspace.

## Stack

- Node/FastAPI/Python stdlib server
- LAN-only binding
- Read-only status cards by default

## Safety rules

- Do not expose publicly without authentication.
- Do not show secrets, tokens, raw env vars, or private file contents.
- Start read-only before adding controls.
- Ask before changing services, ports, system packages, or firewall rules.

## Verification

```bash
# adapt to stack
npm run build
curl -fsS http://127.0.0.1:PORT/health
systemctl --user status SERVICE_NAME
```

## Good dashboard cards

- service status
- disk/memory/load
- recent automation activity
- backup status
- project links

## Done means

- Service is reachable only where intended
- Health endpoint works
- No secrets are displayed
- Restart behavior is known
