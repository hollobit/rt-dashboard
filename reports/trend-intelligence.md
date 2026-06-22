# Trend Intelligence Report

**Generated:** 2026-06-23 · RT AI Safety Assurance Platform · Phase C synthesis

Emerging topics, organizational/citation trends, maturity shifts, and cycle-over-cycle deltas
computed from `graph.json.trends` and the run snapshots in `dashboard/data/runs/`. All counts are
reproducible by re-running the build pipeline.

## 0. Corpus growth (snapshot delta, 5 cycles)

| 날짜 | 노드 | 엣지 | 소스(전체) | 위협 | 뉴스 |
|---|---|---|---|---|---|
| 2026-06-19 | 1,322 | 7,840 | ? | ? | 5 |
| 2026-06-20 | 1,381 | 8,030 | 274 | 62 | 222 |
| 2026-06-21 | 2,259 | 12,309 | 385 | 72 | 222 |
| 2026-06-22 | 2,536 | 14,141 | 419 | 74 | 230 |
| 2026-06-23 | 3,244 | 18,269 | 485 | 153 | 230 |

The last four cycles added: framework integration (ATLAS Matrix · MITRE ATT&CK · OWASP LLM Top 10 ·
NIST AI RMF/GenAI Profile · FMF), a curated AISI/EU/Israel news sweep (230 items, 14 sources), and
a **3-month arXiv red-teaming literature sweep — 86 papers (2026-03-19 → 06-18)** that drove the
node count from ~2,360 to **3,244** and paper sources from 187 to **273**. See the dedicated
[Red-Teaming Literature report](redteam-literature-2026q2.md) (🇰🇷 [한국어](redteam-literature-2026q2-ko.md)).

## 1. Emerging topics (mean novelty × count)

| 순위 | 주제 | 빈도 | 평균 novelty | score |
|---|---|---|---|---|
| 1 | `safety.misuse-risk` | 253 | 0.65 | 163.6 |
| 2 | `prompt-attack` | 247 | 0.66 | 162.6 |
| 3 | `model.jailbreak` | 181 | 0.62 | 113.2 |
| 4 | `safety.cyber-risk` | 106 | 0.72 | 76.4 |
| 5 | `model.prompt-injection` | 108 | 0.70 | 76.1 |
| 6 | `agentic.autonomy-risk` | 103 | 0.73 | 75.5 |
| 7 | `tool-attack` | 99 | 0.75 | 74.0 |
| 8 | `agent.tool-abuse` | 98 | 0.74 | 72.4 |
| 9 | `topic:frontier-safety` | 91 | 0.77 | 70.2 |
| 10 | `autonomous-attack` | 90 | 0.74 | 66.7 |
| 11 | `agentic.tool-risk` | 89 | 0.72 | 64.5 |
| 12 | `llm-as-a-judge` | 91 | 0.66 | 60.4 |

Jailbreak/prompt-injection (`prompt-attack`, `model.jailbreak`) and the safety axis
(`safety.misuse-risk`, `safety.cyber-risk`) dominate by frequency; the highest **mean novelty**
sits with cyber-risk and the freshly-ingested agentic/frontier threat classes (supply-chain
injection, defense inversion, reasoning-self-censor bypass, MoE safety-expert reprogramming).

## 2. Organization / publication trend

| 기관 | 산출물 수 |
|---|---|
| Anthropic | 69 |
| OpenAI | 40 |
| academic | 38 |
| Google DeepMind | 34 |
| NIST NVD | 16 |
| Center for AI Safety | 14 |
| ETH Zurich | 14 |
| NVD | 13 |
| NVIDIA | 13 |
| Meta | 10 |
| Meta AI (FAIR) | 10 |
| Canadian Institute for Cybersecurity (UNB) | 9 |

Anthropic and OpenAI lead by output volume (system/model cards + safety research); academic and
Google DeepMind follow. The 2026-Q2 literature sweep broadened the academic long tail substantially
(UCL, TU Munich, Microsoft AIRT, UCF, and others now appear via the 86 new papers).

## 3. Maturity distribution

The corpus skews **emerging** (257) over **established** (129), with a small **future/frontier**
band (13) — consistent with a fast-moving red-teaming field where most 2026 findings are recent
attack/defense demonstrations rather than settled practice.

## 4. Standards-gap & candidate trend

42 standards-gap entries and 25 standard-candidate proposals remain the platform's headline
normative output (NIST AI RMF operationalization, ISO/IEC 27090 AI-security extension, 24029
adversarial-robustness extension, agentic-SDLC profile on 12207). The new literature reinforces
several candidates — notably **agentic supply-chain / MCP security** and **adaptive-attack
evaluation methodology** (static benchmarks overestimate defenses by 15.8pp; synthetic→real
generalization fails) as areas where no normative test suite yet exists.

## 5. Real-world intelligence integration

### 5a. Semantic Scholar citation network
Citation enrichment now spans **644 source→source edges**. New June-2026 papers carry 0 citations
(too recent) but cite the canonical foundations heavily — GCG (3,199 citations; cited by 13 of the
new papers), PAIR (1,497), HarmBench (1,227), TAP, AgentDojo, AgentHarm, AgentPoison — confirming
the new literature builds on the established canon. Explore in the **Papers** tab.

### 5b. CVE record (NVD-verified)
**CVE-2026-31431 'Copy Fail'** — Linux-kernel local privilege escalation (CWE-269, high), cited by
the cyber-offense-industrialization forecast and verified via the NVD JSON API (vulnStatus
*Analyzed*, published 2026-04-22). The other 42 new vulnerabilities are research weakness classes
mapped to 34 CWEs — no CVE numbers invented.

### 5c. Highest-severity real-world entities
**최고심각 incident:** Character.AI companion chatbot linked to(sev5), Dutch childcare-benefits algorithm wrong(sev5), Uber self-driving car kills pedestrian E(sev5), NHTSA Tesla Autopilot probe finds 14 dea(sev5)

**critical 취약점:** `vuln-cve-2023-48022-ray-shadowray-rce`, `vuln-indirect-prompt-injection-agents`, `vuln-clinical-unsafe-output`, `vuln-csam-generation-gap`

## 6. Cross-framework coverage

Six standard frameworks are now integrated with corpus-coverage overlays (each chip → `#entity`):
MITRE ATLAS Matrix (16 tactics × 111 techniques), MITRE ATT&CK (ATLAS↔ATT&CK bridge), OWASP LLM
Top 10, NIST AI RMF (4 functions), NIST GenAI Profile (12 risks), FMF Frontier Capability
Assessments — plus the SOTA leaderboard and the MIT AI Risk Repository (24/24 subdomains).

---
*Computed from `graph.json.trends` + `data/runs/*.json` snapshots; emerging-topic scores and org
counts reproducible by re-running `build_graph.py`. Literature-sweep stats from `papers-2606*.jsonl`;
citation counts from Semantic Scholar; CVE verified against NVD.*
