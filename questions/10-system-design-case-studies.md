# 10. System Design / Case Studies

Open-ended, senior-level scenarios synthesizing themes across the entire repo. As with the format established in other repos in this series, these are typically extended discussions rather than questions with one correct answer — evaluate reasoning quality, appropriate skepticism about evidence quality, and whether genomic, clinical, statistical, and ethical/regulatory considerations are integrated together rather than treated as separate silos.

---

### 10.1 🔴 Design the end-to-end analytical workflow you would establish for a health system launching a new precision oncology program, from receiving a tumor sequencing result to a treatment recommendation reaching the treating oncologist.

**What a strong answer covers:**
- Starting from the bioinformatics pipeline discussed in category 2 (with appropriate CLIA-certified pipeline validation per category 2.11), through somatic variant calling and the tiered clinical significance framework discussed in category 3.12-3.13.
- Should explicitly address the clonal hematopoiesis interpretive challenge (category 3.16) if the workflow involves any liquid biopsy component (category 7.4-7.5).
- Should propose a molecular tumor board or equivalent structured, multidisciplinary review process for translating tiered variant findings into an actual treatment recommendation, rather than assuming a tiered report alone is sufficient for direct clinical action — reflecting the genuine complexity of matching molecular findings to actual available, appropriate therapeutic options (potentially including the basket/umbrella trial matching discussed in category 5.8).
- Should address data privacy and governance requirements (category 8.1-8.2) for how genomic results flow into and are stored within the EHR (category 4.9), including secondary findings policy if germline testing is also involved.
- Should explicitly build in a mechanism for handling variant reclassification over time (category 3.9) — a workflow that treats a reported variant classification as permanently fixed rather than potentially subject to future revision is incomplete.
- A strong answer proactively addresses turnaround time and the practical clinical urgency of oncology decision-making, and how the workflow balances thoroughness against the real clinical cost of delay.

---

### 10.2 🟡 A hospital administrator asks you to build a business case for adopting a new, expensive genomic testing panel, based primarily on the panel's impressive analytical performance metrics from the manufacturer's validation studies. How would you approach evaluating and communicating whether this investment is actually justified?

**What a strong answer covers:**
- Should immediately apply the analytical validity / clinical validity / clinical utility framework discussed in category 6.13 and 7.14, explicitly noting that strong analytical performance alone doesn't establish clinical utility.
- Should specifically scrutinize the manufacturer's validation study methodology (echoing the skepticism discussed in category 7.14 and 9.12) — was the study population genuinely representative of the intended real-world use population, was performance externally validated, and is the reported performance metric (AUC, sensitivity) actually translated into the clinically and financially relevant metrics (positive predictive value at realistic prevalence, per category 7.11; actual impact on treatment decisions and outcomes) the business case genuinely needs.
- Should address whether the panel is a formally-designated companion diagnostic with regulatory-recognized clinical evidence (category 7.2) versus a laboratory-developed test with less formal regulatory validation (category 7.12), which has real implications for the strength of evidence actually available.
- Should propose a genuinely quantified cost-benefit framing that accounts for the full pathway from test result to actual clinical action and outcome, not just the test's standalone technical performance — echoing the clinical utility standard discussed throughout categories 6 and 7.
- Should communicate this analysis honestly and directly to the administrator, even if it means concluding the available evidence doesn't yet clearly support the requested business case, rather than constructing a favorable-sounding case that outruns the actual evidence.

---

### 10.3 🔴 You're reviewing a colleague's retrospective analysis before it's submitted for publication. The analysis reports a novel, statistically significant association between a specific polygenic risk score and treatment response, developed and validated entirely within a single-ancestry patient cohort. How do you approach this review?

**What a strong answer covers:**
- Should directly apply the portability problem discussed in category 9.2, specifically flagging that a finding developed and validated within a single ancestry population cannot be assumed to generalize to other populations, and that this limitation needs to be explicitly and prominently stated in the paper rather than left implicit or unaddressed.
- Should apply the internal-versus-external validation distinction from category 9.4, checking whether the reported validation genuinely used an independent dataset or only internal cross-validation within the same original cohort.
- Should probe for the label leakage (9.8), immortal time bias (4.6), and general confounding (5.6-5.7) concerns relevant to any retrospective association analysis, applying the same rigor discussed in category 4.14 and 5.18.
- Should raise these concerns constructively and specifically (per the general review-conduct principles discussed in other repos in this series) — citing exactly what's under-supported and what specific additional analysis or explicit limitation-acknowledgment would address the concern, rather than vaguely gesturing at "this needs more rigor."
- A strong answer recognizes that flagging these limitations doesn't mean the finding lacks value — a well-caveated, honestly-limited finding can still be a legitimate, valuable contribution as a hypothesis-generating result, provided it's communicated with appropriate, explicit acknowledgment of its actual evidentiary strength and scope.

---

### 10.4 🟡 A pharmaceutical company is designing a Phase 2 clinical trial for a new targeted therapy and asks for your input on whether to use a basket trial design (testing across multiple cancer types sharing a target mutation) or a more conventional single-cancer-type trial design. Walk through your reasoning.

**What a strong answer covers:**
- Should directly apply the basket trial concept and its underlying motivation discussed in category 5.8, specifically reasoning about the target mutation's expected frequency across different cancer types and whether a single-cancer-type approach could feasibly achieve adequate statistical power (category 5.5) on its own.
- Should raise the genuine complexity and potential heterogeneity risk of a basket design — the same molecular alteration may not necessarily behave identically or predict identical treatment response across genuinely different cancer types and tissue contexts, meaning a basket design's aggregate result could potentially mask meaningful cancer-type-specific heterogeneity in actual treatment effect, a real methodological tradeoff worth explicitly surfacing rather than treating basket designs as a strictly superior default choice.
- Should discuss the adaptive design elements (category 5.9) that might reasonably be incorporated regardless of the basic basket-versus-conventional choice.
- Should propose what specific evidence or preliminary data (existing biological rationale for the target's relevance across the specific cancer types being considered, any available preliminary efficacy signal) would most usefully inform this specific design decision, rather than treating it as a purely abstract methodological choice divorced from the specific biological and clinical context at hand.

---

### 10.5 🔴 Two team members disagree about a precision medicine dashboard your team is building for clinicians: one wants to prominently display machine-learning-derived treatment response predictions (from a model with good but not extensively externally validated performance) directly and prominently in the clinical workflow; the other is concerned this could lead to inappropriate over-reliance on an insufficiently validated tool. How would you help resolve this disagreement?

**What a strong answer covers:**
- Should take both positions seriously, echoing the disagreement-navigation approach modeled throughout this series of repos, rather than assuming either position is simply correct.
- The prominent-display position's legitimate case: a genuinely useful predictive signal, even if not yet extensively externally validated, could provide real clinical value, and burying potentially useful information in a way that makes it hard for clinicians to actually notice and use could waste a real opportunity to improve care.
- The caution position's legitimate case: echoing the black-box and interpretability concerns discussed in category 9.6, and the external validation concerns discussed in 9.4 and 9.12, prominently displaying an insufficiently validated prediction risks exactly the kind of alert-fatigue-adjacent over-reliance discussed in category 6.10, where clinicians may reasonably but mistakenly treat a prominently-displayed model output as more clinically authoritative and well-established than the underlying evidence actually supports.
- A strong answer proposes a resolution grounded in explicitly and transparently communicating the model's actual validation status and appropriate confidence level directly within the interface itself (rather than either fully suppressing potentially useful information or presenting it without appropriate epistemic humility), echoing the general principle that user-facing communication of a genuinely uncertain or incompletely validated finding should make that uncertainty legible rather than either hiding it or glossing over it — and should propose this as a starting point for a broader, ongoing external validation effort (per category 9.4) specifically aimed at eventually supporting a more prominent, higher-confidence display once that additional evidence is actually established, rather than treating the initial display decision as a permanently fixed choice.

---
