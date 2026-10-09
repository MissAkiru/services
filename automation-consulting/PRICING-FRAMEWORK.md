# Pricing Framework — Automation Consulting

**Anchor rule: price the build at 60% of the first-year, employer-side cost
of the hire the client was about to make.** Then tier the build by task
complexity. The retainer is the same shape across tiers: ~30% of the build,
amortized monthly, for monitoring + fixes + model-change maintenance.

*Employer-side cost ≈ advertised salary × 1.25–1.30 (employer levies, tools,
training, management overhead) + one turnover cycle per year (~0.5× salary:
re-recruiting, re-training, the gap).*

---

## The three tiers

| | **T1 — Single Pipeline** | **T2 — Role Replacement** | **T3 — Operations System** |
|---|---|---|---|
| **What it is** | One repetitive task, automated end-to-end | A full job description, minus the judgment lines | A process across 2+ departments, multiple agents, integrations |
| **Typical task** | List building, invoice entry, report-from-fixed-source | Junior analyst, research assistant, scheduling ops | Intake→routing→execution→reporting across CRM+comms+data |
| **Complexity test** | 1 source → 1 destination, rules in a page | 3–5 steps, some branching, 1–2 integrations | 5+ steps, agents hand off, 3+ integrations, escalation to human |
| **Build price** | **$5K** | **$15K** | **$35K** |
| **Timeline** | 5–7 days | 2 weeks | 4 weeks |
| **Retainer** | $300/mo | $800/mo | $2K/mo |
| **The hire it replaces (anchor check)** | $30–45K/yr role | $45–70K/yr role | $90–150K/yr function (or 2 hires) |
| **60% of first-year employer cost** | ~$22–35K — we price at the floor; the client sees the delta on the slide | ~$35–55K — build + ~2 years of retainer ≈ 60% of two years' cost, framed as "cheaper than the first year alone" | ~$68–120K — build + retainer ≈ a fraction; the real pitch is the judgment-stays-human split |

**Reading the table:** T1 is the foot in the door and the case-study
factory. T2 is where the margin lives. T3 is rare — only take it when the
client has process docs or an ops person to interview, or the build scope
becomes a consultancy without an end.

## Sizing checklist (run before quoting)

1. [ ] Task pipeline written in ≤ 5 lines? (If not → don't pitch it)
2. [ ] Sources are all accessible legally? (Public APIs, client's own
       systems, exported files — no scraping behind walls)
3. [ ] Judgment lines marked and kept human?
4. [ ] Volume check: ≥ 20 executions/month? (Below that, a tool + a person
       is cheaper; say so — it builds the referral)
5. [ ] Data sensitivity: any regulated data? (If yes, add 20% to the build
       for the compliance layer, or pass)

## Floor and ceiling

- **Never below $4K build.** Below that you're donating, and the client
  treats donated work as worth nothing.
- **Never above $50K build solo.** Above that, either partner the build or
  sell T2 twice. The ceiling protects the 2-week promise.
- **Retainer is not negotiable down to zero.** A system with no one watching
  it fails in 90 days, and the failure is on the label. A client who won't
  pay for monitoring was shopping for a product, not a partnership.

## Quote format (one page)

```
BUILD (one-time): $X,XXX — scope: [pipeline lines] — delivery: [date]
RETAINER: $X,XXX/mo — monitoring, fixes, model changes — cancel monthly
TOTAL YEAR 1: $X,XXX  vs  HIRE YEAR 1 (employer cost): $X,XXX
Payback: ~X weeks of saved capacity
Ownership: the system, the docs, and the credentials are yours at delivery.
```

That last line is why the retainer converts: they're not renting the thing,
they're buying the thing and paying to keep it healthy.
