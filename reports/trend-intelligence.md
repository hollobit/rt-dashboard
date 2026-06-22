# Trend Intelligence Report

**Generated:** 2026-06-23 (rev.2) · RT AI Safety Assurance Platform · Phase C synthesis

Emerging topics, organizational/citation trends, maturity shifts, and cycle-over-cycle deltas
computed from `graph.json.trends` and the run snapshots in `dashboard/data/runs/`.

## 0. Corpus growth (snapshot delta)

| 날짜 | 노드 | 엣지 | 소스(전체) | 위협 | 뉴스 |
|---|---|---|---|---|---|
| 2026-06-19 | 1,322 | 7,840 | ? | ? | 5 |
| 2026-06-20 | 1,381 | 8,030 | 274 | 62 | 222 |
| 2026-06-21 | 2,259 | 12,309 | 385 | 72 | 222 |
| 2026-06-22 | 2,536 | 14,141 | 419 | 74 | 230 |
| 2026-06-23 | 3,806 | 21,674 | 533 | 201 | 230 |
| 2026-06-23 (venue) | 3,806 | 21,674 | 321(논문) | 153 | 230 |

The recent cycles added framework integration (ATLAS · ATT&CK · OWASP LLM · NIST RMF/GenAI · FMF),
an AISI/EU/Israel news sweep, and a **two-stage literature sweep**: 86 latest arXiv preprints
(2026-03–06) + **48 peer-reviewed conference/journal papers** (IEEE S&P · ACL · NDSS · ICML · ICLR ·
AAAI · USENIX · CCS · EMNLP · ICCV · CVPR · IEEE TPAMI/TDSC/TIFS, 2025–2026). Together they drove the
graph from ~2,360 to **3,806 nodes** and paper sources from 187 to **321**. See the
[Red-Teaming Literature report](redteam-literature-2026q2.md) (🇰🇷 [한국어](redteam-literature-2026q2-ko.md)).

## 1. Emerging topics (mean novelty × count)

| 순위 | 주제 | 빈도 | novelty |
|---|---|---|---|
| 1 | `prompt-attack` | 284 | 0.67 |
| 2 | `safety.misuse-risk` | 260 | 0.65 |
| 3 | `model.jailbreak` | 206 | 0.64 |
| 4 | `model.prompt-injection` | 130 | 0.72 |
| 5 | `tool-attack` | 113 | 0.75 |
| 6 | `topic:frontier-safety` | 110 | 0.77 |
| 7 | `agentic.autonomy-risk` | 110 | 0.74 |
| 8 | `agent.tool-abuse` | 108 | 0.74 |
| 9 | `safety.cyber-risk` | 110 | 0.72 |
| 10 | `llm-as-a-judge` | 106 | 0.68 |
| 11 | `autonomous-attack` | 94 | 0.74 |
| 12 | `agentic.tool-risk` | 92 | 0.73 |

Jailbreak/prompt-injection and the safety axis dominate by frequency; highest **mean novelty** sits
with the freshly-ingested agentic/frontier/**multimodal** threat classes (supply-chain injection,
defense inversion, reasoning-self-censor bypass, MoE safety-expert reprogramming, and the new
multimodal-safety-comprehension / foundation-encoder-super-transfer classes from the CV-venue sweep).

## 2. Venue distribution (peer-reviewed papers)

| venue | 논문 수 |
|---|---|
| ICML 2025 | 5 |
| ACL 2025 | 4 |
| AAAI 2026 | 4 |
| EMNLP 2025 | 4 |
| USENIX Security 2025 | 3 |
| AAAI 2025 | 2 |
| ICML | 2 |
| NDSS Symposium 2026 | 2 |
| IEEE Symposium on Security and Privacy (S&P) 2025 | 2 |
| International Conference on Machine Learning (ICML) 2025 | 2 |

The venue sweep broadened the corpus beyond arXiv preprints into the established peer-reviewed canon —
top-cited additions include DataSentinel (IEEE S&P, 118 cit), Red-Teaming Multi-Agent Systems (ACL,
104), and Prompt-Injection-to-Tool-Selection (NDSS, 97).

## 3. Maturity & literature mix

The corpus skews **emerging** over **established**; the venue sweep added a peer-reviewed,
higher-citation layer that anchors the fast-moving arXiv frontier to vetted prior work. 134 papers
were read in full this campaign (86 arXiv + 48 venue), yielding **640 extracted records** — 244
findings, 95 attack techniques, 73 vulnerabilities, 60 candidate threat classes, 108 controls,
40 risks, 20 harms.

## 4. Standards-gap & candidate trend

42 standards-gap entries and 25 candidate proposals remain the headline normative output. The new
literature reinforces several: **agentic supply-chain / MCP security** (MPMA, SAGA, MCPXKIT),
**adaptive-attack evaluation methodology** (static benchmarks overestimate defenses; judge FNR can
hit 1.00), and **multimodal safety coverage** (alignment fails to generalize across shuffle/OOD/
cross-modal input transforms) — areas with no normative test suite yet.

## 5. Real-world intelligence integration

### 5a. Semantic Scholar citation network
**821 source→source edges**. The new papers cite the canonical foundations heavily — GCG (3,199 cit),
PAIR, HarmBench, TAP, AgentDojo, AgentHarm — and the venue papers add peer-reviewed high-citation
anchors. Explore in the **Papers** tab.

### 5b. CVE record (NVD-verified)
**CVE-2026-31431 'Copy Fail'** (Linux-kernel LPE, CWE-269) — NVD-verified. All other new
vulnerabilities are research weakness classes mapped to CWEs; older CVEs cited as benchmark dataset
examples (CVE-2017/2019) were not added — no CVE numbers invented.

## 6. Cross-framework coverage

Six standard frameworks integrated with corpus-coverage overlays (ATLAS Matrix · MITRE ATT&CK · OWASP
LLM Top 10 · NIST AI RMF · NIST GenAI Profile · FMF) + SOTA leaderboard + MIT AI Risk Repository
(24/24 subdomains).

---
*Computed from `graph.json.trends` + `data/runs/*.json`; reproducible via `build_graph.py`. Literature
stats from `papers-*.jsonl`; citation counts from Semantic Scholar; CVE verified against NVD.*
