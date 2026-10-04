# isp vs residential proxies: when a static ISP IP wins, when you need rotating residential, and what 9Proxy actually costs

The question "ISP or residential?" is usually asked backwards. People compare the two proxy types feature by feature, then pick the one with more green ticks in the table. Then the workflow breaks anyway, because the real decision isn't which type is better — it's whether your task needs **one identity to survive**, or **many identities to spread out**.

Those two needs lead to different proxy types, different billing models, and very different monthly bills.

This guide walks through what each type actually is, where each one fails, and how the billing model underneath — per IP versus per GB — often matters more than the proxy type itself. 9Proxy shows up later, because it sells one of those models at an aggressive price and, honestly, because it doesn't sell everything.

## What an ISP proxy actually is

An ISP proxy is an IP address registered to a consumer internet provider — the kind of ASN that resolves to Comcast, AT&T, or Vodafone — but hosted on server infrastructure instead of someone's living room.

Target sites see a legitimate ISP ASN. Your traffic never touches a home router. That combination is why the type also gets called "static residential," and why the terminology gets messy fast: ISP proxies are *treated* as residential by detection systems, but the IPs are not real user addresses. They're data center hardware wearing a residential-looking ASN.

Two practical consequences follow. First, the IP is static by design, so a login session, a checkout flow, or a browser profile keeps the same address for as long as you hold it. Second, those IPs come in blocks, which means a subnet ban can take out a whole group at once.

## What a residential proxy actually is

Residential proxies route through real devices on real home connections. The IP belongs to a household, changes when that household's router reconnects or the network rotates you, and sits in a pool measured in millions of addresses across dozens or hundreds of countries.

Detection is harder because there's nothing artificial to detect. The trade-offs are the same ones every provider publishes: connection quality depends on a stranger's Wi-Fi, sessions can drop when a device goes offline, and you almost always pay by bandwidth rather than by address.

One clarification that saves a lot of confusion: "sticky residential" is not the same thing as "static residential." Sticky means the same IP is held for a defined window — minutes or hours — before you're rotated. Static means it doesn't change unless you release it. Sticky is a session setting. Static is a product category, and it's the ISP proxy category.

## ISP vs residential side by side

|  | ISP proxy (static residential) | Residential proxy |
| --- | --- | --- |
| IP source | ISP-registered ranges, hosted in data centers | Real household connections |
| IP lifetime | Static, you keep it | Rotating, or sticky for a set window |
| Pool size | Smaller, location list often limited | Large, geo-targeting down to city/ZIP in many networks |
| Speed | Fast and consistent | Varies with the peer connection |
| Session stability | High | Medium; drops when a peer device goes offline |
| Detection profile | Passes ASN checks, but IPs are synthetic | Hardest to fingerprint as proxy traffic |
| Subnet risk | IPs cluster in ranges | IPs rarely cluster |
| Typical pricing | Per IP, often with unlimited or generous bandwidth | Per GB in most networks, sometimes per IP |
| Best for | Logins, account persistence, checkout flows, anything rate-limited against rotating IPs | Scraping at volume, SERP and ad checks by location, anything that needs many distinct IPs |

Read the last two rows together and the pattern is clear: ISP proxies are about **identity persistence**, residential is about **scale and blending in**.

## Where each one breaks

ISP proxies fail in two predictable ways. Location coverage is thin — a network might have strong US coverage and four cities in Germany — and subnet clustering means a hard block on one address can drag its neighbors down with it. If you're running 200 accounts through IPs purchased from the same range, one aggressive ban wave can be a bad afternoon.

Residential proxies fail differently. Speed and uptime are only as good as the peers behind them, so a perfectly good scraping run can stall because a device in Ohio went to sleep. Shared pools also mean other customers' behavior affects the reputation of addresses you get assigned. And because most networks bill per GB, a request-heavy, payload-light job is cheap while a video or large-document job gets expensive fast.

Neither failure mode is a reason to avoid the type. They're reasons to stop treating them as interchangeable.

## The billing model underneath is the decision people skip

Here's the part that most comparisons leave out, and it's where money actually gets lost.

Residential proxy billing splits into two structures:

- **Per GB.** You buy traffic. IP count is irrelevant; rotate through the entire pool as much as you like, generate unlimited endpoints, and get charged for the data you move. Cheap per request, expensive per byte.
- **Per IP with unlimited bandwidth.** You buy addresses. Each one carries as much traffic as you can push through it for as long as it lives. Expensive per request, cheap per byte.

Put real numbers on it and the split stops being theoretical. At published 9Proxy rates, 500 IPs cost **$72** with no bandwidth cap, while 200 GB costs **$200**. If your job pushes more than roughly 50 GB through a handful of heavy sessions, the per-IP model pulls ahead on raw arithmetic — the shorter that session list gets and the heavier each one is, the wider the gap. If your job is 40,000 light requests that each need a fresh address, per-IP is the wrong purchase no matter how the arithmetic looks, because you'll burn through addresses on work that barely moves data.

That check takes five minutes and usually settles the ISP-vs-residential argument before you start comparing vendors.

## Where 9Proxy fits, and where it doesn't

9Proxy is a residential proxy platform — 20M+ residential IPs across 90+ countries, targeting by country, state, city, ZIP, and ISP, with HTTP/HTTPS and SOCKS5 support. It sells two residential models plus bundles.

What it does **not** sell is ISP proxies. There's no static residential tier, no per-IP product with an ISP-registered ASN. Datacenter proxies are listed as coming soon, not available. So if your workflow genuinely needs a static ISP address that survives logout and re-login for months, 9Proxy isn't the provider you're looking for, and no amount of price comparison changes that.

If your requirement is residential — rotating, geo-targeted, or heavy-bandwidth sessions on home IPs — the two product lines map cleanly onto the billing question above.

### Residential by IP vs Residential by GB

|  | Residential by IP | Residential by GB |
| --- | --- | --- |
| Billing | Fixed package by number of IPs | Fixed package by total GB |
| Traffic | Unlimited while the IP is active | Capped by purchased GB |
| Validity | Unused IPs never expire | 180 days, unlimited on Enterprise |
| IP duration | A few hours up to about 24h, varies per IP | Rotates per request, or sticky for a configured window |
| Rotation | No natural rotation; Auto Rotation Proxy available on selected ports | Rotating or sticky, your choice |
| Endpoints | 1 IP = 1 use when forwarded | Unlimited endpoints, only GB deducted |
| Authentication | 9Proxy desktop app, with optional proxy authentication | Username/password or IP whitelist |
| Setup | Desktop client required | Runs from the dashboard, no app |

The GB line is the one you can start using without installing anything, which matters if you're testing against a single target before committing to a volume purchase. The IP line is the one to look at when your sessions run long and your bandwidth guess is unreliable.

👉 [Compare both models and current package prices on 9Proxy](https://bit.ly/9-Proxy)

## Full package list and current pricing

9Proxy raised IP-based and bundle prices on June 1, 2026 — its first adjustment in three years. GB-based packages were untouched. Everything below is the published structure after that change. Prices can move again, so check the checkout total before you commit.

| Package | Type | Unit price | Total | What you get | Buy |
| --- | --- | --- | --- | --- | --- |
| 100 IPs | Residential by IP | $0.24/IP | $24 | 100 residential IPs, unlimited traffic | [Get the 100 IP package](https://bit.ly/9-Proxy) |
| 500 IPs | Residential by IP | $0.144/IP | $72 | 500 residential IPs, unlimited traffic | [Get the 500 IP package](https://bit.ly/9-Proxy) |
| 1,000 + 500 bonus IPs | Residential by IP | $0.084/IP | $126 | 1,500 residential IPs total | [Get the 1,500 IP package](https://bit.ly/9-Proxy) |
| 2,500 IPs | Residential by IP | $0.084/IP | $210 | 2,500 residential IPs | [Get the 2,500 IP package](https://bit.ly/9-Proxy) |
| 5,000 IPs | Residential by IP | $0.072/IP | $360 | 5,000 residential IPs | [Get the 5,000 IP package](https://bit.ly/9-Proxy) |
| 15,000 IPs | Residential by IP | $0.048/IP | $720 | 15,000 residential IPs | [Get the 15,000 IP package](https://bit.ly/9-Proxy) |
| 25,000 IPs | Residential by IP | $0.035/IP | $863 | 25,000 residential IPs | [Get the 25,000 IP package](https://bit.ly/9-Proxy) |
| 50,000 IPs | Residential by IP | $0.029/IP | $1,438 | 50,000 residential IPs | [Get the 50,000 IP package](https://bit.ly/9-Proxy) |
| 100,000 IPs | Residential by IP | $0.023/IP | $2,300 | 100,000 residential IPs | [Get the 100,000 IP package](https://bit.ly/9-Proxy) |
| 200,000 IPs | Residential by IP | $0.021/IP | $4,140 | 200,000 residential IPs | [Get the 200,000 IP package](https://bit.ly/9-Proxy) |
| 500,000 IPs | Residential by IP | $0.018/IP | $8,625 | 500,000 residential IPs | [Get the 500,000 IP package](https://bit.ly/9-Proxy) |
| 5 GB | Residential by GB | $3.00/GB | $15 | 5 GB, 180-day validity | [Get the 5 GB package](https://bit.ly/9-Proxy) |
| 50 GB + 5 GB bonus | Residential by GB | $2.10/GB | $105 | 55 GB total, 180-day validity | [Get the 55 GB package](https://bit.ly/9-Proxy) |
| 100 GB | Residential by GB | $1.50/GB | $150 | 100 GB, 180-day validity | [Get the 100 GB package](https://bit.ly/9-Proxy) |
| 200 GB | Residential by GB | $1.00/GB | $200 | 200 GB, 180-day validity | [Get the 200 GB package](https://bit.ly/9-Proxy) |
| 1,000 GB | Residential by GB | $0.80/GB | $800 | 1,000 GB, 180-day validity | [Get the 1,000 GB package](https://bit.ly/9-Proxy) |
| 2,000 GB | Residential by GB | $0.75/GB | $1,500 | 2,000 GB, 180-day validity | [Get the 2,000 GB package](https://bit.ly/9-Proxy) |
| Starter bundle | Bundle | — | $30 | 100 IPs + 5 GB | [Get the Starter bundle](https://bit.ly/9-Proxy) |
| Popular bundle | Bundle | — | $180 | 1,500 IPs + 50 GB | [Get the Popular bundle](https://bit.ly/9-Proxy) |
| Pro bundle | Bundle | — | $720 | 5,000 IPs + 500 GB | [Get the Pro bundle](https://bit.ly/9-Proxy) |

A few things worth noticing in that table.

The per-IP price drops steadily with volume, but it drops *slowly* between 2,500 and 5,000 IPs and then sharply from 15,000 upward. Reseller-scale buyers get a materially better rate than a solo operator buying 1,000 addresses, which is expected but easy to miss when vendors advertise the bottom-of-table number.

Bundles are priced as a discount against buying the same IPs and GB separately. The Starter bundle is $30 for 100 IPs plus 5 GB, versus $24 for the IPs and $15 for the GB alone — a modest saving, and more importantly a way to test both models in one purchase instead of guessing wrong and buying twice.

There's no subscription requirement anywhere in that list. Packages are balance-based: you buy capacity, it sits on your account, and unused IPs don't expire. That's a different shape from the monthly plans most ISP proxy providers sell, and it's worth accounting for if you're comparing a 9Proxy purchase against a recurring static-residential plan.

👉 [See the live pricing and grab the current deal on 9Proxy](https://bit.ly/9-Proxy)

## Promotions: what's real right now

Proxy vendors run a steady stream of short campaigns, and most coupon-aggregator pages are recycling dead ones. 9Proxy has run an 8% off campaign on regular IP and GB packages during Lunar New Year, an automatic 9% back coupon on first GB orders in April (coupons issued that month expired June 30), and referral-based discounts. Those specific campaigns have closed, and the coupon codes from them aren't worth typing into checkout.

What to check instead: after your first purchase, discounts that get issued to your account land under My Coupons in the dashboard and often auto-apply at checkout on your next order. There's also a coupon entry field at checkout if you've picked one up elsewhere.

9Proxy has described limited trial allocations for new users depending on availability, so if you want to test a target before buying 25,000 IPs, ask support rather than assuming a self-serve free tier exists.

## A decision path that doesn't waste money

Work down this list and you'll usually land in one place:

1. **Does one login need to persist for weeks?** That's a static ISP address. Buy from a provider that sells ISP proxies — 9Proxy doesn't.
2. **Does the job need thousands of distinct IPs from specific locations?** Residential, and per-GB billing if each request moves little data.
3. **Is bandwidth heavy and request count low?** Residential per-IP with unlimited traffic. This is 9Proxy's sweet spot.
4. **Do you have both patterns in one pipeline?** Buy a bundle instead of two products, then split traffic by task.
5. **Unsure?** Start with the smallest GB package you can test on. It carries no desktop install and tells you more about real-world success rates than any review will.

## Fair warning on the marketing numbers

Proxy marketing runs on unverifiable claims. 9Proxy advertises 20M+ residential IPs, 90+ countries, and 99.95% uptime; those figures come from the company and from third-party directories repeating the company's own numbers, not from independent audits. Geekflare's 2026 review of the platform is more useful than any uptime badge, because it tested live targets and noted that 9Proxy's dual billing model lets you match pricing to your actual workflow rather than paying for a structure that doesn't fit.

The same skepticism applies to ISP proxies across the industry. Claims like "ISP proxies pass Cloudflare 94% of the time versus 67% for datacenter" appear in vendor glossaries tied to 2023 benchmarks. Directionally they reflect real ASN behavior. As a precise prediction for your target, treat them as advertising.

## The short version

ISP proxies and residential proxies solve different problems: one gives you a stable, ISP-attributed address that keeps sessions alive; the other gives you a large, rotating pool of genuine home IPs that survives strict anti-bot systems. Most articles stop there, which is why people buy the wrong thing.

The second half of the decision is billing. Per-IP with unlimited bandwidth beats per-GB on heavy, low-request-count work; per-GB wins on high-rotation, low-payload work. 9Proxy only plays in the residential half — no ISP product — but it plays both billing models, at prices that stayed flat on the GB side through its 2026 adjustment.

👉 [Start with 9Proxy and pick the model that matches your workload](https://bit.ly/9-Proxy)
