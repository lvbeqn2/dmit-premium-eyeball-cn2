# DMIT Premium vs Eyeball: Is CN2 GIA Worth Paying For, How Much Extra Traffic Does Eyeball Give, and Which Fits Telecom vs Mobile Users? (Los Angeles Plan Tables)

At the same price, DMIT's Los Angeles Premium and Eyeball lines give you different things. STARTER costs **$29.90/mo** on both, but Premium comes with 3 TB of monthly transfer and a China Telecom CN2 GIA return path that is written into the contract, while Eyeball comes with 5 TB and a China Mobile CMIN2 return path that DMIT describes as a reasonable-effort optimization.

Pick Premium if a meaningful share of your users are on China Telecom and a route shift during Beijing evening peak would cost you money. Pick Eyeball if your audience skews China Mobile, or if you mainly care about transfer per dollar and can live with routing that may be adjusted.

Everything below applies to the Los Angeles location. DMIT also sells Hong Kong and Tokyo lines on the same three-tier structure, but the plan names, quotas, and prices differ, so this comparison stays on LAX where both lines are directly comparable.

> **Quick pick**
> - Mixed carriers, production traffic, no tolerance for routing changes: **LAX.Pro.STARTER**, 2 vCPU / 2 GB / 80 GB, 3 TB, 10 Gbps, $29.90/mo.
> - China Mobile audience or bandwidth-heavy workload: **LAX.EB.STARTER**, same hardware and price, 5 TB, and a 20% recurring code if you pay quarterly or annually.
> - Light personal use on a budget: **LAX.EB.TINY** at $88.88/yr (or $28.88/quarter), which drops to about $23.10 per quarter with the code.
>
> 👉 [Compare the current LAX Pro and Eyeball lineups](https://www.dmit.io/aff.php?aff=9081)

## Los Angeles Premium and Eyeball plans, side by side

Monthly plans, both lines on the same AMD EPYC 9004/9005 hardware in the same facility. Traffic on both is **bidirectional**, meaning upload and download both count against the quota.

| Plan | vCPU / RAM / SSD | Traffic per month | Port | Price | Order |
| --- | --- | --- | --- | --- | --- |
| LAX.Pro.STARTER | 2 / 2 GB / 80 GB | 3 TB | 10 Gbps | $29.90/mo | [Get Pro STARTER](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.STARTER | 2 / 2 GB / 80 GB | 5 TB | 10 Gbps | $29.90/mo | [Get EB STARTER](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.MINI | 4 / 4 GB / 80 GB | 5 TB | 10 Gbps | $58.88/mo | [Get Pro MINI](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.MINI | 4 / 4 GB / 80 GB | 10 TB | 10 Gbps | $58.88/mo | [Get EB MINI](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.MICRO | 4 / 4 GB / 160 GB | 7 TB | 10 Gbps | $74.99/mo | [Get Pro MICRO](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.MICRO | 4 / 4 GB / 160 GB | 14 TB | 10 Gbps | $74.99/mo | [Get EB MICRO](https://www.dmit.io/aff.php?aff=9081) |

Entry-level and annual plans. Some of these are limited-stock releases that sell out without a restock schedule.

| Plan | vCPU / RAM / SSD | Traffic per month | Port | Price | Order |
| --- | --- | --- | --- | --- | --- |
| LAX.Pro.WEE | 1 / 1 GB / 20 GB | 500 GB | 500 Mbps | $36.90/yr | [Get Pro WEE](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.MALIBU | 1 / 1 GB / 20 GB | 1 TB | 1 Gbps | $49.90/yr | [Get Pro MALIBU](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.TINY | 1 / 2 GB / 20 GB | 1 TB | 1 Gbps | $88.88/yr | [Get Pro TINY](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.PalmSpring | 2 / 2 GB / 40 GB | 2 TB | 2 Gbps | $100/yr | [Get Pro PalmSpring](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.TINY | 1 / 1 GB / 20 GB | 600 GB | 1 Gbps | $88.88/yr or $28.88/qtr | [Get EB TINY](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.Pocket | 1 / 2 GB / 40 GB | 1.2 TB | 2 Gbps | $159.98/yr or $14.90/mo | [Get EB Pocket](https://www.dmit.io/aff.php?aff=9081) |

DMIT repriced and reshuffled these plans more than once, and the annual tiers change spec between restocks. Confirm the CPU, RAM, and traffic line on the checkout page before you pay, since that is the version you are actually buying.

## What the two routes actually do differently

**Premium runs China Telecom's CN2 GIA backbone (AS4809) in both directions.** Traffic from your server into China and return traffic coming back both travel inside that path. Unicom outbound takes a direct AS4837 route and Mobile outbound goes through CMI, but the return leg for all three carriers is forced onto CN2 GIA via BGP. Even a China Mobile user's packets enter China over Telecom's premium backbone. That forced routing is why public benchmarks show roughly **140–180 ms** from a Los Angeles Premium instance to major mainland cities, and why that number stays flat during the 20:00–23:00 Beijing peak when cheaper providers degrade.

The routing is contractual. If you need CN2 GIA and cannot accept a substitution, Premium is the only tier where DMIT commits to it in writing.

**Eyeball sends the return path across China Mobile's CMIN2 (AS58807).** Mobile users connect directly over CMIN2, while Telecom and Unicom users come back over AS9929 or CMIN2 depending on how the scheduling falls. Outbound, Telecom and Unicom still use CN2 and Mobile uses CMIN2. DMIT's own wording for this tier is "Reasonable Effort," which is exactly what it sounds like: the optimization is real, but it is not guaranteed, and Eyeball routing can be adjusted during network attacks or for cost reasons.

Practical read on that difference: for China Mobile visitors, CMIN2 is their own premium international line, so the gap between Eyeball and Premium is at its narrowest. For China Telecom visitors the gap is at its widest, and Eyeball may slow down or take a longer path at peak.

## Same price, different traffic: the per-TB numbers

Eyeball hands you 40% to 100% more transfer at the same monthly price. Converted to cost per TB of billable traffic (upload plus download), the spread looks like this:

| Plan tier | Premium per TB | Eyeball per TB |
| --- | --- | --- |
| STARTER ($29.90/mo) | $9.97 (3 TB) | $5.98 (5 TB) |
| MINI ($58.88/mo) | $11.78 (5 TB) | $5.89 (10 TB) |
| MICRO ($74.99/mo) | $10.71 (7 TB) | $5.36 (14 TB) |

The MINI tier is the clearest illustration. For $58.88 you get 5 TB on Premium or 10 TB on Eyeball, and the CPU, RAM, disk, and port speed are identical. If your workload is mostly serving files, images, or video segments to mobile users, the doubled quota is worth more than the routing guarantee.

If you are running a paid API where a latency spike shows up in someone's invoice, the opposite is true and the per-TB math is irrelevant.

## The 20% recurring code and what it changes

DMIT publishes one official discount code for the Eyeball line:

`LAX-EB-LAUNCH-NON-MONTHLY-RECURRING-20OFF`

The conditions are specific, and people miss them:

- It applies to **LAX.EB.TINY and above**, so the smallest Eyeball plan qualifies.
- It requires **quarterly billing or longer**. Monthly orders do not get it.
- It is a **recurring** discount, so renewals stay at the discounted rate rather than jumping back to list price.
- It **does not apply automatically**. You type it into the promo code field at checkout and validate it before paying.

On $28.88 per quarter for EB.TINY, the code brings the bill to about **$23.10 per quarter**, or roughly $7.70/month for a 600 GB CMIN2-optimized box in Los Angeles. That is the single largest lever on price in this comparison, and it applies only to Eyeball.

DMIT also runs seasonal promotions a few times a year, usually tied to holidays, and past events have included recurring discounts plus account credit on LAX Pro and EB annual plans. Those specific codes have expired, so do not plan a purchase around them. Check the promotions page before you pay full price.

👉 [Check Eyeball plans and enter the recurring code at checkout](https://www.dmit.io/aff.php?aff=9081)

## Who should skip both

If your visitors and customers are in North America or Europe with no China component, both tiers charge you for routing optimization you will never use. Vultr, Hetzner, and DigitalOcean cover that case for less, and nothing about DMIT's hardware justifies the premium for pure Western traffic.

If you need raw transfer volume and can tolerate variable latency to China, look at the Tier 1 line instead. T1 rides international carriers such as NTT, Lumen, GTT, and GSL, and it bills **one-directionally**: DMIT counts the larger of inbound or outbound rather than the sum. Download 100 GB and upload 50 GB and T1 records 100 GB, where Pro or EB would record 150 GB. T1 also skips the free IP replacement that Pro and EB include, charges $5 per change, and throttles you after the quota instead of suspending service. For content delivery, mirrors, or a relay node that is not serving mainland users directly, that trade is usually correct.

One trap worth naming: a Hong Kong T1 plan is not automatically faster to the mainland than a Los Angeles Premium plan. Public ping tests of HKG T1 have shown China Telecom averaging far worse than LAX Pro because Telecom traffic detours through Japan, while China Mobile does fine. Geography is not routing.

## Before you pay: refunds, IP swaps, and the overuse throttle

**Refunds.** Three days from purchase with under 30 GB consumed gets a full refund minus the payment gateway fee. Within 30 days you can request a partial refund based on remaining value. Renewal orders are excluded, and a third refund request on the same series is refused. If you are unsure how a line behaves from your location, the three-day window is the reason to test immediately rather than a week later.

**IP replacement.** The frequently repeated "free IP change every 15 days" is incomplete. Per DMIT's documentation, a free replacement on Pro or EB requires all of the following: the instance is at least 7 days old, at least 15 days have passed since the last change, **ICMP and all TCP ports are blocked**, and the service has at least 7 days of remaining validity. If only some ports are blocked, or the instance is younger than 7 days, the change is billed. You can also pay $5 for a change at any time with a 7-day gap between requests. T1 works differently: paid changes only, $5 each, 24-hour minimum age, 3-day gap. Only LAX Pro supports adding extra IP addresses.

**Overuse.** Neither tier cuts you off. You get throttled to a low speed and keep running without overage charges, and DMIT extended this throttled mode to all LAX Pro and EB plans in early 2026. Entry plans throttle hardest, so treat the quota as a real ceiling for anything user-facing.

**Setup.** These are unmanaged servers with password login disabled by default. You need an SSH key configured before your first connection, and the knowledge base covers PuTTY, XShell, and Termius if you are on Windows or mobile.

👉 [Start an order and confirm current plan specs](https://www.dmit.io/aff.php?aff=9081)

## Which one to order

Your carrier mix decides this faster than any benchmark.

- **Mostly China Telecom, revenue on the line:** LAX.Pro.STARTER at $29.90/mo for the contracted CN2 GIA return path, or Pro.TINY at $88.88/yr if 1 TB is enough.
- **Mostly China Mobile:** LAX.EB.TINY with the recurring code, or EB.STARTER if you need 5 TB and a 10 Gbps port.
- **Mixed carriers, heavy traffic, tight budget:** EB.MINI at $58.88/mo for 10 TB is the best transfer-per-dollar plan in the lineup, provided you accept that Eyeball routing is best-effort.
- **No mainland audience:** neither. Tier 1 or a non-China provider.
- **Unsure about latency from your city:** buy the smallest qualifying plan, run your own tests inside the three-day window, and use the refund if the numbers disappoint.

Two things to verify on the checkout page before you commit: the exact traffic and RAM figure attached to the annual plan you picked, since limited-stock releases get revised between batches, and whether your discount code validated, because the Eyeball code will not apply itself.

👉 [Open DMIT's plan list and apply the Eyeball code](https://www.dmit.io/aff.php?aff=9081)
