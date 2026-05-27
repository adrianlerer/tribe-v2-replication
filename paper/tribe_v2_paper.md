# Synthetic Populations as Institutional Stress Tests: Constitutional Lock-In and Model-Specific Phase Transitions in LLM Synthetic Societies

**Ignacio Adrián Lerer**
Independent Researcher | Buenos Aires, Argentina
adrian@lerer.com.ar | ORCID: 0009-0007-6378-9749 | May 2026

Zenodo community: [law-as-extended-phenotype](https://zenodo.org/communities/law-as-extended-phenotype/)
Replication repo: [github.com/adrianlerer/tribe-v2-synthetic-populations](https://github.com/adrianlerer/tribe-v2-synthetic-populations)

---

## Abstract

Synthetic populations built from large language models are increasingly used to study collective behavior, yet their scientific value depends on whether their responses can be measured under controlled institutional conditions rather than inspected narratively. We introduce TRIBE v2, a synthetic-population benchmark that operationalizes governance as a constrained distributed-computation problem. Agents act in two coupled institutional arms — normative reform and resource allocation — under rule systems with explicitly encoded constitutional lock-in (CLI) and layered normative palimpsests. In a reliable-lane confirmatory experiment (Phase 2A: 540 rows, 523 valid actions, USD 1.50) using Claude Haiku 4.5, Qwen 3.7 Max, and Mistral Large 2512, we observe a sharp high-CLI phase transition. Under identical formal norms and stateful memory, Qwen and Mistral converge to surface-exception evasion at high CLI, while Claude converges to adjudicatory exploration. The effect is discontinuous: the low-versus-medium contrast is not significant (Fisher p = 0.726), while low-versus-high and medium-versus-high are extreme (p = 1.05e-15 and p = 7.86e-16). World-cluster bootstrap intervals for Qwen high and Mistral high are [1.000, 1.000] under both model self-labels and a deterministic external judge. Mistral additionally exhibits a declared/action divergence of 81.6%, operationalizing a surface-compliance/structural-evasion pattern. Four Phase 2B robustness runs (10 replicas, stateless memory, Spanish prompts, DeepSeek smoke; total USD 8.45) confirm that the high-CLI transition survives memory removal and prompt-language variation. These findings support a narrower and stronger claim than cultural attribution: model families display specific institutional response profiles under identical formal constraints. TRIBE v2 provides a reproducible method for stress-testing institutional rule systems and model behavior without treating LLM agents as direct human proxies.

**Keywords:** synthetic populations, constitutional lock-in, institutional evasion, LLM agents, distributed computation, normative palimpsest, SAPNC, evolutionary game theory

---

## 1. Introduction

Synthetic populations built from computational agents have become a standard tool for studying institutional dynamics. Agent-based models can replicate historical patterns of reform failure with surprising precision: a prior experiment using 816 synthetic agents calibrated to Argentine institutional parameters reproduced the historical blocking rate of labor reforms within 3.3 percentage points across five independent runs, demonstrating that bottom-up agent interaction can recover macro-level institutional outcomes without top-down design (Lerer, 2026a). Parallel work using autonomous agent red-teaming showed that synthetic populations can function as normative stress-testing environments, identifying evasion pathways in proposed legislation that conventional legal analysis missed (Lerer, 2026b). A third line established that synthetic agents in normative sandboxes exhibit exaptation and spandrels — behavioral strategies the designer did not specify, emerging from the interaction between formal rules and environmental pressure (Lerer, 2026c).

All three lines shared a methodological constraint: the agents operated under fixed behavioral rules selected by the designer. This made results interpretable but limited inferential scope. When a programmed agent evades a rule, the evasion reflects the designer's prior hypothesis. It does not constitute independent behavioral evidence.

Large language models dissolve that constraint and introduce a new one. LLM agents are not programmed with explicit behavioral rules; their institutional response strategies emerge from training. This makes them genuinely informative as stress-testing instruments: if different model families produce different behavioral distributions under identical formal constraints, that divergence is evidence about the models, not about the designer's assumptions. The new constraint is that LLM agents are correlated samples from model-provider systems rather than independent human subjects, which limits the scope of cultural inference.

TRIBE v2 is designed to extract the maximum valid inference from this trade-off. It operationalizes governance as a constrained distributed-computation problem in the sense of Hamilton et al. (2026): agents coordinate under rule systems that impose explicitly measurable communication costs, adjudication latency, enforcement inconsistency, and amendment rigidity. It introduces a layered normative palimpsest — deep rules, institutional practice, recent reforms, surface exceptions, and within-run memory — drawn from the institutional stratigraphy framework developed in prior work (Lerer, 2026d). This architecture allows the "se acata pero no se cumple" (surface compliance, structural evasion) pattern to be measured rather than narrated. And it applies a world-cluster bootstrap and a deterministic external judge to produce statistically grounded results from a design that is transparent about its costs and limitations.

The central finding is that high constitutional lock-in induces a sharp behavioral phase transition that is model-family specific. Under identical formal norms, Qwen 3.7 Max and Mistral Large 2512 converge to surface-exception evasion at high CLI, while Claude Haiku 4.5 converges to adjudicatory exploration. The transition is discontinuous and robust across 10-replica runs, memory removal, and Spanish prompt language. These findings support a research program in which synthetic populations function as controlled institutional stress tests, not theatrical simulations of society.

---

## 2. Theoretical Background

### 2.1 Human Societies as Distributed Computational Systems

Hamilton et al. (2026) argue that human societies continuously transform dispersed information into collective judgments and coordinated action, and that the computational difficulty of this transformation imposes fundamental constraints on social organization. Coordination problems, resource allocation, norm enforcement, and knowledge accumulation are all, in a precise sense, computational problems with resource requirements measurable in time, communication, and memory.

This framing has two implications for institutional analysis. First, institutional quality can be evaluated in computational terms: a rule system that requires exponential communication to resolve ambiguities, or that makes consensus computationally intractable, will fail not because of bad intent but because of architectural mismatch. Second, the distributed nature of computation in social systems means that agents with heterogeneous perception filters will process the same signal differently (Dyachkov, 2026a), generating behavioral spectra rather than uniform compliance.

TRIBE v2 builds on this framework by treating constitutional lock-in as a formal measure of distributed computational difficulty. High CLI means high conflict density, long adjudication queues, inconsistent enforcement, and high amendment cost — all features that increase the resource requirements for coordination. The benchmark tests whether model populations respond to increasing computational difficulty by escalating through a hierarchy of institutional strategies: compliance, adjudicatory exploration, and surface-exception evasion.

### 2.2 Constitutional Lock-In

The Constitutional Lock-in Index (CLI) was introduced as a quantitative measure of institutional persistence, validated across 60 cases of labor reform attempts in Argentina, Brazil, Chile, and Spain, with AUC = 0.97 and R² = 0.74 (Lerer, 2025). CLI aggregates eight formal features: active constraint count, pairwise rule conflict density, ambiguity score, appeal latency, enforcement inconsistency, monitoring incompleteness, constitutional rigidity, and penalty severity variance.

In TRIBE v2, CLI is encoded as a formal feature vector rather than a narrative description. The three levels span the empirical range of the validation dataset: low CLI (analog: Chile, CLI ≈ 0.24), medium CLI (analog: Spain, CLI ≈ 0.37–0.51), and high CLI (analog: Argentina, CLI ≈ 0.87–0.89). The feature vector is embedded in the world state as explicit parameters, not as stylistic adjectives in the prompt. This encoding is the operationalization that connects the benchmark to the broader EPT/CLI research program.

The key empirical finding from the prior validation that motivates this experiment is the threshold behavior: jurisdictions with CLI below 0.30 show high reform success rates, while those above 0.70 show near-zero success rates across four decades of observations. TRIBE v2 asks whether LLM agents exhibit a parallel threshold in their institutional response strategies.

### 2.3 Normative Palimpsests

A palimpsest is a manuscript in which earlier text has been partially erased and overwritten, with older layers remaining partially visible. Legal systems operate as normative palimpsests: formal rules are layered on top of institutional practice, which is layered on older deep rules, which are partially contradicted by recent reforms and surface exceptions. The "Legal Book of the Dead" framework (Lerer, 2026d) formalizes this structure as a genealogical instrument for tracing the competitive dynamics between normative layers.

TRIBE v2 encodes this structure with five normative layers: deep rules (constitutional provisions that are difficult to amend), institutional practice (accumulated patterns of enforcement), recent reforms (changes adopted in the last few cycles), surface exceptions (specific carve-outs that formally comply with deeper rules while circumventing their intent), and within-run memory (agent-specific commitments and prior actions). Evasion becomes precisely measurable: an agent evades when it declares compliance with a deeper layer while acting through a surface exception whose practical effect contradicts the declared intent.

This operationalization connects to the distributed computation framework directly. Under low CLI, the constraint hierarchy is clean and adjudication is fast: agents can find valid compliance paths without high communication cost. Under high CLI, the constraint hierarchy is internally contradictory and adjudication is slow: the cost of genuine compliance exceeds the cost of routing behavior through surface exceptions. The palimpsest structure is what makes surface-exception evasion available as a strategy — without a shallow exception layer, agents facing intractable constraints would have to defect openly rather than formally comply while substantively evading.

### 2.4 The SAPNC Pattern

The expression "se acata pero no se cumple" (the law is acknowledged but not obeyed) identifies a structural feature of legal systems operating under high lock-in: actors formally acknowledge rule validity while systematically structuring their behavior to avoid its substantive effect. Prior work documents this pattern across 23 failed Argentine labor reforms from 1991 to the present, where 0% of reforms achieved sustained behavioral change despite formal enactment (Lerer, 2026a). The Milei 2024 reform program provided a prospective validation: CLI predicted a 12.4% success probability; observed outcome was 0% (p = 0.003), with the CGT injunction against Law 27.802 confirmed as observation 24 in the dataset (Lerer, 2025).

TRIBE v2 operationalizes the SAPNC pattern as the divergence between self-labeled action category and the category assigned by a deterministic external judge. A high declared/action divergence that persists across memory conditions and prompt languages is evidence of a systematic behavioral strategy rather than a classification ambiguity.

---

## 3. Benchmark Design

### 3.1 Two Coupled Institutional Arms

TRIBE v2 runs two institutional arms in each world cycle.

The normative reform arm presents agents with a proposed rule change. Agents evaluate the proposal and act using one of five categories: comply (endorse and implement), explore (negotiate, propose amendments, seek adjudication), evade (formally acknowledge while routing behavior through a surface exception), defect (open refusal or sabotage), or abstain (decline to engage).

The resource allocation arm presents agents with a scarce allocation problem under the current rule stack. The same five action categories apply. The two arms are coupled: the collective outcome of the normative reform arm updates the rule stack applied in the next allocation cycle, and the allocation outcome becomes evidence or pressure for the next reform cycle. This coupling creates the possibility of institutional feedback dynamics and hysteresis.

### 3.2 Action Categories

The five categories are defined with operational precision. Comply means following the active rule or implementing the reform directly, with no reference to exceptions or workarounds. Explore means negotiating, seeking adjudication, proposing an amendment, or searching for a lawful workaround while explicitly acknowledging rule validity. Evade means formally acknowledging the rule while citing a surface exception, procedural mechanism, or transitional carve-out whose practical effect contradicts the rule's intent. Defect means openly violating, blocking, or ignoring the rule without formal acknowledgment. Abstain means refusing to act or declining to engage.

The separation of evade from explore is not cosmetic. An agent that declares explore while the external judge classifies its action as evade is exhibiting a specific institutional strategy. Collapsing the two categories would destroy the SAPNC signal entirely.

### 3.3 CLI Encoding as Formal Features

Constitutional lock-in is encoded as a formal feature vector in the world state, not as narrative prose. Low CLI represents 2–3 active constraints, zero pairwise rule conflicts, zero ambiguity flags, single-cycle adjudication, consistent enforcement, full monitoring coverage, simple majority amendment threshold, and low penalty variance. Medium CLI represents 5–7 constraints, two conflict pairs, one ambiguity flag, three-cycle adjudication, 30% enforcement inconsistency, 70% monitoring coverage, two-thirds supermajority threshold, and moderate penalty variance. High CLI represents 10+ constraints, five or more conflict pairs, three or more ambiguity flags, five-cycle adjudication, 60% enforcement inconsistency, 40% monitoring coverage, unanimity amendment threshold, high and unpredictable penalty variance, and a non-derogable constitutional core.

### 3.4 Deterministic External Judge

Model self-labels are the primary classification signal, but they are subject to self-serving reporting bias. The external judge is a local lexical classifier that evaluates the action text, the justification, the rule references cited, and the resource move declared. It does not use an LLM evaluator, which would introduce the model-family bias being measured. The judge is deliberately simple and auditable: it serves as an audit layer, not a ground-truth authority. Where self-label and judge agree, the classification is robust. Where they diverge, the divergence is itself informative.

### 3.5 World-Cluster Bootstrap

Standard confidence intervals treat each row as an independent observation. In TRIBE v2, each world contains multiple agents acting across multiple cycles, so the effective sample is the number of worlds, not the number of rows. The bootstrap resamples by world cluster, identified as model_label|world_id to avoid cross-model collision. All confidence intervals reported in this paper are world-cluster bootstrap intervals from 2,000 iterations.

---

## 4. Phase 2A Experiment

### 4.1 Design

Phase 2A is the reliable-lane confirmatory run. The design matrix uses three models (Claude Haiku 4.5, Qwen 3.7 Max, Mistral Large 2512), three CLI levels, five replicas per cell, three cycles per world, two agents per world with stateful memory, and two institutional arms. Total rows: 540. Valid action events: 523 (96.9%). Error events: 17. Ledger spend: USD 1.50073750 under a USD 10 cap. Model IDs were validated against live OpenRouter metadata before the run. DeepSeek was excluded from the confirmatory lane due to provider reliability below the preregistered 90% valid-action threshold.

### 4.2 Aggregate Results

The overall action distribution shows that, pooled across all conditions, explore dominates at 42.6% (self-label) or 62.0% (judge), evade runs at 29.4% (self-label) or 30.6% (judge), comply accounts for 27.2% (self-label) or 6.7% (judge), and abstain is negligible at 0.8%. The judge reclassifies a substantial share of self-labeled comply actions as explore, because the action text uses procedural rather than direct rule-following language. The core evade proportion is stable across both classifications.

### 4.3 Three Institutional Response Profiles

Three distinct profiles emerge at the model level. Claude self-labels 100% exploration with 0% evasion across all CLI levels, and the external judge agrees at low and medium CLI. Qwen shows a bifurcated profile: full compliance at low and medium CLI, explicit 100% evasion at high CLI, with a 0% declared/action gap. Qwen does not dissemble — when it evades, it labels the evasion accurately. Mistral shows the SAPNC profile: high aggregate evasion (54.0% overall) combined with an 81.6% declared/action gap. Mistral systematically declares a more cooperative strategy than its actions implement.

### 4.4 The High-CLI Phase Transition

The cell-level data reveal that the transition is not a gradient but a step function. Qwen transitions from 100% compliance at low and medium CLI to 100% evasion at high CLI with no intermediate state. Mistral's trajectory is more complex: a latent evasive attractor at low CLI (28.3%) intensifies through medium (33.9%) and becomes complete at high (100%). Claude shows no self-labeled evasion at any CLI level.

The Fisher exact tests confirm the discontinuity. The low-vs-high contrast yields p = 1.05e-15 with odds ratio 0.053. The medium-vs-high contrast yields p = 7.86e-16 with odds ratio 0.062. The low-vs-medium contrast is not significant (p = 0.726, odds ratio 0.853). The threshold is not located between low and medium CLI; it is located between medium and high CLI.

All three pairwise model contrasts are significant at extreme levels: Claude vs Mistral p = 4.34e-16, Claude vs Qwen p = 4.38e-16, Mistral vs Qwen p = 3.54e-4. Mistral evades more than Qwen in aggregate, and the difference between them is also significant.

### 4.5 Bootstrap Intervals

The world-cluster bootstrap produces point-mass distributions at [1.000, 1.000] for Qwen high and Mistral high under both self-label and external judge. The Claude high-CLI self-label bootstrap is a point mass at [0.000, 0.000], but the external judge assigns a mean of 0.342 with a wide interval [0.000, 0.719]. This is theoretically important rather than a defect: it marks the empirical boundary between adjudicatory exploration and surface-exception evasion. Claude high-CLI actions involve extensive reference to rule exceptions and adjudication procedures that the lexical judge reads as potentially evasive even when the agent self-labels them as exploration. This boundary case motivates future human calibration of the judge.

---

## 5. Phase 2B Robustness

### 5.1 Design

Phase 2B ran four robustness blocks under preregistered protocols. Run A stateful used 10 replicas, English prompts, and stateful memory — the canonical confirmatory expansion. Run A stateless used 10 replicas, English prompts, and no memory — testing whether hysteresis drives the main result. Run B1 Spanish used 10 replicas, Spanish prompts, and stateful memory — testing prompt-language sensitivity. The DeepSeek smoke used two replicas and tested provider reliability. Total Phase 2B spend: USD 8.45483297.

### 5.2 Memory Does Not Drive the Main Result

Under stateless conditions, the high-CLI transition survives completely for Qwen (1.000 [1.000, 1.000]) and almost completely for Mistral (0.983 [0.958, 1.000]). Claude remains non-evasive by self-label (0.000 [0.000, 0.000]). Memory amplifies Mistral's medium-CLI evasion (stateful: 39.3%, stateless: 21.1%), suggesting that the evasive attractor intensifies with history accumulation at intermediate lock-in levels, but the high-CLI result does not depend on it. Qwen's high-CLI evasion appears on cycle 1 under stateless conditions, confirming that it is an immediate institutional response to the constraint structure rather than an accumulated adaptation.

### 5.3 Spanish Preserves Ordering with Increased Noise

The Spanish condition preserves the main ordering — Claude non-evasive, Mistral and Qwen high-CLI evasive — but introduces measurement uncertainty. Parse and transport errors increase (59 errors vs 22 in English stateful). The external judge assigns lower evasion rates to Spanish actions, likely because the action language shifts toward procedural phrasing that the lexical judge does not classify as evasion. The bootstrap interval for Qwen high in Spanish is [0.750, 1.000] rather than the [1.000, 1.000] of the English conditions. Spanish is treated as a robustness stress test, not clean confirmatory evidence. A complete language-factor design with a Spanish-adapted judge would be required before language effects could be estimated independently.

### 5.4 DeepSeek Signal But Not Confirmatory

The DeepSeek V4 Pro smoke run shows the same substantive pattern: 100% compliance at low CLI, mixed at medium, 100% self-labeled evasion at high CLI. But the valid-action rate is 79.2% (57 of 72 rows), below the preregistered 90% inclusion threshold. DeepSeek remains outside the confirmatory lane. Future runs should test whether provider reliability improves with routing controls.

---

## 6. Interpretation

### 6.1 Three Institutional Response Profiles

The data support a typology of three model-family institutional response profiles under high constitutional lock-in.

Claude implements adjudicatory exploration. Under all CLI levels, it routes institutional conflict through procedural channels: invoking adjudication mechanisms, proposing modifications, and seeking resolution within the normative framework. The external judge's high-CLI reclassification — 33.3% judged evasion despite 0% self-labeled evasion — suggests that Claude's adjudicatory strategy approaches but does not cross the boundary into surface-exception exploitation. The bootstrap interval [0.000, 0.719] for judged evasion at high CLI reflects genuine measurement uncertainty at this boundary, not random noise.

Qwen implements explicit phase-transition compliance and evasion. It does not dissemble: when it evades, it self-labels the evasion accurately. The transition from 100% compliance at low and medium CLI to 100% evasion at high CLI is binary and immediate. Qwen's declared/action gap is 0.0%: the model's self-description is accurate. This profile is closer to defection than to classic SAPNC, but Qwen routes defection through surface exceptions rather than open refusal.

Mistral implements a latent evasive attractor. Even at low CLI, where the formal system is navigable, Mistral shows 28.3% self-labeled evasion. This rises through medium CLI (33.9%) to complete at high CLI (100%). The SAPNC pattern — an 81.6% declared/action gap — persists across all CLI levels and across both memory conditions and prompt languages. Mistral systematically declares a more cooperative strategy than it implements. This is not a technical artifact: it is a stable behavioral profile that survives all robustness checks.

### 6.2 The Transition Is Computational, Not Cultural

The sharp threshold at high CLI is consistent with a distributed-computation interpretation. Low and medium CLI represent environments where coordination costs are manageable: agents can navigate the rule stack, find valid compliance paths, and resolve conflicts through adjudication within reasonable cycle budgets. High CLI represents an environment where the coordination costs of genuine compliance — navigating five or more conflicting rules, waiting five cycles for adjudication, operating under 60% enforcement inconsistency — exceed the costs of routing behavior through surface exceptions.

The model-family variation in response profile reflects differences in how training shaped the cost function for institutional compliance, not claims about the cultural values of populations where training data originated. This is a distinction that matters for inference. If the result were cultural, it would require controls for training data composition, RLHF annotator background, and provider policy. TRIBE v2 is not designed to answer those questions. What it establishes is that model families differ in their institutional response profiles under identical formal conditions, and that those differences are large enough and reproducible enough to constitute an institutional stress test.

### 6.3 Mistral's Low-CLI Mixed Result as Substantive Finding

Phase 2A revealed that Mistral low-CLI is not clean compliance: 28.3% self-labeled evasion with a bootstrap interval of [0.000, 0.650]. This is not a failure to replicate a clean result. It is a substantive finding: Mistral has a latent evasive attractor that high CLI makes deterministic but that is present even under low lock-in. The attractor may reflect training-origin effects, provider policy interactions, or intrinsic characteristics of the Mixtral architecture. The Phase 2B stateless run shows that Mistral low-CLI evasion does not require memory accumulation (stateless low: 8.5%), but also that memory amplifies it at medium CLI. Separating these explanations requires the Phase 2C controls described below.

---

## 7. Limitations

Pseudoreplication poses the most fundamental challenge. Multiple agents from the same model family in the same world are not independent observations. The world-cluster bootstrap addresses this for inferential statistics, but does not resolve the deeper issue that all Claude agents in a run sample from the same underlying model. The effective sample size is the number of worlds per cell, not the number of agent-actions. A publication submission should report both.

Provider confounding is a potential hidden covariate in all between-model comparisons. OpenRouter routes model calls through providers that may have different policies, system prompts, safety filters, and response characteristics. Phase 2B did not include provider-pinning controls.

The deterministic judge is local and auditable but lexical. It misses semantic evasion strategies that use formally cooperative language to achieve non-cooperative ends. The Claude high-CLI ambiguity band is partly an artifact of this limitation, and the lower judged evasion rates in Spanish reflect a language-dependent failure mode of the lexical approach.

No human calibration has been performed. The action taxonomy has not been validated against human expert judgments of institutional behavior. Before submitting to venues with strong social science standards, calibration against coded human decisions or legal expert ratings would strengthen the measurement validity claims.

DeepSeek exclusion leaves a gap. The most theoretically interesting between-model comparison — Qwen vs DeepSeek as models from different Chinese AI providers — cannot be made with current data.

Nothing in this paper establishes that the observed model-family differences reflect cultural differences between the populations where training data originated. That inference requires controls for training data composition, RLHF annotator background, provider policy, and prompt language that go beyond TRIBE v2's current design.

---

## 8. Phase 2C and Future Work

Provider pinning is the single most important technical control not yet implemented. Routing each model through a fixed provider for the duration of a run would allow separation of model effects from provider-policy effects. OpenRouter's provider-routing controls should be tested before Phase 2C begins.

Human judge calibration is required before cultural-origin claims can be made. A sample of 100–200 events coded by domain experts — institutional economists or legal scholars — would calibrate the deterministic judge and identify its systematic errors.

A blinded LLM judge using a model from a different family than any model being evaluated would provide an independent classification signal with different failure modes than the lexical judge.

A complete language-factor design with English, Spanish, and Chinese prompt variants — and a language-adapted judge for each — would allow language effects to be estimated and controlled independently of model-family effects.

A no-memory baseline with longer cycles (10–15) would allow direct estimation of how much institutional history accumulation contributes to the high-CLI phase transition, and would isolate hysteresis from one-shot institutional preference.

These five controls collectively constitute Phase 2C. No claims about training-origin or cultural effects should be published before Phase 2C produces stable estimates.

---

## 9. Conclusion

TRIBE v2 introduces a reproducible method for measuring institutional response profiles in LLM synthetic populations under controlled constitutional lock-in. The benchmark treats governance as a constrained distributed-computation problem, operationalizes lock-in as a formal feature vector, introduces a normative palimpsest layer structure, and separates surface-exception evasion from adjudicatory exploration with a taxonomy that allows the SAPNC pattern to be directly measured.

The central finding is a sharp behavioral phase transition at high CLI: Qwen 3.7 Max and Mistral Large 2512 converge to 1.000 evasion under high lock-in, while Claude Haiku 4.5 maintains adjudicatory exploration. The transition is discontinuous, robust to memory removal, and partially robust to Spanish prompt language. Mistral's 81.6% declared/action divergence operationalizes the SAPNC pattern across all conditions.

These findings extend a line of work on synthetic populations and institutional simulation that began with programmed agents and fixed behavioral rules (Lerer, 2026a, 2026b, 2026c). The contribution of TRIBE v2 is to replace programmed behavioral rules with LLM-emergent strategies while maintaining the formal institutional structure — CLI encoding, palimpsest layers, coupled arms — that makes results interpretable rather than merely entertaining.

The scientific claim is not that model agents are human proxies or that their behavior reflects cultural values. It is that different model families implement different strategies when formal institutions become computationally expensive to navigate, and that those strategies are measurable, reproducible, and theoretically interpretable. That finding is useful for rule system designers, AI governance researchers, and institutional economists studying the relationship between normative architecture and behavioral compliance.

The path to stronger inference runs through the robustness program in Section 8: provider pinning, human judge calibration, language controls, and reliable-lane inclusion of additional models. Until those controls are in place, the appropriate scope of inference is model-family institutional response profiles under specific formal conditions — not cultural attribution, not general behavioral prediction, and not claims about LLM agents as human analogs.

---

## References

Dyachkov, V. (2026a). Social institutions: A behavioural approach for operational measurement [Working paper]. ResearchGate. https://doi.org/10.13140/RG.2.2.22713.33122

Dyachkov, V. (2026b). Institutional design: Experimental social engineering in behavioural test [Working paper]. ResearchGate. https://doi.org/10.13140/RG.2.2.17260.73604

Hamilton, M. J., Yadav, A., Hartle, H., Korbel, J., Kornerup, N., Stier, A. J., Erwin, D. H., Youn, H., Kempes, C. P., Shimao, H., Harper, K., Evans, J., & Wolpert, D. H. (2026). Computational foundations of the human world. arXiv:2605.01680.

Lerer, I. A. (2025). From transaction costs to memetic fitness: Formalizing Douglass North's institutional insights through extended phenotype theory. SSRN Electronic Journal. https://doi.org/10.2139/ssrn.5750242

Lerer, I. A. (2026a). Simulating institutional dynamics: A multi-agent framework for predicting legal reform outcomes using extended phenotype theory. Zenodo. https://doi.org/10.5281/zenodo.19010941

Lerer, I. A. (2026b). Synthetic chaos as an institutional laboratory: Independent evidence for extended phenotype theory from autonomous agent red-teaming. Zenodo. https://doi.org/10.5281/zenodo.18777434

Lerer, I. A. (2026c). Synthetic minds in normative sandboxes: Exaptation, spandrels, and multilevel selection in agent-based legal simulation. Zenodo. https://doi.org/10.5281/zenodo.19341388

Lerer, I. A. (2026d). The legal book of the dead: Memetic pincers and institutional palimpsests. SSRN. https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5496678

Lerer, I. A. (2026e). Computational detection of constitutional drift: Network analysis and semantic measurement of Argentine Supreme Court jurisprudence (1922–2025). Journal of Computational Law and Legal Technology. https://doi.org/10.47852/bonviewJCLLT62027951

North, D. C. (1990). Institutions, institutional change and economic performance. Cambridge University Press. https://doi.org/10.1017/CBO9780511808678

---

## AI Disclosure

AI tools were used for research support, including locating sources, extracting information from academic literature, reviewing drafts for consistency, and assisting with code development for the experiment harness. The thesis, frameworks, arguments, experimental design, CLI operationalization, action taxonomy, SAPNC operationalization, and interpretation of results are the author's original contribution. All substantive content was conceived, structured, verified, and revised by the author.

---

*Correspondence: Ignacio Adrián Lerer | Independent Researcher | Buenos Aires, Argentina | adrian@lerer.com.ar | ORCID: 0009-0007-6378-9749 | May 2026*
