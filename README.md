# Galapagos Trip Planner MCP

Galapagos trip planning tools for AI assistants: what the whole trip costs, cruise or island hopping, a day-by-day itinerary, inter-island ferry times with a seasickness meter, weather and wildlife by month, where to see each animal, the park fee and entry rules, visitor sites and the weather right now. Same numbers as the planning tools on [galapagosislands.info](https://galapagosislands.info), an independent Galapagos guide.

- **Endpoint:** `https://galapagosislands.info/mcp` (MCP Streamable HTTP, public, no sign-in, no API key)
- **Docs:** [galapagosislands.info/ai-assistants](https://galapagosislands.info/ai-assistants/)
- **MCP Registry:** `info.galapagosislands/galapagos-trip-planner`
- **npm:** `galapagos-trip-planner-mcp` (stdio bridge to the endpoint, for clients that only run local servers)

## Tools

All tools are read-only (`readOnlyHint: true`), take only trip details and store nothing.

| Tool | What it answers |
|---|---|
| `estimate_trip_cost` | Full trip budget line by line: park fee, transit card, flights from Quito or Guayaquil, hotels or cruise, ferries, tours, food. Renders a receipt card in ChatGPT and MCP Apps hosts. |
| `land_or_cruise` | Cruise or land-based trip, from six answers, with reasons and an 8-day cost comparison. |
| `plan_itinerary` | Day-by-day island-hopping plan (Santa Cruz, Isabela, San Cristóbal) for a wildlife, snorkel or budget focus. Renders a route map. |
| `ferry_board` | Inter-island speedboat times, fares, dock fees and a seasickness meter by month. Renders a departures board. |
| `month_guide` | Air and sea temperature, rain, sea state, crowds and wildlife events for a month. |
| `find_wildlife` | Where and when to see 19 animals, with odds and sites. |
| `entry_rules` | National park fee by nationality group, transit control card and visitor rules, with official sources. |
| `visitor_site` | Kicker Rock, Tortuga Bay, Los Túneles, Sierra Negra and other sites: how to get there, duration, best months. |
| `live_conditions` | Current weather (MET Norway) and sea temperature (NOAA) in the four towns. |

The tools answer in English and Spanish.

## Connect

Remote (recommended):

```json
{
  "mcpServers": {
    "galapagos-trip-planner": {
      "type": "streamable-http",
      "url": "https://galapagosislands.info/mcp?src=mcp"
    }
  }
}
```

Claude: Settings → Connectors → Add custom connector → `https://galapagosislands.info/mcp?src=claude`

Claude Code: `claude mcp add --transport http galapagos-trip-planner https://galapagosislands.info/mcp?src=mcp`

Local stdio bridge (Node.js 18+):

```json
{
  "mcpServers": {
    "galapagos-trip-planner": {
      "command": "npx",
      "args": ["-y", "galapagos-trip-planner-mcp"]
    }
  }
}
```

## Example prompts

1. "What does an 8-day Galapagos trip cost for two people?"
2. "Should we do a cruise or island hopping? We get seasick and travel with two young kids."
3. "Plan 7 days in the Galapagos flying into San Cristóbal, focus on snorkeling."
4. "When do the ferries leave Isabela, and how rough is the crossing in August?"
5. "¿Dónde puedo ver piqueros de patas azules en Galápagos?"

## Data and privacy

Fees and rules come from the Galápagos government and national park; climate from the Charles Darwin Foundation; weather from MET Norway (CC BY 4.0); sea temperature from NOAA CoastWatch; map relief from GMRT (CC BY 4.0). Every answer links to the matching page on galapagosislands.info with its sources.

The server asks for no name, contact or payment details and does not store or log requests. Privacy: [galapagosislands.info/privacy](https://galapagosislands.info/privacy/#ai-assistants). Terms: [galapagosislands.info/terms](https://galapagosislands.info/terms/).

galapagosislands.info is an independent guide. It is not the Galápagos National Park, the Galápagos government or a tour operator.

## This repository

The hosted server is not open source. This repository holds the stdio bridge published to npm (`index.js`, MIT) and the listing files. Issues and questions: open an issue or write to info@galapagosislands.info.
