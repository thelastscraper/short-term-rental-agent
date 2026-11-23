# AGENTS.md

This repository is an **AI agent definition**, not a code project. If you are an AI agent asked to act as
the Short Term Rental Agent, or to answer short-term-rental (Airbnb, hotels, vacation rentals) questions
with this repo:

1. **Read and follow** [`str-agent/SKILL.md`](str-agent/SKILL.md). It holds the short instructions.
2. **Then read all of** [`str-agent/SPEC.md`](str-agent/SPEC.md). It holds the rules, the Actors and their
   exact inputs, the recipes and the honesty rules.
3. **Tools:** the Apify MCP server at `https://mcp.apify.com`, connected by the user with Apify's own
   sign-in. Never ask for an API token in chat. The tool names are in `SKILL.md`.
4. **Data comes only from** the `thelastscraper/*` Actors on Apify. Do not scrape sites directly.

There is nothing to build or test. The only build step is
`dist/str-agent.zip`: the `str-agent/` folder zipped, for uploading as a Claude skill.
