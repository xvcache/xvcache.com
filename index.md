# XVcache

> J'ai caché, j'ai prouvé. Local MCP server (STDIO) that journals sha256 fingerprints of Markdown notes — not the notes themselves. Verdicts: **V** (intacte) and **X** (MODIFIÉE hors XVcache). First customer: the AI agent. Payment is not live. Prices are placeholders marked TBD.

Markdown version of https://xvcache.com. See also [llms.txt](./llms.txt) and [agents.md](./agents.md).

## For agents

XVcache lets you prove what you read, searched, or wrote in a Markdown vault, without putting the note body into the journal. Local verification is free. An independent certifying witness is à venir. Source: https://github.com/xvcache/xvcache (Apache-2.0). npm: [`xvcache-mcp`](https://www.npmjs.com/package/xvcache-mcp). MCP Registry name: `io.github.xvcache/xvcache`.

### Install

With Node.js 20 or later:

```bash
XVCACHE_VAULT=/absolute/path/to/vault npx -y xvcache-mcp
```

Optional: `XVCACHE_LOG` must stay outside the vault. Aliases: `JAYCACHE_VAULT`, `JAYCACHE_LOG`.

Typical STDIO client config:

```json
{
  "mcpServers": {
    "xvcache": {
      "command": "npx",
      "args": ["-y", "xvcache-mcp"],
      "env": { "XVCACHE_VAULT": "/absolute/path/to/vault" }
    }
  }
}
```

### Discovery files

- [llms.txt](./llms.txt)
- [agents.md](./agents.md)
- [plans.json](./plans.json)
- [server.json](./server.json) — official MCP Registry metadata (schema 2025-12-11). Name `io.github.xvcache/xvcache`.
- [/.well-known/ai-catalog.json](./.well-known/ai-catalog.json) — official well-known discovery path (MCP Server Cards extension, draft). No remote HTTP endpoint is published, so there is no Server Card yet. `/.well-known/mcp.json` is not the official well-known URI.

### Tools

Available now: `read_note`, `search_notes`, `write_note`, `verify_journal`.

Buy / certify / resell: `get_offer`, `list_plans`, `recommend_plan`, `request_upgrade` (human-approval stub; Stripe intended, not live; x402 later), `certify_note` (witness à venir).

### Offers

See [plans.json](./plans.json). Current tier: `free` (local journal and V/X). Paid plans `usage`, `bundle-starter`, `bundle-standard`, `bundle-plus` are `coming_soon`. Every amount is TBD. Reseller terms are TBD. Do not invent a price or a checkout URL.

## For humans / Pour les humains

**« J'ai caché, j'ai prouvé. »**

Des agents d'intelligence artificielle lisent, cherchent et écrivent déjà dans des dossiers professionnels. Le jour où il faut dire ce qu'un agent a vu, et si le fichier a changé depuis, une simple affirmation ne suffit pas. On ne peut pas, pour le prouver, livrer le dossier lui-même. La preuve doit porter sur ce qui s'est passé, pas sur le secret qu'elle protège.

### Demo (example wording, not a live run)

After `write_note` then `verify_journal`:

```text
V  intacte — Note Tests/Memo.md intacte depuis <horodatage> par <client>.
```

After the same file is edited outside XVcache, then `verify_journal` again:

```text
X  MODIFIÉE hors XVcache — Note Tests/Memo.md MODIFIÉE hors XVcache après <horodatage>.
```

### For whom

Professionals bound by secrecy who already use an AI assistant: lawyers (avocats) first, notaries, chartered accountants (experts-comptables), physicians, and consultants bound by contractual confidentiality (not to be confused with statutory professional secrecy).

### Livre blanc and demo

- [Livre blanc XVcache (PDF, 10 pages)](./LIVRE-BLANC-XVCACHE.pdf) — not legal advice.
- The « Demander une démo » form on [humains.html](./humains.html#demo) is a mock-up: it sends nothing and stores nothing. To ask for a demo, open an issue on [GitHub](https://github.com/xvcache/xvcache/issues).

XVcache is not, by itself, a compliance tool, legal advice, or a qualified electronic timestamp. French trademark filing (demande n° 5323492), not presented as registered.
