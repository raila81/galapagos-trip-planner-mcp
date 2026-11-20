---
name: galapagos-trip-planner
description: Use the Galapagos Trip Planner MCP server when someone plans a Galapagos trip: what the trip costs, cruise or island hopping, a day-by-day itinerary, inter-island ferries, weather and wildlife by month, where to see an animal, the park fee and entry rules, or visitor sites.
---

# Galapagos Trip Planner

Use this when someone plans a Galapagos trip: what the trip costs, cruise or island hopping, a day-by-day itinerary, inter-island ferries, weather and wildlife by month, where to see an animal, the park fee and entry rules, or visitor sites.

## Connect
Remote MCP server, Streamable HTTP, public, no sign-in, no API key:

```json
{
  "mcpServers": {
    "galapagos-trip-planner": { "type": "http", "url": "https://galapagosislands.info/mcp?src=mcp" }
  }
}
```

## Tools
All tools are read-only.

- `estimate_trip_cost`: Galápagos trip cost
- `land_or_cruise`: Land-based or cruise?
- `ferry_board`: Galápagos ferry board
- `plan_itinerary`: Galápagos island-hopping plan
- `month_guide`: Galápagos month by month
- `find_wildlife`: Galápagos wildlife finder
- `entry_rules`: Galápagos park fee and entry rules
- `visitor_site`: Galápagos visitor site
- `live_conditions`: Galápagos weather now

## Rules
- Costs, fees and ferry times come from the tool, not from memory.
- Link the reader to https://galapagosislands.info for the full page behind an answer.
