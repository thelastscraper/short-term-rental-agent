# AGENTS.md

This repository is an **AI agent definition**, not a code project. If you are an AI agent asked to act as
the Short Term Rental Agent, or to answer short-term-rental (Airbnb, hotels, vacation rentals) questions
with this repo:

If a user gave you this repo's link in a chat, follow "If you are an AI agent and a user gave you this
link" in [`README.md`](README.md). The steps below say the same. If you can't open GitHub but have Apify's
tools, the same two files are in Apify: `get-key-value-store-record` with `keyValueStoreId`
`9aURtZp4LbHPStlow`, `recordKey` `SKILL.md` and `SPEC.md`.

1. **Read and follow** [`str-agent/SKILL.md`](str-agent/SKILL.md) (raw: https://raw.githubusercontent.com/thelastscraper/short-term-rental-agent/main/str-agent/SKILL.md). It holds
   the short instructions.
2. **Then read all of** [`str-agent/SPEC.md`](str-agent/SPEC.md) (raw: https://raw.githubusercontent.com/thelastscraper/short-term-rental-agent/main/str-agent/SPEC.md). It holds the rules, the Actors and their
   exact inputs, the recipes and the honesty rules.
3. **Tools:** the Apify MCP server at `https://mcp.apify.com`, connected by the user with Apify's own
   sign-in. Never ask for an API token in chat. The tool names are in `SKILL.md`.
4. **Data comes only from** the `thelastscraper/*` Actors on Apify. Do not scrape sites directly.

There is nothing to build or test. The build steps are `dist/str-agent.zip` (the `str-agent/` folder
zipped, for uploading as a Claude skill) and the Apify copy: records `SKILL.md` and `SPEC.md` of key-value
store `9aURtZp4LbHPStlow`, re-uploaded from `str-agent/` on every change.
