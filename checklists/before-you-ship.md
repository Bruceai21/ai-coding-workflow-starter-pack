# Before you ship

A short pre-launch checklist for vibe-coded apps.

- [ ] I can explain what the app does in plain English.
- [ ] I know what data it collects and where that data goes.
- [ ] No secrets are committed to Git.
- [ ] Auth and permissions were tested with bad/direct requests.
- [ ] Database rules were reviewed.
- [ ] The app builds from a clean install.
- [ ] Core user flows were tested on mobile and desktop.
- [ ] Error states do not leak private details.
- [ ] Monitoring or logging exists for launch issues.
- [ ] Backup/rollback path is known.

If you cannot check the security/auth/data boxes, do not call it production-ready.
