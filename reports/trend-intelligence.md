# Trend Intelligence Report

**Generated:** 2026-06-20 · RT AI Safety Assurance Platform · Phase C synthesis

Trend signals are computed from finding `novelty_signal`, source `org`, and finding `maturity` over the current cycle. No prior snapshot exists, so deltas are absolute (first baseline).

## 1. Emerging topics (mean novelty × count)

| Rank | Topic / taxonomy node | Findings | Mean novelty | Emergence score |
|---|---|---|---|---|
| 1 | `misuse-risk` | 171 | 0.606 | 103.7 |
| 2 | `prompt-attack` | 134 | 0.591 | 79.23 |
| 3 | `model.jailbreak` | 111 | 0.569 | 63.21 |
| 4 | `cyber-risk` | 80 | 0.707 | 56.55 |
| 5 | `autonomy-risk` | 65 | 0.724 | 47.07 |
| 6 | `alignment-risk` | 62 | 0.745 | 46.21 |
| 7 | `devsecops` | 68 | 0.666 | 45.26 |
| 8 | `tool-risk` | 61 | 0.712 | 43.44 |
| 9 | `capability-risk` | 62 | 0.693 | 42.99 |
| 10 | `frontier-safety` | 50 | 0.795 | 39.77 |
| 11 | `model.prompt-injection` | 57 | 0.673 | 38.37 |
| 12 | `agent.tool-abuse` | 49 | 0.725 | 35.52 |
| 13 | `autonomous-attack` | 49 | 0.711 | 34.84 |
| 14 | `societal-risk` | 62 | 0.55 | 34.07 |
| 15 | `human-factors-risk` | 49 | 0.565 | 27.68 |

The highest-novelty nodes are **agentic and frontier**: `agent.tool-abuse` and `cyber-risk` both score mean-novelty 0.79, and the future-teaming frontier (MCP/A2A security, continuous red teaming, safety-case automation) drives the long tail — confirming the platform's thesis that the live edge of red teaming has moved from model jailbreaks to tool-using agents.

## 2. Org / publication trend

Who is publishing most this cycle (source + finding attribution):

| Org | Records |
|---|---|
| Anthropic | 58 |
| OpenAI | 38 |
| Google DeepMind | 29 |
| NIST NVD | 16 |
| Center for AI Safety | 14 |
| NVIDIA | 13 |
| Meta AI (FAIR) | 11 |
| Meta | 10 |
| Canadian Institute for Cybersecurity (UNB) | 9 |
| ETH Zurich | 9 |
| Microsoft | 9 |
| Gray Swan AI / UK AI Safety Institute | 7 |
| Stanford University | 7 |
| xAI | 7 |
| Microsoft (Azure) | 6 |

## 3. Maturity distribution

| Maturity | Findings |
|---|---|
| emerging | 122 |
| established | 118 |
| future | 11 |
| unknown | 21 |

The corpus is barbell-shaped: 118 established methods (the measured benchmark baseline) vs 122 emerging + 11 future findings (the frontier the standards candidates target). The `future`-maturity findings map almost one-to-one onto the open standard candidates, showing the standardization backlog is being driven by method maturity, not the reverse.

## 4. Standards-gap trend

- Open gaps this cycle: **18**
- Standard candidates surfaced: **9**
- The gap set is concentrated on agentic/tool-use, MCP/A2A trust, continuous red teaming, LLM-as-judge validity, CVD/VDP, and sector verticals — the same clusters that top the emergence ranking.

## 5. Newly ingested PDF corpus (this cycle)

This cycle added **118 PDF papers** to the corpus, yielding **239 findings** (`pdf-find-*.jsonl`). The papers and their source→source citation arrays added new edges into the citation graph (402 citations resolved into existing corpus nodes; 21 created lightweight referenced-source nodes for 21 papers cited but not themselves ingested).

**Dominant topics across the new findings** (by taxonomy axis, finding count):

| Taxonomy node | Findings |
|---|---|
| `safety:misuse-risk` | 83 |
| `attack:prompt-attack` | 66 |
| `threat:model.jailbreak` | 49 |
| `safety:societal-risk` | 45 |
| `se:devsecops` | 44 |
| `safety:cyber-risk` | 39 |
| `safety:capability-risk` | 33 |
| `safety:human-factors-risk` | 31 |
| `agentic:tool-risk` | 30 |
| `agentic:autonomy-risk` | 29 |

The new corpus is dominated by **system-level / agentic red teaming** (`agentic:tool-risk`, `attack:autonomous-attack`, `teaming:llm-as-a-attacker`), **misuse and product-feature abuse** (`safety:misuse-risk`, `safety:societal-risk`), and **disclosure / incident-reporting** themes — a shift from single-turn model jailbreaks toward tool-using coding agents, automated red-teaming pipelines, and coordinated vulnerability disclosure. Representative source ids: `acm-aisec25-ai-cve`, `arxiv-2204-05862`, `arxiv-2212-08073`, `arxiv-2310-02446`, `arxiv-2310-06474`, `arxiv-2311-05608`, `arxiv-2311-08268`, `arxiv-2402-07867` (+110 more).

### 5a. Thematic map of the expanded PDF corpus

The ~118 ingested papers cluster into six research fronts. Each front is cited by `pdf-find-*` findings and every id below resolves to a `source` record in the graph bundle.

## 6. Real-world intelligence integration (this cycle)

Beyond the paper corpus, this cycle wires the graph into **live external intelligence**: a real citation network, the AI-specific CVE record, a patient-safety lens, and deep links into maintained external catalogs.

### 6a. Real Semantic Scholar citation network

arXiv sources now carry **real Semantic Scholar** `s2_id` / `citation_count` and resolved `cites` / `cited_by` arrays. These project into **201 intra-corpus `source —cites→ source` edges** — a genuine citation graph linking the platform's own papers, not a synthetic one. The most-cited papers in the corpus (by S2 citation_count):

| Citations | Paper | Source id |
|---|---|---|
| 16,176 | The Llama 3 Herd of Models | [`arxiv-2407-21783`](https://arxiv.org/abs/2407.21783) |
| 4,131 | Training a Helpful and Harmless Assistant with Reinforcement Learning  | [`arxiv-2204-05862`](https://arxiv.org/abs/2204.05862) |
| 3,702 | Gemini 1.5: Unlocking multimodal understanding across millions of toke | [`arxiv-2403-05530`](https://arxiv.org/abs/2403.05530) |
| 3,263 | Gemini 2.5: Pushing the Frontier with Advanced Reasoning, Multimodalit | [`mc-src-gemini-2-5-report`](https://arxiv.org/abs/2507.06261) |
| 3,199 | Universal and Transferable Adversarial Attacks on Aligned Language Mod | [`arxiv-2307-15043`](https://arxiv.org/abs/2307.15043) |
| 3,173 | Constitutional AI: Harmlessness from AI Feedback | [`arxiv-2212-08073`](https://arxiv.org/abs/2212.08073) |
| 1,497 | Jailbreaking Black Box Large Language Models in Twenty Queries (PAIR) | [`arxiv-2310-08419`](https://arxiv.org/abs/2310.08419) |
| 1,448 | A Survey on LLM-as-a-Judge | [`arxiv-2411-15594`](https://arxiv.org/abs/2411.15594) |

The headline anchors — **The Llama 3 Herd of Models** (16,176), **Universal and Transferable Adversarial Attacks / GCG** (3,199), and **Constitutional AI** (`arxiv-2212-08073`, 3,173) — span the frontier-model, attack, and alignment poles of the field, and each is reachable as a node in the citation subgraph.

### 6b. Real AI CVE record

The CVE reference catalog (`ext-cve`) deep-links **16 real AI CVEs** (NVD entries) into the graph via `reference —details→ vulnerability` edges, and the corpus carries **34 CVE/CWE-bearing vulnerability records**. Representative entries:

| CVE | Description | Maps to |
|---|---|---|
| [CVE-2024-37032](https://nvd.nist.gov/vuln/detail/CVE-2024-37032) | Ollama 'Probllama' digest path-traversal RCE (8.8 HIGH, CWE-22) | `vuln-cve-2024-37032-ollama-probllama` |
| [CVE-2024-7773](https://nvd.nist.gov/vuln/detail/CVE-2024-7773) | Ollama Zip-Slip RCE in GGUF zip import (CWE-22) | `vuln-cve-2024-7773-ollama-zipslip` |
| [CVE-2024-39722](https://nvd.nist.gov/vuln/detail/CVE-2024-39722) | Ollama api/push path-traversal file-existence disclosure (CWE-22) | `vuln-cve-2024-39722-ollama-fileexist` |
| [CVE-2025-62164](https://nvd.nist.gov/vuln/detail/CVE-2025-62164) | vLLM tensor-deserialization memory corruption / RCE (8.8 HIGH, CWE-502 | `vuln-cve-2025-62164-vllm-tensor-deser` |
| [CVE-2025-32434](https://nvd.nist.gov/vuln/detail/CVE-2025-32434) | PyTorch torch.load RCE despite weights_only=True (9.8 CRITICAL, CWE-50 | `vuln-cve-2025-32434-pytorch-torchload` |
| [CVE-2024-3568](https://nvd.nist.gov/vuln/detail/CVE-2024-3568) | HuggingFace Transformers pickle RCE in load_repo_checkpoint (CWE-502) | `vuln-cve-2024-3568-transformers-pickle` |

### 6c. Patient-safety lens

A clinical / patient-safety lens now spans **16 healthcare-sector findings**, grounding the harm taxonomy in real medical-AI failure modes: the **Epic Sepsis Model** external-validation shortfall, clinician **deskilling / automation bias**, and **pulse-oximeter racial bias**. These connect to the WHO LMM and FDA MAUDE reference catalogs and to diagnostic-error / harmful-treatment harm nodes.

### 6d. External-repository deep-link integration

Reference catalogs (§6.3) deep-link maintained external repositories into the graph; each catalog item carries an `ext_id` + `url` and maps to one or more in-corpus nodes (**292 `reference —details→ node` edges** total):

| External catalog | Items | Framework |
|---|---|---|
| [MIT AI Risk Repository](https://airisk.mit.edu/) | 24 | risk-taxonomy |
| [LLM SOTA Dashboard](https://hollobit.github.io/SOTA/) | 22 | benchmark-leaderboard |
| [CVE / NVD](https://www.cve.org/) | 16 | attack-kb |
| [OWASP Agentic AI — Threats and Mitigations (Top 15)](https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/) | 15 | standard |
| [NIST AI Risk Management Framework (AI RMF 1.0)](https://airc.nist.gov/airmf-resources/airmf/) | 14 | regulation |
| [OECD AI Incidents Monitor (AIM)](https://oecd.ai/en/incidents) | 12 | incident-db |
| [MITRE ATLAS](https://atlas.mitre.org/) | 11 | attack-kb |
| [OWASP Top 10 for LLM Applications (2025)](https://genai.owasp.org/llm-top-10/) | 10 | standard |
| [FDA MAUDE — Manufacturer and User Facility Device Experience](https://www.accessdata.fda.gov/scripts/cdrh/cfdocs/cfMAUDE/search.cfm) | 5 | incident-db |
| [WHO — Patient Safety & AI-for-Health Governance](https://www.who.int/teams/integrated-health-services/patient-safety) | 4 | regulation |

These span the **MIT AI Risk Repository** (24 subdomains), **OECD AIM** incident monitor, **MITRE ATLAS**, **OWASP LLM Top-10**, **NIST AI RMF**, **CWE**, and the clinical FDA-MAUDE / WHO-LMM catalogs — making the graph a routing layer into authoritative external sources rather than a closed silo.

| Research front | Papers | Representative source ids |
|---|---|---|
| Red-teaming roadmaps & methodology | 5 | `arxiv-2204-05862`, `arxiv-2212-08073`, `arxiv-2506-05376`, `arxiv-2507-05538`, `elsevier-algorithmic-redteam-llm` |
| Agentic & automated red teaming | 8 | `arxiv-2311-08268`, `arxiv-2404-01833`, `arxiv-2410-05295`, `arxiv-2512-20677`, `arxiv-2602-02164`, `arxiv-2604-23067`, `arxiv-2605-04019`, `arxiv-2605-11047` |
| CVD/VDP & incident reporting | 7 | `acm-aisec25-ai-cve`, `arxiv-2509-06136`, `belfer-attacking-ai-2019`, `cdr-hathaway`, `ceur-tethics2024-ai-vuln`, `cset-ai-incidents`, `elsevier-cvd-effectiveness` |
| Multimodal / multilingual / RAG security | 6 | `arxiv-2310-02446`, `arxiv-2310-06474`, `arxiv-2311-05608`, `arxiv-2402-07867`, `arxiv-2404-03027`, `arxiv-2502-17832` |
| Defenses & eval science | 10 | `arxiv-2403-03218`, `arxiv-2406-04313`, `arxiv-2411-15594`, `arxiv-2412-09565`, `arxiv-2502-05209`, `arxiv-2505-22037`, `arxiv-2508-18076`, `arxiv-2510-07192`, `arxiv-2602-19450`, `arxiv-2603-25176` |
| Autonomous cyber red teaming | 7 | `arxiv-2408-08926`, `arxiv-2410-07283`, `arxiv-2501-13411`, `arxiv-2505-15216`, `arxiv-2508-14925`, `arxiv-2509-05755`, `arxiv-2605-17075` |

- **Red-teaming roadmaps & methodology.** System-level red-teaming roadmaps and sociotechnical / lifecycle framings that move the discipline from ad-hoc jailbreak hunting toward governed, purple-team programs. Sources: [arxiv-2204-05862](https://arxiv.org/abs/2204.05862), [arxiv-2212-08073](https://arxiv.org/abs/2212.08073), [arxiv-2506-05376](https://arxiv.org/abs/2506.05376), [arxiv-2507-05538](https://arxiv.org/abs/2507.05538), [elsevier-algorithmic-redteam-llm](https://doi.org/10.1016/j.mlwa.2025.100815).
- **Agentic & automated red teaming.** Automated attacker agents, strategy self-exploration, multi-turn crescendo/nesting, and orchestrated discovery-and-exploitation pipelines that compress red-team cycles from weeks to hours. Sources: [arxiv-2311-08268](https://arxiv.org/abs/2311.08268), [arxiv-2404-01833](https://arxiv.org/abs/2404.01833), [arxiv-2410-05295](https://arxiv.org/abs/2410.05295), [arxiv-2512-20677](https://arxiv.org/abs/2512.20677), [arxiv-2602-02164](https://arxiv.org/abs/2602.02164), [arxiv-2604-23067](https://arxiv.org/abs/2604.23067), [arxiv-2605-04019](https://arxiv.org/abs/2605.04019), [arxiv-2605-11047](https://arxiv.org/abs/2605.11047).
- **CVD/VDP & incident reporting.** Coordinated vulnerability disclosure, AI-CVE readiness, mandatory incident-reporting regimes, and the finding that abuse risks are often inherent to product features. Sources: [acm-aisec25-ai-cve](https://doi.org/10.1145/3733799.3762969), [arxiv-2509-06136](https://arxiv.org/abs/2509.06136), [belfer-attacking-ai-2019](https://www.belfercenter.org/publication/AttackingAI), [cdr-hathaway](https://doi.org/10.55682/cdr/e6jp-te5c), [ceur-tethics2024-ai-vuln](https://ceur-ws.org/Vol-3901/paper_3.pdf), [cset-ai-incidents](https://cset.georgetown.edu/), [elsevier-cvd-effectiveness](https://doi.org/10.1016/j.cose.2022.102936).
- **Multimodal / multilingual / RAG security.** Vision-language typographic jailbreaks, low-resource / cross-lingual safety failures, and retrieval-augmented-generation knowledge-base poisoning (incl. multimodal RAG). Sources: [arxiv-2310-02446](https://arxiv.org/abs/2310.02446), [arxiv-2310-06474](https://arxiv.org/abs/2310.06474), [arxiv-2311-05608](https://arxiv.org/abs/2311.05608), [arxiv-2402-07867](https://arxiv.org/abs/2402.07867), [arxiv-2404-03027](https://arxiv.org/abs/2404.03027), [arxiv-2502-17832](https://arxiv.org/abs/2502.17832).
- **Defenses & eval science.** Circuit-breakers / representation rerouting, machine unlearning (WMDP), model-tampering evaluations, LLM-as-judge validity and benchmark-contamination critiques — the measurement-science backbone for credible assurance claims. Sources: [arxiv-2403-03218](https://arxiv.org/abs/2403.03218), [arxiv-2406-04313](https://arxiv.org/abs/2406.04313), [arxiv-2411-15594](https://arxiv.org/abs/2411.15594), [arxiv-2412-09565](https://arxiv.org/abs/2412.09565), [arxiv-2502-05209](https://arxiv.org/abs/2502.05209), [arxiv-2505-22037](https://arxiv.org/abs/2505.22037), [arxiv-2508-18076](https://arxiv.org/abs/2508.18076), [arxiv-2510-07192](https://arxiv.org/abs/2510.07192), [arxiv-2602-19450](https://arxiv.org/abs/2602.19450), [arxiv-2603-25176](https://arxiv.org/abs/2603.25176).
- **Autonomous cyber red teaming.** CTF / penetration-testing / bug-bounty agent benchmarks (Cybench, VulnBot, BountyBench), MCP tool-poisoning, coding-agent tool-invocation attacks, and autonomous SOAR/kill-chain robustness evaluation. Sources: [arxiv-2408-08926](https://arxiv.org/abs/2408.08926), [arxiv-2410-07283](https://arxiv.org/abs/2410.07283), [arxiv-2501-13411](https://arxiv.org/abs/2501.13411), [arxiv-2505-15216](https://arxiv.org/abs/2505.15216), [arxiv-2508-14925](https://arxiv.org/abs/2508.14925), [arxiv-2509-05755](https://arxiv.org/abs/2509.05755), [arxiv-2605-17075](https://arxiv.org/abs/2605.17075).

## Current-frontier cards & technical-report safety analyses

The corpus tracks the **current frontier** through vendor system cards. Each card below is a real `model_card` record (`mc-*`) resolving to its published source:

| Current-frontier card | Model-card id | Org | Source |
|---|---|---|---|
| GPT-5 System Card (+ GPT-5.2 update) | `mc-gpt5-system-card` | OpenAI | [openai-gpt5-system-card-2025](https://cdn.openai.com/gpt-5-system-card.pdf) |
| Claude Sonnet 4.5 System Card | `mc-claude-sonnet45-system-card` | Anthropic | [anthropic-claude-sonnet45-card-2025](https://www.anthropic.com/claude-sonnet-4-5-system-card) |
| Claude Opus 4.5 System Card | `mc-claude-opus45-system-card` | Anthropic | [anthropic-claude-opus45-card-2025](https://www-cdn.anthropic.com/bf10f64990cfda0ba858290be7b8cc6317685f47/Claude%20Opus%204.5%20System%20Card.pdf) |
| Gemini 3 Pro Frontier Safety Framework Report | `mc-gemini3-pro-fsf` | Google DeepMind | [google-gemini3-pro-fsf-2025](https://storage.googleapis.com/deepmind-media/gemini/gemini_3_pro_fsf_report.pdf) |

Beyond vendor system cards, the corpus now distills the **safety sections of primary technical reports** into findings — the measurement detail behind the headline threshold verdicts. Each row cites a `find-*` record resolving to its report source:

| Technical-report safety analysis | Finding id | Source |
|---|---|---|
| Llama 3 Herd — cyber + CBRN **uplift study** finds no significant capability uplift; CyberSecEval bounds offensive-cyber risk | `find-llama3-cyber-cbrn-uplift-low` | [arxiv-2407-21783](https://arxiv.org/abs/2407.21783) |
| Llama 3 — safety finetuning trades Violation Rate vs False-Refusal Rate with size-dependent safety-data mixes | `find-llama3-vr-frr-safety-finetuning` | [arxiv-2407-21783](https://arxiv.org/abs/2407.21783) |
| Gemini 1.5 — **dangerous-capability evaluations** clear cyber / self-proliferation / CBRN / persuasion with no critical threshold crossed | `find-gemini15-dangerous-capability-evals` | [arxiv-2403-05530](https://arxiv.org/abs/2403.05530) |
| Phi-4 — two-week Microsoft **AI Red Team (AIRT)** exercise; GCG suffixes from phi-3-medium do not transfer to phi-4 | `find-phi4-airt-redteam-gcg-nontransfer` | [arxiv-2412-08905](https://arxiv.org/abs/2412.08905) |
| Nemotron-4 340B — safety triangulates **AEGIS** content-safety, Garak scanning, and human red teaming | `find-nemotron4-aegis-garak-human-redteam` | [arxiv-2406-11704](https://arxiv.org/abs/2406.11704) |
| Kimi K2 — LLM-attacker/judge RL loop plus Promptfoo automated red-teaming across attack strategies | `find-kimi-k2-promptfoo-attacker-judge-loop` | [arxiv-2507-20534](https://arxiv.org/abs/2507.20534) |
| GLM-4.5 — technical report reports only SafetyBench MCQ scores: a dangerous-capability **disclosure gap** | `find-glm45-safetybench-only-gap` | [arxiv-2508-06471](https://arxiv.org/abs/2508.06471) |

These technical-report analyses anchor the frontier-card verdicts in **reproducible evaluation methodology** (uplift studies, GCG-transfer tests, multi-tool red-team triangulation) rather than vendor summaries alone — the GLM-4.5 SafetyBench-only case marks the open-weight transparency floor against which the others are measured.

## SOTA leaderboard integration & MIT-AI-Risk-Repository risk classification

This cycle adds the **`ext-sota` reference** (hollobit/SOTA frontier benchmark dashboard, `https://hollobit.github.io/SOTA/#overview`) as a first-class external framework node. Its leaderboard tracks **38 benchmarks**; **22** carry a `maps_to` crosswalk into the corpus, resolving to **24 distinct in-corpus benchmark nodes** via `ext-sota —details→ bench:*` edges (e.g. `HarmBench`, `JailbreakBench`, `StrongREJECT`, `CyberSecEval`, `WMDP`, `AgentDojo`, `SWE-bench`). Each edge stashes the live SOTA score/model (e.g. HarmBench 3.1% with `anthropic/claude-opus-4.7`) so the dashboard SOTA panel deep-links every safety benchmark in the corpus to its current frontier result.

Risk classification is grounded in the **MIT AI Risk Repository** via the `ext-mit-airisk` reference node (24 repository items emitting 81 `details` edges that map the repository's risk domains onto the corpus `safety.*` taxonomy, `harm-*`, and `vuln-*` nodes), anchoring the safety-risk axis of the trend ranking above to an external, peer-reviewed taxonomy rather than an ad-hoc scheme.

**MIT 24/24 subdomain coverage (v9).** The MIT-gap pass adds **15 new `societal.*` threat nodes** to close the repository's societal-impact subdomains that the technical-safety corpus previously under-covered, bringing coverage to **24/24 MIT AI Risk Repository subdomains** (all 24 `ext-mit-airisk` items now resolve to in-corpus nodes). The added societal risks include `societal.discrimination`, `societal.misinformation`, `societal.overreliance`, `societal.power-concentration`, `societal.inequality-labor` (labor displacement) and `societal.environmental-harm`, plus governance and information-ecosystem risks (`societal.governance-failure`, `societal.info-ecosystem-pollution`, `societal.autonomy-loss`). These move the trend lens beyond model/agent attack surface to the full societal-risk frontier the MIT taxonomy enumerates.

---
*Computed from `graph.json.trends`; topic scores and org counts are reproducible by re-running `build_graph.py`. PDF-corpus stats from `pdf-find-*.jsonl` + cited source ids; frontier-card / TR rows cite `mc-*` / `find-*` records.*