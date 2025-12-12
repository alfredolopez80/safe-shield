# Safe Research Agent System

An **Open Agent System** for researching and analyzing the Safe (Gnosis Safe) protocol and other blockchain ecosystems.

---

## What Is This?

This folder contains a specialized research system that transforms AI coding assistants (Claude Code, Gemini CLI, Codex) into expert blockchain research agents—no code required, only markdown files.

Instead of writing code, these agents:
- Extract and structure documentation from websites
- Perform deep technical analysis of blockchain protocols
- Generate comprehensive research reports
- Create comparison matrices across protocols
- Produce architecture diagrams and knowledge bases

---

## Quick Start

### For Safe Protocol Research

**Extract Safe documentation:**
```
/safe scrape https://docs.safe.global/home/what-is-safe SDK,Core,API
```

**Deep technical analysis:**
```
/safe research Safe SDK,Core,API
```

**Compare with other wallets:**
```
/safe research "Compare Safe with Argent and Braavos"
```

### Expected Outputs

After running agents, check these folders:

- **`output-research/`** - JSON knowledge bases, raw data
- **`output-reports/`** - Comprehensive markdown reports
- **`output-analysis/`** - CSV comparisons, architecture diagrams

Example files:
- `safe-knowledge-base-20251212.json`
- `safe-technical-analysis-20251212.md`
- `safe-components-20251212.csv`
- `safe-architecture-20251212.mmd`

---

## Available Agents

### 🌐 Web Scraper Agent
**Purpose**: Extract structured information from technical documentation

**Best for**:
- Mapping out API documentation
- Extracting SDK guides and references
- Building knowledge bases from docs
- Coverage analysis of documentation

**Trigger**: "scrape [URL]", "analyze documentation", "extract docs"

### 🔬 Research Blockchain Agent
**Purpose**: Deep technical analysis of blockchain protocols

**Best for**:
- Architectural analysis
- Smart contract security review
- Comparative protocol analysis
- Integration pattern documentation
- Risk assessment

**Trigger**: "research [protocol]", "analyze architecture", "compare protocols"

---

## How It Works

### The Open Agent Pattern

1. **Entry Points** (`CLAUDE.md`, `AGENTS.md`) point to `INSTRUCTIONS.md`
2. **INSTRUCTIONS.md** catalogs agents and routing logic
3. **Agent Files** (`agents/*.md`) define specialized behaviors
4. AI reads instructions and becomes that agent

No code. No APIs. No deployments. Just markdown files.

### Progressive Disclosure

- Only `INSTRUCTIONS.md` loads at conversation start
- Full agent definitions load on-demand when triggered
- Keeps context small, allows complex behaviors

---

## Folder Structure

```
open-agents/
├── README.md              # This file (human-readable intro)
├── INSTRUCTIONS.md        # Agent catalog and routing (AI reads this)
│
├── agents/                # Agent definitions
│   ├── web-scraper.md     # Documentation extraction agent
│   └── research-blockchain.md  # Technical analysis agent
│
├── tools/                 # Scripts created by agents
│   └── (automation tools)
│
├── source/                # Raw inputs
│   └── (URLs, notes, stubs)
│
├── output-research/       # Raw data extraction
│   └── (JSON knowledge bases)
│
├── output-analysis/       # Analytical outputs
│   └── (CSV, diagrams, metrics)
│
└── output-reports/        # Final deliverables
    └── (markdown reports)
```

---

## Use Cases

### For Developers
**Goal**: Integrate Safe into your application

1. Extract SDK documentation
2. Generate integration guide
3. Get code examples and patterns
4. Understand API surfaces

**Command**: `/safe scrape https://docs.safe.global "SDK"`

---

### For Security Researchers
**Goal**: Audit Safe's security model

1. Extract core architecture docs
2. Analyze smart contract security
3. Review audit history
4. Assess risks

**Command**: `/safe research "Safe security model"`

---

### For Protocol Analysts
**Goal**: Compare smart wallet solutions

1. Research multiple protocols
2. Generate comparison matrices
3. Identify trade-offs
4. Make recommendations

**Command**: `/safe research "Compare Safe, Argent, Braavos"`

---

## Complete Documentation

**For full details**, read `INSTRUCTIONS.md`:
- Complete agent descriptions
- Routing logic and triggers
- Workflow patterns
- Output formats
- Best practices
- Troubleshooting

---

## Example Workflow

### Comprehensive Safe Analysis

**Step 1: Extract Documentation**
```
/safe scrape https://docs.safe.global/home/what-is-safe SDK,Core,API
```
Outputs:
- `safe-knowledge-base-20251212.json`
- `safe-analysis-20251212.md`
- `safe-components-20251212.csv`

**Step 2: Deep Technical Analysis**
```
/safe research Safe "SDK,Core,API,Security"
```
Outputs:
- `safe-technical-analysis-20251212.md` (20,000+ words)
- `safe-architecture-20251212.mmd` (diagrams)

**Step 3: Review Outputs**
- Read reports in `output-reports/`
- Check structured data in `output-research/`
- View diagrams in `output-analysis/`

---

## Extending the System

### Add New Agents

This system is extensible. Create agents for:
- **Security Auditing**: Focused vulnerability detection
- **Economic Analysis**: Tokenomics and incentive modeling
- **Integration Testing**: SDK/API testing automation
- **Comparative Analysis**: Multi-protocol deep comparisons

### Add Automation Tools

Agents can create reusable scripts in `tools/`:
- Automated scraping for documentation updates
- Contract ABI extraction
- Diagram generation
- Report formatting

---

## System Requirements

**Works with**:
- Claude Code (recommended)
- Gemini CLI
- Codex

**Best Performance**:
- Use latest model versions
- Provide clear, specific instructions
- Review outputs and provide feedback
- Iterate on results

---

## File Naming Conventions

All outputs follow this pattern:
```
{project}-{type}-{YYYYMMDD}.{ext}
```

Examples:
- `safe-knowledge-base-20251212.json`
- `uniswap-technical-analysis-20251212.md`
- `multisig-comparison-20251212.csv`

---

## Support & Resources

### Safe Ecosystem
- 📚 [Documentation](https://docs.safe.global)
- 💻 [Core SDK](https://github.com/safe-global/safe-core-sdk)
- 🔐 [Smart Contracts](https://github.com/safe-global/safe-smart-account)

### Open Agent System
- 📖 [Specification](../OpenAgentDefinition.md)
- 🌐 [GitHub](https://github.com/bladnman/open-agent-system)

### Questions?
- Read agent files in `agents/` for detailed behaviors
- Check `INSTRUCTIONS.md` for complete system documentation
- Review `../OpenAgentDefinition.md` for the Open Agent pattern

---

## Version

- **System**: 1.0
- **Created**: 2025-12-12
- **Focus**: Safe Protocol Research
- **Agents**: 2 (Web Scraper, Research Blockchain)

---

*Transform AI coding assistants into specialized blockchain research tools using only markdown files.*
