# rip

The open SaaS replacement toolkit. Agent skills for replacing SaaS with AI-built code.

## Install

```bash
npx skills add vendor-rip/rip
```

Works with Claude Code, Cursor, Windsurf, Codex, Copilot, and 40+ other AI agents.

## What It Does

Scans your codebase for SaaS tool integrations, assesses replaceability, generates migration plans, executes replacements, and validates results. Entirely local — no data leaves your machine unless you choose to share.

```
$ vendor-rip scan amplitude

┌─────────────────────────────────────────────────────────────┐
│  ✓ Scan   ▸ Plan   ○ Execute   ○ Validate   ○ Done        │
└─────────────────────────────────────────────────────────────┘

Amplitude | @amplitude/analytics-browser@2.8.0

  Method              Calls   Files   Feature              Complexity   Pattern
  -----------------------------------------------------------------------------
  track               14      4       event tracking       trivial      scattered
  identify             3      2       user identification  trivial      wrapper
  experiments          4      2       experimentation      hard         embedded

  Features: 3 of ~12 (25%) | Complexity: moderate | Est: 3-5 days

$ vendor-rip discover

Found 6 SaaS tools:

  Tool             Category         Points   Complexity    Est. Days   Savings
  ---------------------------------------------------------------------------
  LaunchDarkly     feature flags      8      trivial         1-2       $12k/yr
  Datadog          monitoring        14      moderate        6-8       $50k/yr
  Amplitude        analytics         21      moderate        3-5       $42k/yr
  Statuspage       status page        1      trivial         0.5       $3k/yr

  Addressable savings: $64k+/yr
```

## SaaS Replaceability Index

Top rippable SaaS tools, ranked by [Rip Score](https://vendor.rip) (0-100):

| Tool | Category | Rip Score | Why |
|---|---|---|---|
| [Looker](https://vendor.rip) | BI / Analytics | 84 | recharts + SQL as React components + server-side BigQuery |
| [Amplitude](https://vendor.rip) | Product Analytics | 79 | Custom event tracking + any storage backend |
| [LaunchDarkly](https://vendor.rip) | Feature Flags | 88 | Config file or simple key-value store |
| [Datadog](https://vendor.rip) | Monitoring | 62 | OpenTelemetry + Grafana/self-hosted stack |
| [Statuspage](https://vendor.rip) | Status Pages | 92 | Static site + health check endpoint |

Full index at [vendor.rip](https://vendor.rip).

## Case Studies

**Looker ($50k/yr) — replaced in 1.5 weeks, 1 engineer.** recharts + SQL as React components + server-side BigQuery. Works perfectly. The founding story of vendor.rip.

**Headless CMS ($682k/yr) — replaced in 3 days, $260 in AI tokens.** Lee Robinson (VP Product/DX at Vercel) eliminated $682k/yr in CMS+CDN costs. 67 commits, -322K lines removed. CMS abstractions created network boundaries that actively blocked AI agents from using grep/edit. Source: [leerob.com/agents](https://leerob.com/agents).

## How It Works

Five phases, each producing structured output:

1. **Scan** — Find the SDK, map integration points, assess complexity per feature
2. **Plan** — Generate phased migration plan with tasks, pitfalls, validation criteria
3. **Execute** — Write replacement code phase by phase, with checkpoints
4. **Validate** — Run tests, verify SDK removal, check configuration cleanup
5. **Complete** — Produce completion report, optionally share outcomes

Between Scan and Plan, you can exchange scan data at [vendor.rip/calibrate](https://vendor.rip/calibrate) for community calibration data (peer comparison, calibrated estimates, common gotchas). This is always optional and manual — the skill never sends data anywhere.

## Tool Profiles

Tool profiles in `profiles/{tool-slug}/` make scans faster and more accurate with community-calibrated data. Without profiles, the agent reasons from code patterns and web search — still useful, just less precise.

```
profiles/{tool-slug}/
  features.yaml    # method-to-feature mapping
  pricing.yaml     # typical cost ranges
  data.yaml        # export capabilities, lock-in factors
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to:

- Add or improve tool profiles
- Improve the core skill
- Share replacement experiences

## License

[MIT](LICENSE)
