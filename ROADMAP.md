# WCAG Compliance Machine – Product Roadmap

## Vision
A production-grade, modular accessibility platform delivering continuous WCAG 2.2/2.1 AA+ compliance across web stacks with agentic automation, developer tooling, and business-ready reporting.

## Strategic Pillars
- Modular WCAG Solutions: pluggable scanners, fixers, and UI helpers.
- Agent Workflows: autonomous remediation, regression guards, and human-in-the-loop reviews.
- Continuous Compliance: CI/CD gates, scheduled jobs, and live dashboards.
- Multi-Platform Plugins: WordPress, Shopify, Next.js middleware, browser extension.
- Real-time Dashboards: executive, developer, and ops views with SLAs and alerts.
- Monetization: usage-based API, dashboard licensing, enterprise SSO tiers, services.

## Milestones

### M0 – Foundations (Week 1)
- Next.js 14 (App Router), TypeScript, Tailwind CSS setup.
- Vercel + Railway IaC: vercel.json, Dockerfile, Railway service.
- Global a11y UX: dark mode, keyboard navigation, focus rings, reduced motion, confetti helper.
- Core packages: @axe-core/cli, axe-core, zod, prisma (optional), pino, next-auth (placeholder), shadcn/ui.

Deliverables:
- Bootstrapped repo, CI lint/test/build, preview envs.

### M1 – WCAG Audit API (Weeks 1-2)
- REST endpoints: POST /api/audit { url, depth?, device?, standard? }.
- Queue/worker (Railway) executes headless scans via Playwright + axe-core.
- Result schema with WCAG mappings, severity, selectors, remediation text.
- Storage: Postgres (Railway) with Prisma, or file-based fallback.

Deliverables:
- OpenAPI spec, SDK client, example curl, rate-limit.

### M2 – Regulatory Radar (Week 2)
- Feeds: W3C WAI, EU Accessibility Act, ADA DOJ updates, WCAG errata.
- Watcher cron (Railway + GitHub Action) normalizes updates to a Changes table.
- Diff engine creates actionable changelogs for product and clients.

Deliverables:
- /regulatory dashboard, webhook to Slack/Teams/Email.

### M3 – Competitor Autopsy (Weeks 2-3)
- Input competitor URLs; crawl sitemaps; sample key templates.
- Automated audits + heuristics: color contrast, focus order, ARIA patterns.
- Benchmark scoring; PDF/CSV exports; shareable links.

Deliverables:
- /competitors UI + export pipeline.

### M4 – Empathy Simulator UI (Week 3)
- Layered filters: color blindness, low contrast, dyslexia font, motion sensitivity, low vision zoom, keyboard-only.
- Live DOM overlays via CSS/JS filters with toggleable presets.
- Recording of sessions (opt-in) for demo.

Deliverables:
- /empathy playground that wraps an iframe or proxied URL.

### M5 – Integrations Layer (Weeks 3-4)
- WordPress plugin: settings page, API key storage, audit on publish, badge widget.
- Shopify app: Admin UI, metafield storage, product template scanner, storefront badge.
- Next.js middleware helper and npm package for client-side hints.

Deliverables:
- /integrations docs, example repos/templates.

### M6 – Continuous Compliance & Dashboards (Weeks 4-5)
- Scheduled audits, budget thresholds, failure notifications.
- Exec dashboard: compliance trend, risk heatmap, legal exposure.
- Dev dashboard: issues by component/route, PR annotations, CI widget.

Deliverables:
- /dashboard real-time views; webhook integrations.

### M7 – Monetization & Packaging (Week 5)
- Plans: Free (limits), Pro (usage-based API), Business (SSO, SOC 2), Enterprise (SLA, VPC peering).
- Billing via Stripe; metering per scanned page + seats.
- Licensing for self-hosted dashboard.

Deliverables:
- Pricing page, terms, seat management stubs.

## Agentic Workflows
- Crawl Agent: discovers pages (sitemaps, nav graph), dedupes, schedules audits.
- Audit Agent: runs axe-core with device profiles, merges issues, retries flaky nodes.
- Fix Agent: suggests remediations; produces PRs with lint rules and tests.
- Validation Agent: re-audits preview deploys; blocks merges if budgets exceed.
- Radar Agent: monitors regulatory feeds; updates policies; opens issues.

## KPIs
- Mean time to remediate (MTTR), % WCAG AA pass across top N routes, false-positive rate, audit coverage, SLA compliance, churn vs NPS.

## Risks & Mitigations
- FP/FN: calibrate rules, allow suppressions, human review.
- Site variability: robust crawling fallbacks and timeouts.
- Legal nuance: link to guidance; disclaimers; update policy from Radar.

## Collaboration Notes (for Kimi)
- Module directories are isolated and typed with zod schemas.
- Each feature has dedicated README with public contracts and TODOs.
- OpenAPI spec drives client SDKs; keep endpoints backward-compatible.
