# Red-Teaming Literature Intelligence — 2026 Q2

**Generated:** 2026-06-23 · RT AI Safety Assurance Platform · paper-research-pipeline (rev.2)

A systematic sweep of the **latest red-teaming / AI-safety / AI-security literature** on arXiv,
read in full and distilled into the knowledge graph. **86 papers** spanning **2026-03-19 → 2026-06-18**
(73% from the most recent month) were discovered, downloaded, analyzed by four specialist analysts,
and integrated with strict honesty (verbatim metrics, `^[ambiguous]` flags, no fabricated CVEs).

## 1. Scope & corpus impact

| | Before | After (this sweep) |
|---|---|---|
| Paper sources | 187 | **321** (+134) |
| Graph nodes | 2,360 | **3,806** |
| Attack techniques | 142 | **237** |
| Vulnerabilities | 79 | **152** |
| Threat classes | ~72 | **~200** |
| Controls | 75 | **133** |
| GraphRAG units | 1,731 | **2,464** |
| Citation-network edges | — | **821** (source→source) |

Extracted from the 86 papers: **380 records** — 161 findings, 55 attack techniques, 42 vulnerabilities
(34 distinct CWE classes), 34 candidate threat classes, 58 controls, 21 risks, 9 harms. Quality gates
held throughout: **dangling 0 · isolated 0 · units==embeddings**.

## 2. Key findings by theme

### 2.1 Agent & multi-agent security (dominant area)
- **Supply-chain injection** (`agentic.supply-chain-injection`, ShieldNet) — benign interface + benign I/O,
  malicious behavior **only at network runtime**; static scanners F1 0.03 vs network detection 0.998.
- **Defense inversion** (`agentic.defense-inversion`) — capability-removal defenses *create* new attack
  paths (hallucination bypass, multi-key normalization); input/retrieval-layer defenses ~89% ASR, only
  memory-layer tool-gating reached 0%.
- **Cross-session memory persistence / poisoning** — delayed-trigger persistent-memory attacks survive
  most layers; provenance, authorization, inter-agent-trust and topology recur as unsolved gaps.
- **Compositional leakage & resource drain** (Data Agents) — 8 vulnerability families; non-sandboxed
  `exec()` at 100% ASR; cumulative differencing leakage and policy-compliant DoS.
- **Provenance gap** (Context-Fractured Decomposition) — bounded-observability monitors miss cross-session
  artifact intent (+28pp ASR); single-turn judges fail.

### 2.2 Jailbreak — new mechanisms
- **Modality-grounded alignment gap** — CodeSpear (grammar-constrained decoding) and MaskForge (diffusion
  mask-infill) bypass natural-language-grounded alignment via non-NL output spaces (`model.infilling-abuse`).
- **Positional vulnerability** (SlotGCG) — breaks the suffix-bias of GCG; attention-guided slot dispersion, +14% ASR.
- **Multi-turn escalation** (MultiTurnPSB) — medical-AI unsafe rate 35%→79% via an "emergency + authority" formula.
- **Multilingual / cross-modal gap** (MLingualFC) — harmful instructions encoded as multilingual flowchart
  images (`societal.multilingual-safety-gap`).

### 2.3 Frontier & alignment
- **Reasoning self-censoring is trainable away** (AdvGRPO) — defenses relying on inference-time safety checks
  are fundamentally limited (`frontier.reasoning-self-censor-bypass`).
- **MoE safety-expert reprogramming** (RASET) — editing 0.12% of parameters flips alignment (+37.6pt ASR)
  while preserving routing → stealthy to router monitoring.
- **Cyber-offense industrialization** (Koch) — "attack compression": kill-chain cost collapses with no new
  attack class (`agentic.attack-compression`).

### 2.4 Privacy, integrity & domain harm
- **Cumulative inference leakage** (OCELOT) — individually-benign releases reconstruct secrets; per-release
  filters are structurally insufficient.
- **AI peer-review manipulation** — presentation attacks erode research integrity.
- **Deployment safety ≠ test accuracy** — medical (SafeMed-R1) and physical/robot (Red/Blue) safety.

### 2.5 Methodology meta-findings
- Static benchmarks **overestimate** defenses by 15.8pp vs adaptive attacks (RETA); synthetic→real-document
  generalization fails (PARSE).
- Automated agentic auditing reaches **CVE-grade real-world impact** (EVOHUNT: 28 confirmed OSS vulns +
  $1,500 bounty; identifiers redacted pending coordinated disclosure → recorded as CWE-class).

## 3. New threat classes (60 candidate)
- **agent.** (3): `agent.routing-manipulation` · `agent.prompt-injection-indirect` · `agent.tool-selection-manipulation`
- **agentic.** (29): `agentic.provenance-gap` · `agentic.data-agent-risk` · `agentic.compositional-leakage` · `agentic.resource-exhaustion` · `agentic.internal-relay-leakage` · `agentic.multi-agent-propagation` · `agentic.emergent-misalignment` · `agentic.memory-poisoning-drift` · `agentic.multi-agent-prompt-contagion` · `agentic.embodied-interactive-safety-risk` · `agentic.cross-session-memory-persistence` · `agentic.decision-layer-poisoning` · `agentic.mediation-bypass` · `agentic.rag-poisoning` · `agentic.defense-inversion` · `agentic.inter-agent-comm-mitm` · `agentic.mcp-preference-manipulation` · `agentic.mcp-attack-taxonomy` · `agentic.mcp-shared-context-chain` · `agentic.plan-execute-integrity-subversion` · `agentic.privilege-usage` · `agentic.contextual-authorization` · `agentic.context-fragmented-violation` · `agentic.semantic-laundering` · `agentic.argument-authority-binding` · `agentic.cognitive-poisoning` · `agentic.attack-compression` · `agentic.cross-layer-propagation` · `agentic.supply-chain-injection`
- **automated.** (1): `automated.injection-reformulation`
- **frontier.** (3): `frontier.cognitive-monoculture` · `frontier.reasoning-self-censor-bypass` · `frontier.reasoning-model-risk`
- **model.** (6): `model.reasoning-trace-leakage` · `model.over-refusal` · `model.rag-poisoning` · `model.adversarial-example` · `model.infilling-abuse` · `model.multi-turn-attack`
- **multimodal.** (6): `multimodal.safety-comprehension-gap` · `multimodal.ood-distribution-shift` · `multimodal.vision-centric-context-injection` · `multimodal.cross-modal-attack-distribution` · `multimodal.cross-modal-synergy-perturbation` · `multimodal.foundation-encoder-super-transfer`
- **safety.** (3): `safety.benchmark-validity-risk` · `safety.evaluation-gaming-sandbagging` · `safety.detector-evasion`
- **scientific.** (1): `scientific.cyber-physical-safety`
- **societal.** (4): `societal.opinion-manipulation` · `societal.eval-integrity` · `societal.multilingual-safety-gap` · `societal.medical-harm`
- **software.** (4): `software.vulnerability-detection-gap` · `software.rapid-response-pipeline-poisoning` · `software.code-sabotage` · `software.code-poisoning`
## 4. CVE / vulnerability disclosure
- **CVE-2026-31431 'Copy Fail'** — Linux-kernel local privilege escalation (CWE-269, high), cited by the
  cyber-offense forecast paper and **independently verified via the NVD API** (vulnStatus *Analyzed*,
  published 2026-04-22). cve.org is JS-rendered so NVD's JSON API was used.
- The other 42 new vulnerabilities are **research weakness classes** mapped to **34 distinct CWEs**
  (e.g. CWE-94, CWE-269, CWE-285, CWE-400, CWE-693, CWE-863, CWE-1427) — not product CVEs. No CVE numbers
  were invented; redacted/partial identifiers are recorded as `^[ambiguous]`.

## 5. Citation-network & influence analysis (Semantic Scholar)
New June-2026 papers carry **0 citations** (too recent to accumulate impact) but are **well-grounded in the
canonical red-teaming literature** the corpus already holds — the most-cited foundations among the new work:

| 피인용(신규논문 중) | 총 citations | 기초 논문 |
|---|---|---|
| 23편 | 3199 | Universal and Transferable Adversarial Attacks on Align |
| 20편 | 1497 | Jailbreaking Black Box Large Language Models in Twenty  |
| 16편 | 1227 | HarmBench: A Standardized Evaluation Framework for Auto |
| 13편 | 669 | Tree of Attacks: Jailbreaking Black-Box LLMs Automatica |
| 9편 | 342 | Great, Now Write an Article About That: The Crescendo M |
| 9편 | 282 | AgentHarm: A Benchmark for Measuring Harmfulness of LLM |
| 9편 | ? | Qwen3 Technical Report |
| 8편 | 16176 | The Llama 3 Herd of Models |

Citation enrichment added **644 source→source edges**, weaving the new papers into the Papers-tab citation
network. This confirms the new literature builds on (rather than ignores) the established canon.


## 5.5 Peer-reviewed venue sweep (48 papers, 2025–2026)

Beyond arXiv preprints, a Semantic-Scholar venue-filtered sweep added **48 peer-reviewed
conference/journal papers** (IEEE S&P, ACL, NDSS, ICML, ICLR, AAAI, USENIX Security, CCS, EMNLP,
ICCV, CVPR, IEEE TPAMI/TDSC/TIFS) — higher-citation, vetted prior work (up to 118 citations).

**Venue distribution:**

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

Key venue findings: **MCP/agent security** (MPMA preference manipulation, SAGA ProVerif-verified
governance, MCPXKIT, AgentSentinel); **multimodal jailbreak** (SI-Attack shuffle-inconsistency,
JOOD out-of-distribution, VisCo vision-centric injection, X-Transfer CLIP super-transferable UAP —
a shared-encoder supply-chain single-point-of-failure); **evaluation integrity** (Chatbot-Arena
re-ranking for ~$440; safety-judge FNR driven 0.02→1.00); and **provable defenses** (DataSentinel
game-theoretic detection, MELON masked re-execution, IPIGuard tool-dependency graph). New multimodal
threat classes: `multimodal.safety-comprehension-gap`, `multimodal.ood-distribution-shift`,
`multimodal.foundation-encoder-super-transfer`, `multimodal.vision-centric-context-injection`, and
`societal.eval-integrity`.

### Analyzed venue papers (48)

| 인용 | 연도 | venue | 제목 |
|---|---|---|---|
| 118 | 2025 | IEEE Symposium on Security and Pri | [2504.11358](https://arxiv.org/abs/2504.11358) DataSentinel: A Game-Theoretic Detection of Prompt |
| 104 | 2025 | Annual Meeting of the Association  | [2502.14847](https://arxiv.org/abs/2502.14847) Red-Teaming LLM Multi-Agent Systems via Communicat |
| 97 | 2025 | Network and Distributed System Sec | [2504.19793](https://arxiv.org/abs/2504.19793) Prompt Injection Attack to Tool Selection in LLM A |
| 97 | 2025 | IJCNLP-AACL | [2502.12659](https://arxiv.org/abs/2502.12659) The Hidden Risks of Large Reasoning Models: A Safe |
| 65 | 2025 | International Conference on Machin | [2501.18052](https://arxiv.org/abs/2501.18052) SAeUron: Interpretable Concept Unlearning in Diffu |
| 61 | 2025 | Proceedings of the AAAI/ACM Confer | [2502.06559](https://arxiv.org/abs/2502.06559) Can We Trust AI Benchmarks? An Interdisciplinary R |
| 48 | 2025 | IEEE International Conference on C | [2501.04931](https://arxiv.org/abs/2501.04931) Jailbreaking Multimodal Large Language Models via  |
| 47 | 2025 | Annual Meeting of the Association  | [2502.11127](https://arxiv.org/abs/2502.11127) G-Safeguard: A Topology-Guided Security Lens and T |
| 47 | 2025 | International Conference on Machin | [2502.05174](https://arxiv.org/abs/2502.05174) MELON: Provable Defense Against Indirect Prompt In |
| 45 | 2025 | Journal of King Saud University: C | [2505.01976](https://arxiv.org/abs/2505.01976) A survey on privacy risks and protection in large  |
| 42 | 2025 | Annual Meeting of the Association  | [2503.03586](https://arxiv.org/abs/2503.03586) Benchmarking LLMs and LLM-based Agents in Practica |
| 38 | 2025 | Conference on Empirical Methods in | [2502.19820](https://arxiv.org/abs/2502.19820) Foot-In-The-Door: A Multi-turn Jailbreak for LLMs |
| 35 | 2025 | Network and Distributed System Sec | [2504.21034](https://arxiv.org/abs/2504.21034) SAGA: A Security Architecture for Governing AI Age |
| 35 | 2025 | Computer Vision and Pattern Recogn | [2503.20823](https://arxiv.org/abs/2503.20823) Playing the Fool: Jailbreaking LLMs and Multimodal |
| 34 | 2025 | Conference on Empirical Methods in | [2508.15310](https://arxiv.org/abs/2508.15310) IPIGuard: A Novel Tool Dependency Graph-Based Defe |
| 34 | 2025 | AAAI Conference on Artificial Inte | [2505.11154](https://arxiv.org/abs/2505.11154) MPMA: Preference Manipulation Attack Against Model |
| 32 | 2025 | Network and Distributed System Sec | [2504.20984](https://arxiv.org/abs/2504.20984) ACE: A Security Architecture for LLM-Integrated Ap |
| 32 | 2025 | IEEE transactions on intelligent t | [2501.15850](https://arxiv.org/abs/2501.15850) LLM-Attacker: Enhancing Closed-Loop Adversarial Sc |
| 31 | 2025 | Annual Meeting of the Association  | [2505.17147](https://arxiv.org/abs/2505.17147) MTSA: Multi-turn Safety Alignment for LLMs through |
| 27 | 2025 | International Conference on Learni | [2502.03052](https://arxiv.org/abs/2502.03052) Understanding and Enhancing the Transferability of |
| 26 | 2025 | International Conference on Machin | [2502.01633](https://arxiv.org/abs/2502.01633) Adversarial Reasoning at Jailbreaking Time |
| 26 | 2025 | Annual Meeting of the Association  | [2504.00218](https://arxiv.org/abs/2504.00218) Agents Under Siege: Breaking Pragmatic Multi-Agent |
| 26 | 2025 | AAAI Conference on Artificial Inte | [2506.16402](https://arxiv.org/abs/2506.16402) IS-Bench: Evaluating Interactive Safety of VLM-Dri |
| 26 | 2025 | IEEE Transactions on Dependable an | [2508.12538](https://arxiv.org/abs/2508.12538) MCPXKIT: the Unified Toolkit for Analyzing Model C |
| 25 | 2025 | IEEE Transactions on Pattern Analy | [2506.23844](https://arxiv.org/abs/2506.23844) A Survey on Autonomy-Induced Security Risks in Lar |
| 24 | 2025 | Annual Meeting of the Association  | [2504.01550](https://arxiv.org/abs/2504.01550) Representation Bending for Large Language Model Sa |
| 24 | 2025 | USENIX Security Symposium | [2502.01386](https://arxiv.org/abs/2502.01386) Topic-FlipRAG: Topic-Orientated Adversarial Opinio |
| 24 | 2025 | Conference on Empirical Methods in | [2507.02844](https://arxiv.org/abs/2507.02844) Visual Contextual Attack: Jailbreaking MLLMs with  |
| 24 | 2025 | Conference on Computer and Communi | [2502.00306](https://arxiv.org/abs/2502.00306) Riddle Me This! Stealthy Membership Inference for  |
| 24 | 2025 | USENIX Security Symposium | [2507.10695](https://arxiv.org/abs/2507.10695) Exploring User Security and Privacy Attitudes and  |
| 23 | 2025 | International Conference on Machin | [2504.10694](https://arxiv.org/abs/2504.10694) The Jailbreak Tax: How Useful are Your Jailbreak O |
| 22 | 2026 | AAAI Conference on Artificial Inte | [2605.27823](https://arxiv.org/abs/2605.27823) Disentangling Adversarial Prompts: A Semantic-Grap |
| 21 | 2026 | AAAI Conference on Artificial Inte | [2605.26501](https://arxiv.org/abs/2605.26501) Unveiling the Fragility of Vision-Language Models: |
| 21 | 2025 | Conference on Computer and Communi | [2509.07764](https://arxiv.org/abs/2509.07764) AgentSentinel: An End-to-End and Real-Time Securit |
| 20 | 2025 | IEEE transactions on circuits and  | [2506.01307](https://arxiv.org/abs/2506.01307) Align Is Not Enough: Multimodal Universal Jailbrea |
| 20 | 2025 | International Conference on Machin | [2501.07493](https://arxiv.org/abs/2501.07493) Exploring and Mitigating Adversarial Manipulation  |
| 19 | 2025 | International Conference on Machin | [2505.05528](https://arxiv.org/abs/2505.05528) X-Transfer Attacks: Towards Super Transferable Adv |
| 18 | 2025 | IEEE Symposium on Security and Pri | [2501.09798](https://arxiv.org/abs/2501.09798) Fun-tuning: Characterizing the Vulnerability of Pr |
| 17 | 2025 | International Conference on Learni | [2503.04474](https://arxiv.org/abs/2503.04474) Know Thy Judge: On the Robustness Meta-Evaluation  |
| 17 | 2025 | North American Chapter of the Asso | [2505.17332](https://arxiv.org/abs/2505.17332) SweEval: Do LLMs Really Swear? A Safety Benchmark  |
| 16 | 2025 | Conference on Empirical Methods in | [2503.18172](https://arxiv.org/abs/2503.18172) Unmasking Deceptive Visuals: Benchmarking Multimod |
| 16 | 2025 | Network and Distributed System Sec | [2512.07086](https://arxiv.org/abs/2512.07086) ThinkTrap: Denial-of-Service Attacks against Black |
| 16 | 2025 | Conference on Empirical Methods in | [2503.09598](https://arxiv.org/abs/2503.09598) How to Protect Yourself from 5G Radiation? Investi |
| 15 | 2025 | AAAI Conference on Artificial Inte | [2501.16378](https://arxiv.org/abs/2501.16378) Internal Activation Revision: Safeguarding Vision  |
| 14 | 2025 | IEEE Transactions on Information F | [2509.21011](https://arxiv.org/abs/2509.21011) Automatic Red Teaming LLM-Based Agents With Model  |
| 13 | 2025 | International Conference on Learni | [2502.18176](https://arxiv.org/abs/2502.18176) CLIPure: Purification in Latent Space via CLIP for |
| 12 | 2025 | Annual Meeting of the Association  | [2502.18511](https://arxiv.org/abs/2502.18511) ELBA-Bench: An Efficient Learning Backdoor Attacks |
| 12 | 2025 | International Conference on Machin | [2505.24445](https://arxiv.org/abs/2505.24445) Learning Safety Constraints for Large Language Mod |

## 6. Methodology
Reproducible via the **`paper-research-pipeline`** skill: arXiv discovery (dedup vs corpus) → selective PDF
download → 4 specialist analysts read each PDF in full → record validation → CVE linking (NVD) → Semantic
Scholar citation enrichment → graph + embedding re-synthesis → deploy. All scripts under
`.claude/skills/paper-research-pipeline/`.

## 7. Analyzed papers — arXiv preprints (86)

### 2026-06 (63편)

| 날짜 | arXiv | 제목 |
|---|---|---|
| 2026-06-18 | [2606.19887](https://arxiv.org/abs/2606.19887) | FFinRED: An Expert-Guided Benchmark Generation and Evaluation Framework for Fi |
| 2026-06-18 | [2606.19864](https://arxiv.org/abs/2606.19864) | The Almost Intelligent Revolution: Options for Scaling Up Deliberation and Emp |
| 2026-06-18 | [2606.20470](https://arxiv.org/abs/2606.20470) | Analyzing Defensive Misdirection Against Model-Guided Automated Attacks on Age |
| 2026-06-18 | [2606.19755](https://arxiv.org/abs/2606.19755) | SafeSpec: Fast and Safe LLM via Dynamic Reflective Sampling |
| 2026-06-17 | [2606.19660](https://arxiv.org/abs/2606.19660) | A Layered Security Framework Against Prompt Injection in RAG-Based Chatbots |
| 2026-06-17 | [2606.19588](https://arxiv.org/abs/2606.19588) | Analyzing the Narration Gap in LLM-Solver Loops |
| 2026-06-17 | [2606.19235](https://arxiv.org/abs/2606.19235) | CodeSentinel: A Three-Layer Defense Against Indirect Prompt Injection in Code  |
| 2026-06-17 | [2606.18550](https://arxiv.org/abs/2606.18550) | The Gate Is Only as Honest as Its Contracts: ContractGuard for the Contract La |
| 2026-06-16 | [2606.18193](https://arxiv.org/abs/2606.18193) | A Red-Team Study of Anthropic Fable 5 &amp; Opus 4.8 Models |
| 2026-06-16 | [2606.18356](https://arxiv.org/abs/2606.18356) | SafeClawBench: Separating Semantic, Audit-Evidence, and Sandbox Harm in Tool-U |
| 2026-06-16 | [2606.17467](https://arxiv.org/abs/2606.17467) | PARSE: Provenance-Aware Retrieval Sanitization for Professional Domain LLM Age |
| 2026-06-15 | [2606.16751](https://arxiv.org/abs/2606.16751) | Automated jailbreak attack targeting multiple defense strategies |
| 2026-06-15 | [2606.16527](https://arxiv.org/abs/2606.16527) | DoubtProbe: Black-Box Jailbreak Defense via Structural Verification and Semant |
| 2026-06-15 | [2606.17114](https://arxiv.org/abs/2606.17114) | An Evaluation of Data Leakage Risks in Tool-Using LLM Agents in Realistic Scen |
| 2026-06-15 | [2606.17034](https://arxiv.org/abs/2606.17034) | KVEraser: Learning to Steer KV Cache for Efficient Localized Context Erasing |
| 2026-06-15 | [2606.16242](https://arxiv.org/abs/2606.16242) | Rapid Poison: Practical Poisoning Attacks Against the Rapid Response Framework |
| 2026-06-15 | [2606.16420](https://arxiv.org/abs/2606.16420) | Transferable Self-Evolving Playbooks for Agentic Security Auditing |
| 2026-06-14 | [2606.15788](https://arxiv.org/abs/2606.15788) | GAS-Leak-LLM: Genetic Algorithm-Based Suffix Optimization for Black-Box LLM Ja |
| 2026-06-14 | [2606.15899](https://arxiv.org/abs/2606.15899) | SkillVetBench: LLM-as-Judge for Multi-Dimensional Security Risk Evaluation in  |
| 2026-06-14 | [2606.15609](https://arxiv.org/abs/2606.15609) | FragFuse: Bypassing Access Control of Large Language Model Agents via Memory-B |
| 2026-06-13 | [2606.15441](https://arxiv.org/abs/2606.15441) | Defending against Adaptive Prompt Injection Attacks via Reasoning-enabled Task |
| 2026-06-13 | [2606.17092](https://arxiv.org/abs/2606.17092) | Securing Multi-Agent GIS Systems: Risk Evaluation and Prompt Hardening Optimiz |
| 2026-06-13 | [2606.15308](https://arxiv.org/abs/2606.15308) | Forced Deferral: Manipulating Routing Decisions in Multimodal LLM Cascades |
| 2026-06-13 | [2606.15057](https://arxiv.org/abs/2606.15057) | AutoDojo: Adaptive Attacks Expose Superficial Defenses and User-Underspecifica |
| 2026-06-12 | [2606.14517](https://arxiv.org/abs/2606.14517) | From Shield to Target: Denial-of-Service Attacks on LLM-Based Agent Guardrails |
| 2026-06-12 | [2606.15008](https://arxiv.org/abs/2606.15008) | Security Engineering of OpenClaw: Analyzing Attack Surface Expansion and Trust |
| 2026-06-12 | [2606.14154](https://arxiv.org/abs/2606.14154) | SkillMutator: Benchmarking and Defending Language-and-Code Cross-modal Attacks |
| 2026-06-11 | [2606.12918](https://arxiv.org/abs/2606.12918) | MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems |
| 2026-06-11 | [2606.13737](https://arxiv.org/abs/2606.13737) | FreoStream:Enhancing Stream Guardrails via Future-Aware Reasoning and Safety-A |
| 2026-06-11 | [2606.13385](https://arxiv.org/abs/2606.13385) | Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real |
| 2026-06-11 | [2606.13044](https://arxiv.org/abs/2606.13044) | No Hidden Prompts Needed! You Can Game AI Peer Review with Presentation-Only R |
| 2026-06-11 | [2606.13038](https://arxiv.org/abs/2606.13038) | Nous: An Attempt to Extract and Inject the Cognition Behind Prediction-Market  |
| 2026-06-10 | [2606.12737](https://arxiv.org/abs/2606.12737) | PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections |
| 2026-06-10 | [2606.12709](https://arxiv.org/abs/2606.12709) | Smarter Saboteurs, Better Fixers: Scaling &amp; Security in Linear Multi-Agent |
| 2026-06-10 | [2606.12341](https://arxiv.org/abs/2606.12341) | OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents |
| 2026-06-10 | [2606.11949](https://arxiv.org/abs/2606.11949) | Online Shift Detection and Conformal Adaptation for Deployed Safety Classifier |
| 2026-06-10 | [2606.11817](https://arxiv.org/abs/2606.11817) | Grammar-Constrained Decoding Can Jailbreak LLMs into Generating Malicious Code |
| 2026-06-10 | [2606.12716](https://arxiv.org/abs/2606.12716) | Does AI Reviewer See the Full Picture? Attacking and Defending Multimodal Peer |
| 2026-06-09 | [2606.11425](https://arxiv.org/abs/2606.11425) | JailbreakOPT: Tool-Assisted Iterative Jailbreak Prompt Optimization |
| 2026-06-09 | [2606.11409](https://arxiv.org/abs/2606.11409) | Risk Under Pressure: Compute-Aware Evaluation of Adversarial Robustness in Lan |
| 2026-06-09 | [2606.10525](https://arxiv.org/abs/2606.10525) | Assessing Automated Prompt Injection Attacks in Agentic Environments |
| 2026-06-09 | [2606.10749](https://arxiv.org/abs/2606.10749) | Toward Secure LLM Agents: Threat Surfaces, Attacks, Defenses, and Evaluation |
| 2026-06-08 | [2606.09701](https://arxiv.org/abs/2606.09701) | Learning to Attack and Defend: Adaptive Red Teaming of Language Models via GRP |
| 2026-06-08 | [2606.09556](https://arxiv.org/abs/2606.09556) | AI Scientists Are Only as Good as Their Evidence: A Stratified Ablation of Pro |
| 2026-06-08 | [2606.09408](https://arxiv.org/abs/2606.09408) | Can Data Work be Reparative? |
| 2026-06-08 | [2606.09178](https://arxiv.org/abs/2606.09178) | Culturally-Adapted Red-Teaming Across East and Southeast Asian Contexts: A Met |
| 2026-06-08 | [2606.09084](https://arxiv.org/abs/2606.09084) | Context-Fractured Decomposition Attacks on Tool-Using LLM Agents: Exploiting A |
| 2026-06-08 | [2606.09549](https://arxiv.org/abs/2606.09549) | SecureClaw: Clawing Back Control of LLM Agents |
| 2026-06-07 | [2606.08661](https://arxiv.org/abs/2606.08661) | Data Agents Under Attack: Vulnerabilities in LLM-Driven Analytical Systems |
| 2026-06-06 | [2606.08372](https://arxiv.org/abs/2606.08372) | SoK: Reconstruction Attacks on Synthetic Tabular Data (Insights from Winning t |
| 2026-06-05 | [2606.07833](https://arxiv.org/abs/2606.07833) | Beyond Pass/Fail: Using Process Mining to Understand How LLMs Resist (and Fail |
| 2026-06-05 | [2606.07335](https://arxiv.org/abs/2606.07335) | Defending Jailbreak Attacks on Large Language Models via Manifold Trajectory K |
| 2026-06-05 | [2606.07706](https://arxiv.org/abs/2606.07706) | MLingualFC: Evaluating Jailbreak Vulnerabilities in Multilingual Vision-Langua |
| 2026-06-04 | [2606.06140](https://arxiv.org/abs/2606.06140) | RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo |
| 2026-06-04 | [2606.05952](https://arxiv.org/abs/2606.05952) | Learning of Robot Safety Policies via Adversarial Synthetic Scenarios |
| 2026-06-04 | [2606.05743](https://arxiv.org/abs/2606.05743) | Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense |
| 2026-06-04 | [2606.05609](https://arxiv.org/abs/2606.05609) | SlotGCG: Exploiting the Positional Vulnerability in LLMs for Jailbreak Attacks |
| 2026-06-04 | [2606.05566](https://arxiv.org/abs/2606.05566) | GuardNet: Ensemble Strategies of Shallow Neural Networks for Robust Prompt Inj |
| 2026-06-03 | [2606.06529](https://arxiv.org/abs/2606.06529) | Attack Selection in Agentic AI Control Evaluations Meaningfully Decreases Safe |
| 2026-06-03 | [2606.05233](https://arxiv.org/abs/2606.05233) | Domain-Conditioned Safety in Frontier Computer-Using Agents: A 793-Episode Bro |
| 2026-06-02 | [2606.03647](https://arxiv.org/abs/2606.03647) | Black-box, Adaptive, Efficient, Transferable, Harmful, Applicable... Attacks A |
| 2026-06-01 | [2606.04027](https://arxiv.org/abs/2606.04027) | MaskForge: Structure-Aware Adaptive Attacks for Jailbreaking Diffusion Large L |
| 2026-06-01 | [2606.02302](https://arxiv.org/abs/2606.02302) | SeClaw: Spec-Driven Security Task Synthesis for Evaluating Autonomous Agents |

### 2026-05 (12편)

| 날짜 | arXiv | 제목 |
|---|---|---|
| 2026-05-30 | [2606.02630](https://arxiv.org/abs/2606.02630) | MultiTurnPSB: Evaluating Multi-Turn Jailbreak Attacks an dClassifier-Based Def |
| 2026-05-29 | [2605.31593](https://arxiv.org/abs/2605.31593) | Stateful Online Monitoring Catches Distributed Agent Attacks |
| 2026-05-28 | [2605.29708](https://arxiv.org/abs/2605.29708) | Understanding Safety-Sensitive Expert Behavior in Mixture-of-Experts LLMs |
| 2026-05-27 | [2605.28338](https://arxiv.org/abs/2605.28338) | SafeMed-R1: Clinician-Audited Safety and Ethics Alignment for Medical Large La |
| 2026-05-26 | [2605.26497](https://arxiv.org/abs/2605.26497) | Aligning Provenance with Authorization: A Dual-Graph Defense for LLM Agents |
| 2026-05-23 | [2605.24309](https://arxiv.org/abs/2605.24309) | Reframing LLM Agent Security as an Agent-Human Interaction Problem |
| 2026-05-17 | [2605.17453](https://arxiv.org/abs/2605.17453) | Trust No Tool: Evaluating and Defending LLM Agents under Untrusted Tool Feedba |
| 2026-05-11 | [2605.11039](https://arxiv.org/abs/2605.11039) | The Granularity Mismatch in Agent Security: Argument-Level Provenance Solves E |
| 2026-05-08 | [2605.08442](https://arxiv.org/abs/2605.08442) | Defense effectiveness across architectural layers: a mechanistic evaluation of |
| 2026-05-07 | [2605.06812](https://arxiv.org/abs/2605.06812) | Towards Security-Auditable LLM Agents: A Unified Graph Representation |
| 2026-05-06 | [2605.06713](https://arxiv.org/abs/2605.06713) | Agentic AI and the Industrialization of Cyber Offense: Forecast, Consequences, |
| 2026-05-01 | [2605.00741](https://arxiv.org/abs/2605.00741) | Self-Adaptive Multi-Agent LLM-Based Security Pattern Selection for IoT Systems |

### 2026-04 (9편)

| 날짜 | arXiv | 제목 |
|---|---|---|
| 2026-04-30 | [2605.00081](https://arxiv.org/abs/2605.00081) | Alignment Contracts for Agentic Security Systems |
| 2026-04-30 | [2604.27464](https://arxiv.org/abs/2604.27464) | Security Attack and Defense Strategies for Autonomous Agent Frameworks: A Laye |
| 2026-04-25 | [2604.23374](https://arxiv.org/abs/2604.23374) | Ghost in the Agent: Redefining Information Flow Tracking for LLM Agents |
| 2026-04-24 | [2604.22879](https://arxiv.org/abs/2604.22879) | Beyond Single-Agent Alignment: Preventing Context-Fragmented Violations in Mul |
| 2026-04-20 | [2604.18718](https://arxiv.org/abs/2604.18718) | Towards Optimal Agentic Architectures for Offensive Security Tasks |
| 2026-04-19 | [2604.17562](https://arxiv.org/abs/2604.17562) | SafeAgent: A Runtime Protection Architecture for Agentic Systems |
| 2026-04-14 | [2604.13298](https://arxiv.org/abs/2604.13298) | Can Agents Secure Hardware? Evaluating Agentic LLM-Driven Obfuscation for IP P |
| 2026-04-08 | [2604.06762](https://arxiv.org/abs/2604.06762) | ARuleCon: Agentic Security Rule Conversion |
| 2026-04-06 | [2604.04426](https://arxiv.org/abs/2604.04426) | ShieldNet: Network-Level Guardrails against Emerging Supply-Chain Injections i |

### 2026-03 (2편)

| 날짜 | arXiv | 제목 |
|---|---|---|
| 2026-03-30 | [2603.28166](https://arxiv.org/abs/2603.28166) | Evaluating Privilege Usage of Agents with Real-World Tools |
| 2026-03-19 | [2603.19469](https://arxiv.org/abs/2603.19469) | A Framework for Formalizing LLM Agent Security |

---
*Records in `_workspace/02_findings/papers-2606*.jsonl`; sources in `01_sources/sources.jsonl`. Reproducible
by re-running `build_graph.py` → `build_graphrag.py` → `build_embeddings.py`. Metrics verbatim from the
cited arXiv papers; CVE verified against NVD; citation counts from Semantic Scholar.*
