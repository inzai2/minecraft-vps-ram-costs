# Best VPS for Minecraft: How Much RAM for 2, 10 or 20 Players, What Year Two Costs, and When a Panel Server Wins

A vanilla server for four friends runs comfortably on 2GB. A Create or All the Mods pack needs 8GB before the stutter stops. Most "best VPS for Minecraft" lists stop at the spec sheet, and skip the two numbers that decide whether you're still happy in a year: the clock speed of the core your world ticks on, and the renewal price after the promo term ends.

Renting a VPS gets you root access, no queue at login, no sleep timer, and full control over the Java version and the server jar. It also makes you the sysadmin. What follows is the RAM math that holds up, verified prices from five hosts, the four-year cost of a discounted plan, the manual setup you're signing up for, and the point where a managed game panel is genuinely the better buy.

> Most small servers need 4GB: vanilla or Paper, up to roughly 20 players. Modpacks start at 8GB. Sort plans by CPU clock speed before you count vCPUs. 👉 [Check Evoxt's current VPS plans and pricing](https://bit.ly/EvoXt) to line its RAM tiers up against the numbers below.

## One fast core beats four slow ones

The server tick, mob AI, redstone updates and chunk generation all run on the main thread. A 4-vCPU plan on a 2.4GHz core produces worse tick times than a 2-vCPU plan on a 4.2GHz Ryzen, and the 2-vCPU box is usually cheaper. Cloudzy says this outright in its Minecraft FAQ: "Minecraft is single-thread heavy, so single-thread performance matters more than vCPU count," which is also why it sells a high-frequency 4.2GHz+ Ryzen line alongside its EPYC tiers. Compare plans by clock speed first.

The second decision is which server software you're running:

- **Paper or Purpur** for survival with plugins. Both are Spigot derivatives with performance patches; LuckPerms, EssentialsX and WorldEdit drop straight into the plugins folder.
- **Fabric** for light mod sets and quick version updates.
- **Forge or NeoForge** for heavy packs like ATM or FTB.
- **Bedrock Dedicated Server** if your group plays on consoles or phones. It listens on 19132/UDP rather than Java's 25565, and it's a separate server, not a mode.

Cross-platform play needs GeyserMC sitting in front of a Java server, which costs a few hundred MB of RAM on top of everything else.

Location is the third decision, and it's the one money can't fix later. Latency is distance. Cloudzy reports median P50 latency under 10ms across its North American and European regions, and that only happens when the box sits near the players. Choose the region first, then the plan. Moving a server afterwards means copying world files and handing your players a new IP.

## How much RAM by player count

Two published sets of numbers disagree, and both are defensible.

Cloudzy's FAQ puts vanilla survival for a few friends at 2GB, modpacks at 4–8GB, and busy Spigot/Paper networks at 8–16GB. Its 4GB tier is labelled for modded Java and Bedrock at 10–20 players. Apex Hosting recommends starting at 6GB for Java or 4GB for Bedrock, which the server calculators it cites map to roughly 20 concurrent players.

The gap comes from assumptions. The 2GB figure assumes vanilla defaults and a short render distance. The 6GB figure budgets for plugins, a longer view distance, and enough headroom that a 20-player evening doesn't spike into garbage collection.

Working version:

| Your server | RAM | What to watch |
| --- | --- | --- |
| 2–5 friends, vanilla or Paper | 2–4GB | the cheapest tier is usually enough |
| 10–20 players, Paper plus plugins | 4–6GB | pre-generate chunks, keep view-distance at 6–8 |
| Modpack (ATM, FTB, Create-heavy), 5–10 players | 8GB | single-core clock speed decides whether it stutters |
| Public server on BungeeCord or Velocity | 8–16GB | one fast core per Paper backend |

If you expect to grow, ask whether the host resizes RAM in place. Rebuilding means re-uploading the world and changing the address your players saved.

## The part that isn't on the spec sheet

A VPS is an empty Linux box. The first boot goes like this: install Java (`apt install openjdk-21-jre-headless`), upload `server.jar`, accept the EULA, launch it inside `screen` or a systemd unit so it survives an SSH disconnect, then open 25565 in `ufw`. Cloudzy's own documentation walks through this and hands you the command: `screen -S mc java -Xmx4G -Xms4G -jar server.jar nogui`.

Budget an hour the first time. Backups, restarts, plugin updates and Java upgrades are yours to script from then on. That is what you trade for root access and a price that doesn't include a control panel you never asked for. If an hour of Linux setup and a cron job for backups sounds fine, 👉 [see Evoxt's current plan list and billing terms](https://bit.ly/EvoXt) and confirm the RAM tier, CPU clock and region before ordering.

## What the second year actually costs

Hostinger's own pricing page shows the pattern clearly. Game Panel 1 is advertised at $6.99/mo, billed as $167.76 for 24 months, and renews at $11.99/mo for the same term. Two years at the promo price plus two at renewal comes to $455.52, or $9.49/mo across four years. That's 1.36× the number on the banner.

The bigger tiers move further. Game Panel 4 goes from $13.99 to $28.99 at renewal, a 107% jump. Game Panel 8 climbs from $27.99 to $49.99. A two-year prepay is a four-year commitment on a world you'll still be running when the price changes.

BisectHosting prices the other direction: 4GB at $12/mo month-to-month, or $115.20 billed annually, which works out to $9.60/mo, with no renewal increase. More expensive in year one, cheaper in year three.

Before paying for a long term, read the renewal line rather than the discount badge.

## "Supports 10 players" for $2 is a marketing number

ScalaCube advertises a $2/mo plan that supports 10 players. Run 10 players through a standard Minecraft server calculator and you land near 4.5GB, which is the $13/mo tier on the same host. BisectHosting labels its 4GB plan as a 6-player server while the same calculators say 10.

Neither number is a lie. They just assume different view distances, plugin loads and mob farms.

Use RAM as the currency instead of the player count in the ad. For vanilla, 200–400MB per player is a working estimate: a 4GB box holds 10–20 people if you keep the render distance modest, and a $2 box holds a test world.

## Panel host or VPS: verified prices side by side

| Route | Verified price | What you get | Trade-off |
| --- | --- | --- | --- |
| Hostinger Game Panel 1 | $6.99/mo on 24-month prepay ($167.76 total), renews $11.99/mo | 1 vCPU, 4GB, 50GB NVMe, 4TB transfer, panel, weekly backups | long prepay, renewal jump |
| Hostinger Game Panel 2 | $9.49/mo on 24-month prepay ($227.76 total), renews $14.99/mo | 2 vCPU, 8GB, 100GB NVMe, 8TB transfer | same terms |
| BisectHosting 4GB | $12/mo monthly, $115.20/yr ($9.60/mo) | daily backups, 21 datacenters, 2,300+ modpacks | less RAM per dollar |
| Apex Hosting entry | $3 first month, renews $4/mo | cheapest entry point, 512MB up to 32GB | very little RAM at the low end |
| ScalaCube | from $2/mo, 64GB tier at $192/mo | multiple servers per plan | advertised player counts are optimistic |
| Cloudzy 4GB | $14.48/mo (2GB at $7.48; the page banner says $7.47) | root, 13 regions, 14-day money-back, live resize | you install everything |
| Evoxt | current prices on its plan page | the do-it-yourself route | setup, ports and backups are on you |

The panel hosts win on convenience. Hostinger includes one-click installers for Paper, Purpur, Forge, Fabric and a long list of modpacks, plus weekly automated backups you can upgrade to daily from $3/mo. BisectHosting backs up daily and doesn't raise the price at renewal, which matters more than the first-month discount if you plan to keep a world for years.

The VPS route wins on control and on cost per gigabyte of RAM once you're past the entry tiers. Cloudzy's 8GB tier is $26.48/mo and its 12GB tier is $34.98/mo with 4 vCPU and 300GB NVMe, and RAM, vCPU and storage resize from the panel without a rebuild.

## Who should skip the VPS entirely

Free hosting is fine for testing and bad for a community. Aternos is permanently free but queues you at peak times, and free tiers generally come with ads, idle shutdowns and neighbours on the same hardware.

If what you want is a server that starts in two clicks, backs itself up nightly, and has a support ticket when it breaks at 2am, a managed panel is the cheaper decision. BisectHosting at $12/mo for 4GB costs less than a $7 VPS plus the evening you'll spend learning why the server won't start after a Java update.

## FAQ

**Is 2GB enough for a Minecraft server?**
For vanilla survival with two to four friends, yes. Add plugins, a longer render distance or any modpack and 4GB is the practical floor.

**Can Java and Bedrock players share one server?**
Yes, with GeyserMC running in front of a Java server. Expect to pay a few hundred MB of RAM for the bridge, and remember that a pure Bedrock server uses 19132/UDP instead of 25565.

**How much RAM does an ATM or FTB pack need?**
6GB is tight, 8GB is comfortable for a small group. The CPU matters as much: a heavy pack on a slow core lags with 16GB free.

**Will my price go up at renewal?**
Depends on the host. Hostinger's Game Panel 1 rises from $6.99 to $11.99/mo at renewal; BisectHosting doesn't raise prices on renewal. Check that line before you commit to a prepay.

**Does location matter more than the CPU?**
For anyone outside the datacenter's region, yes. A faster core shaves milliseconds off tick time; a wrong continent adds a hundred milliseconds to every action.

**Can I add RAM later without rebuilding?**
Some hosts resize RAM, vCPU and storage from the panel with no reinstall, and Cloudzy states this explicitly. Confirm the same for whichever provider you pick before you order, because a rebuild means re-uploading the world.

## Picking one

Match the plan to the server you're actually running:

- **2–5 friends, vanilla or Paper:** the smallest tier, 2–4GB.
- **10–20 players with plugins:** 4–6GB, and check the CPU clock before the core count.
- **ATM, FTB or a Create-heavy pack:** 8GB on the fastest single core you can afford.
- **Public server behind BungeeCord or Velocity:** 8–16GB, one fast core per Paper backend.

Three things to confirm before paying: the renewal price for the term after this one, the refund window, and where the machine sits relative to your players. Get those three right and the RAM tier is the easy part. 👉 [Compare Evoxt's current VPS plans and prices](https://bit.ly/EvoXt) to see which RAM tier fits the player count you're planning for.
