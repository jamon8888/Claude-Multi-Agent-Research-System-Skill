# Project Context for Claude Code

## Project Overview
This is a multi-agent research plugin for Claude Code (v2.5.0) that enables advanced research workflows using multiple specialized agents with parallel execution and comprehensive synthesis.

## Directory Structure
- **agents/**: Agent definitions (researcher, report-writer, incremental-synthesizer)
- **commands/**: Custom slash commands (research, research-quick, research-deep, setup-mcp-keys)
- **hooks/**: Event hooks for automation
- **skills/**: Multi-agent researcher skill with adaptive decomposition
- **files/**: Research outputs (research_notes/, reports/)
- **logs/**: Agent execution logs

## Plugin MCP Servers (User-Facing)
The plugin integrates 4 MCP search providers for research:
- **exa**: Neural-powered search (academic/technical)
- **tavily**: AI-optimized search (current events)
- **brave**: Privacy-focused web search
- **perplexity**: AI reasoning for complex queries

## Instructions for Claude

### When to Use Context7
Use Context7 (configured globally, not part of the plugin) when you need:
1. **Fresh Claude Code documentation** - Check latest features, best practices, API changes
2. **Codebase analysis** - Semantic search across this plugin's code
3. **Code navigation** - Find specific functions, patterns, or implementations

**Context7 Tools:**
- `search_code`: Semantic code search
- `get_file_contents`: Retrieve file contents
- `list_directory`: Browse structure
- `search_symbols`: Find functions/classes

### When to Use WebFetch
Use WebFetch for Claude Code documentation at:
- https://code.claude.com/docs/en/ (main docs)
- https://code.claude.com/docs/en/claude_code_docs_map.md (docs index)

Fetch relevant pages when enhancing the plugin to align with latest best practices.

## Development & Enhancement Guidelines
1. Check Claude Code docs via WebFetch for latest best practices
2. Use Context7 to analyze current plugin implementation
3. Compare implementation with official recommendations
4. Implement improvements following official patterns
5. Test changes with plugin commands (/research, /research-quick, etc.)
