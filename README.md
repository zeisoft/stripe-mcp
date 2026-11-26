<div align="center">

<img src="assets/cover.png" alt="Stripe through HeyMetra's MCP server" width="100%">

# Stripe &times; HeyMetra

**Payments, subscriptions, invoices and payouts, read with your own key.**

Your pipeline lives in Stripe. What it cost to fill it lives somewhere else entirely. Ask once, across both.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-stripe-1f6feb)](https://heymetra.com/connectors/stripe/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Ask it things like

> What did we take in net last month, and how much was refunded?

> How many subscriptions are active, and what are they worth per month?

> Which payments failed last week, and what reason did the bank give?

> How much did Stripe take in fees this month?

> Which invoices are still open and past due?

> Are any disputes open, and how much is at stake?

No dashboard, no export, no query language. You ask in the assistant you already use and the answer comes back with the account it came from.

## Connect Stripe

**1. Copy a secret key or create a restricted one**

Stripe Dashboard → Developers → API keys. The secret key there works, and so does a restricted key you create on the same page. HeyMetra reaches only what the key allows in Stripe, and every change your assistant proposes still waits for your yes in your assistant.

> A restricted key carries only the permissions set on it. A resource left at None answers as not permitted, and the rest keep working.

**2. Paste it into HeyMetra**

A live key starts with sk_live_ or rk_live_. Choose Stripe on the Connections screen and paste it. It is stored encrypted and never shown again, here or anywhere else.

> A key starting sk_test_ or rk_test_ is the test mode one. It connects and answers about test data, which reads as a business with almost no revenue.

**3. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Grok, Perplexity, Claude Code, Codex, Cursor or Antigravity. Your Stripe account answers there once it connects.

The same steps are on the docs page: [Stripe setup guide](https://heymetra.com/docs/stripe/).

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans, an owner adds the connector for the whole organization under Organization settings → Connectors, and each member then connects to it._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — chatgpt.com/plugins → + → Add custom MCP server</summary>

Paste the address above into chatgpt.com/plugins → + → Add custom MCP server.

_Add it on chatgpt.com in a browser, because the mobile app cannot add one. Every ChatGPT plan can, Free included. In a Business, Enterprise or Edu workspace, an admin or owner decides whether members can add custom MCP servers. ChatGPT needs the full address, including /mcp at the end._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_On Grok Business and Enterprise, a team admin has to provision the connector in xAI's cloud console before members can use it._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Plugins → Add custom → Connector → Add MCP connector → Remote</summary>

Paste the address above into Plugins → Add custom → Connector → Add MCP connector → Remote.

_In an organization, members can add a custom connector only after an admin turns on Allow members to add custom connectors, which is off by default._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_You can also add the server to a .mcp.json file at the project root. Run /mcp in a session to sign in and to check that it connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Codex reads the server from an [mcp_servers.<name>] section in config.toml, and you sign in with codex mcp login <name>._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Cursor signs in to HeyMetra without a client ID or secret, so the server entry needs no auth block._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Antigravity's documented key for the address is serverUrl, though it also accepts url._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Full account access** | Lets your assistant read anything in this account to answer your questions. The figures are the provider's own, not ones HeyMetra has checked. It can also propose changes: none is applied until you approve it, and HeyMetra cannot undo one afterwards. | Yes — every change waits for your approval |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Ask anything about this account and get the answer from its live data. Reads only, and the figures are the provider's own rather than ones HeyMetra has checked.
- Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.
</details>

Anything that would change something comes back as a proposal you approve. Nothing is applied before your yes, and only on an account you connected with permission to change it. [How that works](https://heymetra.com/security/).

## When something goes wrong

<details>
<summary>It connects, and the figures are a fraction of what Stripe shows.</summary>

**Why:** A test-mode key. It answers about the test ledger, which is a different set of books rather than an error.

**Fix:** Switch the dashboard out of test mode before copying or creating the key, and check it starts sk_live_ or rk_live_.

</details>

<details>
<summary>Some answers work and others are refused as not permitted.</summary>

**Why:** A restricted key without Read on that resource. Each kind of question reads a different one, so a missing permission shows up as one question failing rather than the connection failing.

**Fix:** Edit the restricted key in Stripe and give it Read on the resource named in the refusal. The same key updates in place; there is nothing to paste again.

</details>

<details>
<summary>You approved a change and Stripe refused it.</summary>

**Why:** A restricted key with Read but not Write on that resource, or a connection set up read-only.

**Fix:** Give the key Write on the resource in Stripe. A read-only connection is changed by connecting again and allowing changes.

</details>

<details>
<summary>A platform's connected accounts are missing.</summary>

**Why:** A key reads the account it belongs to. Stripe Connect accounts are separate accounts.

**Fix:** Connect each account HeyMetra should see with its own key. If that is unworkable at your scale, tell us: your assistant can send HeyMetra a request, and it is counted.

</details>

## What HeyMetra reads from Stripe

Connect with a Stripe secret key or a restricted key. HeyMetra adds no limit of its own: your assistant reads whatever the key may read, including payments, refunds, disputes, payouts, the balance and Stripe's fees, customers, subscriptions, invoices, products, prices, coupons and checkout sessions. When you connect, you choose whether your assistant may also propose changes, and every change it proposes waits for your approval.

<details>
<summary>About Stripe</summary>

Stripe is the payments platform that processes your charges, subscriptions, and payouts. It’s the source of truth for revenue, MRR, and churn.
</details>

## One connection, not seven

The reason to read Stripe through HeyMetra rather than through a server that only knows Stripe is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://github.com/zeisoft/google-ads-mcp) · [Meta](https://github.com/zeisoft/meta-ads-mcp)

**Analytics** — [Google Analytics 4](https://github.com/zeisoft/google-analytics-4-mcp) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [n11](https://github.com/zeisoft/n11-mcp) · [Çiçeksepeti](https://github.com/zeisoft/ciceksepeti-mcp) · [Amazon Seller Central](https://github.com/zeisoft/amazon-seller-central-mcp) · [ikas](https://github.com/zeisoft/ikas-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — **Stripe** · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://github.com/zeisoft/revenuecat-mcp) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — [Jira](https://github.com/zeisoft/jira-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Stripe connector page](https://heymetra.com/connectors/stripe/)
- [Stripe setup guide](https://heymetra.com/docs/stripe/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with Stripe. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
