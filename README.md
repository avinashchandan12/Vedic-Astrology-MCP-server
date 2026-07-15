# Navamsha — Vedic Astrology MCP Server

**Hosted Vedic astrology MCP** for Claude, ChatGPT, Cursor, and other Model Context Protocol clients.

Give AI agents real Jyotish tools — Kundali, Panchang, Dasha, Gun Milan — backed by **Swiss Ephemeris** and **Lahiri** sidereal defaults, instead of invented planetary positions.

| | |
|---|---|
| **Live MCP URL** | `https://navamsha.fastmcp.app/mcp` |
| **Product docs** | [www.navamsha.in/mcp](https://www.navamsha.in/mcp) |
| **REST API** | [api.navamsha.in](https://api.navamsha.in) · [OpenAPI](https://api.navamsha.in/openapi.json) |
| **Free tier** | 10,000 calls/month · no credit card · same `X-API-Key` as REST |
| **Compare servers** | [Best Vedic astrology MCP servers 2026](https://www.navamsha.in/blog/best-vedic-astrology-mcp-servers-2026) |

Keywords: **Vedic astrology MCP**, Jyotish MCP, kundli MCP, free astrology MCP, Claude Vedic astrology, Cursor astrology MCP.

---

## Why Navamsha MCP

- **Hosted** — paste a URL; no Docker required for common desktop clients
- **Deterministic** — Swiss Ephemeris calculations on `api.navamsha.in` with stamped response metadata
- **One key** — REST app + MCP agent share the Navamsha hub quota
- **Production-proven** — same engine as [Astro Vedica](https://www.astrovedica.in)

---

## Quick start (Cursor)

1. Create a free API key: [www.navamsha.in/auth/signup](https://www.navamsha.in/auth/signup)
2. Add to Cursor MCP settings (or `~/.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "navamsha": {
      "url": "https://navamsha.fastmcp.app/mcp",
      "headers": {
        "X-API-Key": "YOUR_NAVAMSHA_API_KEY"
      }
    }
  }
}
```

3. Try prompts such as:
   - `List Navamsha MCP capabilities`
   - `Get today's panchang for Mumbai`
   - `Compute a basic kundali for 15 May 1990, 10:30 IST, Mumbai`

Claude / ChatGPT: add the same URL as a remote **Streamable HTTP** MCP server and pass `X-API-Key` in headers (client UI varies).

---

## Tool families (v1)

| Family | Example tools |
|---|---|
| Kundali | `get_kundali_basic`, `get_kundali_complete`, `get_planets`, `get_houses`, `get_divisional_chart` |
| Panchang | `get_panchang`, `get_muhurta_choghadiya` |
| Dasha / timing | `get_vimshottari_dasha`, `get_current_dasha`, `get_transits` |
| Dosha | `get_mangal_dosha`, `get_doshas_summary` |
| Matchmaking | `get_ashtakoot_match`, `get_manglik_compatibility` |
| Western | `get_western_natal`, `get_western_synastry` |
| Numerology | `get_life_path`, `get_name_numerology` |
| Meta | `list_navamsha_capabilities`, `get_api_health` |

MCP is a thin proxy; astronomy runs on the Navamsha API. Timezone fields use UTC offset hours (`5.5` = IST), not IANA names.

---

## This repository

Python package `navamsha-mcp` (FastMCP) used to build/deploy the hosted server.

```bash
# Dev (uv)
cd mcp
uv sync --extra dev
export NAVAMSHA_API_KEY=your_key   # for stdio / local HTTP
./scripts/run_http.sh              # or: uv run navamsha-mcp
```

Examples:

- [`examples/cursor-mcp.json`](examples/cursor-mcp.json) — remote hosted URL
- [`examples/cursor-mcp.stdio.json`](examples/cursor-mcp.stdio.json) — local stdio

Env template: [`.env.example`](.env.example)

---

## Auth

| Mode | How |
|---|---|
| Hosted HTTP | Header `X-API-Key: <key>` (or `Authorization: Bearer <key>`) |
| Local stdio | Env `NAVAMSHA_API_KEY` |

Signup: [www.navamsha.in/auth/signup](https://www.navamsha.in/auth/signup) · Pricing: [www.navamsha.in/pricing](https://www.navamsha.in/pricing)

---

## Related

- Free Vedic astrology API landing: [www.navamsha.in/free-astrology-api](https://www.navamsha.in/free-astrology-api)
- Agent discovery: [llms.txt](https://www.navamsha.in/llms.txt) · [agents.json](https://www.navamsha.in/.well-known/agents.json)
- Connect Claude/ChatGPT guide: [blog/mcp-server-claude-chatgpt-vedic-data](https://www.navamsha.in/blog/mcp-server-claude-chatgpt-vedic-data)

---

## License / support

Commercial Navamsha API usage is governed by [www.navamsha.in/legal](https://www.navamsha.in/legal).  
Contact: avinashchandan12@gmail.com
