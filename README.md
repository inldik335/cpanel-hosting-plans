# cPanel Hosting: Is It Free, What Costs Extra, and Which Plan Do You Actually Need? (Shared vs VPS, Managed vs Self-Managed, With a Plan Table)

cPanel is the browser control panel that ships with most Linux hosting. You use it to upload files, create databases, set up domain email and install WordPress without touching a terminal. On shared hosting it is almost always bundled into the plan price. On a raw cloud server it usually is not, because cPanel is licensed software: cloud providers typically hand you a 15-day trial and then require you to buy the license separately.

Most people shopping for cPanel hosting are really asking one of three things. Is the panel included or extra? Is shared hosting enough, or do I need a VPS? And how much of that monthly figure is the server versus everything stacked on top of it? This page works through all three, using RackNerd's cPanel plans as the reference point.

> **For most readers the answer is a shared cPanel plan.** RackNerd's entry tier lists at $10.49 a year for 30 GB NVMe storage, two domains and 3 TB of monthly transfer, with CloudLinux, LiteSpeed and offsite daily backups included. 👉 [Check RackNerd's current cPanel hosting offers](https://bit.ly/RacKnerd)

## What you actually do inside cPanel

Six tasks cover most of the first hour after you buy:

- **Install WordPress.** Softaculous Apps Installer handles WordPress plus 400-odd other scripts in a few clicks.
- **Upload files.** File Manager, then Upload.
- **Create a database.** MySQL Databases, then Create Database.
- **Set up email.** Email Accounts creates name@yourdomain. You read it in Webmail (Roundcube or Horde) or connect a mail client over IMAP/POP3/SMTP.
- **Install an SSL certificate.** SSL/TLS Manager. Most hosts issue Let's Encrypt certificates and renew them automatically.
- **Schedule backups.** Backup Wizard, if the host is not already running them for you.

Login is normally `yourdomain.com/cpanel` or `yourdomain.com:2083`. If the page refuses to load, clear the browser cache, try the `:2083` address directly, then open a ticket with your host.

Everything else in the panel is a variation on those six. The Domains area holds addon domains, subdomains and DNS records. The Security area holds directory password protection, IP blocking and two-factor authentication. The Software area manages installers and PHP versions. That is the whole appeal: one login for domains, mail, files, databases and certificates, with no SSH required.

## RackNerd's cPanel plans

RackNerd runs cPanel across both its shared and reseller lines. The shared servers use CloudLinux with KernelCare (kernel patches applied without reboots), LiteSpeed with LSCache, free Let's Encrypt SSL, free migration from another cPanel host, offsite daily backups through JetBackup, a free Clientexec license and premium email routing. Locations span the US, EU and Asia, and you pick one during checkout.

| Plan | Storage / transfer | Sites | Price | Order |
| --- | --- | --- | --- | --- |
| Shared 30 GB | 30 GB NVMe / 3 TB monthly | 2 domains | $10.49/year | [See this plan](https://bit.ly/RacKnerd) |
| Shared 85 GB | 85 GB NVMe / 10 TB monthly | 10 domains | around $25/year on promo | [See this plan](https://bit.ly/RacKnerd) |
| Shared 200 GB | 200 GB NVMe / 30 TB monthly | Unlimited domains | promo pricing shown at checkout | [See this plan](https://bit.ly/RacKnerd) |
| Reseller | 180 GB NVMe, 12 cPanel accounts | 12 client accounts | $94/year | [See reseller plans](https://bit.ly/RacKnerd) |

A few things the table does not show. RackNerd rotates its annual promo batches, so the exact storage and price combination moves between batches; the number on the order page at checkout is the one that applies to you. The annual promo rate is also the rate you renew at, which matters more than the headline. There is a smaller reseller tier as well, aimed at people with fewer clients than the 12-account plan above.

The 30 GB tier is genuinely enough for a blog, a portfolio or a small business site with a contact form. The jump to 85 GB buys you ten domains instead of two, which is the real reason to move up: most sites that fit in 30 GB of storage will never use 3 TB of transfer.

## The three costs that get mixed up

**1. The hosting itself.** Disk, bandwidth, CPU share, support. This is the number on the pricing page.

**2. The cPanel license.** cPanel is commercial software sold per account tier, billed monthly. Shared and reseller hosts absorb that cost into the plan. Self-managed cloud hosts do not: DigitalOcean, for example, lets you deploy a cPanel image from its Marketplace but states plainly that you need to buy a license once the 15-day trial ends. This is why a $4/month VPS with "cPanel hosting" in the description can cost more per year than a $10/year shared plan. The license is the reason budget shared hosting exists at all.

**3. Backups.** Often a second bill, sometimes a third. On DigitalOcean, Droplet backups are weekly snapshots charged at 20% of the Droplet price, and backups for cPanel itself have to be configured separately inside the cPanel account. So you can pay for a server snapshot that will not restore your site, and a cPanel backup that will not restore the server.

When you see a price ending in "/month", ask four questions before you pay:

- Is the cPanel license included for as long as I keep the plan, or just the first year? Some hosts bundle cPanel on shared plans but only cover it for the first year on VPS and dedicated servers.
- Is this the renewal price, or a first-term price?
- Are backups included, how often do they run, how long are they kept, and can I restore without opening a ticket?
- What is the refund or cancellation policy if the server turns out to be wrong for me?

That last one is worth taking seriously. RackNerd handles refunds case by case rather than advertising an automatic 30-day money-back window, so the cheap way to test any host is to start with the smallest plan that fits.

## Managed or self-managed?

This is the decision that changes your life more than the spec sheet.

Self-managed means the provider gives you a server and an image. You handle operating system updates, software patching, security configuration and cPanel itself. DigitalOcean describes its cPanel hosting as self-managed by default, with documentation, a one-click Marketplace install and optional paid support. Nothing stops you from running an unpatched box for two years.

Fully managed means the provider does that work. KnownHost, for example, lists OS updates, cPanel patches, security fixes and performance optimization as part of the service, along with free migrations, DDoS protection and an optional Imunify360 add-on.

The rule I would give a friend: if a failed update at 2 a.m. would have you reading forum threads instead of sleeping, buy managed or buy shared. If you are comfortable on the command line, self-managed gives you more server per dollar. RackNerd's shared and reseller plans sit in the managed-platform camp: the OS, the panel and the security patching are their job, your WordPress and your content are yours.

👉 [See what RackNerd bundles into its cPanel hosting](https://bit.ly/RacKnerd)

## Where cPanel stops

Three limits worth knowing before you buy.

**Windows is out.** cPanel is built for Linux. If you need ASP.NET or MSSQL, you want Plesk on a Windows server instead.

**One account, several sites, shared resources.** Addon domains let you run multiple websites from a single cPanel account, and the practical ceiling is the server's CPU, RAM and bandwidth, not a checkbox in the panel. Ten low-traffic sites on a small plan is fine; three busy WooCommerce stores on the same plan is not.

**Multiple accounts need WHM.** Web Host Manager is the server-level panel that creates and manages individual cPanel accounts. You need it if you are hosting for clients or reselling, which is exactly what RackNerd's reseller plans include, along with the free Clientexec billing license. For a personal site, WHM is irrelevant.

If you are running a multi-tenant server, CloudLinux is the usual recommendation for resource isolation and CageFS, and RackNerd already runs it on shared.

## What other cPanel options cost

The figures below come from provider pages, and the pricing models are not directly comparable. The first five are server prices with the cPanel license billed separately after a 15-day trial.

| Provider | Model | Entry price | What's extra |
| --- | --- | --- | --- |
| DigitalOcean | Self-managed VPS | $4/month | cPanel license after 15-day trial |
| Amazon Lightsail | Self-managed VPS | $3.50/month | cPanel license |
| Linode | Self-managed VPS | $5/month | cPanel license |
| Vultr | Self-managed VPS | $2.50/month+ | cPanel license |
| Google Cloud | Self-managed VM | $8/month+ | cPanel license |
| KnownHost | Fully managed VPS | $98.75/month | Nothing for management; page dated July 2023, so treat the figure as historical |

Read the first five rows as "server only". Once the license is added, the gap between a $4 VPS and a bundled shared plan narrows or disappears. KnownHost's number belongs to a different product category: 8 cores, 12 GB guaranteed RAM, 300 GB RAID-10 SSD and full management, priced for businesses that need guaranteed resources and someone else on call.

## FAQ

**Is cPanel free?**
The software is not. It is licensed per account, and most shared hosts pay for it and include it in the plan. On a self-managed cloud server you buy the license yourself after the trial ends.

**Can I host more than one website on one cPanel account?**
Yes, using addon domains or subdomains. Performance depends on the server underneath, so a dozen heavy sites will need a bigger plan, not a bigger panel.

**Do I need cPanel to run WordPress?**
No, but it makes the routine jobs easier: one-click installs, database access, SSL renewal, email accounts and backups behind one login. cPanel manages the hosting environment; WordPress manages the content.

**Can I use Google Workspace or Zoho Mail with cPanel hosting?**
Yes. Create the mailboxes at the external provider, then update the MX and DNS records inside cPanel. Alternatively, keep email in cPanel's own Webmail and skip the extra subscription. For a single mailbox, cPanel email is usually the cheaper call.

**The cPanel login page will not load. What now?**
Clear the cache, check your connection, try `yourdomain.com:2083` directly, and if it still fails, contact support. Login errors are frequently a browser or DNS issue rather than a server outage.

## Which plan fits

- **One or two sites, no interest in server administration:** the shared 30 GB tier. At $10.49/year, with cPanel, LiteSpeed, CloudLinux and offsite daily backups included, it costs less than most domain renewals.
- **Five to ten sites, or one site with real traffic:** the 85 GB tier, mainly for the ten-domain allowance.
- **Unlimited domains and heavier transfer:** the 200 GB tier.
- **Client sites or resale:** the reseller plan with WHM and 12 cPanel accounts, which is a different product line rather than an upsell.
- **Guaranteed CPU and RAM with someone else managing the server:** a managed VPS, at several times the price.
- **You want the lowest possible monthly and enjoy SSH:** a self-managed VPS plus a cPanel license, and you own every outage.

Two things to confirm before you click order: whether the cPanel license and backups are included for the life of the plan rather than the first term, and what the cancellation terms are. Then buy the smallest plan that covers your sites, because moving up later is a support ticket and moving down is a migration.

👉 [Start with RackNerd's smallest cPanel plan and upgrade when you need to](https://bit.ly/RacKnerd)
