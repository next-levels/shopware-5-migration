# Shopware 5 to Shopware 6 Migration – Links, Tips & Checklists

> A curated collection of resources for migrating a **Shopware 5** online shop to **Shopware 6**: official documentation, checklists, data-mapping templates, cost calculators, SEO redirect tips and best practices from real migration projects.

Shopware 5 reached **end of life on 31 July 2024** – no more security updates or bug fixes. PHP 8.2, the newest PHP line targeted by the last Shopware 5.7 releases, leaves security support on **31 December 2026** ([php.net](https://www.php.net/supported-versions.php)). If you still run a Shopware 5 store, now is the time to plan the move to Shopware 6.

*Deutsch: [Kurzfassung auf Deutsch](#deutsch-shopware-5-auf-6-migration) weiter unten.*

---

## Contents

- [Why migrate now?](#why-migrate-now)
- [Checklists & Guides](#checklists--guides)
- [Cost & Planning](#cost--planning)
- [Official Shopware Documentation](#official-shopware-documentation)
- [Migration Tools](#migration-tools)
- [Development: Plugins, Themes & Apps](#development-plugins-themes--apps)
- [SEO During the Migration](#seo-during-the-migration)
- [Hosting & Deployment](#hosting--deployment)
- [Migration Tips from Practice](#migration-tips-from-practice)
- [Step-by-Step Overview](#step-by-step-overview)
- [FAQ](#faq)
- [Deutsch: Shopware 5 auf 6 Migration](#deutsch-shopware-5-auf-6-migration)
- [Contributing](#contributing)

---

## Why migrate now?

- **No security updates** for Shopware 5 since July 2024 – every new vulnerability stays open.
- **PHP end of life** – PHP 8.2 security support ends 31 Dec 2026; hosters will phase it out.
- **Plugin ecosystem is gone** – most extension vendors have stopped maintaining Shopware 5 plugins.
- **Compliance risk** – unpatched shops put PCI DSS and GDPR (DSGVO) compliance at risk.
- **Shopware 6 is a full rewrite** (Symfony, Vue.js admin, API-first, Rule Builder, Flow Builder) – this is a re-platforming project, not a simple update.

Background: [Shopware 5 in 2026: risks, costs & migration to 6](https://next-levels.de/blog/shopware-5-2026-risiken-migration) (German).

## Checklists & Guides

- [Shopware 5 Migration Checklist & Costs 2026](https://sites.google.com/view/shopware-5-migration-checklist/startseite) – complete checklist covering preparation, data, plugins, SEO and go-live.
- [Shopware 5 auf 6 migrieren – Step-by-Step Guide (Google Doc)](https://docs.google.com/document/d/1JT8fYVbRAp4vNya7YIuCOBk-QqlHRd3pVYoXXBidb78/edit?usp=sharing) – step-by-step migration guide (German).
- [SW5 → SW6 Mapping Sheet (Google Sheet)](https://docs.google.com/spreadsheets/d/1AfPQBPfOwh9OWu42aLUIl09B6bxigOrN/edit?usp=sharing&ouid=113602758158144545487&rtpof=true&sd=true) – template to map Shopware 5 entities, plugins and features to their Shopware 6 equivalents.
- [Shopware 5 in 2026: Risiken, Kosten & Migration](https://next-levels.de/blog/shopware-5-2026-risiken-migration) – what EOL means for your store and how to plan the migration.

## Cost & Planning

- [Shopware 5 → 6 Migration Calculator](https://next-levels.de/shopware-migration-rechner) – enter your domain, answer a few questions and get a fixed price and go-live date estimate in about 3 minutes (free).
- [SW5 → SW6 Mapping Sheet](https://docs.google.com/spreadsheets/d/1AfPQBPfOwh9OWu42aLUIl09B6bxigOrN/edit?usp=sharing&ouid=113602758158144545487&rtpof=true&sd=true) – use it to scope plugins and custom features, the biggest cost drivers.

## Official Shopware Documentation

- [Shopware Migration Portal (EN)](https://docs.shopware.com/en/migration-en) / [(DE)](https://docs.shopware.com/de/migration-de) – official merchant guide for switching from Shopware 5 (and Magento) to Shopware 6.
- [Migration Assistant – Developer Docs](https://developer.shopware.com/docs/products/extensions/migration-assistant/) – architecture, profiles, gateways and how to extend the migration.
- [Version Upgrades and Migrations](https://developer.shopware.com/docs/guides/upgrades-migrations/) – upgrading within Shopware 6.
- [Shopware 6 Developer Documentation](https://developer.shopware.com/docs/) – the full developer reference.
- [Data Abstraction Layer (DAL)](https://developer.shopware.com/docs/concepts/framework/data-abstraction-layer.html) – the replacement for Shopware 5's Doctrine models.
- [Shopware 6 Release Notes](https://developer.shopware.com/release-notes/) – pick a target version and check breaking changes.

## Migration Tools

- [SwagMigrationAssistant](https://github.com/shopware/SwagMigrationAssistant) – official Shopware 6 plugin that imports products, categories, customers, orders, media and more from Shopware 5.
- [SwagMigrationConnector](https://github.com/shopware/SwagMigrationConnector) – Shopware 5 plugin that exposes your old shop's data to the Migration Assistant via API.
- [SwagMigrationMagento](https://github.com/shopware/SwagMigrationMagento) – Magento 1 & 2 profiles for the Migration Assistant (in case you consolidate shops).
- [Shopware CLI](https://developer.shopware.com/docs/products/cli/) / [FriendsOfShopware/shopware-cli](https://github.com/FriendsOfShopware/shopware-cli) – build, validate and deploy Shopware 6 projects and extensions.

## Development: Plugins, Themes & Apps

Shopware 5 plugins and Smarty themes **cannot be ported 1:1** – they must be rebuilt for Shopware 6.

- [Plugin Development Guide](https://developer.shopware.com/docs/guides/plugins/plugins/) – Symfony-based plugins for Shopware 6.
- [App System](https://developer.shopware.com/docs/guides/plugins/apps/) – cloud-compatible extensions via webhooks and the Admin API.
- [Storefront Themes](https://developer.shopware.com/docs/guides/plugins/themes/) – Twig + Bootstrap replaces Smarty templates.
- [Shopware Frontends](https://developer.shopware.com/frontends/) / [GitHub](https://github.com/shopware/frontends) – headless Vue/Nuxt storefront as an alternative to the Twig storefront.
- [Shopware Store](https://store.shopware.com/en/) – check which of your Shopware 5 plugins have a Shopware 6 successor.
- [Shopware 6 Core](https://github.com/shopware/shopware) / [Shopware 5 Core](https://github.com/shopware5/shopware) – source code for comparing implementations.

## SEO During the Migration

Losing rankings is the most common – and most expensive – migration mistake.

- [Google: Site Moves and Migrations](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes) – Google's official guidance for URL changes.
- [Shopware 6 SEO Settings](https://docs.shopware.com/en/shopware-6-en/settings/seo) – configure SEO URL templates for products and categories.

**SEO checklist:**

1. Crawl the Shopware 5 shop before migrating (all URLs, titles, meta descriptions, canonicals, hreflang).
2. Export top landing pages and backlinks from Google Search Console and analytics.
3. Rebuild the SEO URL templates in Shopware 6 to match the old structure where possible.
4. Create **301 redirects** for every URL that changes (products, categories, CMS/shopping worlds, blog, filters, images).
5. Migrate meta titles, descriptions and alt texts – not just product data.
6. Submit the new XML sitemap and monitor Search Console for 404s after go-live.

## Hosting & Deployment

- [Shopware 6 Hosting Guide](https://developer.shopware.com/docs/guides/hosting/) – server requirements, caching, queues, performance.
- [Installation & Updates](https://developer.shopware.com/docs/guides/hosting/installation-updates/) – recommended Composer-based setup.
- [Installation Guide](https://developer.shopware.com/docs/guides/installation/) – local development setups.
- [shopware/docker](https://github.com/shopware/docker) – official Docker images for Shopware 6.

## Migration Tips from Practice

- **Treat it as a relaunch, not an update.** Use the migration to drop unused plugins, outdated customizations and dead data.
- **Inventory every plugin first.** For each one decide: Shopware 6 standard feature, Store extension, custom rebuild – or drop it. Many SW5 plugins are now core features (Rule Builder, Flow Builder, Shopping Experiences).
- **Migrate data early and repeatedly.** Run the Migration Assistant on a staging system, validate the results, and re-run delta migrations right before go-live.
- **Check passwords & customers.** Customer accounts migrate; plan how legacy password hashes and newsletter opt-ins are handled.
- **Rebuild shopping worlds** as Shopware 6 Shopping Experiences – layouts do not migrate automatically.
- **Mind your interfaces.** ERP, PIM, payment, shipping and marketplace connectors usually need new Shopware 6 versions.
- **Freeze content before go-live** and plan a short final delta migration window for orders and customers.
- **Plan SEO from day one**, not on launch day (see [SEO checklist](#seo-during-the-migration)).
- **Budget for testing.** Checkout, payments, taxes, emails and invoices need full end-to-end tests.

## Step-by-Step Overview

1. **Analysis** – shop audit, plugin inventory, interfaces, data volume ([mapping sheet](https://docs.google.com/spreadsheets/d/1AfPQBPfOwh9OWu42aLUIl09B6bxigOrN/edit?usp=sharing&ouid=113602758158144545487&rtpof=true&sd=true)).
2. **Concept & budget** – target architecture, feature mapping, estimate ([calculator](https://next-levels.de/shopware-migration-rechner)).
3. **Setup** – Shopware 6 installation, hosting, CI/CD.
4. **Data migration** – Migration Assistant + Connector on staging.
5. **Theme & extensions** – storefront, plugins/apps, integrations.
6. **SEO** – URL structure, redirects, metadata.
7. **Testing** – functional, checkout, performance, acceptance.
8. **Go-live** – final delta migration, DNS switch, monitoring.

Detailed walkthrough: [Shopware 5 Migration Checklist](https://sites.google.com/view/shopware-5-migration-checklist/startseite).

## FAQ

**Can I update Shopware 5 to Shopware 6 directly?**
No. Shopware 6 is a completely new system. You install a fresh Shopware 6 and transfer data with the official Migration Assistant. Themes and plugins have to be rebuilt.

**What data can be migrated?**
Products, variants, categories, manufacturers, properties, customers, orders, media, CMS pages, newsletter recipients, reviews, promotions and more – see the [Migration Portal](https://docs.shopware.com/en/migration-en).

**How long does a Shopware 5 to 6 migration take?**
Small shops with few customizations often take a few weeks; large shops with many plugins and integrations take several months.

**How much does a Shopware migration cost?**
It depends mainly on the number of plugins, custom features and interfaces. Get an estimate with the [migration calculator](https://next-levels.de/shopware-migration-rechner).

**Will I lose my Google rankings?**
Not if URLs are preserved or redirected with 301s and metadata is migrated. See [SEO During the Migration](#seo-during-the-migration).

**Is Shopware 5 still safe to run in 2026?**
No. It receives no security updates since July 2024, and its PHP runtime is approaching end of life.

---

## Deutsch: Shopware 5 auf 6 Migration

Shopware 5 ist seit dem **31. Juli 2024 End of Life** – es gibt keine Sicherheitsupdates mehr, und PHP 8.2 erhält ab dem **31.12.2026** keine Sicherheitsupdates mehr. Ein direktes Update auf Shopware 6 ist nicht möglich: Daten werden mit dem offiziellen Migrationsassistenten übernommen, Theme und Plugins müssen neu umgesetzt werden.

**Die wichtigsten Ressourcen:**

- [Shopware 5 Migration: Checkliste & Kosten 2026](https://sites.google.com/view/shopware-5-migration-checklist/startseite)
- [Shopware 5 auf 6 migrieren – Schritt-für-Schritt-Leitfaden](https://docs.google.com/document/d/1JT8fYVbRAp4vNya7YIuCOBk-QqlHRd3pVYoXXBidb78/edit?usp=sharing)
- [SW5 → SW6 Mapping-Tabelle](https://docs.google.com/spreadsheets/d/1AfPQBPfOwh9OWu42aLUIl09B6bxigOrN/edit?usp=sharing&ouid=113602758158144545487&rtpof=true&sd=true)
- [Shopware 5 → 6 Migrations-Rechner: Festpreis in 3 Minuten](https://next-levels.de/shopware-migration-rechner)
- [Shopware 5 in 2026: Risiken, Kosten & Migration auf 6](https://next-levels.de/blog/shopware-5-2026-risiken-migration)
- [Offizielles Shopware Migration Portal (DE)](https://docs.shopware.com/de/migration-de)

**Tipps:** Plugin-Inventur zuerst, Datenmigration früh und mehrfach auf Staging testen, 301-Weiterleitungen für alle geänderten URLs anlegen, Einkaufswelten als Erlebniswelten neu aufbauen und Schnittstellen (ERP, PIM, Payment) rechtzeitig prüfen.

---

## Contributing

Know a helpful tool, guide or tip for Shopware 5 to 6 migrations? Pull requests are welcome – please add one link per line with a short description in the matching section.

---

Maintained by [next-levels](https://next-levels.de) – Shopware agency for migrations from Shopware 5 to Shopware 6.

**Keywords:** Shopware 5 migration, Shopware 6 migration, Shopware 5 to 6, Shopware 5 end of life, Shopware Migration Assistant, Shopware upgrade, Shopware 5 auf 6, Shopware Umstieg, Shopware 5 EOL, Shopware Migration Kosten, Shopware Migration Checkliste
