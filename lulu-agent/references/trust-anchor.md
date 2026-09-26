# Verify the installed product

1. Accept only `/Applications/Lulu.app` and its `/Applications/Lulu.app/Contents/MacOS/lulu-agent-cli`, using the current-user `com.lulu.transcribe.agent-core` service.
2. Run `python3 -B scripts/verify_lulu.py` from this Skill directory, with no arguments. It checks generation 9, committed installation materials, the exact external manifest bytes, the full App tree, constrained relative links and native signatures for delivery v2. It does not import App code or read Keychain. Core independently verifies HMAC ownership before business.
3. Continue only with `lulu.install-verification/v2`, `verified=true`, candidate generation 9 and CLI protocol `1.0.0`. Query actual installed capabilities next. Unknown versions fail closed.
4. This public Skill is optional and is not part of Lulu's signed installation. It does not require `~/.local/bin/lulu` or `~/.agents/skills/lulu-agent`. The App's bundled Skill resources remain part of the verified App tree.
5. Never discover an executable via PATH, another App, a socket, old Core or caller-provided identity. Missing Team ID is normal for the currently supported ad-hoc delivery; it is not evidence of author identity.
6. On mismatch stop with zero business effect. Ask the user to repair Lulu with its complete official delivery folder. Never edit receipts or manufacture a manifest. Existing legacy managed copies in `~/.agents/skills/lulu-agent` must not be overwritten or removed manually; they belong to that installation's receipts.

This checks damage and mixed product versions within a trusted macOS account. It does not defend against malicious software that already controls that account. Independent Skill removal leaves product files and service untouched.
