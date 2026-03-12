# SJ Finance

Financial analysis toolkit powered by Daloopa's institutional-grade financial data, designed for fundamental equity research.

## Git Identity

- Author: SJ (jain.saurabh.048@gmail.com)
- GitHub: saurabhjain080488

## Analyst Context
- Perspective: long/short equity, fundamental analysis
- Data source: Daloopa MCP server (SEC filings, earnings, financial statements)
- Market data: MCP-first (use whatever market data MCP the user has configured), fallback to `scripts/market_data.py`
- Consensus estimates: optional (when available, adds beat/miss and forward context)
- All analysis should be thorough, data-driven, and cite sources
- Follow `design-system.md` for number formatting, analytical density, and styling

## MCP Tool Workflow
Always follow this pattern when working with Daloopa data:

1. **`discover_companies`** — Look up company by ticker or name to get `company_id`
2. **`discover_company_series`** — Find available financial metrics and KPIs for the company
3. **`get_company_fundamentals`** — Pull actual data for specific series and periods
4. **`search_documents`** — Search SEC filings (10-K, 10-Q, 8-K) for qualitative information

## Skills

All skills live in `.claude/skills/`. Invoke with `/skill-name TICKER`:

| Skill | Description |
|-------|-------------|
| `/build-model` | Build a multi-tab Excel financial model |
| `/bull-bear` | Bull/bear/base case scenario framework |
| `/capital-allocation` | Capital deployment, buybacks, dividends analysis |
| `/comp-sheet` | Industry comp sheet Excel model with operational KPIs |
| `/comps` | Trading comparables with peer multiples |
| `/dcf` | Discounted cash flow valuation with sensitivity |
| `/earnings` | Full earnings analysis with guidance tracking |
| `/guidance-tracker` | Track management guidance accuracy over time |
| `/ib-deck` | Investment banking pitch deck (HTML to PDF) |
| `/industry` | Cross-company industry comparison |
| `/inflection` | Auto-detect metric acceleration/deceleration inflections |
| `/initiate` | Initiate coverage (research note + Excel model) |
| `/research-note` | Professional Word document research note |
| `/setup` | Initial setup and authentication walkthrough |
| `/supply-chain` | Interactive supply chain dashboard |
| `/tearsheet` | Quick one-page company overview |
| `/update` | Refresh existing research with latest data |
| `/meta-skill` | Convert skills to MCP prompts |

Shared references (used by all skills):
- `.claude/skills/data-access.md` — Data access patterns and tool resolution
- `.claude/skills/design-system.md` — Formatting, colors, and styling conventions

## Design System
All skills reference `.claude/skills/design-system.md` for consistent formatting:
- Number formatting ($X.Xbn, X.X%, X.Xx multiples, +/-Xbps)
- Three-layer analytical density (data point + context + implication)
- Table conventions (columns = periods, rows = metrics, growth sub-rows)
- Commentary blocks after every major table
- Color palette (navy #1B2A4A, steel blue #4A6FA5, gold #C5A55A)

## Citation Format
Every financial figure must link back to its Daloopa source:
```
[$X.XX million](https://daloopa.com/src/{fundamental_id})
```

## Table Format
- **Columns** = time periods (Q1 2024, Q2 2024, etc.)
- **Rows** = financial metrics (Revenue, Net Income, etc.)

## Guidance vs Actuals Rules
- Quarterly guidance from Q(N) applies to Q(N+1) results
- Annual guidance from Q1/Q2/Q3 applies to current fiscal year
- Annual guidance from Q4 applies to NEXT fiscal year
- Never compare same-quarter guidance to same-quarter actual

## Key Operating KPIs
When analyzing any company, always discover and include company-specific KPIs beyond standard financials (e.g., subscribers, ARR, GMV, same-store sales, DAU/MAU, ARPU, units, bookings, backlog).

## Repository Structure

```
sj-finance/
├── .claude/
│   ├── skills/       # Claude Code skills (slash commands)
│   └── agents/       # Autonomous subagents
├── config/           # Tool config, MCP setup
├── scripts/          # Python helpers (market data, etc.)
├── data/             # Cached data
├── outputs/          # Generated reports and models
├── templates/        # Document templates
└── .gitignore
```

## Reports
All generated outputs go to `outputs/` with naming convention:
- Models: `outputs/{TICKER}_model_{YYYY-MM-DD}.xlsx`
- Research notes: `outputs/{TICKER}_note_{YYYY-MM-DD}.docx`
- Tearsheets: `outputs/{TICKER}_tearsheet_{YYYY-MM-DD}.md`
- Decks: `outputs/{TICKER}_deck_{YYYY-MM-DD}.html`
