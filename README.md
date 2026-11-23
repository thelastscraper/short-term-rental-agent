# Short Term Rental Agent

An AI agent for short-term-rental (STR) questions that answers with **live data**. It reads Airbnb listings,
calendars and reviews, Google Hotels prices, and, from Google Hotels' price lists, the same property's price
on Booking.com, Expedia, Agoda, Vrbo and its official site. It runs as a **Claude skill** or a **Grok Bot template**, and gets its
data from my Apify Actors (`thelastscraper/*`). It is written for **any AI agent that can use MCP tools and run code**:
Claude, ChatGPT, Grok, Gemini, Cursor and others. The setup steps below follow each platform's documentation;
it has not been tested end to end on every one yet.

## What it does

| You are | You ask | It does |
|---|---|---|
| Airbnb host | "How do my listings compare with my real competition?" | Builds a comp set of up to 20 truly comparable listings for each of your listings (at least 10, or it tells you): same size and format, the same key amenities, nearest first. Then shows your price percentile, occupancy range, rating gaps and the top 3 actions. |
| Property manager | "Which of my 40 listings are mispriced?" | Triages the whole portfolio against nearby comps, then runs the full analysis on the 5 worst. |
| Company on several channels | "Is my Booking.com price above my own site?" | Your price on every booking site Google shows for your dates, next to your Airbnb price. |
| Investor | "What can a 2-bedroom earn in Lisbon?" | Supply, asking rates, occupancy range and revenue range, each with its sample size. Investor math only with your own numbers. |

**How it answers:**
- Ranges and sample sizes always, never invented numbers.
- It never compares a host with their own listings.
- It never shows guests' personal data.
- It says what the data cannot tell, for example booked vs. blocked nights.

## Install

Every platform needs the same two things:
- **Data:** Apify's MCP server, `https://mcp.apify.com`. You connect it with your own Apify account; no
  token is pasted in chat.
- **Instructions:** [`str-agent/SKILL.md`](str-agent/SKILL.md), which is short, plus
  [`str-agent/SPEC.md`](str-agent/SPEC.md), the full brief.

| Platform | Connect Apify | Load the agent |
|---|---|---|
| Claude (claude.ai, Desktop) | Settings → Connectors → Apify, or a custom connector with `https://mcp.apify.com` | Upload [`dist/str-agent.zip`](dist/str-agent.zip) as a skill |
| Claude Code | `claude mcp add apify "https://mcp.apify.com" -t http` | `mkdir -p ~/.claude/skills && cp -r str-agent ~/.claude/skills/` |
| ChatGPT | Developer mode → Apps & Connectors → Create, with `https://mcp.apify.com` (beta; depends on your plan) | A Project or GPT: paste `SKILL.md` into the instructions and add `SPEC.md` as a file |
| Grok | Apify's Grok Bot plugin | Build a template from `SPEC.md` |
| Any other agent with MCP (Gemini CLI, Cursor, VS Code…) | Add the remote MCP server `https://mcp.apify.com` | Use `SKILL.md` as the system prompt and give it `SPEC.md`. Coding agents read [`AGENTS.md`](AGENTS.md). |

### Claude (claude.ai or Claude Desktop), step by step

1. **Connect Apify:** Settings → Connectors → Apify. If it isn't listed, choose Add custom connector and
   enter `https://mcp.apify.com`. Then sign in to Apify.
2. **Turn on code execution:** Settings → Capabilities.
3. **Upload the skill:** download [`dist/str-agent.zip`](dist/str-agent.zip), then go to Customize → Skills →
   Upload a skill.
4. **Ask,** for example: *"Compare my Airbnb listings with their competition:
   https://www.airbnb.com/users/show/&lt;your profile id&gt;"*.

### Claude Code

```bash
claude mcp add apify "https://mcp.apify.com" -t http
mkdir -p ~/.claude/skills && cp -r str-agent ~/.claude/skills/
```

### Grok

1. Connect Apify with its official Grok Bot plugin.
2. Build a Grok Bot template from [`str-agent/SPEC.md`](str-agent/SPEC.md): its instructions, first message
   and skills.

## Cost

- **The agent itself is free.**
- **The data runs on your own Apify account.** Apify includes $5 of free usage every month.
- **A typical host analysis** (3 listings, 20 comps each) is estimated at about $1.22 on Apify's Free
  plan (about $0.96 on Bronze, Apify's Starter plan), or about $0.83 for a quick version without the
  competitors' reviews and the hotels.
- **The agent quotes the cost** before every paid run and caps it.

Prices per Actor are on their Apify Store pages:
- [Airbnb Scraper](https://apify.com/thelastscraper/airbnb-scraper)
- [Airbnb Listing Details](https://apify.com/thelastscraper/airbnb-listing-details)
- [Airbnb Occupancy & Revenue](https://apify.com/thelastscraper/airbnb-calendar-occupancy)
- [Airbnb Reviews](https://apify.com/thelastscraper/airbnb-reviews)
- [Google Hotels & Vacation Rental Prices vs Airbnb](https://apify.com/thelastscraper/google-hotels-vacation-rentals)

## Files

| File | What it is |
|---|---|
| `str-agent/SKILL.md` | The skill's entry point for Claude |
| `str-agent/SPEC.md` | The agent's full brief: rules, Actors, recipes and honesty rules. It is also the source for the Grok template. |
| `dist/str-agent.zip` | The skill, ready to upload to Claude |
| `AGENTS.md` | What coding agents (Codex, Copilot, Cursor, Gemini CLI…) read first |
| `CLAUDE.md` | The same pointer, for Claude Code |
| `LICENSE` | MIT |

## Disclosure

I build and maintain the Apify Actors this agent uses. They are pay-per-event: you pay Apify for what each
run fetches, at the prices on their Store pages.

Airbnb, Booking.com, Expedia, Agoda, Vrbo, Google, Gemini, Apify, Grok, xAI, Claude, Anthropic, OpenAI,
ChatGPT, Cursor, Microsoft, Visual Studio Code and the other names mentioned are trademarks of their owners. This project is not affiliated with or endorsed by any of them.

## License

[MIT](LICENSE)
