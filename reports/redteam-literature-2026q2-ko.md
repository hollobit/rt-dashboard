# Red-Teaming 논문 인텔리전스 — 2026 2분기

**생성:** 2026-06-23 · RT AI 안전성 보증 플랫폼 · paper-research-pipeline (rev.2)

arXiv의 **최신 red-teaming / AI 안전 / AI 보안 논문**을 체계적으로 수집해 전문 정독하고 지식그래프로
정제했습니다. **86편**(2026-03-19 → 2026-06-18, 73%가 최근 한 달)을 발굴·다운로드하여 4명의 전문
분석가가 분석하고, 엄격한 정직성 원칙(수치 verbatim, `^[ambiguous]` 표기, CVE 날조 금지)으로 통합했습니다.

## 1. 범위 및 코퍼스 영향

| | 이전 | 이후(이번 사이클) |
|---|---|---|
| 논문 소스 | 187 | **321** (+134) |
| 그래프 노드 | 2,360 | **3,806** |
| 공격기법 | 142 | **237** |
| 취약점 | 79 | **152** |
| 위협 분류 | 약 72 | **~200** |
| 통제 | 75 | **133** |
| GraphRAG 유닛 | 1,731 | **2,464** |
| 인용망 엣지 | — | **821** (논문→논문) |

86편에서 추출: **380 레코드** — finding 161, 공격기법 55, 취약점 42(고유 CWE 34종), candidate 위협 34종,
통제 58, 리스크 21, 위해 9. 전 과정 품질 게이트 유지: **dangling 0 · 고립 0 · 유닛=임베딩 정합**.

## 2. 주제별 발견 사항

### 2.1 에이전트·멀티에이전트 보안 (최대 영역)
- **공급망 주입** (`agentic.supply-chain-injection`, ShieldNet) — 양성 인터페이스 + 양성 I/O 유지,
  **런타임에만 악성 네트워크 행위**(exfil/C2). 정적 스캐너 F1 0.03 vs 네트워크 탐지 0.998.
- **방어 역전** (`agentic.defense-inversion`) — capability-removal 방어가 오히려 새 공격경로 생성
  (hallucination bypass, multi-key normalization). 입력/검색층 방어 ~89% ASR, 메모리층 tool-gating만 0% 달성.
- **교차세션 메모리 영속/오염** — delayed-trigger 영속메모리 공격이 대부분 계층을 우회. provenance·
  authorization·inter-agent-trust·topology가 반복 등장하는 미해결 갭.
- **합성 누출 & 자원 고갈** (Data Agents) — 8개 취약점 패밀리; 비샌드박스 `exec()` 100% ASR;
  누적 differencing 누출 및 정책위반 없는 DoS.
- **provenance gap** (Context-Fractured Decomposition) — bounded-observability 모니터가 교차세션
  아티팩트 의도를 못 봄(+28pp ASR); 단일턴 judge 실패.

### 2.2 Jailbreak — 신규 기법
- **모달리티 grounding 취약** — CodeSpear(문법제약 디코딩)·MaskForge(디퓨전 마스크인필): 정렬이
  자연어에만 grounded → 비자연어 출력공간(코드/인필)으로 우회 (`model.infilling-abuse`).
- **위치 취약성** (SlotGCG) — GCG의 접미사 편향을 깨고 attention 기반 슬롯 분산, ASR +14%.
- **멀티턴 누적** (MultiTurnPSB) — 의료AI 비안전율 35%→79%, "응급 + 권위주장" 2요소 공식.
- **다국어/교차모달 갭** (MLingualFC) — 유해명령을 다국어 플로차트 이미지로 인코딩
  (`societal.multilingual-safety-gap`).

### 2.3 Frontier·정렬
- **추론모델 self-censoring은 학습으로 제거 가능** (AdvGRPO) — 추론-시점 안전점검에 의존하는 방어의
  근본적 한계 (`frontier.reasoning-self-censor-bypass`).
- **MoE 안전-expert 재프로그래밍** (RASET) — 0.12% 파라미터만 편집해 정렬 역전(+37.6pt ASR),
  라우팅 보존 → 라우터 모니터링에 stealth.
- **사이버 공세 산업화** (Koch) — "attack compression": 새 공격클래스 없이 킬체인 비용 붕괴
  (`agentic.attack-compression`).

### 2.4 프라이버시·무결성·도메인 위해
- **누적 추론 누출** (OCELOT) — 개별 무해 릴리스가 누적돼 비밀 재구성; per-release 필터의 구조적 한계.
- **AI peer review 조작** — presentation 공격으로 연구 무결성 훼손.
- **배포안전 ≠ 시험정확도** — 의료(SafeMed-R1)·물리/로봇(Red/Blue) 안전.

### 2.5 방법론 메타 발견
- 정적 벤치마크가 적응형 공격 대비 방어를 **15.8pp 과대평가**(RETA); 합성→실문서 일반화 실패(PARSE).
- 자동 에이전트 보안감사가 **CVE급 실세계 영향** 달성(EVOHUNT: 28개 OSS 취약점 확인 + $1,500 바운티;
  식별자는 책임공개 중 redaction → CWE-class로 기록).

## 3. 신규 위협 분류 (candidate 60종)
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
## 4. CVE / 취약점 공개
- **CVE-2026-31431 'Copy Fail'** — Linux 커널 로컬 권한상승(CWE-269, high), 사이버 공세 예측 논문이
  인용했고 **NVD API로 독립 검증**(vulnStatus *Analyzed*, 발행 2026-04-22). cve.org는 JS 렌더라
  NVD JSON API 사용.
- 나머지 42개 신규 취약점은 **연구 약점 클래스**로 **34종 CWE**에 매핑(예: CWE-94, CWE-269, CWE-285,
  CWE-400, CWE-693, CWE-863, CWE-1427) — 제품 CVE 아님. CVE 번호 날조 없음, redacted/부분 식별자는
  `^[ambiguous]`로 기록.

## 5. 인용망 & 영향력 분석 (Semantic Scholar)
신규 2026년 6월 논문은 **인용 0회**(너무 최신이라 영향력 누적 전)이나, 코퍼스가 이미 보유한 **정전급
red-teaming 논문을 충실히 인용**합니다 — 신규 논문이 가장 많이 인용한 기초 논문:

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

Citation 보강으로 **644 논문→논문 엣지**를 추가해 신규 논문을 Papers 탭 인용망에 편입했습니다.
최신 연구가 정전을 무시하지 않고 기반으로 삼고 있음을 확인합니다.


## 5.5 피어리뷰 학회/저널 sweep (48편, 2025–2026)

arXiv 프리프린트를 넘어, Semantic Scholar venue 필터로 **48편의 피어리뷰 학회/저널 논문**
(IEEE S&P·ACL·NDSS·ICML·ICLR·AAAI·USENIX·CCS·EMNLP·ICCV·CVPR·IEEE TPAMI/TDSC/TIFS)을 추가했습니다 —
고인용·검증된 선행연구(최대 118 citations).

**venue 분포:**

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

주요 발견: **MCP/에이전트 보안**(MPMA 선호조작·SAGA ProVerif 검증 거버넌스·MCPXKIT·AgentSentinel);
**멀티모달 jailbreak**(SI-Attack 셔플불일치·JOOD OOD·VisCo vision-centric·X-Transfer CLIP super-전이
=공유인코더 공급망 단일실패점); **평가 무결성**(Chatbot Arena ~$440 재순위·safety judge FNR 0.02→1.00);
**증명가능 방어**(DataSentinel·MELON·IPIGuard). 신규 멀티모달 위협: `multimodal.safety-comprehension-gap`·
`ood-distribution-shift`·`foundation-encoder-super-transfer`·`vision-centric-context-injection`·`societal.eval-integrity`.

### 분석 venue 논문 (48)

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

## 6. 방법론
**`paper-research-pipeline`** 스킬로 재현 가능: arXiv 발굴(코퍼스 대비 중복제거) → 선별 PDF 다운로드 →
4 전문 분석가 전문 정독 → 레코드 검증 → CVE 연계(NVD) → Semantic Scholar citation 보강 → 그래프·임베딩
재합성 → 배포. 전 스크립트는 `.claude/skills/paper-research-pipeline/`.

## 7. 분석 논문 — arXiv 프리프린트 (86)

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
*레코드: `_workspace/02_findings/papers-2606*.jsonl`, 소스: `01_sources/sources.jsonl`.
`build_graph.py` → `build_graphrag.py` → `build_embeddings.py` 재실행으로 재현 가능. 수치는 인용 arXiv
논문에서 verbatim, CVE는 NVD 검증, citation 수는 Semantic Scholar 기준.*
