# BandwagonHost VPS for beginners: How to Pick the Right Plan, Set It Up in Minutes, and Avoid Paying for Power You Won't Use

Getting your first VPS is a slightly weird experience. You pay a few dollars, get an IP address and a root password, and then a control panel asks you what to do next. If nobody explains the basics, that moment is where most beginners stall — or worse, overpay for a plan they'll never use half of.

BandwagonHost (often shortened to BWH or "搬瓦工" in Chinese communities) is one of the longest-running budget VPS providers around, and it shows up constantly in beginner recommendations. But it's also a service with some quirks you should know before clicking the buy button: it's strictly self-managed, billing cycles are unusual (annual for the cheapest plan, quarterly for some others), and the plan catalog stretches from a $49.99/year starter box to dedicated Hong Kong servers costing well over $1,000 a month.

This guide walks through the parts that actually matter when you're starting out: what you get for your money, which plan fits which situation, how the first-time setup works, and the limits you should accept going in.

## What BandwagonHost actually is

BandwagonHost is a VPS brand run by IT7 Networks, an American hosting company that also operates the IT7 datacenters in Los Angeles and New York. It's been around since the early 2010s, which in the VPS world counts as "ancient and still alive" — a reasonable sign that it's not going to vanish with your data next quarter.

The service is built entirely on KVM virtualization and managed through a custom control panel called **KiwiVM**. Every plan includes:

- Full root access
- One dedicated IPv4 address and a routed /64 IPv6 subnet
- Free snapshots (two sticky snapshots kept permanently, the rest stored for 30 days)
- Free automatic backups on current plans
- Free migration between eligible datacenters, without data loss
- OS templates for CentOS, Debian, Ubuntu, Rocky Linux, and AlmaLinux, plus manual ISO installs if you want something else
- A 99.95% uptime guarantee on standard plans, rising to 99.99% with an SLA on the E-Commerce line

One word in there deserves emphasis: **self-managed**. BandwagonHost keeps prices low precisely because nobody will configure your server for you. If something breaks at the OS level, you fix it. There's no cPanel license, no one-click WordPress installer, no support chat that will tune your nginx config. If that sounds exhausting rather than exciting, a managed host or a shared hosting plan is probably the better fit — and that's fine.

## The full plan lineup, as currently listed

BandwagonHost's catalog splits into a few distinct lines. The table below reflects what's currently shown on the official order pages, with prices in USD.

### Standard KVM promo plans (multiple locations, free migration)

| Plan | CPU | RAM | SSD (RAID-10) | Transfer | Port | Price | Billing | Buy |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 20G KVM | 2 cores | 1 GB | 20 GB | 1 TB/mo | 1 Gbps | $49.99 | Annually | [ Get the 20G KVM starter plan](https://bit.ly/BandwagonHost) |
| 40G KVM | 3 cores | 2 GB | 40 GB | 2 TB/mo | 1 Gbps | $52.99 (semi-annual) / $99.99 (annual) | Semi-annual or annual | [ Check the 40G KVM plan](https://bit.ly/BandwagonHost) |
| 80G KVM | 4 cores | 4 GB | 80 GB | 3 TB/mo | 1 Gbps | from $19.99/mo, $199.99/yr | Monthly to annual | [ See the 80G KVM pricing](https://bit.ly/BandwagonHost) |
| 160G KVM | 5 cores | 8 GB | 160 GB | 4 TB/mo | 1 Gbps | from $39.99/mo, $399.99/yr | Monthly to annual | [ View the 160G KVM plan](https://bit.ly/BandwagonHost) |
| 320G KVM | 6 cores | 16 GB | 320 GB | 5 TB/mo | 1 Gbps | from $79.99/mo, $799.99/yr | Monthly to annual | [ Compare the 320G KVM plan](https://bit.ly/BandwagonHost) |
| 480G KVM | 7 cores | 24 GB | 480 GB | 6 TB/mo | 1 Gbps | from $119.99/mo, $1,199.99/yr | Monthly to annual | [ Get the 480G KVM plan](https://bit.ly/BandwagonHost) |

These plans can be deployed in several US and EU locations (Los Angeles, New York, New Jersey, Amsterdam, and others depending on stock), and you can migrate between them from the KiwiVM panel at any time, free, without losing data.

### CN2 GIA premium-line plans (fixed location, China-optimized routes)

These use premium network routes (China Telecom CN2 GIA/CTGNet, China Unicom premium AS10099, China Mobile CMIN2), which is the entire reason they cost more. Each size ladder runs from a 2-core / 2 GB / 40 GB entry tier up to a 12-core / 64 GB / 1,280 GB top tier:

| Line | Location | Entry tier (2C/2GB/40GB, 500 GB/mo) | Top tier (12C/64GB, 8 TB/mo) | Buy |
| --- | --- | --- | --- | --- |
| Osaka CN2 GIA | Osaka (Equinix) | $49.99/mo or $499.99/yr | $1,059.99/mo or $10,559.99/yr | [ Check Osaka CN2 GIA plans](https://bit.ly/BandwagonHost) |
| Singapore CN2 GIA | Singapore (Equinix SG1) | $49.99/mo or $499.99/yr | $1,059.99/mo or $10,559.99/yr | [ Check Singapore CN2 GIA plans](https://bit.ly/BandwagonHost) |
| Tokyo CN2 GIA | Tokyo (Equinix TY8) | $89.99/mo or $899.99/yr | $1,889.99/mo or $18,989.99/yr | [ Check Tokyo CN2 GIA plans](https://bit.ly/BandwagonHost) |
| Hong Kong CN2 GIA | Hong Kong (Equinix HK2) | $89.99/mo or $899.99/yr | $1,889.99/mo or $18,989.99/yr | [ Check Hong Kong CN2 GIA plans](https://bit.ly/BandwagonHost) |

The Osaka and Singapore lines run on 1.5–2.5 Gbps ports depending on tier; Tokyo and Hong Kong run 1–1.2 Gbps. All of them include free automatic backups and snapshots.

### E-Commerce SLA line (Los Angeles, 99.99% SLA)

A newer line built on AMD EPYC hardware with NVMe storage, aimed at production sites that can't afford downtime. Verified tiers include:

| Plan | CPU | RAM | Transfer | Port | Price | Buy |
| --- | --- | --- | --- | --- | --- | --- |
| 20G SLA | 2× AMD | 1 GB ECC | 1 TB/mo | 2.5 Gbps | $65.89/quarter, $239.99/yr | [ See the 20G SLA plan](https://bit.ly/BandwagonHost) |
| 40G SLA | 3× AMD | 2 GB ECC | 2 TB/mo | 2.5 Gbps | $116.99/quarter, $399.99/yr | [ See the 40G SLA plan](https://bit.ly/BandwagonHost) |
| 80G SLA | 4× AMD | 4 GB ECC | 3 TB/mo | 2.5 Gbps | $69.99/mo, $699.99/yr | [ See the 80G SLA plan](https://bit.ly/BandwagonHost) |
| 160G SLA | 6× AMD | 8 GB ECC | 5 TB/mo | 5 Gbps | $109.99/mo, $1,099.99/yr | [ See the 160G SLA plan](https://bit.ly/BandwagonHost) |

The ladder continues to larger configurations on the order page. These plans come with a contractual 99.99% SLA, dual redundant network paths, and Tier III facility certifications (SOC 1/2 Type 2, ISO 27001, PCI DSS) — the kind of fine print that only matters when a website is actually making money.

> If a plan in the table above doesn't match what you see at checkout, it usually means one of two things: a limited-edition SKU sold out, or prices were updated. BandwagonHost rotates limited stock plans fairly often.

## Which plan should a beginner actually buy?

Here's the honest version, based on what the specs and prices support.

**Most people starting out: the 20G KVM at $49.99/year.** Two CPU cores, 1 GB RAM, 20 GB SSD, 1 TB of monthly transfer. That's enough for a personal blog with moderate traffic, a small API project, a Discord bot, a monitoring stack, or a Linux playground you can break and rebuild without guilt. At roughly $4.17 a month, the cost of being wrong about your requirements is basically zero. The main constraint is RAM: 1 GB fills up fast if you stack services on it, and you can't upgrade in place — you'd buy a bigger plan later and move your data.

**If 1 GB of RAM sounds immediately limiting: the 40G KVM.** Doubling to 2 GB RAM and 40 GB storage for $99.99/year is a reasonable jump once you know you'll run a database plus an app, or a couple of small sites. Note that this plan bills semi-annually or annually rather than yearly-only.

**If you want monthly flexibility: the 80G KVM at $19.99/month.** Four cores, 4 GB RAM, 3 TB transfer. Monthly billing makes sense when you're testing something for a few weeks and don't want to commit a year upfront. The annual rate ($199.99) works out to about $16.67 a month if it becomes a long-term box.

**Skip the premium lines unless you have a specific reason.** The CN2 GIA and SLA plans exist for people whose traffic actually benefits from them — mainly sites serving visitors in China (where CN2 GIA routing measurably cuts latency and packet loss) and revenue-producing sites that want the 99.99% SLA. Paying $89.99/month for a Hong Kong box to host a hobby blog is spending $1,080 a year to solve a problem you don't have.

## Promo codes: what they're worth

BandwagonHost doesn't do flashy 70%-off sales, but it does maintain recurring promo codes — meaning the discount applies not just to the first invoice but to renewals. Codes rotate every few months, and older ones get retired, so check a recent source before checkout. Two codes that have been circulating through 2026 per coupon trackers:

- **BWHCGLUKKB** — 6.78% recurring discount
- **BWH3HYATVBJW** — 6.58% recurring discount

On a $49.99/year plan, 6.78% saves you about $3.39 a year. That's not life-changing, but it's free money for typing six characters into the promo field — and on a $899.99/year plan it's over $60. Also worth knowing: the cheapest plans are already positioned as promo SKUs (they're literally labeled "PROMO" in the cart), so no code is required just to get the listed price.

If you want to browse current prices and stock before deciding, the sensible move is to [👉 open the plan catalog and check what's in stock](https://bit.ly/BandwagonHost) — limited SKUs do sell out, and restock timing is unpredictable.

## First-time setup: what actually happens after you pay

The buying and setup flow is straightforward. No sales calls, no "account manager," no waiting a business day.

1. **Choose plan and billing cycle, then checkout.** Payment options include major cards, PayPal, and — importantly for many buyers — Alipay and crypto. Account creation is instant.
2. **Wait a few minutes for provisioning.** New VPSes come online automatically. You'll get an email with your KiwiVM login.
3. **Pick a location and OS.** If you didn't choose during checkout, the KiwiVM panel lets you select the datacenter and install an OS template — Ubuntu and Debian are the usual beginner picks, since almost every tutorial on the internet assumes one of them.
4. **Log in as root.** You'll get an IP, and root credentials via the panel. First thing to do: update packages (`apt update && apt upgrade` on Debian/Ubuntu), set up SSH keys, and disable password root login. This takes ten minutes and removes the most common way new servers get compromised.
5. **Explore the panel.** KiwiVM covers start/stop, OS reload, an emergency console (a lifesaver when you firewall yourself out — and you will, once), rDNS management, usage graphs, and an API if you want to script things.

That emergency console deserves a mention. On a lot of budget hosts, locking yourself out of SSH means filing a support ticket and waiting. On BandwagonHost you open the console in the browser and fix it yourself in two minutes. For a self-managed service, good tooling matters more than hand-holding support, and the tooling is good.

## Datacenter locations and switching later

One of the quietly best features for beginners: **you can migrate your VPS to another eligible datacenter at any time, free, without losing data.** Bought on the US East Coast and later decide your audience is mostly in Europe? Open the panel, trigger the migration, done. No ticket, no fee, no reinstall.

Two caveats worth knowing upfront:

- Migration moves your data but **your IP address changes**. If you've pointed a domain at your server, you'll need to update DNS records.
- Free migration applies to the multi-location standard plans. The premium fixed-location lines (Hong Kong, Tokyo, and so on) are tied to their location — that's part of what you're paying for, since those routes can't be replicated everywhere.

For a beginner, the practical advice is: start in Los Angeles unless you have a specific reason not to. It's BandwagonHost's home turf, capacity is usually better, and it's a solid middle-ground location for visitors across the Pacific Rim and the Americas.

## Backups, snapshots, and the refund safety net

Current plans include **free automatic backups** and free snapshots — two sticky snapshots kept for good, with additional ones retained for 30 days. Snapshots are point-in-time images you can restore or clone to another VM, which makes them perfect for the "I'm about to try something possibly dumb" moment. Take a snapshot before every experiment; it costs nothing.

The other safety net is the **30-day money-back guarantee**, confirmed in the official knowledge base. Request a refund through the refund page in your client area and the billing department processes it, subject to the terms of service. Combined with monthly billing on the bigger plans, your realistic worst case for trying the service is a few dollars.

## The honest list of limitations

No VPS review for beginners is complete without the parts that annoy people:

- **Self-managed, full stop.** No managed support, no cPanel bundled. If "SSH into a server" sounds like a foreign language, factor in a real learning curve — or choose managed hosting instead.
- **No hourly billing.** Unlike Vultr or DigitalOcean, you can't spin up a server for three hours and pay cents. Billing cycles are monthly at minimum. For throwaway short-term testing, those competitors fit better.
- **No one-click app marketplace.** You install software yourself. Community scripts (like various one-click LAMP/LEMP installers) partially fill the gap.
- **1 GB of RAM is a real ceiling.** The cheapest plan is great until you add MySQL plus a Java app to it. Plan to start small but know when to move up.
- **Stock fluctuates.** The most attractive limited plans sell out, sometimes for weeks.

Against that, the trade is clear: lower prices than most of the mainstream cloud crowd, a mature panel, free backups and snapshots, free location migration, and a business that's survived a very long time in a market where most budget hosts don't.

## Quick answers to the questions beginners actually ask

**Is BandwagonHost good for hosting a website?** Yes, for small to medium sites, as long as you're comfortable running the server software yourself. The SLA line exists specifically for sites where uptime is money.

**Can I upgrade my plan later?** Not in place — you order a bigger plan and migrate your data. Snapshots make this less painful than it sounds, and the free datacenter migration handles location moves automatically.

**Does it accept Alipay?** Yes, along with PayPal, cards, and crypto. This is one reason it's especially popular with buyers in China, alongside the CN2 GIA network lines.

**What OS should I install first?** Ubuntu LTS or Debian. Every tutorial assumes one of them, and package documentation is everywhere.

**Is the cheapest plan enough for learning Linux?** More than enough. Two cores and 1 GB RAM runs a full LEMP stack, Docker containers for practice, and a VPN without breaking a sweat.

## The bottom line

For a first VPS, BandwagonHost hits a sweet spot that's genuinely hard to find elsewhere: real KVM virtualization, a capable in-house panel, free backups and snapshots, free migration between datacenters, and entry pricing that starts at $49.99 per year — about the cost of two coffees a month. The trade-off is that you're the sysadmin, and the premium network lines are expensive if you don't need them.

So the decision tree is short. Start with the [👉 20G KVM plan at $49.99/year](https://bit.ly/BandwagonHost) if you're learning or hosting something small; step up to the [👉 40G KVM or 80G KVM plans](https://bit.ly/BandwagonHost) if you already know you need more RAM; and only look at the [👉 CN2 GIA and SLA premium lines](https://bit.ly/BandwagonHost) if China-facing latency or a contractual 99.99% uptime guarantee is part of your actual requirements. And if the whole thing turns out not to be your thing, the 30-day refund policy means you're out nothing but a little time.
