# Jev Usage Router & Circuit Breaker

> "If your autonomous agent repeats the same error 3 times, it's not a model problem. It's an architecture problem."

An autonomous agent circuit breaker skill implementing the 5-action decision router pattern (inspired by TypeSafe Jev System 1 and Grok Bot architecture).

It intercepts costly, recursive, or irreversible operations across **Claude Code**, **Antigravity**, **Codex**, and **Hermes** before they burn tokens or get trapped in repetitive loops.

---

## ⚡ Quick Install

Install across your coding agents via [`npx skills`](https://github.com/vercel-labs/skills):

```bash
# Universal install
npx skills add mommocmoc/jev-usage-router

# Specific agent installs
npx skills add mommocmoc/jev-usage-router -a claude-code -g -y
npx skills add mommocmoc/jev-usage-router -a antigravity -g -y
npx skills add mommocmoc/jev-usage-router -a codex -g -y
```

---

## 🛡️ The 5 Circuit-Breaker Actions

1. `proceed`: Safe to execute as planned.
2. `reuse_cache`: Local artifacts already exist; bypass expensive headless browsers or external fetches.
3. `stop_retry`: Same error repeated twice; break execution and report root cause instead of spinning.
4. `research_capped`: 3–5 solid references gathered; cap further web browsing and start synthesizing.
5. `ask_human`: External publishing, sending emails, or destructive file operations must pause for human confirmation.

---

## License

MIT © [mommocmoc](https://github.com/mommocmoc)
