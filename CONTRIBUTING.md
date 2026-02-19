# Contributing to rip

Thanks for helping make SaaS replacement easier for everyone.

## Ways to Contribute

### Add a tool profile

Tool profiles make scans faster and more accurate. Each profile lives in `profiles/{tool-slug}/` with YAML files describing the tool's features, pricing, and data portability.

**Structure:**

```
profiles/{tool-slug}/
  features.yaml    # Feature inventory: name, description, SDK methods
  pricing.yaml     # Typical costs by company size, pricing model, gotchas
  data.yaml        # Export capabilities, data format, lock-in factors
```

**Example `features.yaml`:**

```yaml
tool: amplitude
sdk_package: "@amplitude/analytics-browser"
features:
  - name: event_tracking
    description: "Track custom events with properties"
    sdk_methods: ["track", "logEvent"]
    complexity_hint: trivial
    oss_alternatives: ["posthog-js", "custom fetch + endpoint"]
  - name: experiments
    description: "A/B testing and feature flags"
    sdk_methods: ["experiment.fetch", "experiment.variant"]
    complexity_hint: hard
    oss_alternatives: ["posthog feature flags", "custom Redis + random"]
```

**Example `pricing.yaml`:**

```yaml
tool: amplitude
typical_annual_cost:
  small: 5000       # < 20 employees
  medium: 30000     # 20-100 employees
  large: 80000      # 100+ employees
pricing_model: "event-based, per-seat for some tiers"
pricing_gotchas:
  - "Event volume can spike unpredictably with product changes"
  - "Enterprise contracts often include minimum commitments"
```

**Example `data.yaml`:**

```yaml
tool: amplitude
export:
  api_available: true
  api_rate_limited: true
  formats: ["json", "csv"]
  historical_depth: "full history available via export API"
  gotchas: ["Rate limited to 100 requests/minute"]
data_format: proprietary_json
lock_in_factors:
  - "Event schema is Amplitude-specific"
  - "Cohort definitions do not export"
```

### Improve the core skill

The main skill lives in `skills/vendor-rip/SKILL.md`. If you find bugs, unclear instructions, or missing edge cases, open a PR.

Things that are particularly valuable:
- Error handling for edge cases you encountered
- Better heuristics for complexity assessment
- SDK detection patterns for less common tools

### Share replacement experiences

Run through a replacement and share what you learned:
- What tool did you replace?
- What approach worked?
- What gotchas did you hit?
- How long did it actually take vs. the estimate?

You can share via [vendor.rip/calibrate](https://vendor.rip/calibrate) (anonymous, plain text) or open an issue describing your experience.

## PR Process

1. Fork the repo
2. Create a branch (`add-amplitude-profile`, `fix-scan-edge-case`)
3. Make your changes
4. Open a PR with a clear description of what and why

For tool profiles: include your source for pricing and feature data. Community-verified data is more trustworthy.

For skill changes: describe the scenario that motivated the change and how you tested it.

## Creating a New Skill

Use `templates/SKILL-TEMPLATE.md` as a starting point. Every skill follows the same five-phase journey (Scan, Plan, Execute, Validate, Complete) with structured output at each phase.

## Code of Conduct

Be helpful. Be honest. Share what you learn.

Profiles should contain accurate data — don't guess pricing or feature capabilities. Mark anything uncertain. The community benefits from honest "I don't know" more than confident misinformation.
