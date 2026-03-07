# Domain Search

Interactive domain name brainstorming tool for Claude Code.

## How It Works
1. User describes their business/project
2. Claude generates brandable domain ideas
3. `check-domains.mjs` checks .com availability via Namecheap API
4. Results saved to file for reference

## Usage
```bash
# Set env vars
export NAMECHEAP_API_USER="username"
export NAMECHEAP_API_KEY="your_key"
export NAMECHEAP_USERNAME="username"
export NAMECHEAP_CLIENT_IP="your_ip"

# Check domains (results saved to file)
node check-domains.mjs domain1 domain2 domain3
```

## Workflow
- Ask Claude for domain ideas based on concept/theme
- Claude checks availability in batches of ~25 via Namecheap API
- Available domains saved to `results/` folder
- Iterate with new themes until finding the right name
- Present results in ranked tables with domain, vibe/rationale columns
- Always pipe a filename into the script: `echo "batch-name" | node check-domains.mjs domain1 domain2 ...`
- Load env vars before running: `export $(grep -v '^#' .env.local | xargs)`

## Search Type Templates

When brainstorming domains, use these search strategies. Layer multiple strategies per session for best results.

### 1. Direct Compound
Combine the core concept with action/descriptor words.
```
leadzap, routefire, connectpop, qualifysnap
```

### 2. Prefix/Suffix Modifier
Add SaaS-style prefixes or suffixes to the core word.
```
get___, try___, use___, go___, ___hq, ___ai, ___lab, ___hub
```

### 3. Portmanteau / Embedded Word
Hide the key business word inside a larger made-up word that sounds like a real word. The embedded word IS the business.
```
"lead" → leadgacy (legacy), releadiant (radiant), leadosity (velocity)
"qualify" → squalified, tranqualify (tranquil), qualifaire (affair)
"monetize" → remonaissance (renaissance), monetivate (motivate), remonetique (boutique)
"relay" → relayvant (relevant), relaygacy (legacy)
```

### 4. Double Meaning / Innuendo
Words that mean one thing in business context and something cheeky/fun otherwise.
```
hookup (connect + romantic), leadflirt (engage leads + flirting)
hothandoff (lead handoff + suggestive), leadmadam (runs the house of leads)
matchivate (match leads + captivate), hookvana (hooked + nirvana)
```

### 5. Synonym Rotation
Take the core concept, list synonyms, then run each through other templates.
```
"route" synonyms: relay, dispatch, funnel, channel, shuttle, bridge, path, track
"connect" synonyms: link, hook, match, couple, fuse, mesh, signal, ping
"qualify" synonyms: vet, screen, grade, rate, score, filter, sort
```

### 6. Character / Personality
Give the brand a persona — rogue, pirate, maverick, queen, etc.
```
routerogue, routebandit, routepirate, leadmadam, routequeen
```

### 7. Creative Misspelling
Alternate spellings, dropped letters, Flickr-style truncation.
```
remonetizr, squalifai, kwalify, qualifik, routewerk
```

### 8. Science / Element Style
Make it sound like a periodic element or scientific term.
```
leadium, qualifium, remonetique, pulsadium, surgenium, celeadium
```

### 9. Mashup with Routing/Tracking Synonyms
Combine routing/tracking/connecting synonyms into portmanteau words.
```
relayvant, surgevate, matchivate, hookosity, dispatchium, signaliant
```

### Search Execution Pattern
1. Start with 2-3 strategies, run 25 domains per batch
2. Note which direction resonates with the user
3. Double down on that direction with 2-3 more targeted batches
4. Present results in tiered tables: Top Tier, Strong, Sleepers
5. Include rationale for top picks

## Files
- `check-domains.mjs` - Namecheap API domain checker
- `.env.local` - API credentials (gitignored)
- `results/` - Saved search results
