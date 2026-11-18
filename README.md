# Bangkok VPS: Cloud or Dedicated CPU, What $7.71/Month Really Buys, and How to Pick a Plan (Full Price Tables + Thai IP Notes)

LightNode's Thailand Cloud VPS starts at **$7.71/month** for 1 vCPU, 2GB DDR4, 50GB NVMe and 1TB of bandwidth in a Bangkok data center, with a dedicated Thai IP included. If a workload holds a CPU core busy for hours at a time (a trading bot, a database, a busy API endpoint), the dedicated-CPU Bangkok VPS (VDS) line starts at **$21.2/month** for the same nominal 1 vCPU / 2GB. The rest of this page is about which of those two lines you actually need, what stays the same across every plan, and where the spec sheet stops answering questions.

## Quick pick: three plans cover most buyers

> - **Need a Bangkok IP and short hops to Thai users?** Thailand Cloud VPS **Start, $7.71/mo** (1 vCPU, 2GB, 50GB NVMe, 1TB).
> - **Running MT4/MT5 bots, a database, or a 24/7 API that keeps a core loaded?** Bangkok VDS **Start, $21.2/mo** with a dedicated core.
> - **Hosting several sites that need 4GB RAM?** Cloud VPS **Agency, $14.7/mo**; the VDS equivalent is $40.7/mo for the same 2 vCPU / 4GB.

👉 [Start with the Cloud VPS or VDS plan that matches your workload](https://account.lightlayer.net/?affid=74)

## The two product lines look identical on paper

Both lines run KVM on NVMe SSD in Bangkok, both include a static Thai IP, both bill hourly by default, and both use the same four plan names: Start, Agency, Premium, Enterprise. That naming is where most people get confused, because the specs and prices behind those names are different. Here is each line separately.

**Thailand Cloud VPS** (shared vCPU, marketed as Thailand VPS):

| Plan | vCPU / RAM | NVMe | Bandwidth | Price (monthly) | Order |
| --- | --- | --- | --- | --- | --- |
| Start | 1 vCPU / 2GB DDR4 | 50GB | 1TB | $7.71 | [Deploy Cloud VPS Start](https://account.lightlayer.net/?affid=74) |
| Agency | 2 vCPU / 4GB DDR4 | 50GB | 2TB | $14.7 | [Deploy Cloud VPS Agency](https://account.lightlayer.net/?affid=74) |
| Premium | 4 vCPU / 8GB DDR4 | 50GB | 3TB | $27.7 | [Deploy Cloud VPS Premium](https://account.lightlayer.net/?affid=74) |
| Enterprise | 8 vCPU / 16GB DDR4 | 50GB | 4TB | $52.7 | [Deploy Cloud VPS Enterprise](https://account.lightlayer.net/?affid=74) |

**Bangkok VPS (VDS)** (dedicated CPU cores):

| Plan | vCPU / RAM | NVMe | Bandwidth | Price (monthly) | Order |
| --- | --- | --- | --- | --- | --- |
| Start | 1 vCPU / 2GB DDR4 | 50GB | 1TB | $21.2 | [Deploy VDS Start](https://account.lightlayer.net/?affid=74) |
| Agency | 2 vCPU / 4GB DDR4 | 50GB | 1TB | $40.7 | [Deploy VDS Agency](https://account.lightlayer.net/?affid=74) |
| Premium | 4 vCPU / 8GB DDR4 | 50GB | 2TB | $80.7 | [Deploy VDS Premium](https://account.lightlayer.net/?affid=74) |
| Enterprise | 8 vCPU / 16GB DDR4 | 50GB | 2TB | $158.7 | [Deploy VDS Enterprise](https://account.lightlayer.net/?affid=74) |

Prices are the monthly figures shown on the product pages. Billing is hourly by default, so the monthly number is a reference point rather than a fixed invoice, and the pages do not publish an hourly rate or a monthly cap.

## What the extra $13.49/month actually pays for

The VDS page describes its cores as dedicated CPU cores and exclusive vCPUs. The Cloud VPS page only says vCPU, with no exclusivity claim. That is the entire technical difference between the two tables above, and it gets more expensive as you go up the stack:

| Plan | Cloud VPS | VDS | Difference | Multiple |
| --- | --- | --- | --- | --- |
| Start | $7.71 | $21.2 | +$13.49 | 2.75× |
| Agency | $14.7 | $40.7 | +$26.0 | 2.77× |
| Premium | $27.7 | $80.7 | +$53.0 | 2.91× |
| Enterprise | $52.7 | $158.7 | +$106.0 | 3.01× |

For a WordPress site, a proxy gateway, a staging environment, or a bot that wakes up every few minutes, shared cores are fine and the Cloud line is the obvious buy. Paying 2.75× for a dedicated core to serve PHP pages that mostly wait on MySQL is money spent on a guarantee you will not notice. The VDS line earns its price when CPU time is the bottleneck and stays that way: continuous backtesting, a trading terminal holding a position all day, a database under steady query load, media encoding, or an API where a noisy neighbour on the host would show up as latency spikes in your own response times.

## Every plan gets 50GB of NVMe, including the $158.7 one

Storage does not scale with the rest of the plan. All eight configurations above ship with 50GB of NVMe, from the $7.71 Cloud Start to the $158.7 VDS Enterprise. If your reason for upgrading is disk space, upgrading will not solve it; you would need to ask about add-on volumes, which the pages do not describe.

Bandwidth scales more sensibly, but on different curves. On the Cloud line it runs 1TB, 2TB, 3TB, 4TB. On the VDS line it runs 1TB, 1TB, 2TB, 2TB, so the VDS Agency plan at $40.7 has the same 1TB allowance as the $7.71 Cloud Start. If you are serving large files or video, check that number before you pay for CPU you do not need.

Neither page states what happens when you exceed the monthly transfer allowance. That is worth asking before you migrate a media-heavy site onto a 1TB plan.

## Hourly billing, and the $15 first-recharge credit

Billing starts hourly, which suits short tests, campaign bursts, or a two-week migration window. LightNode's documentation says you can keep the same instance and switch it to monthly billing later without downtime, and that there are no long-term contracts. Whether monthly works out cheaper per hour is not stated anywhere on the product pages, so treat the switch as a convenience, not a discount.

The product pages also show a promotional line about getting up to $15 when you recharge for the first time. The conditions behind that number are not published: it is unclear whether it applies only to new accounts, whether it is a credit or a rebate, or whether it stacks with anything else. Confirm what it is worth on the checkout page before you size your first top-up around it.

👉 [Check the current Cloud VPS pricing and first-recharge offer](https://account.lightlayer.net/?affid=74)

## The Thai IP is the part you can actually use

Every instance includes its own static Thai IP. For anyone doing local SEO, testing Thai payment gateways, running ad accounts that care about login geography, or checking how a checkout flow behaves for a Bangkok user, this is the feature that matters more than CPU count. It is also the reason a Singapore VPS at half the price will not do the same job.

You can change the IP from the Network page in the console, and the first two changes are free. That is a practical detail if you burn an IP on a service that gets flagged, or if you want to test how a site behaves from a different Thai address block. After the first two, the pricing for further changes is not stated on these pages.

Latency is described as optimised for Thailand, Vietnam, Malaysia and the wider Southeast Asia region. No measured latency figures are published, and I have not seen independent Bangkok ping tests for these nodes, so treat the routing claim as a claim until you test it from your own users' networks.

## Windows, Linux, and how long deployment takes

Both lines support Windows Server 2022, 2019 and 2016, plus Ubuntu, Debian, AlmaLinux and CentOS Stream on the Linux side, with full root access and reinstall from the console at any time. The VDS page quotes roughly 1–2 minutes to a running server; the Cloud VPS page says servers come up within minutes.

Two operational notes worth knowing before you buy. Disk is 50GB on every plan, which is tight for a Windows Server install plus applications, so budget the space before you pick Windows for a convenience reason. And the 99.95% availability figure appears only on the VDS page; the Cloud VPS page carries no SLA number at all. If uptime commitments matter to your contract with a client, ask which line the figure applies to.

## Where the spec sheet goes quiet

A few things a Bangkok VPS buyer usually wants to know are simply not on these pages:

- **Compliance and data residency.** The pages say the data center is in Bangkok and the IP is Thai. There is no PDPA statement, no ISO certification listed, and no data-residency guarantee. If your business is bound by Thailand's PDPA, get written confirmation from support before you put personal data on it.
- **Refunds, trials, backups, DDoS protection, CPU model, NVMe RAID level or IOPS, and data center tier.** None of these are published. Some providers list them prominently, which makes the silence here noticeable rather than damning; just ask.
- **Customer evidence.** The only testimonial on the product pages is a single short quote from a customer named John Thompson, presented by LightNode itself. That is not an independent review, and there is no aggregate rating to look at.

The company behind the platform says LightNode launched in 2021 and now serves more than 80,000 customers across 130+ countries, with over 1,100,000 cloud servers launched, backed by a parent company with two decades of IDC experience. That history applies to the parent, not to the LightNode brand, which is four years old.

## How the price compares with a local Thai provider

LightNode's own pages put Vultr at $10 and DigitalOcean at $12 for a 1 vCPU / 2GB base VPS (checked 2026-10-28), which makes the $7.71 Cloud Start look cheap. Those reference prices are not stated to be Bangkok plans, so the comparison tells you about base pricing generally, not about the same city, and you should not read it as "cheaper in the same location".

For a same-city comparison, Triplify sells Bangkok KVM VPS with a very different feature set. Its site lists a Tier III data center, NVMe SSD RAID, 1Gbps with unlimited transfer, a 99.9% SLA, ISO/IEC 27001 and 27701, PCI DSS and PDPA compliance claims, 24/7 Thai and English support, and free migration, with deployment in about 60 seconds. Prices are in Thai baht:

| Triplify plan | vCPU / RAM | NVMe | Price (monthly, THB) |
| --- | --- | --- | --- |
| NANO | 1 / 1GB | 32GB | ฿149 |
| MINI | 2 / 2GB | 50GB | ฿249 |
| STARTER | 2 / 4GB | 60GB | ฿349 |
| BASIC | 4 / 8GB | 100GB | ฿599 |
| BUSINESS | 8 / 16GB | 150GB | ฿1,099 |
| ENTERPRISE | 12 / 32GB | 250GB | ฿2,199 |

Windows Server costs extra there as a licence fee. Its site also claims typical in-Thailand latency under 10ms through direct TH-IX peering, which is the provider's own figure. I have not converted the baht prices, since no verified exchange rate is part of this research, so do that conversion yourself against today's rate before comparing.

The honest split: if PDPA compliance, a published SLA, unlimited bandwidth and a larger disk at each tier are requirements, a provider that states them in writing is the safer pick. If you want a cheap Bangkok IP on hourly billing with Windows images available and no contract, LightNode's Cloud Start is hard to beat on entry price.

## Questions buyers actually ask

**Can I get a refund or a free trial?** Neither is described on the product pages. Ask support before your first payment.

**Can I upgrade later?** Yes, from the dashboard. The VDS page notes the process causes minimal downtime depending on workload; in-place CPU/RAM/disk changes without rebuilding are not described in detail.

**Which payment methods work?** Credit cards, PayPal, Alipay, Google Pay and regional methods.

**Is there a contract?** No. Hourly by default, switchable to monthly on the same instance.

**Is 50GB enough?** For a Linux web stack, usually. For Windows plus applications and logs, plan carefully, because no larger disk option is listed.

## Picking your plan

Match the plan to what the server spends its time doing. A site, a proxy or VPN gateway, an SEO landing page, a dev environment, or a bot that runs intermittently: **Cloud VPS Start at $7.71**. Several sites or a small app with a 4GB working set: **Cloud VPS Agency at $14.7**. Sustained CPU load where a noisy neighbour would hurt, such as a trading bot, a database or a busy API: **VDS Start at $21.2**, and only climb to VDS Agency or Premium once you can see the cores maxed out.

Before you pay, confirm three things that the pages do not answer: what happens when you pass your bandwidth allowance, whether any refund window exists, and whether the compliance documentation your business needs is available. Then size the first recharge knowing the $15 credit has unpublished conditions.

👉 [Open a LightNode account and pick the Bangkok plan you settled on](https://account.lightlayer.net/?affid=74)
