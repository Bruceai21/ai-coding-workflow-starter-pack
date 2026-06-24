# AGENTS.md - Python automation example

## Project purpose

This is a small Python automation project. It should be deterministic, logged, and safe to run from cron.

## Stack

- Python 3.11+
- virtual environment
- requests / pyyaml as needed
- cron or systemd timer

## Commands

```bash
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
python -m py_compile *.py
pytest -q
```

## Automation rules

- Stay silent when idle if used in cron.
- Log errors clearly.
- Use env vars for settings.
- Never hard-code secrets.
- Keep state files small and human-readable.

## Safety rules

Ask before adding destructive actions, external sends, credential changes, or service changes.

## Done means

- Script runs manually
- Idle behavior is verified
- Error behavior is understandable
- Cron/service instructions are documented
