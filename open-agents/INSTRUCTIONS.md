# Safe Research Agent System

An Open Agent System specialized in researching, analyzing, and documenting blockchain protocols, with initial focus on Safe (Gnosis Safe) ecosystem.

---

## How This System Works

This is an **Open Agent System** - a structure that transforms AI coding assistants into specialized research agents using only markdown files.

### Three-Layer Architecture

1. **Entry Points** (`CLAUDE.md`, `AGENTS.md`, `GEMINI.md`) point to this file
2. **This File** (`INSTRUCTIONS.md`) catalogs available agents and routing logic
3. **Agent Files** (`agents/*.md`) load on-demand when triggered

This pattern keeps context small while allowing complex agent behaviors.

---

## Project Structure

```
safe-shield/
├── CLAUDE.md                          # Entry point (with pointer to this file)
├── AGENTS.md                          # Entry point for Codex
│
├── .claude/commands/safe/             # Slash commands for Claude Code
│   ├── scrape.md                      # /safe scrape command
│   └── research.md                    # /safe research command
│
└── open-agents/                       # Agent system container
    ├── README.md                      # Human-readable intro
    ├── INSTRUCTIONS.md                # This file (agent catalog)
    │
    ├── agents/                        # Agent definitions
    │   ├── web-scraper.md             # Documentation scraping agent
    │   └── research-blockchain.md     # Technical research agent
    │
    ├── tools/                         # Scripts created by agents
    │   └── (future automation scripts)
    │
    ├── source/                        # Raw inputs and research notes
    │   └── (user-provided stubs, URLs, notes)
    │
    ├── output-research/               # Raw data extraction
    │   └── (JSON knowledge bases, raw scrapes)
    │
    ├── output-analysis/               # Analytical outputs
    │   └── (CSV comparisons, diagrams, metrics)
    │
    └── output-reports/                # Final deliverables
        └── (markdown reports, technical analyses)
```

---

## Available Agents

### 1. Web Scraper Agent (`agents/web-scraper.md`)

**Purpose**: Extract and structure information from technical documentation websites.

**Specialized for**:
- Navigating complex documentation hierarchies
- Extracting API specifications, SDK docs, and guides
- Generating structured outputs (JSON, Markdown, CSV)
- Building comprehensive knowledge bases from web sources

**When to use**:
- User asks to "scrape" or "analyze" documentation
- User wants to "extract" or "map out" documentation
- User provides a documentation URL and wants structured data
- User needs comprehensive documentation coverage analysis

**Output locations**:
- JSON: `output-research/{project}-knowledge-base-{date}.json`
- Markdown: `output-reports/{project}-analysis-{date}.md`
- CSV: `output-analysis/{project}-components-{date}.csv`

**To use this agent**: Read `open-agents/agents/web-scraper.md`

**Slash command**: `/safe scrape [URL] [focus areas]`

---

### 2. Research Blockchain Agent (`agents/research-blockchain.md`)

**Purpose**: Conduct deep technical analysis of blockchain protocols, smart contracts, and Web3 systems.

**Specialized for**:
- Architectural analysis of blockchain protocols
- Smart contract security and mechanism review
- Comparative analysis across similar protocols
- Economic model and tokenomics evaluation
- Integration and developer experience assessment
- Risk assessment and security auditing

**When to use**:
- User asks to "research" or "analyze" a blockchain protocol
- User wants "technical analysis" or "deep dive"
- User needs "comparison" between protocols
- User asks "how does [protocol] work" technically
- User needs "security analysis" or "risk assessment"
- User wants to understand integration patterns

**Output locations**:
- Technical Report: `output-reports/{protocol}-technical-analysis-{date}.md`
- Comparison: `output-analysis/{topic}-comparison-{date}.csv`
- Diagrams: `output-analysis/{protocol}-architecture-{date}.mmd`

**To use this agent**: Read `open-agents/agents/research-blockchain.md`

**Slash command**: `/safe research [protocol/topic] [focus areas]`

---

## Routing Logic

| User Request | Agent to Use | Notes |
|--------------|--------------|-------|
| "Scrape Safe documentation" | Web Scraper | Extracts structured data |
| "Analyze Safe docs from [URL]" | Web Scraper | Start with URL, extract everything |
| "Map out Safe SDK documentation" | Web Scraper | Focus on SDK sections |
| "Research Safe protocol" | Research Blockchain | Deep technical analysis |
| "How does Safe work?" | Research Blockchain | Architectural deep dive |
| "Compare Safe with Argent" | Research Blockchain | Comparative analysis |
| "Analyze Safe security model" | Research Blockchain | Security-focused research |
| "Extract Safe API reference" | Web Scraper | API-specific extraction |
| "Safe SDK integration guide" | Research Blockchain | Integration-focused |
| "Complete Safe analysis" | Web Scraper → Research Blockchain | Chain both agents |

---

## Workflow Patterns

### Pattern 1: Documentation Extraction → Analysis

**Use case**: Comprehensive protocol research

1. **Web Scraper** extracts all documentation from docs.safe.global
   - Outputs: JSON knowledge base, markdown summary, CSV components
2. **Research Blockchain** performs deep technical analysis
   - Inputs: Scraper outputs + additional web research
   - Outputs: Technical report, architecture diagrams, risk assessment

**When to use**: User wants complete understanding of a protocol

**Command sequence**:
```
/safe scrape https://docs.safe.global/home/what-is-safe SDK,Core,API
/safe research Safe SDK,Core,API
```

---

### Pattern 2: Direct Technical Research

**Use case**: Quick answers to technical questions

1. **Research Blockchain** directly researches without scraping
   - Uses WebSearch and WebFetch as needed
   - Generates focused technical analysis

**When to use**: User has specific technical questions, doesn't need full documentation extraction

**Command**:
```
/safe research "How does Safe's ERC-4337 integration work?"
```

---

### Pattern 3: Comparative Analysis

**Use case**: Comparing multiple protocols

1. **Web Scraper** extracts documentation from multiple sources (parallel)
2. **Research Blockchain** performs comparative analysis
   - Creates comparison matrices
   - Identifies trade-offs and innovations
   - Provides recommendations

**When to use**: User needs to choose between protocols or understand landscape

**Command**:
```
/safe research "Compare Safe, Argent, and Braavos"
```

---

## Safe-Specific Focus Areas

When researching Safe, prioritize these components:

### Safe SDK
- **Starter Kit**: Entry point for new developers
- **Protocol Kit**: Core interactions with Safe contracts
- **API Kit**: Transaction Service integration
- **Relay Kit**: ERC-4337 and gasless transactions

### Safe Core
- **Smart Account Architecture**: Proxy pattern, Singleton
- **Owner Management**: Multi-sig mechanisms
- **Module System**: Allowance, Recovery, 4337, Passkey modules
- **Guard System**: Transaction validation

### Safe API Infrastructure
- **Transaction Service**: Multi-sig transaction coordination
- **Events Service**: Webhook notifications
- **Client Gateway**: Aggregated data access
- **Config Service**: Network configurations

### Safe Integration Patterns
- **Account Abstraction**: ERC-4337 implementation
- **DeFi Integration**: CoW Swap, Uniswap, Aave
- **Multi-chain**: Ethereum, L2s, Gnosis Chain
- **Developer Experience**: SDK usage, API integration

---

## File Naming Conventions

### For Outputs

**Format**: `{project}-{type}-{YYYYMMDD}.{ext}`

**Examples**:
- `safe-knowledge-base-20251212.json`
- `safe-technical-analysis-20251212.md`
- `safe-components-20251212.csv`
- `safe-architecture-20251212.mmd`
- `multisig-comparison-20251212.csv`

**Rules**:
- Lowercase project/protocol names
- Use hyphens instead of spaces or underscores
- ISO date format (YYYYMMDD)
- Descriptive type names (knowledge-base, analysis, comparison, architecture)

### For Source Materials

**Format**: `{topic}-{type}.md`

**Examples**:
- `safe-sdk-research-notes.md`
- `erc4337-implementation-notes.md`
- `multisig-comparison-sources.md`

---

## Git Commit Protocol

### When to Commit

**DO commit**:
- After completing an agent run (new outputs generated)
- After creating or editing agents
- After updating this INSTRUCTIONS.md file
- When user explicitly requests

**DON'T commit**:
- During agent execution (wait until complete)
- Partial or incomplete research
- Temporary/draft files

### Commit Message Format

```
{agent-name}: {brief description}

{optional details about what was analyzed/created}
```

**Examples**:
```
web-scraper: Extract Safe SDK documentation

Scraped docs.safe.global focusing on Protocol Kit, API Kit, and Relay Kit.
Generated knowledge base, analysis report, and component CSV.

research-blockchain: Analyze Safe Core architecture

Deep dive into Smart Account contracts, module system, and security model.
Includes architecture diagrams and risk assessment.

agents: Create initial Safe research agents

Added web-scraper and research-blockchain agents optimized for Safe ecosystem.
```

---

## Managing This System

### Adding a New Agent

1. Create `open-agents/agents/{name}.md` with:
   - Purpose, triggers, behaviors, output format
2. Create commands in `.claude/commands/safe/{command}.md`
3. Add agent entry to "Available Agents" section above
4. Add routing entries to routing table
5. Commit:
   ```bash
   git add open-agents/agents/{name}.md .claude/commands/safe/{command}.md open-agents/INSTRUCTIONS.md
   git commit -m "agents: Add {name} agent"
   ```

### Editing an Agent

1. Modify `open-agents/agents/{name}.md`
2. Update routing table if triggers changed
3. Test the modified agent
4. Commit:
   ```bash
   git add -A
   git commit -m "agents: Update {name} - {what changed}"
   ```

### Removing an Agent

1. Delete agent file and command files
2. Remove from "Available Agents" and routing table
3. Commit:
   ```bash
   git add -A
   git commit -m "agents: Remove {name} agent"
   ```

---

## Quick Start Guide

### For New Users

**Goal**: Research Safe protocol (SDK, Core, API)

**Steps**:
1. Start with documentation scraping:
   ```
   /safe scrape https://docs.safe.global/home/what-is-safe SDK,Core,API
   ```

2. Review generated outputs in `output-*` folders

3. Perform deep technical analysis:
   ```
   /safe research Safe SDK,Core,API
   ```

4. Read comprehensive technical report in `output-reports/`

5. For comparisons:
   ```
   /safe research "Compare Safe with [other protocol]"
   ```

**Expected Outputs**:
- `safe-knowledge-base-{date}.json` - Structured documentation data
- `safe-analysis-{date}.md` - Comprehensive documentation summary
- `safe-components-{date}.csv` - Component/feature matrix
- `safe-technical-analysis-{date}.md` - Deep technical analysis
- `safe-architecture-{date}.mmd` - Architecture diagrams

---

### For Developers Integrating Safe

**Goal**: Understand how to integrate Safe into your application

**Steps**:
1. Extract SDK documentation:
   ```
   /safe scrape https://docs.safe.global/sdk "Protocol Kit,API Kit,Relay Kit"
   ```

2. Get integration-focused analysis:
   ```
   /safe research "Safe SDK integration patterns"
   ```

3. Review outputs for:
   - Code examples
   - API references
   - Integration flows
   - Best practices

**Expected Outputs**:
- SDK-specific knowledge base
- Integration-focused technical report
- Code examples and patterns

---

### For Security Researchers

**Goal**: Audit Safe's security model

**Steps**:
1. Extract core documentation:
   ```
   /safe scrape https://docs.safe.global "Smart Account,Modules,Guards"
   ```

2. Perform security-focused research:
   ```
   /safe research "Safe security model and audit history"
   ```

3. Review outputs for:
   - Access control mechanisms
   - Upgrade patterns
   - Module security
   - Audit reports
   - Risk assessment

**Expected Outputs**:
- Security-focused technical analysis
- Risk assessment report
- Contract architecture diagrams

---

## Advanced Usage

### Chaining Agents

For comprehensive analysis, chain agents:

```
1. /safe scrape {url} {focus}
   → Generates knowledge base

2. /safe research {protocol} {focus}
   → Uses knowledge base + additional research
   → Generates deep analysis

3. Review all outputs together for complete picture
```

### Comparative Research

Research multiple protocols and compare:

```
1. /safe scrape https://docs.safe.global SDK,Core,API
2. /safe scrape https://docs.argent.xyz SDK,Core,API
3. /safe research "Compare Safe and Argent smart wallet architectures"
```

Agent will:
- Use both knowledge bases
- Research additional sources
- Create comparison matrices
- Identify trade-offs
- Provide recommendations

### Iterative Deep Dives

Start broad, then go deep:

```
1. /safe research "Safe protocol overview"
   → High-level understanding

2. /safe research "Safe ERC-4337 implementation"
   → Specific mechanism deep dive

3. /safe research "Safe Module security analysis"
   → Security-focused on specific component
```

---

## Best Practices

### Before Starting Research

1. **Identify Focus Areas**: Be specific about what aspects to research
2. **Check Existing Outputs**: Review `output-*` folders for previous research
3. **Provide Context**: Explain why you're researching (integration, security audit, comparison)

### During Research

1. **Monitor Progress**: Agents will report as they work
2. **Provide Feedback**: Guide agents if they're going off-track
3. **Ask Questions**: Request clarification or deeper dives

### After Research

1. **Review All Outputs**: Check JSON, MD, and CSV files
2. **Verify Information**: Spot-check critical claims
3. **Request Follow-ups**: Ask for deeper analysis of specific areas
4. **Save Research**: Commit valuable outputs to git

### Quality Indicators

Good research outputs include:
- [ ] Multiple authoritative sources cited
- [ ] Code examples when relevant
- [ ] Architecture diagrams for complex systems
- [ ] Coverage analysis (what's documented vs. gaps)
- [ ] Actionable recommendations
- [ ] Clear next steps

---

## Troubleshooting

### Agent Not Triggering

**Problem**: Agent doesn't activate when expected

**Solutions**:
1. Use explicit slash command: `/safe scrape` or `/safe research`
2. Check routing table for correct trigger phrases
3. Mention agent name explicitly: "Use the web-scraper agent to..."

### Incomplete Outputs

**Problem**: Agent stops before completing full analysis

**Solutions**:
1. Ask agent to continue: "Please complete the analysis"
2. Be more specific about scope: Focus on smaller area
3. Check if agent needs additional information

### Wrong Agent Used

**Problem**: Research blockchain agent used when scraper needed (or vice versa)

**Solutions**:
1. Use specific slash command
2. Explicitly name the agent: "Use web-scraper agent to..."
3. Check routing table and use listed trigger phrases

---

## Extending the System

### Adding Domain-Specific Agents

This system can be extended for other protocols:

**Example: Uniswap Research Agent**
1. Create `agents/uniswap-researcher.md`
2. Specialize behaviors for AMM/DEX analysis
3. Add commands: `.claude/commands/uniswap/`
4. Update routing table

**Example: Security Audit Agent**
1. Create `agents/security-auditor.md`
2. Focus on vulnerability detection
3. Add specialized security analysis patterns
4. Integrate with existing research agents

### Creating Automation Tools

Agents can create reusable scripts in `tools/`:

**Example Uses**:
- Automated scraping scripts for regular documentation updates
- Contract ABI extraction tools
- Diagram generation automation
- Report formatting scripts

---

## Related Resources

### Safe Ecosystem
- **Documentation**: https://docs.safe.global
- **GitHub**: https://github.com/safe-global
- **Core SDK**: https://github.com/safe-global/safe-core-sdk
- **Smart Contracts**: https://github.com/safe-global/safe-smart-account

### Open Agent System
- **Specification**: See `OpenAgentDefinition.md` in project root
- **GitHub**: https://github.com/bladnman/open-agent-system

### AI Coding Assistants
- **Claude Code**: https://claude.ai/code
- **Gemini CLI**: https://gemini.google.com
- **Codex**: https://openai.com/blog/openai-codex

---

## Support

### Questions or Issues

1. **About the Open Agent System**: Read `OpenAgentDefinition.md`
2. **About specific agents**: Read agent files in `agents/`
3. **About Safe protocol**: Use the research agents to find answers

### Improving the System

This is an experimental research system. Improvements welcome:
- Refine agent behaviors based on results
- Add new specialized agents
- Create automation tools
- Enhance output formats

---

## Metadata

- **System Version**: 1.0
- **Created**: 2025-12-12
- **Primary Focus**: Safe (Gnosis Safe) Protocol Research
- **Agent Count**: 2 (Web Scraper, Research Blockchain)
- **Target Users**: Developers, Researchers, Security Auditors
- **Status**: Production-ready for Safe research

---

*This Open Agent System transforms Claude Code into a specialized blockchain research environment using only markdown files.*
