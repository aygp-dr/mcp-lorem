# MCP Lorem Ipsum Server - Agent Guidelines

## Project Overview
This is an MCP (Model Context Protocol) server that provides Lorem Ipsum text generation capabilities. The project supports both local and remote deployment with OAuth authentication for production use.

## Repository Information
- **GitHub**: https://github.com/aygp-dr/mcp-lorem
- **Type**: Public repository
- **Primary Language**: TypeScript/Python
- **Package Registry**: GitHub Packages npm registry

## Development Workflow

### Git Commit Practices
1. Use conventional commits (feat:, fix:, docs:, test:, refactor:, chore:)
2. Add co-author attribution: `Co-Authored-By: Aidan Pace <noreply@anthropic.com>`
3. After each commit, add git notes documenting:
   ```bash
   git notes add -m "Context: [prompt/reasoning/testing/considerations]" HEAD
   git push origin refs/notes/commits
   ```

### Project Structure
```
mcp-lorem/
├── setup.org           # Main project specification (SOURCE OF TRUTH)
├── src/
│   ├── core/          # Language-agnostic Lorem generation logic
│   ├── local/         # Python MCP server for local testing
│   └── remote/        # TypeScript server with OAuth for production
├── tests/             # Test suites for all components
└── examples/          # Integration examples for various clients
```

## Implementation Status

### Completed
- [x] Repository setup with topics and description
- [x] Comprehensive setup.org documentation
- [x] Git notes workflow established

### In Progress
- [ ] Core Lorem generation engine (src/core/lorem.py)
- [ ] Local MCP server implementation
- [ ] OAuth flow for remote deployment

### TODO Priority (UPDATED - Prompts are the game changer!)
1. **Implement core lorem.py** - Start with standard Lorem Ipsum generation
2. **Create local MCP server with BOTH tools and prompts** - Prompts enable slash commands in Claude!
3. **Design prompt templates** - Email, blog, presentation, UI mockup templates
4. **Test with MCP Inspector** - Validate both tools and prompts functionality
5. **Build TypeScript remote server** - Add OAuth support with prompts capability

## Technical Decisions

### Core Engine
- Multiple Lorem modes: standard, cicero, bacon, hipster
- Configurable output: words, sentences, paragraphs
- Extensible word bank system

### MCP Implementation
- **Tools API**: `generate_lorem` with type, count, and mode parameters (programmatic access)
- **Prompts API**: Pre-configured templates (email, blog, presentation, UI) - **KEY FEATURE** for slash commands
- **Resources API**: Custom word banks and style guides (future)

### OAuth Configuration
- Callback URL: https://claude.ai/api/mcp/auth_callback
- Client Name: Claude
- Support DCR (Dynamic Client Registration)
- Implement PKCE for security

## Testing Guidelines

### Local Testing
```bash
# Test Python server locally
python src/local/server.py

# Use MCP Inspector
mcp-inspector python src/local/server.py
```

### Integration Testing
- Test with Claude Desktop settings
- Validate with Claude Code
- Verify mcp.el compatibility

## Security Considerations
- Never commit secrets or API keys
- Use environment variables for sensitive config
- Implement rate limiting for production
- IP whitelist Claude endpoints when known

## Development Commands

### Build and Test
```bash
# Install dependencies
npm install
pip install -r requirements.txt

# Run tests
npm test
pytest

# Build TypeScript
npm run build
```

### Deployment
```bash
# Publish to GitHub Packages
npm publish

# Deploy to Cloudflare Workers (future)
wrangler deploy
```

## Important Notes

1. **setup.org is the source of truth** - All architectural decisions and specifications are documented there
2. **tls-prompts-analysis.org contains key insights** - Prompts are the UX game-changer for lorem ipsum!
3. **Test before committing** - Use MCP Inspector to validate both tools AND prompts
4. **Document decisions** - Use git notes for context not suitable for commit messages
5. **Follow MCP spec** - Refer to https://modelcontextprotocol.io for protocol details
6. **OAuth complexity** - Remote server requires careful OAuth implementation per RFC specifications
7. **TLS 1.3 is automatic** - Cloudflare/modern platforms handle TLS transparently

## Resources
- MCP Specification: https://modelcontextprotocol.io
- MCP Inspector: https://github.com/modelcontextprotocol/inspector
- OAuth Testing: https://oauth.tools
- Claude MCP Docs: https://support.anthropic.com/en/articles/11175166

## Contact
- GitHub: @aygp-dr (Aidan Pace)
- Repository Issues: https://github.com/aygp-dr/mcp-lorem/issues