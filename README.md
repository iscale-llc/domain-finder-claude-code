# Domain Search

Interactive domain name brainstorming tool designed for use with Claude Code. Describe your business idea, get brandable domain suggestions, and instantly check .com availability via the Namecheap API.

## Setup

1. Get API access from [Namecheap](https://www.namecheap.com/support/api/intro/) (requires account with $50+ spend or 20+ domains)
2. Whitelist your IP in Namecheap Dashboard > Profile > Tools > API Access
3. Copy the env template and fill in your credentials:

```bash
cp .env.example .env.local
```

4. Source your env before running:

```bash
source .env.local
```

## Usage

```bash
node check-domains.mjs domain1 domain2 domain3
```

You'll be prompted for a filename — results are saved to `results/` with availability status.

### With Claude Code

This tool is built to pair with [Claude Code](https://docs.anthropic.com/en/docs/claude-code). The `CLAUDE.md` file gives Claude context to:

1. Brainstorm brandable domain names based on your concept
2. Run `check-domains.mjs` in batches
3. Iterate on themes until you find the right name

Just open Claude Code in this directory and describe what you're building.

## Example

```
$ node check-domains.mjs brightpath lumivox zentrade crestline

Save results to (e.g. "pharma-ideas"): startup-names

Domain Availability Results:

brightpath.com                 ✗ Taken
lumivox.com                    ✓ Available
zentrade.com                   ✗ Taken
crestline.com                  ✗ Taken

Results saved to: results/startup-names-1709500000000.txt
```

## Requirements

- Node.js 18+
- Namecheap API credentials

## Built with AI

This project is part of the [Built with AI](https://builtwithai.com/open-source) open source collection — free tools built by the AI builder community.

**[Join the community →](https://builtwithai.com/apply)**

## License

MIT
