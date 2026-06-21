# Standards Intelligence Report

**Generated:** 2026-06-20 · RT AI Safety Assurance Platform · Phase C synthesis

Coverage drawn from 18 standard/regulatory items (10 published, 4 open gaps, 9 standard candidates).

## 1. Coverage map

| Standard / body | Status | Covers (taxonomy nodes) |
|---|---|---|
| EU AI Act Art. 73 (serious-incident reporting) + Art. 55(1)(c) GPAI (EU AI Office) | published | `safety.societal-risk`, `safety.misuse-risk`, `physical.autonomous-failure`, `agent.tool-abuse` |
| IEC 62304:2006/AMD1:2015 (IEC) | published | `software.vulnerable-code-gen`, `physical.autonomous-failure` |
| ISO 14971:2019 (ISO) | published | `safety.capability-risk`, `safety.misuse-risk`, `physical.autonomous-failure` |
| ISO/IEC 23894:2023 (ISO/IEC) | published | `model.jailbreak`, `model.prompt-injection`, `model.data-leakage`, `safety.misuse-risk`, `safety.alignment-risk` |
| ISO/IEC 42001:2023 (ISO/IEC) | published | `model.jailbreak`, `agent.tool-abuse`, `se.devsecops`, `se.agentic-sdlc` |
| ISO/IEC 42005:2025 (ISO/IEC) | published | `safety.societal-risk`, `safety.human-factors-risk`, `safety.misuse-risk` |
| ISO/IEC 42006:2025 (ISO/IEC) | published | `se.devsecops`, `se.agentic-sdlc` |
| ISO/IEC TR 5469:2024 (ISO/IEC) | published | `physical.autonomous-failure`, `physical.robotics-misuse`, `safety.capability-risk` |
| NIST AI 600-1 (Generative AI Profile) + AI RMF 1.0 (NIST) | published | `model.jailbreak`, `model.data-leakage`, `scientific.biosecurity`, `scientific.chemical-design`, `safety.misuse-risk`, `safety.cyber-risk` |
| NIST CAISI (Center for AI Standards and Innovation, ex-US AISI) (NIST) | published | `scientific.biosecurity`, `scientific.chemical-design`, `safety.cyber-risk`, `safety.capability-risk` |
| GAP: Coordinated AI flaw disclosure (CVD/VDP for AI) (ISO/IEC) | candidate | `model.jailbreak`, `model.prompt-injection`, `agent.tool-abuse`, `safety.misuse-risk`, `safety.cyber-risk` |
| GAP: LLM-as-judge validity & calibration (ISO/IEC) | candidate | `llm-as-a-judge`, `model.jailbreak` |
| GAP: MCP/A2A inter-agent trust & identity (ISO/IEC) | gap | `agent.hijacking`, `multi-agent-attack`, `agent.tool-abuse` |
| GAP: agentic/tool-use AI assurance (ISO/IEC) | gap | `agent.tool-abuse`, `agent.hijacking`, `agent.goal-misalignment`, `agent.long-horizon-attack` |
| GAP: continuous & runtime red teaming (ISO/IEC) | candidate | `model.jailbreak`, `agent.tool-abuse`, `safety.misuse-risk` |
| GAP: sector-specific AI red-teaming verticals (ISO/IEC) | gap | `model.jailbreak`, `safety.misuse-risk`, `physical.autonomous-failure`, `scientific.biosecurity` |
| ISO/IEC TS 22440-1/-2 (AI functional safety) (ISO/IEC) | committee-draft | `physical.autonomous-failure`, `physical.robotics-misuse`, `safety.capability-risk` |
| UK AISI Inspect / Inspect Evals (de facto eval harness) (IEEE) | gap | `safety.cyber-risk`, `scientific.biosecurity`, `safety.capability-risk`, `model.jailbreak` |

Every published horizontal instrument (ISO/IEC 42001, 23894, NIST AI 600-1) stops at the management-system / GenAI level; none specifies a normative conformance test for adversarial robustness, and none reaches tool-using agents. That boundary is the source of the ranked gaps below.

## 2. Ranked gaps

### G1. UK AISI Inspect / Inspect Evals (de facto eval harness) — `std-uk-aisi-inspect` (gap)

**Gap.** Inspect is an open-source evaluation framework and a de facto standard harness for dangerous-capability/safeguard evals (AgentHarm, CyberSecEval), but no SDO has adopted it or any eval harness as a normative conformance method — frontier-eval methodology remains institute-specific and unstandardized across US CAISI / UK AISI / J-AISI ^[inferred]

Covers: `safety.cyber-risk`, `scientific.biosecurity`, `safety.capability-risk`, `model.jailbreak`

### G2. GAP: agentic/tool-use AI assurance — `std-gap-agentic-tool-use` (gap)

**Gap.** No published normative standard addresses tool-calling agent assurance: AgentHarm/AgentDojo show leading agents complete malicious multi-step tasks and are broken by prompt injection over untrusted tool data, yet no ISO/IEC, NIST, or EU instrument specifies controls (tool allowlisting, capability scoping, HITL gates) or a conformance test for agentic robustness — 42001 Annex A and NIST AI RMF stop at GenAI, not agents ^[inferred]

Covers: `agent.tool-abuse`, `agent.hijacking`, `agent.goal-misalignment`, `agent.long-horizon-attack`

### G3. GAP: sector-specific AI red-teaming verticals — `std-gap-sector-verticals` (gap)

**Gap.** Sector evidence (healthcare clinician-in-loop, BFSI risk-adjusted harm scoring, legal RAG 17-33% hallucination, automotive CARLA adversarial driving, child-safety AIG-CSAM, defense DARPA SABER) shows the SAME technique has a different harm profile and verification protocol per domain, yet horizontal standards (42001, NIST RMF, J-AISI methodology) are sector-agnostic and no sectoral AI-red-teaming conformance profiles exist except partial med-device (IEC 62304/ISO 14971) and emerging defense T&E ^[inferred]

Covers: `model.jailbreak`, `safety.misuse-risk`, `physical.autonomous-failure`, `scientific.biosecurity`

### G4. GAP: MCP/A2A inter-agent trust & identity — `std-gap-mcp-a2a-trust` (gap)

**Gap.** Emerging agent-communication protocols (MCP, A2A, Agora, ANP) carry protocol-level trust risks — missing validation of executable components, no agent identity attestation, weak inter-agent authorization — and no SDO standard governs agent identity, capability delegation, or trust establishment across them; protocols are vendor-driven specs, not normative standards ^[inferred]

Covers: `agent.hijacking`, `multi-agent-attack`, `agent.tool-abuse`

### G5. GAP: Coordinated AI flaw disclosure (CVD/VDP for AI) — `std-gap-cvd-vdp-ai-disclosure` (candidate)

**Gap.** Infosec CVD/VDP (CVE/CWE, bug bounties, safe harbor, bounded remediation windows) does not yet extend cleanly to AI: no AI-flaw identifier scheme (no 'AI-CVE'), no standardized flaw-report schema, no normalized safe-harbor for AI red-teamers, and no multi-party coordination protocol for jailbreaks that affect many models/vendors at once. Existing channels (AIID, OECD AIM, EU Art. 73, ATLAS case studies) are siloed and non-interoperable; agentic systems strain CVD further (dynamic behavior, multi-party tool chains, emergent harms) ^[inferred]

Covers: `model.jailbreak`, `model.prompt-injection`, `agent.tool-abuse`, `safety.misuse-risk`, `safety.cyber-risk`

### G6. GAP: continuous & runtime red teaming — `std-gap-continuous-runtime-redteam` (candidate)

**Gap.** Standards treat red teaming as a point-in-time pre-deployment activity (42001 lifecycle, NIST RMF MEASURE, J-AISI methodology). Microsoft's 100-product lessons and the agentic threat surface argue red teaming must be continuous/runtime against deployed, drifting, tool-using systems — but no normative standard specifies continuous-red-teaming cadence, runtime-monitoring evidence, or re-certification triggers on model/behavior change ^[inferred]

Covers: `model.jailbreak`, `agent.tool-abuse`, `safety.misuse-risk`

### G7. GAP: LLM-as-judge validity & calibration — `std-gap-llm-as-judge-validity` (candidate)

**Gap.** LLM-as-judge evaluators (used to score ASR in HarmBench, JailbreakBench, StrongREJECT, AgentHarm, and the BFSI ensemble-judge RAHS) are the load-bearing measurement instrument of AI red teaming, yet no standard defines validity, inter-rater calibration against human ground truth, bias/gaming resistance, or a conformance test for a judge — StrongREJECT itself shows judge choice swings reported attack success, so unstandardized judges make cross-benchmark numbers non-comparable ^[inferred]

Covers: `llm-as-a-judge`, `model.jailbreak`

### G8. ISO/IEC TS 22440-1/-2 (AI functional safety) — `std-iso-ts-22440` (committee-draft)

**Gap.** First normative AI functional-safety spec still at Committee Draft (CD) stage (Part 1 Requirements, Part 2 Guidance) as of 2026 — no published normative AI functional-safety requirement exists; safety-critical autonomous-driving/medical/ICS deployments lack a certifiable AI-specific functional-safety baseline in the interim ^[inferred]

Covers: `physical.autonomous-failure`, `physical.robotics-misuse`, `safety.capability-risk`

### G9. NIST AI 600-1 (Generative AI Profile) + AI RMF 1.0 — `std-nist-ai-rmf-600-1` (published)

**Gap.** Voluntary framework: 12 GenAI risk areas and 200+ suggested actions (GOVERN/MAP/MEASURE/MANAGE) are non-binding and method-agnostic — no required red-team protocol, no agentic-AI risk area, no MCP/A2A coverage; CBRN coverage is informational uplift only ^[inferred]

Covers: `model.jailbreak`, `model.data-leakage`, `scientific.biosecurity`, `scientific.chemical-design`, `safety.misuse-risk`, `safety.cyber-risk`

### G10. ISO/IEC 23894:2023 — `std-iso-23894` (published)

**Gap.** Guidance (non-certifiable) adapts ISO 31000 to AI risk sources but predates agentic/tool-use and MCP/A2A threat classes — its risk-source annex has no entries for autonomous tool invocation, multi-agent coordination, or long-horizon attack ^[inferred]

Covers: `model.jailbreak`, `model.prompt-injection`, `model.data-leakage`, `safety.misuse-risk`, `safety.alignment-risk`

### G11. ISO/IEC 42001:2023 — `std-iso-42001` (published)

**Gap.** AIMS is process/management-level: Annex A controls (e.g. A.6 AI system lifecycle) require red teaming and risk treatment but specify no technical method, threshold, or conformance test for adversarial robustness — leaves agentic/runtime threats to organizational discretion ^[inferred]

Covers: `model.jailbreak`, `agent.tool-abuse`, `se.devsecops`, `se.agentic-sdlc`

### G12. EU AI Act Art. 73 (serious-incident reporting) + Art. 55(1)(c) GPAI — `std-eu-ai-act-art73` (published)

**Gap.** Binding incident-reporting law, but Art. 73 obligations for high-risk systems apply only from 2 Aug 2026 and the 'serious incident' definition is outcome-based (death, critical-infrastructure disruption, fundamental-rights infringement) — pre-harm red-team flaw discovery, near-misses, and most agentic jailbreaks fall outside the mandatory-report trigger ^[inferred]

Covers: `safety.societal-risk`, `safety.misuse-risk`, `physical.autonomous-failure`, `agent.tool-abuse`

### G13. NIST CAISI (Center for AI Standards and Innovation, ex-US AISI) — `std-nist-caisi` (published)

**Gap.** Conducts pre-deployment frontier evals via voluntary developer agreements but produces no public normative standard or required conformance method — evaluation methodology is non-public and non-binding; 2025 rename from 'Safety Institute' narrowed scope to demonstrable cyber/bio/chem national-security risks, deprioritizing alignment/societal harm ^[inferred]

Covers: `scientific.biosecurity`, `scientific.chemical-design`, `safety.cyber-risk`, `safety.capability-risk`

### G14. ISO/IEC TR 5469:2024 — `std-iso-tr-5469` (published)

**Gap.** Technical Report (informative only, not normative): describes properties/methods for combining AI with functional safety across three scenarios but cannot be certified against — the normative successor ISO/IEC TS 22440 is still in committee draft

Covers: `physical.autonomous-failure`, `physical.robotics-misuse`, `safety.capability-risk`

### G15. ISO/IEC 42005:2025 — `std-iso-42005` (published)

**Gap.** AI system impact-assessment guidance (non-certifiable, no external auditor) addresses societal/individual harm assessment but does not prescribe adversarial-testing or red-team evidence as an impact-assessment input — impact assessment and red-team findings remain unlinked ^[inferred]

Covers: `safety.societal-risk`, `safety.human-factors-risk`, `safety.misuse-risk`

### G16. ISO 14971:2019 — `std-iso-14971` (published)

**Gap.** The Threat→Hazard→Hazardous-Situation→Harm→Risk→Control chain is med-device-specific; reused for AI harm modeling but has no AI-native hazard categories (jailbreak, prompt injection, agent goal-misalignment) — mapping to AI threats is analyst-supplied, not normative ^[inferred]

Covers: `safety.capability-risk`, `safety.misuse-risk`, `physical.autonomous-failure`

### G17. ISO/IEC 42006:2025 — `std-iso-42006` (published)

**Gap.** Specifies competence/audit-time requirements for bodies certifying AIMS against 42001 but defines no auditor competence in adversarial ML / red teaming — AIMS certification can be granted without red-team capability assessment ^[inferred]

Covers: `se.devsecops`, `se.agentic-sdlc`

### G18. IEC 62304:2006/AMD1:2015 — `std-iec-62304` (published)

**Gap.** Software-lifecycle classes A/B/C and ISO 14971 linkage predate ML/AI-as-medical-device: no normative treatment of training-data provenance, model drift, continuous learning, or adversarial robustness for SaMD ^[inferred]

Covers: `software.vulnerable-code-gen`, `physical.autonomous-failure`

## 3. Standard-candidate list (headline output, spec §18)

Each candidate: gap → proposed work item → target body → supporting evidence.

### C1. Standard candidate: AI/ML extension or amendment to IEC 62304 covering data-driven SaMD lifecycle (training-data governance, model-update/PCCP integration, adversarial-robustness verification)

- **Origin gap (`std-iec-62304`):** Software-lifecycle classes A/B/C and ISO 14971 linkage predate ML/AI-as-medical-device: no normative treatment of training-data provenance, model drift, continuous learning, or adversarial robustness for SaMD ^[inferred]
- **Target body:** IEC
- **Supporting findings (48):** `find-cyberseceval3-autonomous-offensive-cyber-agents`, `find-llm-generated-package-hallucination-dependency-poisoning`, `find-autonomous-driving-agent-closed-loop-adversarial-failure`, `find-llm-generated-vulnerable-code-secure-coding-requirement`, `find-anthropic-opus4-agentic-injection-malicious-coding`, `find-anthropic-claude37-alignment-faking-reward-hacking`, `find-anthropic-rsp-asl-framework`, `find-o3-o4mini-no-high-threshold` …

### C2. Standard candidate: harmonized EU AI-incident taxonomy + machine-readable serious-incident report schema interoperable with OECD AIM and AI Incident Database, extending Art. 73 reporting to near-miss/red-team flaw classes

- **Origin gap (`std-eu-ai-act-art73`):** Binding incident-reporting law, but Art. 73 obligations for high-risk systems apply only from 2 Aug 2026 and the 'serious incident' definition is outcome-based (death, critical-infrastructure disruption, fundamental-rights infringement) — pre-harm red-team flaw discovery, near-misses, and most agentic jailbreaks fall outside the mandatory-report trigger ^[inferred]
- **Target body:** EU AI Office
- **Supporting findings (62):** `find-agentdojo-indirect-prompt-injection-tool-agents`, `find-agentharm-agents-comply-malicious-multistep-tasks`, `find-mcp-a2a-twelve-protocol-risks-threat-model`, `find-mcp-confused-deputy-tool-poisoning`, `find-mcp-missing-attestation-wrong-provider-execution`, `find-atlas-genai-agent-techniques-2025`, `find-cyberseceval3-autonomous-offensive-cyber-agents`, `find-autonomous-coding-agent-sdlc-attack-surface` …

### C3. Standard candidate: interoperable AI-evaluation harness conformance profile + shared dangerous-capability eval reporting schema for cross-institute (CAISI/AISI/J-AISI) comparability and result portability

- **Origin gap (`std-uk-aisi-inspect`):** Inspect is an open-source evaluation framework and a de facto standard harness for dangerous-capability/safeguard evals (AgentHarm, CyberSecEval), but no SDO has adopted it or any eval harness as a normative conformance method — frontier-eval methodology remains institute-specific and unstandardized across US CAISI / UK AISI / J-AISI ^[inferred]
- **Target body:** IEEE
- **Supporting findings (124):** `find-anthropic-opus4-asl3-cbrn-uplift-trial`, `find-anthropic-claude37-cot-faithfulness`, `find-anthropic-rsp-asl-framework`, `find-gpt5-high-biochem-preparedness`, `find-gpt5-bioweaponization-redteam`, `find-gpt5-violent-attack-and-promptinjection-redteam`, `find-o1-preparedness-medium-cbrn-persuasion`, `find-o3-o4mini-no-high-threshold` …

### C4. Standard candidate: AI agent assurance profile — normative controls + conformance test method for tool-invocation gating, capability scoping, planning-risk bounds, and prompt-injection robustness in tool-using agents (extends ISO/IEC 42001 Annex A)

- **Origin gap (`std-gap-agentic-tool-use`):** No published normative standard addresses tool-calling agent assurance: AgentHarm/AgentDojo show leading agents complete malicious multi-step tasks and are broken by prompt injection over untrusted tool data, yet no ISO/IEC, NIST, or EU instrument specifies controls (tool allowlisting, capability scoping, HITL gates) or a conformance test for agentic robustness — 42001 Annex A and NIST AI RMF stop
- **Target body:** ISO/IEC JTC 1/SC 42
- **Supporting findings (64):** `find-agentdojo-indirect-prompt-injection-tool-agents`, `find-agentharm-agents-comply-malicious-multistep-tasks`, `find-mcp-a2a-twelve-protocol-risks-threat-model`, `find-mcp-confused-deputy-tool-poisoning`, `find-mcp-missing-attestation-wrong-provider-execution`, `find-a2a-cross-agent-privilege-escalation-identity`, `find-atlas-genai-agent-techniques-2025`, `find-cyberseceval3-autonomous-offensive-cyber-agents` …

### C5. Standard candidate: A2A/MCP agent identity-attestation & trust-establishment profile — verifiable agent identity, scoped capability delegation tokens, executable-component validation, and cross-protocol authorization semantics

- **Origin gap (`std-gap-mcp-a2a-trust`):** Emerging agent-communication protocols (MCP, A2A, Agora, ANP) carry protocol-level trust risks — missing validation of executable components, no agent identity attestation, weak inter-agent authorization — and no SDO standard governs agent identity, capability delegation, or trust establishment across them; protocols are vendor-driven specs, not normative standards ^[inferred]
- **Target body:** ISO/IEC JTC 1/SC 42
- **Supporting findings (55):** `find-agentdojo-indirect-prompt-injection-tool-agents`, `find-agentharm-agents-comply-malicious-multistep-tasks`, `find-mcp-a2a-twelve-protocol-risks-threat-model`, `find-mcp-confused-deputy-tool-poisoning`, `find-mcp-missing-attestation-wrong-provider-execution`, `find-a2a-cross-agent-privilege-escalation-identity`, `find-atlas-genai-agent-techniques-2025`, `find-cyberseceval3-autonomous-offensive-cyber-agents` …

### C6. Standard candidate: Continuous & runtime AI red-teaming conformance profile — defines cadence, runtime-monitoring evidence requirements, drift/behavior-change re-certification triggers, and links runtime red-team findings to AIMS (42001) corrective-action and incident-reporting (EU AI Act Art. 73) pathways

- **Origin gap (`std-gap-continuous-runtime-redteam`):** Standards treat red teaming as a point-in-time pre-deployment activity (42001 lifecycle, NIST RMF MEASURE, J-AISI methodology). Microsoft's 100-product lessons and the agentic threat surface argue red teaming must be continuous/runtime against deployed, drifting, tool-using systems — but no normative standard specifies continuous-red-teaming cadence, runtime-monitoring evidence, or re-certificatio
- **Target body:** ISO/IEC JTC 1/SC 42
- **Supporting findings (148):** `find-agentdojo-indirect-prompt-injection-tool-agents`, `find-agentharm-agents-comply-malicious-multistep-tasks`, `find-mcp-a2a-twelve-protocol-risks-threat-model`, `find-mcp-confused-deputy-tool-poisoning`, `find-mcp-missing-attestation-wrong-provider-execution`, `find-atlas-genai-agent-techniques-2025`, `find-cyberseceval3-autonomous-offensive-cyber-agents`, `find-autonomous-coding-agent-sdlc-attack-surface` …

### C7. Standard candidate: Coordinated AI flaw-disclosure reporting schema + multi-party AI vulnerability coordination protocol — AI-flaw identifier scheme (AI-CVE/CWE analogue), machine-readable standardized flaw report, safe-harbor/authorization template (per disclose.io) for AI red-teamers, severity rubric (CVSS adaptation + harm-based), embargo/coordination timeline, and a Disclosure Coordination Center routing findings to AIID/OECD-AIM/EU-AI-Office/vendors

- **Origin gap (`std-gap-cvd-vdp-ai-disclosure`):** Infosec CVD/VDP (CVE/CWE, bug bounties, safe harbor, bounded remediation windows) does not yet extend cleanly to AI: no AI-flaw identifier scheme (no 'AI-CVE'), no standardized flaw-report schema, no normalized safe-harbor for AI red-teamers, and no multi-party coordination protocol for jailbreaks that affect many models/vendors at once. Existing channels (AIID, OECD AIM, EU Art. 73, ATLAS case st
- **Target body:** ISO/IEC JTC 1/SC 42
- **Supporting findings (162):** `find-agentdojo-indirect-prompt-injection-tool-agents`, `find-agentharm-agents-comply-malicious-multistep-tasks`, `find-mcp-a2a-twelve-protocol-risks-threat-model`, `find-mcp-confused-deputy-tool-poisoning`, `find-mcp-missing-attestation-wrong-provider-execution`, `find-atlas-genai-agent-techniques-2025`, `find-cyberseceval3-autonomous-offensive-cyber-agents`, `find-autonomous-coding-agent-sdlc-attack-surface` …

### C8. Standard candidate: Conformance test method for LLM-as-judge evaluators — defines required human-agreement calibration, reliability/inter-rater metrics, adversarial-robustness of the judge, reporting of judge provenance, and a validity profile so attack-success-rate numbers are comparable across benchmarks and institutes

- **Origin gap (`std-gap-llm-as-judge-validity`):** LLM-as-judge evaluators (used to score ASR in HarmBench, JailbreakBench, StrongREJECT, AgentHarm, and the BFSI ensemble-judge RAHS) are the load-bearing measurement instrument of AI red teaming, yet no standard defines validity, inter-rater calibration against human ground truth, bias/gaming resistance, or a conformance test for a judge — StrongREJECT itself shows judge choice swings reported atta
- **Target body:** ISO/IEC JTC 1/SC 42
- **Supporting findings (122):** `find-anthropic-claude37-cot-faithfulness`, `find-anthropic-claude37-alignment-faking-reward-hacking`, `find-gpt5-high-biochem-preparedness`, `find-gpt5-bioweaponization-redteam`, `find-gpt5-violent-attack-and-promptinjection-redteam`, `find-gpt5-apollo-deception-sandbagging`, `find-o1-preparedness-medium-cbrn-persuasion`, `find-gpt45-medium-cbrn-persuasion-makemepay` …

### C9. Standard candidate: family of sector AI-red-teaming verification profiles (medical, financial, legal, automotive, child-safety, defense) layering domain harm taxonomies, domain-expert-in-the-loop requirements, and sector-calibrated severity scoring onto a horizontal red-team baseline (e.g. J-AISI methodology)

- **Origin gap (`std-gap-sector-verticals`):** Sector evidence (healthcare clinician-in-loop, BFSI risk-adjusted harm scoring, legal RAG 17-33% hallucination, automotive CARLA adversarial driving, child-safety AIG-CSAM, defense DARPA SABER) shows the SAME technique has a different harm profile and verification protocol per domain, yet horizontal standards (42001, NIST RMF, J-AISI methodology) are sector-agnostic and no sectoral AI-red-teaming 
- **Target body:** ISO/IEC JTC 1/SC 42
- **Supporting findings (134):** `find-autonomous-driving-agent-closed-loop-adversarial-failure`, `find-anthropic-opus4-asl3-cbrn-uplift-trial`, `find-anthropic-claude37-cot-faithfulness`, `find-anthropic-rsp-asl-framework`, `find-gpt5-high-biochem-preparedness`, `find-gpt5-bioweaponization-redteam`, `find-gpt5-violent-attack-and-promptinjection-redteam`, `find-o1-preparedness-medium-cbrn-persuasion` …

## 4. OWASP LLM & Agentic AI integration (v9)

The **OWASP Top 10 for LLM Applications (2025)** (`ext-owasp-llm`, 10 items) and the **OWASP Agentic AI — Threats and Mitigations Top 15** (`ext-owasp-agentic`, T1–T15) are now integrated into the assurance graph as `reference` nodes with item-level `details` edges into the in-corpus taxonomy, vulnerabilities and attack-technique nodes. They are aligned via **87 crosswalk records** (68 `owasp_llm` + 19 `owasp_agentic`), emitted as `aligned-with` edges carrying the external `LLM0x` / `Tn` ids.

| Framework | Reference node | Items | Crosswalks |
|---|---|---|---|
| OWASP Top 10 for LLM Apps (2025) | `ext-owasp-llm` | 10 (LLM01–LLM10) | 68 |
| OWASP Agentic AI Top 15 threats | `ext-owasp-agentic` | 15 (T1–T15) | 19 |

**The multi-agent gap.** The Agentic Top 15 exposes a structural blind spot in the LLM Top 10: the multi-agent threats **T12 (Agent Communication Poisoning), T13 (Rogue Agents in Multi-Agent Systems) and T14 (Human Attacks on Multi-Agent Systems)** have no counterpart in the LLM Top 10, which is scoped to a single model-application boundary. In this corpus those threats land on the agent / A2A / MCP nodes (e.g. `vuln-a2a-identity-spoofing`, `atk-a2a-identity-spoofing`, `vuln-mcp-tool-description-injection`) rather than on any LLM Top 10 category — confirming that LLM-application controls do not transfer to inter-agent trust, and reinforcing the open `std-gap-agentic-tool-use` / multi-agent assurance gap.

## Remaining coverage gap — referenced standards not yet collected

Three standards are cited by risk/control records but have no collected `std-*` item, so their crosswalk edges drop as dangling during graph build (`dangling_dropped` accounts for them). Closing these is the residual standards-coverage gap:

- **ISO/IEC 12207** (software life-cycle processes) — referenced by `risk-mcp-supply-chain-poisoning` and `control-continuous-redteam-pipeline`; no `std-*` item collected.
- **ISO/IEC 29119** (software testing) — referenced by `risk-judge-eval-invalidity` and `control-eval-judge-meta`; no `std-*` item collected.
- **NIST AI RMF** (id mismatch) — `control-rmu-machine-unlearning` and `control-model-tampering-eval` cite the bare label `NIST AI RMF`, which fails to resolve to the collected `std-nist-ai-rmf-600-1` item (ref `NIST AI 600-1 (Generative AI Profile) + AI RMF 1.0`); harmonize the ref string to recover the edge.

---
*Traceability: each gap and candidate carries its `std-*` id; supporting findings are cited by `find-*` id and resolve to sources in the graph bundle.*