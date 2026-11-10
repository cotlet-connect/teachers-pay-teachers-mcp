# How to connect Teachers Pay Teachers to Claude Code, ChatGPT and any AI agent

**Yes, Claude, ChatGPT and other AI agents can work in your Teachers Pay Teachers account.** Teachers Pay Teachers has no official connector in Claude's directory. Cotlet.dev connects your own signed-in Teachers Pay Teachers seller account to any AI agent, so the AI updates your listings and reads your sales for you.

## What you can ask

> Change the price of my "Fractions Task Cards Grade 4" to $4.50 and add a line to the description about the answer key.

> How many units did I sell last week? List my top 5 products by earnings.

> Rewrite the titles of my 10 lowest-selling listings so each one includes the grade level and subject.

> Which of my products had no sales in the last 60 days? Make a list with their current price.

> Compare my sales this October with last October, product by product.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Run it locally (stdio)

This repo is a real MCP server. It speaks MCP over stdio, lists its Teachers Pay Teachers tools without any key, and forwards every tool call to the hosted Cotlet.dev server. The hosted URL above stays the recommended way. Use this when your client only starts local servers.

```json
{"mcpServers":{"teachers-pay-teachers":{"command":"uvx","args":["teachers-pay-teachers-mcp"],"env":{"COTLET_API_KEY":"your-key"}}}}
```

Or with Docker:

```bash
docker build -t teachers-pay-teachers-mcp .
docker run -i --rm -e COTLET_API_KEY teachers-pay-teachers-mcp
```

Tools: `teachers_pay_teachers_guide`, `teachers_pay_teachers_status`, `teachers_pay_teachers_open`, `teachers_pay_teachers_read`, `teachers_pay_teachers_click`, `teachers_pay_teachers_type`, `teachers_pay_teachers_close`. Without `COTLET_API_KEY` a tool call answers: "Set COTLET_API_KEY. Get a key at https://cotlet.dev/app".

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install teachers-pay-teachers-mcp        # or run it once: uvx teachers-pay-teachers-mcp connect
teachers-pay-teachers-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 teachers_pay_teachers_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 teachers_pay_teachers_agent.py status    # is Teachers Pay Teachers ready in your Cotlet.dev account
python3 teachers_pay_teachers_agent.py guide     # Teachers Pay Teachers screens and sign-in link
python3 teachers_pay_teachers_agent.py read      # open Teachers Pay Teachers, read the page, close the browser
python3 teachers_pay_teachers_agent.py tools     # list Cotlet.dev tools
python3 teachers_pay_teachers_agent.py serve     # start the stdio MCP server (same as no argument)
```

## Questions from Teachers Pay Teachers users

**Does Teachers Pay Teachers have an API for sellers?**

You don't need a Teachers Pay Teachers API to use Cotlet.dev. It works in your own signed-in seller account, so your AI agent can update listings and read your sales directly.

**How do I connect Teachers Pay Teachers to ChatGPT?**

Add Cotlet.dev as an app in ChatGPT (Settings → Apps, connector URL `https://cotlet.dev/mcp/v1`), sign in to Teachers Pay Teachers once in your Cotlet.dev Cloud Browser, and ask ChatGPT in plain words. No code and no Teachers Pay Teachers API key.

**Is there a way to use Claude with Teachers Pay Teachers?**

Yes. In Claude Code run the one-line `claude mcp add` command above; in the Claude app add `https://cotlet.dev/mcp/v1` as a custom connector. Claude then works in your own Teachers Pay Teachers account.

**Is there a Teachers Pay Teachers MCP server?**

Teachers Pay Teachers has no official MCP server. Cotlet.dev is a hosted MCP server that works in Teachers Pay Teachers for you, 24/7, with Claude, ChatGPT, Cursor, Codex, n8n, Make and Zapier.

## Find it on

- [Teachers Pay Teachers on Cotlet.dev](https://cotlet.dev/integrations/teachers-pay-teachers-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=teachers-pay-teachers&utm_content=find)
- [PyPI package teachers-pay-teachers-mcp](https://pypi.org/project/teachers-pay-teachers-mcp/)
- [Odel](https://odel.app/modules/cotlet/teachers-pay-teachers)
- [Step-by-step guide (PDF) on Internet Archive](https://archive.org/details/cotlet-connect-teachers-pay-teachers-to-ai-agents-guide)

## Also works with

- [Mangomint MCP](https://github.com/cotlet-connect/mangomint-mcp)
- [Wanderlog MCP](https://github.com/cotlet-connect/wanderlog-mcp)
- [SmugMug MCP](https://github.com/cotlet-connect/smugmug-mcp)
- [Garmin Connect MCP](https://github.com/cotlet-connect/garmin-mcp)
- [Housecall Pro MCP](https://github.com/cotlet-connect/housecall-pro-mcp)
- [Medium MCP](https://github.com/cotlet-connect/medium-mcp)
- [Crexi MCP](https://github.com/cotlet-connect/crexi-mcp)
- [DistroKid MCP](https://github.com/cotlet-connect/distrokid-mcp)
- [LinkedIn MCP](https://github.com/cotlet-connect/linkedin-mcp)
- [EstimateOne MCP](https://github.com/cotlet-connect/estimateone-mcp)
- [Google Search Console MCP](https://github.com/cotlet-connect/google-search-console-mcp)
- [Lichess MCP](https://github.com/cotlet-connect/lichess-mcp)
- [Strava MCP](https://github.com/cotlet-connect/strava-mcp)
- [StreamElements MCP](https://github.com/cotlet-connect/streamelements-mcp)
- [Meetup MCP](https://github.com/cotlet-connect/meetup-mcp)
- [AccuRanker MCP](https://github.com/cotlet-connect/accuranker-mcp)
- [GetYourGuide MCP](https://github.com/cotlet-connect/getyourguide-mcp)
- [Idealista MCP](https://github.com/cotlet-connect/idealista-mcp)
- [Riverside MCP](https://github.com/cotlet-connect/riverside-mcp)
- [Udemy MCP](https://github.com/cotlet-connect/udemy-mcp)
- [Faire MCP](https://github.com/cotlet-connect/faire-mcp)
- [Buildertrend MCP](https://github.com/cotlet-connect/buildertrend-mcp)
- [Fresha MCP](https://github.com/cotlet-connect/fresha-mcp)
- [Booksy MCP](https://github.com/cotlet-connect/booksy-mcp)
- [BookingKoala MCP](https://github.com/cotlet-connect/bookingkoala-mcp)
- [Milanote MCP](https://github.com/cotlet-connect/milanote-mcp)
- [Partiful MCP](https://github.com/cotlet-connect/partiful-mcp)
- [Contractor Foreman MCP](https://github.com/cotlet-connect/contractor-foreman-mcp)
- [Pixieset MCP](https://github.com/cotlet-connect/pixieset-mcp)
- [GlossGenius MCP](https://github.com/cotlet-connect/glossgenius-mcp)
- [ZenMaid MCP](https://github.com/cotlet-connect/zenmaid-mcp)
- [FieldEdge MCP](https://github.com/cotlet-connect/fieldedge-mcp)
- [Phorest MCP](https://github.com/cotlet-connect/phorest-mcp)
- [DINGG MCP](https://github.com/cotlet-connect/dingg-mcp)
- [Invoice Simple MCP](https://github.com/cotlet-connect/invoice-simple-mcp)
- [PhotoShelter MCP](https://github.com/cotlet-connect/photoshelter-mcp)
- [RazorSync MCP](https://github.com/cotlet-connect/razorsync-mcp)
- [ShootProof MCP](https://github.com/cotlet-connect/shootproof-mcp)
- [Invoice2go MCP](https://github.com/cotlet-connect/invoice2go-mcp)
- [Appointy MCP](https://github.com/cotlet-connect/appointy-mcp)
- [Contractor+ MCP](https://github.com/cotlet-connect/contractor-plus-mcp)
- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/teachers-pay-teachers-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=teachers-pay-teachers

Start free: https://cotlet.dev/signup?app=teachers-pay-teachers&utm_source=github&utm_medium=readme&utm_campaign=teachers-pay-teachers
