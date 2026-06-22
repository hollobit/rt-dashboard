# Trend Intelligence Report

**Generated:** 2026-06-23 (rev.3) · RT AI Safety Assurance Platform · Phase C synthesis

Emerging topics, organizational/citation trends, maturity shifts, and cycle-over-cycle deltas
computed from `graph.json.trends` and the run snapshots in `dashboard/data/runs/`.

## 0. Corpus growth (snapshot delta)

| 날짜 | 노드 | 엣지 | 소스(전체) | 위협 | 뉴스 |
|---|---|---|---|---|---|
| 2026-06-19 | 1,322 | 7,840 | ? | ? | 5 |
| 2026-06-20 | 1,381 | 8,030 | 274 | 62 | 222 |
| 2026-06-21 | 2,259 | 12,309 | 385 | 72 | 222 |
| 2026-06-22 | 2,536 | 14,141 | 419 | 74 | 230 |
| 2026-06-23 | 4,069 | 23,337 | 556 | 219 | 230 |
| 2026-06-23 (venue) | 4,069 | 23,337 | 344(논문) | 153 | 230 |

Recent cycles added framework integration (ATLAS · ATT&CK · OWASP LLM · NIST RMF/GenAI · FMF), an
AISI/EU/Israel news sweep, and a **three-stage literature sweep — 157 papers read in full**: 86 latest
arXiv preprints (2026-03–06) + **71 peer-reviewed conference/journal papers** (IEEE S&P · ACL · NDSS ·
ICML · ICLR · AAAI · USENIX · CCS · EMNLP · NAACL · ICCV · CVPR · ECCV · IEEE TPAMI/TDSC/TIFS · TACL,
2024–2026, incl. canonical 2024 works up to 644 citations). Together they grew the graph from ~2,360
to **4,069 nodes** and paper sources from 187 to **344**. See the
[Red-Teaming Literature report](redteam-literature-2026q2.md) (🇰🇷 [한국어](redteam-literature-2026q2-ko.md)).

## 1. Emerging topics (mean novelty × count)

| 순위 | 주제 | 빈도 | novelty |
|---|---|---|---|
| 1 | `prompt-attack` | 294 | 0.67 |
| 2 | `safety.misuse-risk` | 271 | 0.65 |
| 3 | `model.jailbreak` | 226 | 0.65 |
| 4 | `model.prompt-injection` | 137 | 0.72 |
| 5 | `tool-attack` | 118 | 0.75 |
| 6 | `topic:frontier-safety` | 113 | 0.76 |
| 7 | `agent.tool-abuse` | 113 | 0.74 |
| 8 | `agentic.autonomy-risk` | 111 | 0.74 |
| 9 | `safety.cyber-risk` | 110 | 0.72 |
| 10 | `llm-as-a-judge` | 114 | 0.68 |
| 11 | `autonomous-attack` | 96 | 0.74 |
| 12 | `agentic.tool-risk` | 94 | 0.72 |

## 2. Venue distribution (peer-reviewed papers)

| venue | 논문 수 |
|---|---|
| EMNLP 2024 | 7 |
| ICML 2025 | 5 |
| ACL 2025 | 4 |
| AAAI 2026 | 4 |
| EMNLP 2025 | 4 |
| ACL 2024 | 4 |
| NAACL 2024 | 4 |
| USENIX Security 2025 | 3 |
| CVPR 2024 | 3 |
| AAAI 2025 | 2 |
| ICML | 2 |
| NDSS Symposium 2026 | 2 |

The venue sweep anchors the arXiv frontier to vetted, high-citation prior work spanning NLP (ACL/EMNLP/
NAACL), ML (ICML/ICLR/AAAI), security (IEEE S&P/NDSS/USENIX/CCS) and vision (CVPR/ICCV/ECCV) venues —
top additions include How-Johnny-Can-Persuade (PAP, ACL, 644 cit), InjecAgent (ACL, 380), ArtPrompt
(ACL, 257), and DataSentinel (IEEE S&P, 118).

## 3. Maturity & literature mix

The corpus skews **emerging** over **established**; the venue sweep added a peer-reviewed, higher-
citation layer. 157 papers read in full this campaign (86 arXiv + 71 venue) yielding **773 extracted
records** — 296 findings, 115 attack techniques, 93 vulnerabilities, 74 candidate threat classes,
123 controls, 47 risks, 25 harms.

## 4. Standards-gap & candidate trend

42 standards-gap entries and 25 candidate proposals remain the headline normative output. The new
literature reinforces: **agentic supply-chain / MCP security**, **adaptive-attack evaluation
methodology** (static benchmarks overestimate defenses; safety-judge FNR can hit 1.00; LLM-as-a-Judge
is itself adversarially attackable), and **multimodal/audio safety coverage** (alignment fails to
generalize across image/audio/shuffle/OOD/cross-modal transforms).

## 5. Real-world intelligence integration

### 5a. Semantic Scholar citation network
**938 source→source edges**. The corpus now contains its own citation foundations — GCG (117
in-corpus citations), PAIR (79), HarmBench (63), TAP (45), Anthropic-HH (33), Llama-3 (32) are the top
in-corpus citation hubs, with the 2026 frontier citing them heavily. Explore in the **Papers** tab.

### 5b. CVE record (NVD-verified)
**CVE-2026-31431 'Copy Fail'** (Linux-kernel LPE, CWE-269) — NVD-verified. All other new
vulnerabilities are research weakness classes mapped to CWEs; older CVEs cited only as benchmark
dataset examples were not added — no CVE numbers invented.

## 6. Cross-framework coverage

Six standard frameworks integrated with corpus-coverage overlays (ATLAS Matrix · MITRE ATT&CK · OWASP
LLM Top 10 · NIST AI RMF · NIST GenAI Profile · FMF) + SOTA leaderboard + MIT AI Risk Repository
(24/24 subdomains).

---
*Computed from `graph.json.trends` + `data/runs/*.json`; reproducible via `build_graph.py`. Literature
stats from `papers-*.jsonl`; citation counts from Semantic Scholar; CVE verified against NVD.*
