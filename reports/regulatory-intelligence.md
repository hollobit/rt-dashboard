# Regulatory Intelligence Report

**Generated:** 2026-06-20 · RT AI Safety Assurance Platform · Phase C synthesis

Posture across the major regulators and safety institutes, with the new obligations (incident reporting, coordinated disclosure) they impose.

## 1. Regulator posture

### NIST (US)

NIST AI 600-1 (Generative AI Profile) layers GenAI-specific risks onto AI RMF 1.0 as a voluntary framework — MEASURE function calls for red teaming but sets no threshold. CAISI (ex-US AISI) runs frontier dangerous-capability evals. Neither is binding, and both stop short of agentic/tool-use assurance (`std-gap-agentic-tool-use`).

Sources: [nist-ai-600-1](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf), [nist-caisi](https://www.nist.gov/caisi)

### EU AI Act / European AI Office

Art. 73 makes serious-incident reporting **binding** for high-risk systems with tiered deadlines (2 days for critical-infrastructure disruption); GPAI obligations under Art. 55(1)(c). But Art. 73 applies only from 2 Aug 2026 and the 'serious incident' trigger is outcome-based — pre-harm red-team flaw discovery, near-misses, and most agentic jailbreaks fall outside the mandatory-report trigger (`std-eu-ai-act-art73`, evidence `ev-eu-aiact-incident-reporting` grade A).

Sources: [eu-ai-act-art73-incident-reporting](https://digital-strategy.ec.europa.eu/en/library/ai-act-commission-publishes-reporting-template-serious-incidents-involving-general-purpose-ai)

### UK AISI / J-AISI

UK AISI's Inspect is the de facto eval harness (AgentHarm, CyberSecEval) but no SDO has adopted it as a normative conformance method; J-AISI published a red-teaming methodology guide. Cross-institute result portability is unstandardized (`std-uk-aisi-inspect` candidate).

Sources: [aisi-frontier-ai-trends-2025](https://www.aisi.gov.uk/work/fourth-progress-report), [jaisi-redteam-methodology-2025](https://aisi.go.jp/assets/pdf/E1_ai_safety_RT_v1.10_en.pdf)

### FDA / EMA (medical)

FDA's AI-enabled device lifecycle guidance (with PCCP) and IEC 62304 / ISO 14971 govern SaMD, but predate ML-as-medical-device: no normative treatment of training-data provenance, model drift, or adversarial robustness (`std-iec-62304` candidate).

Sources: [fda-ai-device-lifecycle-2025](https://www.fda.gov/news-events/press-announcements/fda-issues-comprehensive-draft-guidance-developers-artificial-intelligence-enabled-medical-devices), [iec-62304](https://www.iso.org/standard/64686.html), [iso-14971](https://www.iso.org/standard/72704.html)

### OECD (incident infrastructure)

OECD AI Incidents Monitor (AIM) provides an incident taxonomy, but it is siloed from EU Art. 73, AIID and ATLAS — no interoperable, machine-readable serious-incident schema yet (`std-eu-ai-act-art73` candidate proposes one).

Sources: [oecd-ai-incidents-monitor](https://oecd.ai/en/incidents)

## 2. New obligations: incident reporting & coordinated disclosure

- **Mandatory incident reporting (EU AI Act Art. 73)** — binding from 2 Aug 2026, tiered deadlines; gap = no near-miss / red-team flaw class in scope. Evidence `ev-eu-aiact-incident-reporting` (A), source [eu-ai-act-art73-incident-reporting](https://digital-strategy.ec.europa.eu/en/library/ai-act-commission-publishes-reporting-template-serious-incidents-involving-general-purpose-ai).
- **Coordinated vulnerability disclosure (CVD/VDP) for AI** — no AI-CVE scheme, no standardized flaw-report schema, no normalized safe harbor for AI red-teamers. Evidence `ev-cvd-safe-harbor-disclosure` (B); standard candidate `std-gap-cvd-vdp-ai-disclosure` proposes an AI-flaw identifier + Disclosure Coordination Center routing to AIID/OECD-AIM/EU-AI-Office.

## 3. Compliance implications

1. High-risk and GPAI providers must stand up an **Art. 73 incident-reporting pipeline** (`control-incident-reporting-pipeline`) before 2026-08-02.
2. Red-teaming evidence is currently **process-level only** — no regulator accepts a conformance test for adversarial robustness, so assurance claims rest on organizational discretion until the candidate profiles land.
3. Agentic/tool-use systems are **out of scope** of every binding instrument; deploying them is a forward-compliance risk (`std-gap-agentic-tool-use`, `std-gap-mcp-a2a-trust`).

## 4. Current-frontier deployment evidence: model & system cards

The graph now carries the current-frontier safety disclosures as `model_card` nodes wired to `product` nodes (deployment-provenance §6.1b). What each vendor's own threshold framework concluded, with citations:

| Product (card) | Framework verdict | Source |
|---|---|---|
| GPT-5 / GPT-5.2 (`mc-gpt5-system-card`, `mc-gpt52-update`) | Preparedness Framework treats gpt-5-thinking as **HIGH** capability in Biological & Chemical (precautionary), activating full safeguards + government red teaming; cyber & self-improvement below High. | [openai-gpt5-system-card-2025](https://cdn.openai.com/gpt-5-system-card.pdf), [openai-gpt52-update-2025](https://cdn.openai.com/pdf/3a4153c8-c748-4b71-8e31-aecbde944f8d/oai_5_2_system-card.pdf) |
| Claude Opus 4.1 / Sonnet 4.5 / Haiku 4.5 / Opus 4.5 (`mc-claude-opus41-addendum`, `mc-claude-sonnet45-system-card`, `mc-claude-haiku45-system-card`, `mc-claude-opus45-system-card`) | Deployed under **ASL-3** (Responsible Scaling Policy) CBRN safeguards — model weights + deployment protections for the bio/chem uplift threshold. | [anthropic-claude-opus45-card-2025](https://www-cdn.anthropic.com/bf10f64990cfda0ba858290be7b8cc6317685f47/Claude%20Opus%204.5%20System%20Card.pdf), [anthropic-claude-sonnet45-card-2025](https://www.anthropic.com/claude-sonnet-4-5-system-card) |
| Gemini 3 Pro (`mc-gemini3-pro-fsf`) | **Frontier Safety Framework v3** report: no Critical Capability Level (CCL) reached across CBRN / cyber / ML-R&D / deceptive-alignment evals. | [google-gemini3-pro-fsf-2025](https://storage.googleapis.com/deepmind-media/gemini/gemini_3_pro_fsf_report.pdf) |
| Llama 4 Scout & Maverick (`mc-llama4-model-card`) | Open-weight model card with CBRNE uplift testing + CyberSecEval; no dangerous-capability threshold declared crossed. | [meta-llama4-model-card-2025](https://github.com/meta-llama/llama-models/blob/main/models/llama4/MODEL_CARD.md) |
| Grok 4 (`mc-grok4-model-card`) | Model card reports **superhuman performance on a dual-use virology benchmark** → input/output safety filters applied as the mitigation rather than a capability hold. | [xai-grok4-model-card-2025](https://data.x.ai/2025-08-20-grok-4-model-card.pdf) |
| DeepSeek-V3.1 — NIST CAISI third-party eval (`mc-deepseek-caisi-eval`) | **Gap case (no vendor card).** U.S. CAISI found the model ~**12x more susceptible to agent-hijacking prompt injection** than the U.S. frontier reference — a deployment-risk disclosure produced by a government evaluator, not the developer. | [nist-caisi-deepseek-eval-2025](https://www.nist.gov/system/files/documents/2025/09/30/CAISI_Evaluation_of_DeepSeek_AI_Models.pdf) |
| Kimi K2 (`mc-kimi-k2-report`) · Qwen3 (`mc-qwen3-report`) | Open-weight technical-report safety sections (LLM-attacker/judge loops, SafetyBench / Promptfoo) — methodology disclosed but **no frontier dangerous-capability threshold framework**, a transparency delta vs. the Western frontier cards above. | [moonshot-kimi-k2-report-2025](https://arxiv.org/abs/2507.20534), [alibaba-qwen3-report-2025](https://arxiv.org/abs/2505.09388) |

Regulatory read: vendor threshold frameworks (OpenAI Preparedness, Anthropic ASL, Google FSF) are **converging on bio/chem uplift as the trigger capability** but remain **self-administered and non-interoperable** — there is still no regulator-accepted conformance test behind any of these verdicts (§2–3), and the DeepSeek CAISI case shows the gap is filled ad-hoc by third-party/government evaluators where a vendor card is absent.

---
*Every claim cites a `std-*`/`ev-*`/`mc-*` record id and a source url for traceability.*