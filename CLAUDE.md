**CRITICAL: Read `open-agents/INSTRUCTIONS.md` immediately.**

---

# Safe Shield - Blockchain Research System

This project uses an **Open Agent System** for researching and analyzing the Safe (Gnosis Safe) protocol and blockchain ecosystems.

## Quick Reference

| Agent | Command | Purpose |
|-------|---------|---------|
| Web Scraper | `/safe scrape [URL] [focus]` | Extract documentation, build knowledge bases |
| Research Blockchain | `/safe research [topic] [focus]` | Deep technical analysis, architecture review |

## Common Tasks

### Research Safe Protocol
```
/safe scrape https://docs.safe.global/home/what-is-safe SDK,Core,API
/safe research Safe SDK,Core,API
```

### Compare Protocols
```
/safe research "Compare Safe with Argent"
```

### Security Analysis
```
/safe research "Safe security model and audit history"
```

## Output Locations
- **Research Data**: `open-agents/output-research/` (JSON knowledge bases)
- **Reports**: `open-agents/output-reports/` (Markdown technical reports)
- **Analysis**: `open-agents/output-analysis/` (CSV, diagrams)

---

For complete documentation, see `open-agents/INSTRUCTIONS.md` and `open-agents/README.md`.
