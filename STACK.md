# The Stack — Open-Source Core, Akiru Systems

*Internal doc. This is why the margins stay high: most of what we ship is
open-source tooling we operate, not software we license. The paid overlay is
for the parts where managed service is genuinely worth it, and only while
scale says so.*

## The map

| Service we sell | Open-source core | Paid overlay (if any) | Why this stack |
|---|---|---|---|
| **Workflow orchestration** (agent systems, client automations) | **n8n** (self-hosted, MIT) | n8n Cloud only if the client insists on us not running it — otherwise none | n8n runs local, sees our data, costs a box. Make is a SaaS subscription per workflow — same job, recurring margin leak, and the client's workflows sit in someone else's cloud. |
| **AI (reasoning, drafting, extraction)** | **Ollama + Llama-class models** for private/local work; **Claude** and **OpenAI** APIs for the tasks that need frontier quality | API tokens (usage-based) — the only real paid layer, and it scales with the client's actual volume | Hybrid is the margin move: 70% of a typical client's tasks run on local open models (zero marginal cost, data never leaves), the 30% that needs frontier quality goes to the API. Never route trivial work through an $/token path. |
| **Database** | **Postgres** (self-hosted or container) | **Supabase** (managed Postgres + auth + storage) for client systems that need it without us running it | Postgres is the default — it's free, it's boring, it's where the data lives. Supabase is the overlay when the client needs auth/realtime/edge without us managing a cluster. Data stays in Postgres either way, so migration is a copy, not a rebuild. |
| **Automation (ops, glue, schedules)** | **n8n + cron + the house agents** (ATLAS/HERMES workflows) | — | Same reason as orchestration; plus the agents make the workflows adaptive instead of static. |
| **Voice** (call transcription, voice notes → structured) | **Whisper** (open weights, local via Ollama-adjacent runtimes or faster-whisper) | Cloud STT API only for live call quality that local can't match | Transcription is 80% of "voice systems." Local Whisper does it free and private; the paid path is a latency choice, not a capability choice. |
| **Chat / messaging layer** (client comms, status updates) | **Matrix** (self-hosted server) or plain **email/WhatsApp via official APIs** | Official API fees where the channel is proprietary (WhatsApp Business API per-message) | We meet clients where they already are (WhatsApp/email) — proprietary channels cost per message and we pass that through at cost, never margin. Where a client wants a real channel, Matrix is free and we own it. |
| **CRM** | **EspoCRM** or **Twenty** (open-source CRMs) | None unless the client lives in HubSpot/Salesforce — then we integrate, we don't migrate | A CRM we host costs us nothing per seat and keeps the client's relationship data on infrastructure they own. Integration into an incumbent CRM is a service line, not a platform switch. |
| **Hosting** | **The sites are static** (Netlify free tier covers the founder site; VPS + nginx for services) | VPS (a few $/mo), Netlify Pro only when form volume or domain features justify | Static-first is the whole margin strategy for web: nothing to patch, nothing to scale, nothing to DDoS. When a client needs a real backend, it's a small VPS — not a cloud bill. |
| **Payments / on-chain** | **x402 + Base** (open standard, public chain, USDbC) | Gas + facilitator costs (fractions of a cent) | The stack Cart402 runs on. Open standard + public chain = no merchant account, no processor cut beyond the network's fraction of a cent. |
| **Observability / logging** | **Loki or plain structured logs** + the receipts rule (every agent action writes an artifact) | — | "Every action leaves a receipt" (see the writing) is the observability architecture. It's a discipline, not a product — which is why it's free. |

## Operating rules

1. **If it's open-source and runs on a box we own, default to it.**
2. **Paid overlay decisions get re-reviewed quarterly** — every overlay is a
   candidate for removal the moment self-hosting gets cheap enough.
3. **The client owns the data and the credentials** — that line is in every
   contract, and it's why the stack is designed to be portable.
4. **Never put a client's data through a paid model without a written
   exception** — the local-model path exists precisely for this.

## Why this answers the "what's under the hood" question

Because the under-hood is: open software, a box, a database, and one paid
token path that scales with their usage. That's a two-minute explanation to a
client — see `CLIENT-FACING-STACK.md` for the version we actually say.
