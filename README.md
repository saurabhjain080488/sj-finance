# SJ Finance

Financial analysis toolkit powered by Daloopa data and Claude Code skills.

## Quick Start

1. Open this repo in VS Code with Claude Code extension
2. Run `/setup` to configure Daloopa MCP and market data access
3. Run any skill with a ticker: `/tearsheet AAPL`, `/dcf MSFT`, `/earnings NVDA`

## Skills

18 analysis skills covering financial modeling, valuation, earnings analysis, industry comparables, and more. See `CLAUDE.md` for the full list.

## Stack

- **Data**: Daloopa MCP server (SEC filings, financial statements)
- **Market Data**: MCP-first, fallback to Python scripts
- **Output**: Excel (.xlsx), Word (.docx), HTML, Markdown
