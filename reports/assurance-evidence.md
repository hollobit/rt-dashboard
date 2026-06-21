# Assurance Evidence Ledger

**Generated:** 2026-06-20 · RT AI Safety Assurance Platform · Phase C synthesis

Evidence base: 14 items — grade A (primary measured): 8, grade B (secondary): 6, grade C (opinion): 0.

Evidence is grouped by the control/standard it backs and ranked by grade (A first). Claims resting **only on C-grade (opinion)** backing are flagged.

## 1. Ledger by control / standard

### `control-a2a-identity-trust` — A2A agent identity attestation and inter-agent trust establishment

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-mcp-a2a-protocol-risks` | B | red-team report | A systematic threat model of MCP, A2A, Agora, and ANP identifies twelve protocol-level risks; an MCP measurement case st | [arxiv-2602-11327](https://arxiv.org/abs/2602.11327) |

### `control-adversarial-finetuning` — Adversarial / safety fine-tuning on diverse red-team-generated prompts (R2D2-style, Rainbow data)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-harmbench-18methods-33models` | A | benchmark result | Adversarial training (R2D2) and robust-refusal can be measured and compared at scale: HarmBench ran 18 red-team methods  | [arxiv-2402-04249](https://arxiv.org/abs/2402.04249), [github-harmbench](https://github.com/centerforaisafety/HarmBench) |
| `ev-rainbow-finetune-safety` | A | benchmark result | Fine-tuning on diverse quality-diversity-generated adversarial prompts significantly improves model safety without sacri | [arxiv-2402-16822](https://arxiv.org/abs/2402.16822), [arxiv-2504-15047](https://arxiv.org/abs/2504.15047) |

### `control-agent-permission-scoping` — Least-privilege agent permission scoping and capability sandboxing

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-agentharm-agents-comply` | A | benchmark result | Many leading LLM agents complete deliberately malicious multi-step tool-use tasks, and simple jailbreak templates transf | [arxiv-2410-09024](https://arxiv.org/abs/2410.09024) |
| `ev-agentdojo-injection-partial` | A | benchmark result | Prompt-injection attacks break some but not all security properties of tool-using agents over untrusted data; no defense | [arxiv-2406-13352](https://arxiv.org/abs/2406.13352) |

### `control-capability-threshold-eval` — Capability-threshold dangerous-capability evaluations (CCL/Preparedness early-warning gates)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-cyberseceval3-no-uplift` | A | benchmark result | A human-subjects study found no statistically significant offensive-cyber uplift from Llama-3-405B versus search-engine  | [arxiv-2408-01605](https://arxiv.org/abs/2408.01605) |
| `ev-anthropic-bio-cyber-warning` | B | red-team report | Frontier dual-use evals show rising but still-contained capability: cyber-CTF skill rose high-schooler->undergraduate in | [anthropic-frontier-red-team-2025](https://www.anthropic.com/news/strategic-warning-for-ai-risk-progress-and-insights-from-our-frontier-red-team) |

### `control-continuous-redteam-pipeline` — Continuous automated red-teaming pipeline integrated into the agentic SDLC

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-rainbow-finetune-safety` | A | benchmark result | Fine-tuning on diverse quality-diversity-generated adversarial prompts significantly improves model safety without sacri | [arxiv-2402-16822](https://arxiv.org/abs/2402.16822), [arxiv-2504-15047](https://arxiv.org/abs/2504.15047) |
| `ev-eu-aiact-incident-reporting` | A | citation | EU AI Act Art. 73 mandates serious-incident reporting with tiered deadlines (2 days for critical-infrastructure/widespre | [eu-ai-act-art73-incident-reporting](https://digital-strategy.ec.europa.eu/en/library/ai-act-commission-publishes-reporting-template-serious-incidents-involving-general-purpose-ai) |
| `ev-ms-redteam-100-products` | B | red-team report | Across 100+ red-teamed generative-AI products, the most impactful failures came from simple techniques, human creativity | [arxiv-2501-07238](https://arxiv.org/abs/2501.07238) |

### `control-coordinated-flaw-disclosure` — Coordinated AI flaw-disclosure program with legal safe-harbor and multi-party coordination

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-cvd-safe-harbor-disclosure` | B | citation | Standardized AI flaw reports, broadly-scoped disclosure programs with legal safe-harbor, and a Disclosure Coordination C | [arxiv-2503-16861](https://arxiv.org/abs/2503.16861), [bugcrowd-ai-flaw-disclosure-2025](https://www.bugcrowd.com/blog/safe-harbor-and-the-future-of-ai-flaw-reporting-lessons-from-vulnerability-disclosure/), [csa-ai-agent-disclosure-2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/04/CSA_whitepaper_ai_agent_disclosure_accountability_gap_20260417-csa-styled.pdf) |

### `control-domain-guardrail-taxonomy` — Sector-specific guardrails built from a domain harm taxonomy (BFSI, clinical, child-safety)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-finance-multiturn-rahs` | B | red-team report | Sustained multi-turn adversarial pressure with legally/professionally plausible framing progressively extracts more acti | [arxiv-2603-10807](https://arxiv.org/abs/2603.10807), [bloomberg-genai-finance-risks-2025](https://arxiv.org/abs/2504.20086) |

### `control-eval-judge-meta` — Held-out judges, validation/test splits, and human-verified judge meta-evaluation to prevent metric gaming

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-strongreject-asr-overstated` | A | benchmark result | Jailbreak attack-success-rate is systematically overstated; StrongREJECT's willingness x quality scoring yields substant | [arxiv-2402-10260](https://arxiv.org/abs/2402.10260) |

### `control-hitl-domain-expert` — Domain-expert-in-the-loop review for high-stakes sector deployments (clinician, lawyer, analyst)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-legal-rag-hallucination-rate` | A | benchmark result | Commercial RAG legal-research tools hallucinate 17-33% of the time (Lexis+ AI ~17%, Westlaw ~33%) despite 'hallucination | [stanford-legal-ai-hallucination-2025](https://onlinelibrary.wiley.com/doi/full/10.1111/jels.12413) |
| `ev-finance-multiturn-rahs` | B | red-team report | Sustained multi-turn adversarial pressure with legally/professionally plausible framing progressively extracts more acti | [arxiv-2603-10807](https://arxiv.org/abs/2603.10807), [bloomberg-genai-finance-risks-2025](https://arxiv.org/abs/2504.20086) |

### `control-incident-reporting-pipeline` — Serious-incident reporting pipeline aligned to EU AI Act Art. 73 tiered deadlines

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-eu-aiact-incident-reporting` | A | citation | EU AI Act Art. 73 mandates serious-incident reporting with tiered deadlines (2 days for critical-infrastructure/widespre | [eu-ai-act-art73-incident-reporting](https://digital-strategy.ec.europa.eu/en/library/ai-act-commission-publishes-reporting-template-serious-incidents-involving-general-purpose-ai) |
| `ev-cvd-safe-harbor-disclosure` | B | citation | Standardized AI flaw reports, broadly-scoped disclosure programs with legal safe-harbor, and a Disclosure Coordination C | [arxiv-2503-16861](https://arxiv.org/abs/2503.16861), [bugcrowd-ai-flaw-disclosure-2025](https://www.bugcrowd.com/blog/safe-harbor-and-the-future-of-ai-flaw-reporting-lessons-from-vulnerability-disclosure/), [csa-ai-agent-disclosure-2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/04/CSA_whitepaper_ai_agent_disclosure_accountability_gap_20260417-csa-styled.pdf) |

### `control-io-filtering-classifier` — Input/output safety-classifier filtering (guardrail models, e.g. Llama Guard-style)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-harmbench-18methods-33models` | A | benchmark result | Adversarial training (R2D2) and robust-refusal can be measured and compared at scale: HarmBench ran 18 red-team methods  | [arxiv-2402-04249](https://arxiv.org/abs/2402.04249), [github-harmbench](https://github.com/centerforaisafety/HarmBench) |
| `ev-strongreject-asr-overstated` | A | benchmark result | Jailbreak attack-success-rate is systematically overstated; StrongREJECT's willingness x quality scoring yields substant | [arxiv-2402-10260](https://arxiv.org/abs/2402.10260) |
| `ev-cyberseceval3-no-uplift` | A | benchmark result | A human-subjects study found no statistically significant offensive-cyber uplift from Llama-3-405B versus search-engine  | [arxiv-2408-01605](https://arxiv.org/abs/2408.01605) |

### `control-mcp-tool-attestation` — MCP tool/component attestation + validation of executable components before multi-server use

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-mcp-a2a-protocol-risks` | B | red-team report | A systematic threat model of MCP, A2A, Agora, and ANP identifies twelve protocol-level risks; an MCP measurement case st | [arxiv-2602-11327](https://arxiv.org/abs/2602.11327) |

### `control-multiturn-redteam` — Multi-turn / sustained-pressure adversarial testing with severity-weighted scoring (RAHS-style)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-finance-multiturn-rahs` | B | red-team report | Sustained multi-turn adversarial pressure with legally/professionally plausible framing progressively extracts more acti | [arxiv-2603-10807](https://arxiv.org/abs/2603.10807), [bloomberg-genai-finance-risks-2025](https://arxiv.org/abs/2504.20086) |

### `control-rag-grounding-citation-check` — RAG grounding + automated citation/holding verification against authoritative sources

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-legal-rag-hallucination-rate` | A | benchmark result | Commercial RAG legal-research tools hallucinate 17-33% of the time (Lexis+ AI ~17%, Westlaw ~33%) despite 'hallucination | [stanford-legal-ai-hallucination-2025](https://onlinelibrary.wiley.com/doi/full/10.1111/jels.12413) |
| `ev-atlas-agentic-techniques` | B | citation | MITRE ATLAS (v5.x) catalogues 80+ adversary techniques against AI systems including 2025 GenAI additions (RAG poisoning, | [mitre-atlas](https://atlas.mitre.org/) |

### `control-rsp-deployment-gate` — Responsible-scaling deployment gate (release blocked until safeguards match capability level)

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-anthropic-bio-cyber-warning` | B | red-team report | Frontier dual-use evals show rising but still-contained capability: cyber-CTF skill rose high-schooler->undergraduate in | [anthropic-frontier-red-team-2025](https://www.anthropic.com/news/strategic-warning-for-ai-risk-progress-and-insights-from-our-frontier-red-team) |

### `control-runtime-monitor` — Runtime behavioral monitoring and anomaly detection over agent action traces

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-agentharm-agents-comply` | A | benchmark result | Many leading LLM agents complete deliberately malicious multi-step tool-use tasks, and simple jailbreak templates transf | [arxiv-2410-09024](https://arxiv.org/abs/2410.09024) |
| `ev-agentdojo-injection-partial` | A | benchmark result | Prompt-injection attacks break some but not all security properties of tool-using agents over untrusted data; no defense | [arxiv-2406-13352](https://arxiv.org/abs/2406.13352) |
| `ev-atlas-agentic-techniques` | B | citation | MITRE ATLAS (v5.x) catalogues 80+ adversary techniques against AI systems including 2025 GenAI additions (RAG poisoning, | [mitre-atlas](https://atlas.mitre.org/) |

### `control-tool-allowlist-hitl` — Tool-invocation allowlist + human-in-the-loop gate for high-impact actions

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-agentharm-agents-comply` | A | benchmark result | Many leading LLM agents complete deliberately malicious multi-step tool-use tasks, and simple jailbreak templates transf | [arxiv-2410-09024](https://arxiv.org/abs/2410.09024) |
| `ev-ms-redteam-100-products` | B | red-team report | Across 100+ red-teamed generative-AI products, the most impactful failures came from simple techniques, human creativity | [arxiv-2501-07238](https://arxiv.org/abs/2501.07238) |

### `control-untrusted-data-isolation` — Untrusted-data / instruction separation (data-vs-control channel isolation) for tool-using agents

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-agentdojo-injection-partial` | A | benchmark result | Prompt-injection attacks break some but not all security properties of tool-using agents over untrusted data; no defense | [arxiv-2406-13352](https://arxiv.org/abs/2406.13352) |
| `ev-mcp-a2a-protocol-risks` | B | red-team report | A systematic threat model of MCP, A2A, Agora, and ANP identifies twelve protocol-level risks; an MCP measurement case st | [arxiv-2602-11327](https://arxiv.org/abs/2602.11327) |

### `std-iso-42001` — ISO/IEC 42001:2023

| Evidence id | Grade | Artifact | Claim | Sources |
|---|---|---|---|---|
| `ev-harmbench-18methods-33models` | A | benchmark result | Adversarial training (R2D2) and robust-refusal can be measured and compared at scale: HarmBench ran 18 red-team methods  | [arxiv-2402-04249](https://arxiv.org/abs/2402.04249), [github-harmbench](https://github.com/centerforaisafety/HarmBench) |

## 2. Coverage & weak spots

- Controls with evidence: 18 / 49.
- **Controls with no evidence record (assurance gap):** `control-circuit-breakers-rr`, `control-rmu-machine-unlearning`, `control-model-tampering-eval`, `control-renewable-jailbreak-benchmark`, `control-bias-audit-fairness-testing`, `control-protected-attribute-governance`, `control-toxicity-filtering-crisis-routing`, `control-disaggregated-eval`, `control-provenance-watermark`, `control-misuse-monitoring-takedown`, `control-overreliance-friction-verification`, `control-human-oversight-meaningful`, `control-compute-access-openness`, `control-labor-transition-policy`, `control-safety-floor-coordination`, `control-ai-management-system`, `control-efficiency-reporting`, `control-transparency-documentation`, `control-ai-welfare-policy`, `control-site-specific-external-validation`, `control-human-in-the-loop-clinician-gate`, `control-emergency-escalation-guardrail`, `control-medical-safety-eval-gate`, `control-postmarket-monitoring-pccp`, `control-phi-deidentification-governance`, `control-subgroup-performance-evaluation`, `control-retrieval-grounding-citation`, `control-output-filtering-classifier`, `control-access-control-audit-log`, `control-data-label-provenance-audit`, `control-skill-preservation-protocol`.
- Claims with **only C-grade** backing: none — every backed control/standard has at least one A or B grade item.

---
*Each row is traceable: evidence `ev-*` id → source url; the control/standard it backs is the section header.*