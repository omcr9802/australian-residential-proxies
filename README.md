# australia residential proxy: what Australian IPs really cost, how to target Sydney or Melbourne, and which package fits your workload

If you need to see what a website serves to Sydney, a datacenter IP in Sydney usually isn't enough. Plenty of Australian sites now score the connection, not just the country: they check whether the address belongs to a residential ISP subnet, whether it's been flagged by other traffic, and whether the ASN looks like a home broadband line. An Australian residential proxy is the answer to that specific problem — your traffic exits from an IP registered to a real household connection at an Australian ISP, like Telstra or Optus, so the target sees an ordinary local visitor rather than a rented server.

This guide covers what those IPs are good for, where they fall short, and how 9Proxy's Australian coverage and pricing actually work — including the package list and how to target AU cities in the username string.

## What an Australian residential proxy actually does

A residential proxy is an intermediary that forwards your request through someone's home internet connection. The IP you appear as belongs to that connection, so geolocation checks, ISP lookups and reputation scores all read as "Australian consumer."

Two things make the Australian case distinct from the generic "get a US IP" advice:

- **Domain and locale logic.** Sites like `google.com.au`, `realestate.com.au` or local retail storefronts serve different inventory, pricing and even layouts depending on where the request comes from. A US IP often gets a redirected international version.
- **Ad and content inventory.** Australian ad campaigns, sponsorship slots and regional streaming catalogues are only visible from inside the country. If you're verifying what an Australian user actually sees, the IP has to be Australian.

Datacenter proxies are faster and cheaper per request, and there's nothing wrong with them for bulk, low-friction targets. The moment a target's bot protection cares about IP class, you're paying for residential. That's the trade.

## What people use Australian IPs for

The use cases are fairly consistent across the proxy market, and most of them are unglamorous:

- **Local price and stock checks.** Australian e-commerce pricing in AUD, local promotions and shipping rules that don't show up on the international version of the site. Retailers routinely run country-specific deals.
- **SEO and SERP tracking.** Rankings on `google.com.au` differ from `.com`, and the local pack is geography-dependent. Agencies tracking Australian clients need AU exit IPs, ideally from more than one city.
- **Ad verification.** Checking that a campaign bought for Australian inventory is actually being served, and that competitors' creatives render properly.
- **Property and travel data.** Listing portals and fare aggregators gate a lot of detail behind geography. Oxylabs lists travel fare aggregation and review monitoring among the core Australia proxy use cases for exactly this reason.
- **Account and identity work.** Managing Australian social or marketplace accounts, or running a buying bot for a local drop, where a session needs to look like one consistent local user.
- **Testing.** Verifying how a site, app or CDN behaves for Australian visitors before you commit to a launch.

The dividing line between these is session behaviour. Price checks and SERP tracking want a rotating IP on every request. Account work wants the same AU IP held for the length of the session. That difference decides which pricing model you buy.

## Does 9Proxy have Australian residential IPs?

Yes. 9Proxy is a residential-only provider — no datacenter, mobile or ISP proxy line — advertising a pool of 20M+ residential IPs across 90+ countries, with Australia listed among its covered markets. Its own documentation describes targeting down to country, state/region, city, ZIP/postal code and ISP, over HTTP/HTTPS and SOCKS5.

What 9Proxy does *not* publish is an Australia-specific IP count. You'll see competitors quoting explicit AU figures — Bright Data advertises around 480,000 Australian IPs, IPRoyal around 585,000, Oxylabs over a million — but those are vendor-published numbers on a different measurement basis, so comparing them head-to-head with 9Proxy's total pool tells you very little. The honest reading: 9Proxy's Australia depth is not documented publicly, and if you need guaranteed city-level AU volume, that's a question to put to their support before committing.

There are two products, and they behave differently:

|  | Residential by IPs | Residential by GB |
| --- | --- | --- |
| Billing | Per IP, unlimited bandwidth | Per GB consumed |
| Expiry | Unused IPs never expire | 180 days (unlimited on Enterprise) |
| IP lifetime | A few hours to ~24h | Rotates per request or per sticky session |
| Endpoints | 1 IP = 1 activation when forwarded | Unlimited endpoints generated |
| Auth | 9Proxy desktop app, local port forwarding | Username/password or IP whitelist |
| Best for | Long logged-in sessions, heavy transfers | High rotation, light requests, cloud runs |

That last row matters more than the marketing around it. If you're running from a cloud server, the GB product is the one that works without a desktop app in the loop.

## How to target Australia

Targeting isn't configured through a dashboard toggle for the IP product — it's baked into the proxy username. The general format from 9Proxy's documentation is:


<subuser>-country-<cc>-st-<state>-city-<city>-isp-<isp>-sst-<minutes>-ssid-<id>


Only `country-au` is required. Everything else narrows the pool, and narrowing the pool reduces availability — the docs explicitly recommend targeting by country alone when you want the fastest response.

A practical setup:

1. Create an account and top up a package — either a GB package or an IP package.
2. For GB packages, create a sub-user and generate proxies from the dashboard. For IP packages, install the desktop app (Windows, macOS or Linux) and log in.
3. Build the username. Rotating Australian IP: `subuser-country-au`. Sydney, rotating: `subuser-country-au-city-sydney`.
4. For a session that has to hold one AU identity, add stickiness: `subuser-country-au-sst-20` keeps the same IP for 20 minutes. Add `-ssid-bot01` if you need several parallel sticky sessions from the same configuration.
5. Verify the exit country before you run anything real:

bash
curl -x your_proxy_host:your_port \
     -U "subuser-country-au-city-sydney:YOUR_PASSWORD" \
     https://ipinfo.io


If `ipinfo.io` reports anything other than Australia, the filter combination is too tight and the pool is falling back. Drop the city, or the ISP filter, and retry.

A common first-time mistake is stacking state, city *and* ISP filters in one username. Each additional parameter cuts the candidate IP set. Start at country level, and only add geography when a result actually depends on it.

👉 [Start with an Australian-targeted 9Proxy account here](https://bit.ly/9-Proxy)

## 9Proxy pricing: every package in one table

9Proxy runs on a balance-based model with no recurring subscription. Prices below reflect the June 1, 2026 adjustment, which raised IP-based and bundle pricing while leaving GB packages untouched.

| Package | Type | Price | Effective rate |
| --- | --- | --- | --- |
| 100 IPs | IP-based | $24 | $0.24/IP |
| 500 IPs | IP-based | $72 | $0.144/IP |
| 1,000 + 500 bonus IPs | IP-based | $126 | $0.084/IP |
| 2,500 IPs | IP-based | $210 | $0.084/IP |
| 5,000 IPs | IP-based | $360 | $0.072/IP |
| 15,000 IPs | IP-based | $720 | $0.048/IP |
| 25,000 IPs | IP-based | $863 | $0.035/IP |
| 50,000 IPs | IP-based | $1,438 | $0.029/IP |
| 100,000 IPs | Business IP | $2,300 | $0.023/IP |
| 200,000 IPs | Business IP | $4,140 | $0.021/IP |
| 500,000 IPs | Business IP | $8,625 | $0.018/IP |
| 5 GB | GB-based, 180-day validity | $15 | $3.00/GB |
| 50 + 5 bonus GB | GB-based, 180-day validity | $105 | $2.10/GB |
| 100 GB | GB-based, 180-day validity | $150 | $1.50/GB |
| 200 GB | GB-based, 180-day validity | $200 | $1.00/GB |
| 1,000 GB | GB-based, 180-day validity | $800 | $0.80/GB |
| 2,000 GB | GB-based, 180-day validity | $1,500 | $0.75/GB |
| 3,000 GB | Enterprise GB, no expiry | $2,160 | $0.72/GB |
| 6,000 GB | Enterprise GB, no expiry | $4,200 | $0.70/GB |
| 10,000 GB | Enterprise GB, no expiry | $6,800 | $0.68/GB |
| Starter bundle: 100 IPs + 5 GB | Bundle | $30 | — |
| Popular bundle: 1,500 IPs + 50 GB | Bundle | $180 | — |
| Pro bundle: 5,000 IPs + 500 GB | Bundle | $720 | — |
| Any of the above | Purchase | [Open an account with this invite link](https://bit.ly/9-Proxy) | — |

A few notes that the table doesn't capture. Enterprise GB packages add team mode for one owner plus up to five members, per-member traffic controls and unlimited share-code creation. Payment options include cards, bank cards, crypto (USDT, BTC, ETH, LTC, DOGE and others), Alipay, Apple Pay and Google Pay. And the advertised entry price of "$0.018/IP" only exists at the 500,000-IP tier — the realistic entry cost for an individual is $24.

> On June 1, 2026, 9Proxy raised IP-based and bundle pricing for the first time. GB-based package prices were explicitly left unchanged. Anything you read quoting $0.015/IP or a $20 entry package is pre-adjustment.

## IP-based or GB-based for Australian work

This is the decision that actually changes your bill, so it's worth doing the arithmetic rather than following the "unlimited bandwidth" line.

**Choose the GB model when** you're collecting Australian data across many different IPs — SERP checks, price monitoring, ad verification, stock lookups. Each request is small and you want a fresh AU IP each time. A 5 GB package at $15 is a cheap way to test whether 9Proxy's Australian pool even performs on your targets.

**Choose the IP model when** a single stable Australian identity matters more than IP variety. Unlimited bandwidth per IP means a long scraping or automation session costs the same whether you pull 50 MB or 5 GB through that one address. The IP lasts a few hours to roughly a day before it drops, and you can enable auto-refresh to swap in a fresh one automatically.

A rough comparison: if your Australian workload pushes around 10 GB a month, the 100 GB GB-package at $150 covers ten months of that. If instead you're holding three Australian accounts logged in for multi-hour sessions with unpredictable data volume, 100 IPs for $24 is the cheaper structure. Same provider, same pool, completely different cost curve depending on session behaviour.

👉 [Check 9Proxy's live package pricing before you pick a model](https://bit.ly/9-Proxy)

## Limits worth knowing before you buy

- **The entry point is not small.** 100 IPs at $24 or 5 GB at $15 is the cheapest way in. There's no permanent free tier published; 9Proxy has offered limited trials to new users subject to availability, so ask support rather than assuming.
- **IPs are not static.** The IP-based product gives you real residential addresses that stay live for hours up to about 24 hours, then drop. If your Australian requirement is a permanently fixed ISP IP — for a payment gateway, a long-running bot with a whitelisted address, or account warming over months — this isn't that product. 9Proxy doesn't sell ISP or static residential proxies at all.
- **Desktop app required for IP packages.** Port forwarding happens locally on Windows, macOS or Linux. If your Australian scraping runs on a headless cloud instance, you need the GB product.
- **Pool depth shrinks as you narrow.** Australian city targeting will return fewer candidates than country-wide targeting. There's no published figure for how many Melbourne or Brisbane IPs are available.
- **GB traffic expires.** 180 days on standard packages. Only Enterprise GB packages carry unlimited validity.
- **Residential only.** No mobile IPs, no datacenter IPs. If your Australian project needs a 4G/5G AU address, you're looking at the wrong provider entirely.

## How the Australian pool compares

The uncomfortable truth about Australia proxy coverage is that pool sizes are self-reported and rarely audited. Bright Data publishes around 480,000 AU IPs, Oxylabs claims over a million, IPRoyal lists roughly 585,000, and Geonode advertises 500,000+ at $0.27/GB. 9Proxy publishes a total figure — 20M+ across 90+ countries — and no country breakdown, so you can't line its Australian depth up against those numbers directly.

Independent review coverage is mixed but generally positive on price. Geekflare's 2026 review treats the IP-based model as the stronger fit for sustained sessions and notes the post-adjustment entry costs of $24 and $72. ProxyLook flags that the widely-quoted 20M figure grew from around 9M following a merger with BeeProxy, and warns that pool headline numbers vary considerably between sources. That's a reasonable caution: treat pool size as a marketing claim from every provider in this category, including this one.

Where 9Proxy's position is genuinely defensible is cost structure, not pool size. Per-IP billing with unlimited bandwidth is unusual in the residential market, and $0.68/GB at the top tier competes with providers charging several times that. If your Australian workload is bandwidth-heavy and session-stable, that's the argument for it. If it needs the deepest possible AU city-level pool with guaranteed static addresses, the larger providers are built for that.

## Bottom line

For Australian price monitoring, SERP tracking, ad verification and geo-testing, the cheap way to find out whether 9Proxy's pool handles your targets is the 5 GB package at $15 — pay per GB, rotate freely, don't worry about IP allocation. For Australian account sessions and long automation runs where one stable local identity does a lot of data transfer, the 100 IPs at $24 with unlimited bandwidth is the better structure, as long as you're running it from a machine where the desktop app can live.

Skip it if you need static Australian ISP IPs, Australian mobile proxies, or a fully headless IP-based setup. Those aren't gaps in 9Proxy's execution; they're products it doesn't sell.

👉 [Open a 9Proxy account through this invite link and test the Australian pool](https://bit.ly/9-Proxy)
