# Blockchain Research & Code Review Agent System

An **Open Agent System** for blockchain research, code auditing, and technical documentation—specialized in Safe (Gnosis Safe) protocol and Web3 ecosystems.

---

## What Is This?

This folder contains a specialized system that transforms AI coding assistants (Claude Code, Gemini CLI, Codex) into expert blockchain research, code review, and technical publishing agents—no code required, only markdown files.

These agents:

- Extract and structure documentation from websites
- Perform deep technical analysis of blockchain protocols
- Audit code for AI patterns, security issues, and quality
- Generate comprehensive research reports with citations
- Create professional Notion posts with Mermaid diagrams
- Produce comparison matrices across protocols
- Review smart contracts for security vulnerabilities

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

**Command**: `/safe scrape [URL] [focus]`

---

### 🔬 Research Blockchain Agent

**Purpose**: Deep technical analysis of blockchain protocols

**Best for**:

- Architectural analysis
- Smart contract security review
- Comparative protocol analysis
- Integration pattern documentation
- Risk assessment

**Command**: `/safe research [protocol] [focus]`

---

### 🛡️ AI Output & Code Review Super-Auditor

**Purpose**: Ensemble-style AI detector and code quality auditor

**Best for**:

- Detecting AI-generated patterns in code/docs
- Security vulnerability identification
- Code quality assessment (maintainability, testing)
- Hallucination and factual accuracy verification
- Comprehensive code review with concrete fixes

**Command**: `/review audit [artifact] [focus]`

---

### 📝 Technical Research to Notion Post Generator

**Purpose**: Transform blockchain research into professional Notion posts

**Best for**:

- Structured Notion post creation with Mermaid diagrams
- Citation and reference management
- Senior technical audience targeting
- Analytical narrative with coherent thesis
- Comparative analysis with tables and matrices

**Command**: `/notion create-post [source-material] [focus]`

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
│   ├── web-scraper.md                      # Documentation extraction
│   ├── research-blockchain.md              # Technical analysis
│   ├── ai-code-auditor.md                  # Code review & AI detection
│   └── notion-technical-post-generator.md  # Notion post creation
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
├── output-analysis/       # Analytical outputs & audit reports
│   └── (CSV, diagrams, metrics, audits)
│
└── output-reports/        # Final deliverables
    └── (markdown reports, Notion posts)
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

- **System**: 1.1
- **Created**: 2025-12-12
- **Last Updated**: 2025-12-12
- **Focus**: Blockchain Research, Code Review, Technical Documentation
- **Agents**: 4 (Web Scraper, Research Blockchain, AI Code Auditor, Notion Post Generator)
- **Target Users**: Developers, Researchers, Security Auditors, Technical Writers

---

*Transform AI coding assistants into specialized blockchain research, code review, and technical publishing tools using only markdown files.*
