# 🌟 Decoding the Mirage: A Pipeline-Oriented Survey of Hallucinations in MLLMs (Awesome-MLLMs-Hallucination)

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)


> A comprehensive, up-to-date, and pipeline-oriented survey on hallucinations in Multimodal Large Language Models (MLLMs). This repository systematically categorizes publication trends, root causes, mitigation strategies, and evaluation benchmarks.

---

## 📑 Table of Contents
- [📊 Publication Statistics](#-publication-statistics)
- [🧠 Causes of Hallucination](#-causes-of-hallucination)
- [📚 Survey](#-survey)
- [🛡️ Hallucination Mitigation](#️-hallucination-mitigation)
    - [Training & Alignment](#training--alignment)
    - [Decoding Strategies](#decoding-strategies)
    - [Attention & Architecture Intervention](#attention--architecture-intervention)
    - [External Augmentation & Prompting](#external-augmentation--prompting)
- [🎯 Evaluation Benchmark](#-evaluation-benchmark)
- [📝 Citation](#-citation)
- [🤝 Contributing](#-contributing)

---

## 📊 Publication Statistics

<p align="center">
  <img src="./paper_number.png" width="85%" alt="Publication Trend Bar Chart" />
</p>

<p align="center">
  <img src="./method_tree.png" width="85%" alt="Methodology Distribution Tree" />
</p>

The rapid growth of research on Multimodal Large Language Model (MLLM) hallucinations. *(Updated to July 23, 2026)*

| Year | Mitigation Methods | Evaluation Benchmarks | Surveys & Reviews | **Total Papers** |
| :---: | :---: | :---: | :---: | :---: |
| **2018** | 0 | 1 | 0 | **1** |
| **2023** | 17 | 17 | 0 | **34** |
| **2024** | 96 | 50 | 3 | **149** |
| **2025** | 136 | 23 | 3 | **162** |
| **2026** | 127 | 27 | 1 | **155** |
| **Total**| **376** | **118** | **7** | **501** |

> 💡 **Tip:** The year represents the initial arXiv publication date or the conference acceptance date. The statistics charts are auto-generated. You can reproduce or update them by running our python scripts using Matplotlib.

---

## 🧠 Causes of Hallucination

<p align="center">
  <img src="./hall_cause.png" width="85%" alt="Hierarchical Causes of Hallucination in MLLMs" />
</p>

The hallucinations in Multimodal Large Language Models (MLLMs) are systemic issues that compound across the entire pipeline, from initial data input to the final generated text. Based on the hierarchical framework illustrated above, the fundamental causes can be categorized into five distinct levels:

| Hierarchical Level | Specific Causes | Description |
| :--- | :--- | :--- |
| **1. Data-Level**<br>*(Foundational Issues)* | Data Bias / Priors | Overrepresentation of specific patterns or stereotypical object/social pairs (e.g., assuming a "keyboard" is always with a "monitor") creates a skewed distribution. |
| | Data Scarcity / Fidelity | Incomplete, noisy, or low-resolution datasets lead to poor generalization. |
| **2. Token-Level**<br>*(Interaction Issues)* | Cross-Modal Attention Sparsity | Text tokens dominate the attention mechanism, causing the model to ignore or only weakly attend to visual tokens. |
| | Visual Token Redundancy | Excessive, noisy, and overlapping visual tokens create information overload and confusion, leading to imbalanced cross-modal representation. |
| **3. Module-Level**<br>*(Architectural Limitations)* | Vision Encoder: Limited Resolution | Hardware constraints or specific architecture choices result in the loss of fine-grained visual details. |
| | Projector: Inadequate Projection | Information bottlenecks in the connector lead to information loss, noise injection, or misalignment during modality mapping. |
| **4. Model-Level**<br>*(Core LLM Issues)* | Suboptimal Training Objective | The autoregressive next-token prediction path favors linguistic plausibility over factual correctness. |
| | Sampling Stochasticity | Randomness in the decoding process (e.g., Top-p/Top-k sampling) can result in selecting low-probability or incorrect tokens over correct/factual ones. |
| **5. Response-Level**<br>*(Final Output Manifestation)* | Sycophancy | To maximize user agreement and appear helpful/compliant, the model agrees with the user's biased or incorrect premise (e.g., agreeing that the sky is green). |
| | Contextual Inertia / Snowball Effect | Initial small errors (e.g., "The cat is flying") propagate and amplify throughout the generation like a snowball, leading to an elaborately fabricated response (compounded hallucination). |

---

## 📚 Survey

### I. Foundations and Comprehensive Surveys of Hallucination in LLMs
1. [Survey of Hallucination in Natural Language Generation](https://arxiv.org/pdf/2202.03629.pdf) (2022.02.07)
2. [Siren's Song in the AI Ocean: A Survey on Hallucination in Large Language Models](https://arxiv.org/pdf/2309.01219.pdf) (2023.09.03)
3. [A Survey of Hallucination in Large Foundation Models](https://arxiv.org/pdf/2309.05922.pdf) (2023.09.11)
4. [Cognitive Mirage: A Review of Hallucinations in Large Language Models](https://arxiv.org/pdf/2309.06794.pdf) (2023.09.13)
5. [LightHouse: A Survey of AGI Hallucination](https://arxiv.org/pdf/2401.06792.pdf) (2024.01.08)
6. [Loki's Dance of Illusions: A Comprehensive Survey of Hallucination in Large Language Models](https://arxiv.org/pdf/2507.02870.pdf) (2025.07.06)
7. [A Comprehensive Taxonomy of Hallucinations in Large Language Models](https://arxiv.org/pdf/2508.01781) (2025.08.03)
8. [Large Language Models Hallucination: A Comprehensive Survey](https://arxiv.org/pdf/2510.06265.pdf) (2025.10.05)
9. [A Concise Review of Hallucinations in LLMs and their Mitigation](https://arxiv.org/pdf/2512.02527) (2025.12.02)

### II. Core Surveys on Hallucination in MLLMs/VLMs
10. **[A Survey on Hallucination in Large Vision-Language Models](https://arxiv.org/pdf/2402.00253.pdf) (2024.02.01)**
11. **[Hallucination of Multimodal Large Language Models: A Survey](https://arxiv.org/pdf/2404.18930.pdf) (2024.04.29)**
12. **[Unveiling Hallucination in Text, Image, Video, and Audio Foundation Models: A Comprehensive Survey](https://arxiv.org/pdf/2405.09589.pdf) (2024.05.20)**
13. **[Review of Hallucination Understanding in Large Language and Vision Models](https://arxiv.org/pdf/2510.00034.pdf) (2025.09.26)**
14. [From Perception to Cognition: A Survey of Vision-Language Interactive Reasoning in Multimodal Large Language Models](https://arxiv.org/pdf/2509.25373.pdf) (2025.09.29)
15. **[Distorted or Fabricated? A Survey on Hallucination in Video LLMs](https://arxiv.org/pdf/2604.12944) (2026.04.14)**

### III. Hallucination Evaluation, Detection, and Benchmarks
16. **[Benchmark Evaluations, Applications, and Challenges of Large Vision Language Models: A Survey](https://arxiv.org/pdf/2501.02189.pdf) (2025.01.04)**
17. **[A Survey of Multimodal Hallucination Evaluation and Detection](https://arxiv.org/pdf/2507.19024.pdf) (2025.07.25)**
18. [Hallucination to Truth: A Review of Fact-Checking and Factuality Evaluation in Large Language Models](https://arxiv.org/pdf/2508.03860) (2025.08.05)

### IV. Hallucination Mitigation, RAG Augmentation, and Agents
19. [A Comprehensive Survey of Hallucination Mitigation Techniques in Large Language Models](https://arxiv.org/pdf/2401.01313.pdf) (2024.01.02)
20. [Towards Trustworthy Retrieval Augmented Generation for Large Language Models: A Survey](https://arxiv.org/pdf/2502.06872.pdf) (2025.02.08)
21. [Ask in Any Modality: A Comprehensive Survey on Multimodal Retrieval-Augmented Generation](https://arxiv.org/pdf/2502.08826.pdf) (2025.02.12)
22. [LLM-based Agents Suffer from Hallucinations: A Survey of Taxonomy, Methods, and Directions](https://arxiv.org/pdf/2509.18970.pdf) (2025.09.26)
23. [Mitigating Hallucination in Large Language Models (LLMs): An Application-Oriented Survey on RAG, Reasoning, and Agentic Systems](https://arxiv.org/pdf/2510.24476.pdf) (2025.10.28)
24. [Attribution Techniques for Mitigating Hallucinated Information in RAG Systems: A Survey](https://arxiv.org/pdf/2601.19927.pdf) (2026.01.10)
25. [Explainable Hallucination Mitigation in Large Language Models: A Survey](https://doi.org/10.1002/widm.70110) (2026.07.01)

### V. Domain-Specific Applications and Novel Perspectives
26. [A Survey on Large Language Model Hallucination via a Creativity Perspective](https://arxiv.org/pdf/2402.06647.pdf) (2024.02.02)
27. [A Survey of LLM-based Agents in Medicine: How far are we from Baymax?](https://arxiv.org/pdf/2502.11211.pdf) (2025.02.16)
28. [Medical Hallucinations in Foundation Models and Their Impact on Healthcare](https://arxiv.org/pdf/2503.05777.pdf) (2025.02.26)
29. [A Systematic Literature Review of Code Hallucinations in LLMs](https://arxiv.org/pdf/2511.00776) (2025.11.02)
30. [Trustworthiness Evaluation of Medical Vision-Language Models: A Scoping Review of Robustness, Grounding, Hallucination, and Uncertainty](https://doi.org/10.2196/preprints.102330) (2026.05.25)
31. [Phantom References: Hallucinated Citations That Survive Peer Review at Top-Tier Conferences](https://arxiv.org/pdf/2607.00738) (2026.07.01)


---

## 🛡️ Hallucination Mitigation 

*Click on each category to expand and view the detailed summary of papers.*

<details open>
<summary><h3>⚖️ Training & Alignment</h3></summary>

*Basis: Actually updates the underlying weights of the model through pre-training, instruction tuning, reinforcement learning, or preference optimization (e.g., DPO).*

| Method | Pub | Date | Methodology |
| :--- | :--- | :--- | :--- |
| [ObjMLM](https://arxiv.org/pdf/2210.07688.pdf) | arXiv'23 | 2023.2.10 | **Pre-training**: Proposes a novel vision-language pre-training (VLP) objective to suppress hallucinations. |
| [MMCoT](https://arxiv.org/pdf/2302.00923.pdf) | arXiv'23 | 2023.2.17 | **Fine-tuning**: Adopts a two-stage fine-tuning framework, training the model to generate a CoT reasoning process before the answer. |
| [LRV-GAVIE](https://arxiv.org/pdf/2306.14565.pdf) | **ICLR'24** | 2023.6.26 | **Instruction Tuning**: Constructs a robust instruction tuning dataset with positive and negative samples to update the model. |
| [LLaVA-RLHF](https://arxiv.org/pdf/2309.14525.pdf) | **ACL'24** | 2023.9.25 | **RLHF**: Introduces a factually augmented mechanism, using reinforcement learning from human feedback to align the model. |
| [VOLCANO](https://arxiv.org/pdf/2311.07362.pdf) | **NAACL'24** | 2023.11.14 | **Fine-tuning**: Specifically trains the MLLM to generate self-feedback and revise its output based on it. |
| [HalluciDoctor](https://arxiv.org/pdf/2311.13614.pdf) | **CVPR'24** | 2023.11.22 | **Data Curation**: Cleans "hallucinatory toxicity" in existing visual instruction datasets and generates counterfactual data for fine-tuning. |
| [RAH-Bench](https://arxiv.org/pdf/2311.16479.pdf) | arXiv'23 | 2023.11.27 | **Instruction Tuning**: Constructs a fine-grained RAI-30k dataset and integrates the SAM model during instruction tuning. |
| [HA-DPO](https://arxiv.org/pdf/2311.16839.pdf) | **ICME'24** | 2023.11.28 | **Preference Optimization**: Constructs hallucination-aware data pairs and applies the DPO algorithm directly to update model weights. |
| [FGHE](https://arxiv.org/pdf/2312.01701.pdf) | arXiv'23 | 2023.12.4 | **Fine-tuning**: Uses ChatGPT to rewrite image captions for data construction and performs two-stage fine-tuning. |
| [RLHF-V](https://arxiv.org/pdf/2312.00849.pdf) | **CVPR'24** | 2023.12.1 | **RLHF**: Collects fine-grained, segment-level human correctional feedback for reward modeling and PPO optimization. |
| [MOCHa](https://arxiv.org/pdf/2312.03631.pdf) | arXiv'23 | 2023.12.6 | **RLHF**: Trains a reward model based on Natural Language Inference (NLI) and uses RL to fine-tune the MLLM. |
| [HACL](https://arxiv.org/pdf/2312.06968.pdf) | arXiv'23 | 2023.12.12 | **Contrastive Learning**: Introduces a hallucination-augmented contrastive learning loss function during the training phase. |
| [SILKIE](https://arxiv.org/pdf/2312.10665.pdf) | arXiv'23 | 2023.12.17 | **Preference Distillation**: Uses AI to construct the VLFeedback dataset and distills preferences into the model via DPO. |
| [KAM-CoT](https://arxiv.org/pdf/2401.12863.pdf) | arXiv'24 | 2024.1.23 | **Joint Training**: Jointly trains a language model, a vision encoder, and a Graph Neural Network (GNN) to integrate knowledge graphs for reasoning. |
| [ViGoR](https://arxiv.org/pdf/2402.06118.pdf) | **CVPR'24** | 2024.2.9 | **Reward Modeling**: Trains a fine-grained visual reward model to guide the model toward better visual alignment. |
| [IDK-Instructions](https://arxiv.org/pdf/2402.09717.pdf) | **ACL'24** | 2024.2.15 | **Instruction Tuning**: Teaches the model to actively output "I don't know" when evidence is insufficient via specialized instruction tuning. |
| [EFUF](https://arxiv.org/pdf/2402.09801.pdf) | arXiv'24 | 2024.2.15 | **Unlearning**: Proposes an efficient fine-grained unlearning framework to "forget" the tendency to hallucinate via reverse parameter updates. |
| [POVID](https://arxiv.org/pdf/2402.11411.pdf) | **NeurIPS'24** | 2024.2.18 | **Preference Fine-tuning**: Constructs a preference-based dataset to align the model with high-quality image descriptions via preference fine-tuning. |
| [Less is More](https://arxiv.org/pdf/2402.14545.pdf) | **ACL'24** | 2024.2.22 | **Instruction Tuning**: Reconstructs the fine-tuning dataset to teach the model to output the End-Of-Sequence (EOS) token early to truncate generation. |
| [AIT](https://arxiv.org/pdf/2403.10492.pdf) | **ACL'24** | 2024.3.15 | **Instruction Tuning**: Introduces adversarial instruction tuning to improve model robustness against misleading user queries. |
| [FGAIF](https://arxiv.org/pdf/2404.05046.pdf) | arXiv'24 | 2024.4.7 | **Preference Optimization**: Uses fine-grained AI feedback to construct preference data and applies DPO for alignment training. |
| [Prescribing the Right Remedy](https://arxiv.org/pdf/2404.10332.pdf) | arXiv'24 | 2024.4.16 | **Fine-tuning**: Constructs targeted repair instruction datasets for different hallucination types to perform targeted fine-tuning. |
| [FACT](https://arxiv.org/pdf/2404.11129) | arXiv'24 | 2024.4.17 | **Rationale Training**: Introduces faithful and concise reasoning rationales as supervision signals during training to enhance logical generation. |
| [TextSquare](https://arxiv.org/pdf/2404.12803) | arXiv'24 | 2024.4.19 | **Instruction Tuning**: Massively scales up text-centric visual instruction tuning data to specifically address text hallucinations in OCR tasks. |
| [HSA-DPO](https://arxiv.org/pdf/2404.14233) | arXiv'24 | 2024.4.22 | **Preference Optimization**: Proposes hallucination-aware DPO, utilizing fine-grained AI feedback to construct positive and negative pairs for weight updates. |
| [CSR](https://arxiv.org/pdf/2405.14622) | **NeurIPS'24** | 2024.5.23 | **Self-Rewarding Learning**: Proposes a self-calibrating reward mechanism enabling iterative self-generated feedback and preference alignment. |
| [HIO](https://arxiv.org/pdf/2405.15356) | arXiv'24 | 2024.5.24 | **Contrastive Tuning**: Introduces a hallucination-inducing mechanism during training to construct sample pairs for parameter optimization. |
| [RLAIF-V](https://arxiv.org/pdf/2405.17220) | arXiv'24 | 2024.5.27 | **RLAIF**: Utilizes fine-grained feedback from open-source AIs to build a preference dataset and updates weights using alignment algorithms. |
| [HALVA](https://arxiv.org/pdf/2405.18654) | arXiv'24 | 2024.5.28 | **Contrastive Tuning**: Constructs hard negative samples via data augmentation and introduces a contrastive loss to strengthen visual grounding. |
| [mDPO](https://arxiv.org/pdf/2406.11839) | arXiv'24 | 2024.6.17 | **Preference Optimization**: Proposes a conditional preference optimization algorithm to reduce hallucinations without degrading general capabilities. |
| [BDHS](https://arxiv.org/pdf/2407.02477) | arXiv'24 | 2024.7.2 | **Fine-tuning**: Systematically builds datasets covering various alignment strategies to empirically verify their impact on hallucinations. |
| [REVERIE](https://arxiv.org/pdf/2407.11422) | **ECCV'24** | 2024.7.16 | **Instruction Tuning**: Constructs a reflective instruction dataset to teach the model to perform internal visual fact-checking before outputting answers. |
| [MHR](https://arxiv.org/pdf/2408.00550) | arXiv'24 | 2024.8.1 | **Instruction Tuning**: Builds a correctional dataset specifically for multilingual scenarios to mitigate cross-lingual hallucinations caused by language bias. |
| [CLIP-DPO](https://arxiv.org/pdf/2408.10433) | arXiv'24 | 2024.8.19 | **Preference Optimization**: Uses a pre-trained CLIP model directly as an AI judge to generate preference pairs for DPO training. |
| [RoVRM](https://arxiv.org/pdf/2408.12109) | arXiv'24 | 2024.8.22 | **Reward Modeling**: Optimizes a visual reward model using auxiliary text-only preference data during RLHF to enhance hallucination discrimination. |
| [See or Guess](https://arxiv.org/pdf/2408.16809) | arXiv'24 | 2024.8.29 | **Regularization Training**: Introduces a counterfactual regularization term during training to force distinction between seen visuals and guessed priors. |
| [FaithD2T](https://arxiv.org/pdf/2409.03961) | arXiv'24 | 2024.9.6 | **Fine-tuning**: Constructs a multimodal factual consistency dataset and fine-tunes the model to improve faithfulness in data-to-text generation. |
| [HELPD](https://arxiv.org/pdf/2409.20429) | arXiv'24 | 2024.9.30 | **Feedback Learning**: Proposes a fine-tuning framework combining vision-enhanced penalty decoding with hierarchical feedback learning for behavior alignment. |
| [OHD-Caps](https://arxiv.org/pdf/2410.03176) | **EMNLP'24** | 2024.10.4 | **Pre-training Intervention**: Cleans and rewrites captions in CLIP pre-training data to reduce object hallucinations at the vision-language source. |
| [Fine-Grained Verifiers](https://arxiv.org/pdf/2410.14148) | arXiv'24 | 2024.10.18 | **Preference Modeling**: Formulates preference modeling as a next-token prediction task to update the model using fine-grained verifier data. |
| [MFPO](https://arxiv.org/pdf/2410.15334) | arXiv'24 | 2024.10.20 | **Preference Optimization**: Proposes a modality-fair preference optimization algorithm to balance penalties and prevent language prior dominance. |
| [V-DPO](https://arxiv.org/pdf/2411.02712) | **EMNLP'24** | 2024.11.5 | **Preference Optimization**: Uses a vision-guided mechanism to construct high-quality positive and negative preference pairs for DPO. |
| [HDPO](https://arxiv.org/pdf/2411.10436) | arXiv'24 | 2024.11.15 | **Preference Optimization**: Generates targeted preference data specifically for hallucinations and applies DPO to penalize hallucination-prone features. |
| [Verb Mirage](https://arxiv.org/pdf/2412.04939) | arXiv'24 | 2024.12.6 | **Instruction Tuning**: Constructs a dataset targeting verb concept hallucinations and applies specific instruction tuning to correct action biases. |
| [TPO](https://arxiv.org/pdf/2412.14487) | arXiv'24 | 2024.12.19 | **Preference Optimization**: Proposes a token-level preference optimization strategy based on self-calibrated visual-anchored rewards. |
| [SENA](https://arxiv.org/pdf/2412.15650) | arXiv'24 | 2024.12.20 | **Self-Evolution Learning**: Automatically generates and filters high-quality alignment data through an iterative self-evolution mechanism. |
| [OPA-DPA](https://arxiv.org/search/cs?query=hallucination+vision+&searchtype=all&abstracts=show&order=-announced_date_first&size=50) | **CVPR'25** | 2025.1.16 | **Preference Optimization**: Demonstrates the critical role of on-policy data in DPO and constructs on-policy preference data to update parameters. |
| [CHiP](https://arxiv.org/pdf/2501.16629) | arXiv'25 | 2025.1.28 | **Preference Optimization**: Proposes cross-modal hierarchical DPO to penalize global image-text matching and local object features at different levels. |
| [RE-ALIGN](https://arxiv.org/pdf/2502.13146) | arXiv'25 | 2025.2.18 | **Preference Optimization**: Introduces Retrieval-Augmented Generation (RAG) into preference data construction to guide DPO training. |
| [Symmetrical Visual Contrastive Optimization](https://arxiv.org/pdf/2502.13928) | arXiv'25 | 2025.2.19 | **Contrastive Optimization**: Proposes symmetrical visual contrastive optimization using minimal contrastive images for alignment fine-tuning. |
| [PerturboLLaVA](https://arxiv.org/pdf/2503.06486) | arXiv'25 | 2025.3.9 | **Visual Perturbation Training**: Introduces subtle visual perturbations during training forward passes to force the learning of robust visual representations. |
| [HLPU](https://arxiv.org/pdf/2503.20673) | arXiv'25 | 2025.3.27 | **Negative Sample Fine-tuning**: Builds a low-level visual hallucination database and applies negative sampling to enhance awareness of low-level features. |
| [Critique Before Thinking](https://arxiv.org/pdf/2505.07172) | arXiv'25 | 2025.5.12 | **Instruction Tuning**: Adopts rationale-augmented instruction tuning to teach the model to generate critique logic before providing an answer. |
| [OViP](https://arxiv.org/pdf/2505.15963) | arXiv'25 | 2025.5.21 | **Preference Learning**: Proposes an online preference learning framework to dynamically generate preference pairs during training. |
| [BIMA](https://arxiv.org/pdf/2505.24649) | arXiv'25 | 2025.5.30 | **Maximum Likelihood Learning**: Employs a bijective maximum likelihood learning approach to suppress hallucinations by optimizing joint probability distributions. |
| [EMPO](https://arxiv.org/pdf/2506.04039) | arXiv'25 | 2025.6.4 | **Preference Optimization**: Proposes entity-centric multimodal preference optimization, focusing penalty granularity precisely on specific visual entity tokens. |
| [TL-DPO](https://arxiv.org/pdf/2506.11417) | arXiv'25 | 2025.6.13 | **Target-Localized DPO**: Stops learning redundant backgrounds and forces weight updates to focus exclusively on target areas causing hallucinations. |
| [SEED](https://arxiv.org/pdf/2507.04680) | arXiv'25 | 2025.7.7 | **Knowledge Distillation**: Identifies and purges hallucinated samples from fine-tuning data, using the refined high-quality data for knowledge distillation. |
| [ReLoop](https://arxiv.org/pdf/2507.04943) | arXiv'25 | 2025.7.7 | **Closed-loop Training**: Proposes a closed-loop framework where the model generates predictions, performs backward verification, and uses errors as training signals. |
| [Obliviate](https://arxiv.org/pdf/2508.04567) | arXiv'25 | 2025.8.6 | **Bias Unlearning**: Analyzes object biases introduced during pre-training and debiases the model using a reverse objective function during fine-tuning. |
| [TARS](https://arxiv.org/pdf/2507.21584) | arXiv'25 | 2025.8.9 | **Adaptive Preference Strategy**: Adopts an adaptive MinMax Token preference strategy to dynamically adjust reward allocation. |
| [CHAIR-DPO](https://arxiv.org/pdf/2508.20181) | arXiv'25 | 2025.8.27 | **Object-Aware DPO**: Integrates the CHAIR metric, utilizing object-level matching scores as the preference reward for DPO. |
| [VPFC](https://arxiv.org/pdf/2509.00371) | arXiv'25 | 2025.8.30 | **Decoupled Fine-Tuning**: Distinguishes "omission" and "fabrication" hallucination causes and constructs respective fine-tuning data for decoupled training. |
| [SCPO](https://arxiv.org/pdf/2509.24491) | arXiv'25 | 2025.9.29 | **Curriculum Preference Optimization**: Proposes semantic curriculum preference optimization, training the model in increasing difficulty to smoothly eliminate hallucinations. |
| [Unified Mitigation](https://arxiv.org/pdf/2511.17254v2) | arXiv'25 | 2025.11.21 | **Unified Alignment Framework**: Proposes a universal training framework across multiple alignment formats (e.g., DPO, PPO) to eliminate vision-language biases. |
| [Attention Guided Alignment](https://arxiv.org/pdf/2511.17793v1) | arXiv'25 | 2025.11.21 | **Attention-Guided Alignment**: Introduces an attention-based regularization term during fine-tuning to force the model to align with correct visual regions. |
| [Optimizing LVLMs with On-Policy Data](https://arxiv.org/pdf/2512.00706v1) | arXiv'25 | 2025.11.30 | **On-Policy Optimization**: Emphasizes using on-the-fly model-generated data for alignment fine-tuning to mitigate distribution shifts. |
| [Mitigating Object and Action Hallucinations](https://arxiv.org/pdf/2512.04356v1) | arXiv'25 | 2025.12.04 | **Contrastive Alignment**: Constructs multimodal action and object contrastive data via self-augmentation for alignment training. |
| [Cost-efficient Difficulty-aware Preference Optimization](https://arxiv.org/pdf/2601.00623v1) | arXiv'26 | 2026.01.02 | **Difficulty-Aware DPO**: Introduces a difficulty-aware mechanism for low-cost preference optimization, prioritizing hard hallucination samples. |
| [Beyond Superficial Unlearning](https://arxiv.org/pdf/2601.16527v1) | arXiv'26 | 2026.01.23 | **Robust Unlearning**: Proposes a sharpness-aware unlearning mechanism to thoroughly erase deep associations causing hallucinations in model parameters. |
| [IRIS](https://arxiv.org/pdf/2602.01769) | arXiv'26 | 2026.02.02 | **On-Policy Preference Optimization**: Sifts self-generated pairs with continuous implicit rewards that expose fine-grained modal competition. |
| [Seeing Through the Chain](https://arxiv.org/pdf/2602.03380) | arXiv'26 | 2026.02.03 | **CoT Preference Optimization**: Compresses redundant reasoning tokens and applies contrastive preference optimization to hallucination-inducing traces. |
| [HII-DPO](https://arxiv.org/pdf/2602.10425) | arXiv'26 | 2026.02.11 | **Counterfactual Preference Alignment**: Synthesizes scene-conditioned hallucination-inducing images to construct fine-grained preference pairs. |
| [MIRROR](https://arxiv.org/pdf/2602.18746) | arXiv'26 | 2026.02.21 | **Reflective Supervision**: Trains closed-loop drafting, critique, region verification, and revision with the ReflectV multi-turn dataset. |
| [CCCaption](https://arxiv.org/pdf/2602.21655) | arXiv'26 | 2026.02.25 | **Dual-Reward Reinforcement Learning**: Jointly rewards visual completeness and penalizes hallucinated sub-caption claims. |
| [Hallucination-Resistant Multimodal Content Generation](https://doi.org/10.1016/j.inffus.2025.103783) | **Information Fusion'26** | 2026.03 | **Knowledge-Graph Reinforcement Learning**: Grounds multimodal generation in structured knowledge and optimizes graph-based rewards to suppress unsupported content. |
| [MoD-DPO](https://arxiv.org/pdf/2603.03192) | arXiv'26 | 2026.03.03 | **Modality-Decoupled DPO**: Enforces sensitivity to relevant modalities and invariance to irrelevant audiovisual corruption while debiasing language priors. |
| [Adaptive Hallucination Alleviation](https://doi.org/10.1609/aaai.v40i32.39955) | **AAAI'26** | 2026.03.14 | **Severity-Guided DPO**: Selects hallucination-oriented samples, assigns severity-specific loss weights, and modulates localized visual attention during HD-DPO. |
| [EchoBat](https://doi.org/10.1609/aaai.v40i42.40875) | **AAAI'26** | 2026.03.14 | **Audiovisual Preference Optimization**: Builds temporally grounded video preferences from visual and audio evidence and improves supervision with echo-layered keyframe sampling. |
| [FINER-Tuning](https://arxiv.org/pdf/2603.17662) | arXiv'26 | 2026.03.18 | **Fine-Grained DPO**: Trains on hard negative queries spanning object, attribute, and relation mismatches to reduce subtle hallucinations. |
| [VRE](https://arxiv.org/pdf/2603.26348) | arXiv'26 | 2026.03.27 | **Self-Evolving Visual Re-Examination**: Learns reflection traces that reactivate late-stage visual verification during long-chain reasoning. |
| [AVES-DPO](https://arxiv.org/pdf/2604.24395) | arXiv'26 | 2026.04.27 | **Verified Self-Correction DPO**: Builds in-distribution preference pairs through consensus diagnosis and model-native self-correction. |
| [OSCAR](https://arxiv.org/pdf/2605.00323) | arXiv'26 | 2026.05.01 | **Online Self-Calibration**: Uses tree search and dual-granularity rewards to generate online preference data for iterative DPO. |
| [UE-DPO](https://arxiv.org/pdf/2605.04874) | arXiv'26 | 2026.05.06 | **Uncertainty-Aware DPO**: Concentrates learning pressure on visually deficient tokens using token-level epistemic uncertainty. |
| [Stage-wise Preference Optimization](https://arxiv.org/pdf/2605.16411) | arXiv'26 | 2026.05.13 | **Failure-Boundary DPO**: Progressively constructs minimally perturbed preference pairs around spatial, relational, OCR, and false-premise errors. |
| [Emphasizing Image-Negative Tokens](https://arxiv.org/pdf/2605.21300) | arXiv'26 | 2026.05.20 | **Visual-Dependence Reweighting**: Reweights training tokens by image dependence and filters hallucination-prone samples. |
| [RC-DPO](https://arxiv.org/pdf/2605.27906) | arXiv'26 | 2026.05.27 | **Reasoning-Conditioned DPO**: Separately optimizes CoT quality by contrasting the same answer under grounded and pruned reasoning traces. |
| [P²-DPO](https://arxiv.org/pdf/2606.03376) | arXiv'26 | 2026.06.02 | **Perceptual Processing DPO**: Learns on-policy focus-and-enhance preferences with calibration loss for visually causal token generation. |
| [VGL-DPO](https://doi.org/10.1145/3796715) | **TOMM'26** | 2026.06.24 | **Vision-Guided Lexical DPO**: Reweights positive words by visual relevance and adapts the negative preference loss using lexical importance differences. |
| [VIGIL](https://arxiv.org/pdf/2606.26387) | arXiv'26 | 2026.06.24 | **Counterfactual Visual Alignment**: Penalizes confidence under masked visual attention to maximize visual information gain during RL post-training. |
| [ViPSy](https://arxiv.org/pdf/2606.28401) | arXiv'26 | 2026.06.24 | **Vision-Driven Preference Synthesis**: Derives recurring visual cues across aligned image variants and conditions policy-native rollouts on them. |
| [Reflect-R1](https://arxiv.org/pdf/2606.27922) | arXiv'26 | 2026.06.26 | **Stage-Decoupled Reinforcement Learning**: Trains intuition, evidence verification, and arbitration stages independently for long-video self-correction. |
| [OPPO](https://arxiv.org/pdf/2606.29805) | arXiv'26 | 2026.06.29 | **Evidence-Strength Preference Optimization**: Orders preference views by visual-evidence strength and adds span- and token-level regularization. |
| [ADAPT](https://arxiv.org/pdf/2606.31054) | arXiv'26 | 2026.06.30 | **Attention Dynamics Alignment**: Combines cross-attention anchors, online drift correction, and visual-attention-guided DPO. |
| [CORAL](https://arxiv.org/pdf/2607.03647) | arXiv'26 | 2026.07.04 | **Hard-Negative Contrastive Training**: Penalizes answer invariance under medically plausible but visually incorrect image substitutions. |
| [Groc-PO](https://arxiv.org/pdf/2607.13712) | arXiv'26 | 2026.07.15 | **Grounded Context Preference Optimization**: Assigns stage-specific preferences to object grounding, contextual grounding, and grounded reasoning. |

</details>

<details>
<summary><h3>🎛️ Decoding Strategies</h3></summary>

*Basis: Entirely training-free. Intervenes in the autoregressive generation phase (Logits layer) by ensembling probabilities, contrasting samples, or calibrating confidence to suppress hallucinations.*

| Method | Pub | Date | Methodology |
| :--- | :--- | :--- | :--- |
| [HallE-Switch](https://arxiv.org/pdf/2310.01779.pdf) | arXiv'23 | 2023.10.3 | **Inference Intervention**: Introduces a control parameter during decoding to force switching between pure contextual description and parameterized knowledge imagination. |
| [VCD](https://arxiv.org/pdf/2311.16922.pdf) | **CVPR'24** | 2023.11.28 | **Contrastive Decoding**: Penalizes decoding by contrasting the logit output distributions of original and distorted images during inference. |
| [MARINE](https://arxiv.org/pdf/2402.08680.pdf) | **CVPR'24** | 2024.2.13 | **Inference Guidance**: Introduces Classifier-Free Guidance (CFG) during inference to amplify the influence of visual features in the generation process. |
| [CGD](https://arxiv.org/pdf/2402.15300.pdf) | arXiv'24 | 2024.2.23 | **External Guided Decoding**: Introduces an external CLIP model to score and guide candidate tokens during decoding to improve image-text consistency. |
| [IBD](https://arxiv.org/pdf/2402.18476.pdf) | **ECCV'24** | 2024.2.28 | **Image-Biased Decoding**: Penalizes pure language priors by contrasting the logits of inputs with and without images. |
| [HALC](https://arxiv.org/pdf/2403.00425.pdf) | **ICML'24** | 2024.3.1 | **Focal Contrastive Decoding**: Proposes adaptive focal-contrast decoding to fine-grainedly suppress hallucinations at the local token level. |
| [M3ID](https://arxiv.org/pdf/2403.14003.pdf) | **CVPR'24** | 2024.3.20 | **Visual Information Contrast**: Introduces a visual grounding mechanism during decoding to correct biases by contrasting different information streams. |
| [ICD](https://arxiv.org/pdf/2403.18715.pdf) | **ACL'24** | 2024.3.27 | **Instruction Contrastive Decoding**: Constructs positive and negative instructions, contrasting their logits during inference to guide decoding. |
| [CODE](https://arxiv.org/pdf/2406.01920v1) | arXiv'24 | 2024.6.4 | **Contrastive Decoding**: Contrasts logit distributions based on the original image versus self-generated descriptions to penalize text-reliant tokens. |
| [Residual Visual Decoding](https://arxiv.org/pdf/2407.00569) | **ACL'24** | 2024.6.30 | **Residual Decoding**: Introduces residual visual connections to add early visual features directly into subsequent decoding computations. |
| [VACoDe](https://arxiv.org/pdf/2408.05337) | arXiv'24 | 2024.7.26 | **Visual Augmented Contrastive Decoding**: Contrasts the logits of visually augmented images and original images to penalize inconsistent generations. |
| [SID](https://arxiv.org/pdf/2408.02032) | arXiv'24 | 2024.8.4 | **Self-Introspective Decoding**: Filters hallucinated words by comparing the confidence of different generation paths via the model's own introspective mechanism. |
| [LCD](https://arxiv.org/pdf/2408.04664) | arXiv'24 | 2024.8.6 | **Language Contrastive Decoding**: Constructs an image-free text input as a negative reference and subtracts language prior scores during logit calculation. |
| [LQCD](https://arxiv.org/pdf/2408.11261) | arXiv'24 | 2024.8.21 | **Contrastive Decoding**: Introduces language contrastive decoding to weaken misleading priors from user prompts to combat sycophancy-induced hallucinations. |
| [ConVis](https://arxiv.org/pdf/2408.13906) | **AAAI'25** | 2024.8.25 | **Visualized Contrastive Decoding**: Uses attention visualization to locate hallucination regions and constructs interference images for contrastive decoding. |
| [RBD](https://arxiv.org/pdf/2409.06485) | arXiv'24 | 2024.9.10 | **Re-Balancing Contrastive Decoding**: Dynamically adjusts the logit weight distribution of text and image features during inference. |
| [TCD](https://arxiv.org/pdf/2409.16597) | arXiv'24 | 2024.9.25 | **Temporal Contrastive Decoding**: Suppresses event hallucinations by contrasting output probabilities between full and truncated videos. |
| [SGD](https://arxiv.org/pdf/2410.13321) | arXiv'24 | 2024.10.17 | **Summary-Guided Decoding**: Utilizes image summaries as guidance signals to intervene in output probabilities for contextual consistency. |
| [CATCH](https://arxiv.org/pdf/2411.12713) | arXiv'24 | 2024.11.19 | **Adaptive Contrastive Decoding**: Dynamically switches contrastive penalty intensity based on local token features. |
| [VaLiD](https://arxiv.org/pdf/2411.15839) | arXiv'24 | 2024.11.24 | **Layer Fusion Contrastive Decoding**: Fuses deep and shallow visual signals for contrast to penalize language hallucinations during decoding. |
| [From Uncertainty to Trust](https://arxiv.org/pdf/2412.06474) | arXiv'24 | 2024.12.9 | **Dropout-Guided Decoding**: Utilizes uncertainty mechanisms to dynamically drop high-uncertainty tokens during generation. |
| [VCD Analysis](https://arxiv.org/pdf/2412.06775) | arXiv'24 | 2024.12.9 | **Mechanism Optimization**: Analyzes visual contrastive decoding and optimizes hyperparameters and sampling distributions to enhance suppression. |
| [VORD](https://arxiv.org/pdf/2412.15739) | arXiv'24 | 2024.12.20 | **Visual Ordinal Calibration**: Directly post-processes and calibrates logits during generation to mitigate overconfidence. |
| [IMCCD](https://arxiv.org/pdf/2501.01926) | arXiv'25 | 2025.1.3 | **Correlation Calibration Decoding**: Dynamically adjusts the correlation weights between text token generation probabilities and visual inputs. |
| [IFCD](https://arxiv.org/pdf/2502.01056) | arXiv'25 | 2025.2.3 | **Internal Fact Contrastive Decoding**: Extracts internally generated facts as references for contrastive decoding to suppress over-extrapolation. |
| [DeGF](https://arxiv.org/pdf/2502.06130) | **ICLR'25** | 2025.2.10 | **Self-Correcting Decoding**: Introduces a generative feedback loop to detect and correct the probability distribution of the current token in real time. |
| [Octopus](https://arxiv.org/pdf/2503.00361) | **CVPR'25** | 2025.3.1 | **Dynamic Contrastive Decoding**: Adaptively adjusts the contrastive penalty based on image complexity and local token features. |
| [Decoupling Contrastive Decoding](https://arxiv.org/pdf/2504.08809) | arXiv'25 | 2025.4.9 | **Decoupled Contrastive Decoding**: Decouples language penalties from visual enhancements in CD to handle complex hallucinations. |
| [ECD](https://arxiv.org/pdf/2504.12137) | arXiv'25 | 2025.4.16 | **Efficient Contrastive Decoding**: Combines probabilistic detection, triggering contrastive calculations only for tokens with high hallucination risks. |
| [CICD](https://arxiv.org/pdf/2505.10634) | arXiv'25 | 2025.5.20 | **Cross-Image Contrastive Decoding**: Losslessly suppresses language priors by contrasting logits from semantically similar but visually different images. |
| [ED](https://arxiv.org/pdf/2505.17529) | arXiv'25 | 2025.5.23 | **Attention-Guided Ensemble Decoding**: Integrates multiple generation paths processed with different attention masks. |
| [C-PMI](https://arxiv.org/pdf/2505.19678) | arXiv'25 | 2025.5.26 | **Mutual Information Calibration Decoding**: Reshapes candidate token probabilities by quantifying image-text Conditional Pointwise Mutual Information (PMI). |
| [RVCD](https://arxiv.org/pdf/2505.20569) | arXiv'25 | 2025.5.29 | **Retrieval Visual Contrastive Decoding**: Contrasts logits from the original image and retrieved similar reference images to highlight core facts. |
| [SECOND](https://arxiv.org/pdf/2506.08391) | arXiv'25 | 2025.6.10 | **Selective Contrastive Decoding**: Triggers penalty calculations only for specific perceptive vocabulary categories to avoid disrupting grammar. |
| [MoD](https://arxiv.org/pdf/2505.17061) | **ACL'25** | 2025.6.10 | **Mixture of Decoding**: Adaptively switches between different sampling algorithms based on attention strength. |
| [ReVisiT](https://arxiv.org/pdf/2506.09522) | arXiv'25 | 2025.6.11 | **Language Prior Guided Decoding**: Exposes language priors in visual tokens and uses them to guide the decoding direction. |
| [ASCD](https://arxiv.org/pdf/2506.14766) | arXiv'25 | 2025.6.17 | **Steerable Contrastive Decoding**: Dynamically alters the negative sample distribution for contrast based on underlying attention flows. |
| [DLC](https://arxiv.org/pdf/2506.21509) | arXiv'25 | 2025.6.26 | **Dynamic Logits Calibration**: Dynamically calibrates the output vocabulary in real-time based on multimodal feature responses. |
| [Energy-Guided Decoding](https://arxiv.org/pdf/2507.07731) | arXiv'25 | 2025.7.10 | **Energy-Guided Decoding**: Introduces a probability normalization term based on energy models for decoding constraints. |
| [INTER](https://arxiv.org/pdf/2507.05056) | arXiv'25 | 2025.7.22 | **Interaction Guidance Sampling**: Dynamically evaluates interaction strength between visual and text features to weight sampling probabilities. |
| [MRFD](https://arxiv.org/pdf/2508.10264) | arXiv'25 | 2025.8.14 | **Multi-Region Fusion Decoding**: Fuses feature logits from different local image regions combined with self-consistency during decoding. |
| [MRGD](https://arxiv.org/pdf/2508.11616) | arXiv'25 | 2025.8.15 | **Reward-Guided Decoding**: Introduces a lightweight reward model to score and reshape candidate token probabilities in real-time. |
| [LayerCD](https://arxiv.org/pdf/2509.25177) | arXiv'25 | 2025.9.29 | **Layer Contrastive Decoding**: Imposes penalties by contrasting logits from deep layers (language priors) and shallow layers (visual features). |
| [MaskCD](https://arxiv.org/pdf/2510.02790v1) | arXiv'25 | 2025.10.3 | **Masked Contrastive Decoding**: Masks specific image processing heads to construct negative distributions for contrastive calculation. |
| [Self-Augmented Visual Contrastive Decoding](https://arxiv.org/pdf/2510.13315v1) | arXiv'25 | 2025.10.15 | **Self-Augmented Contrastive Decoding**: The model self-generates augmented and decayed visual representations using internal features for CD. |
| [Watermarking for Factuality](https://arxiv.org/pdf/2510.14304v1) | arXiv'25 | 2025.10.16 | **Tri-layer Contrastive Decoding**: Combines factuality watermarking to guide outputs toward truth via contrast across three probability spaces. |
| [Token-Level Inference-Time Alignment](https://arxiv.org/pdf/2510.21794) | arXiv'25 | 2025.10.20 | **Inference-Time Alignment**: Applies a lightweight classifier to intervene alignment when generating each token. |
| [Beyond Single Models](https://arxiv.org/pdf/2510.18321v1) | arXiv'25 | 2025.10.21 | **Adaptive Ensemble Decoding**: Adaptively ensembles token probability distributions from multiple models during autoregression. |
| [Visual Inference-Time Intervention](https://arxiv.org/pdf/2512.03542v1) | arXiv'25 | 2025.12.03 | **Inference-Time Intervention**: Uses real-time feedback from visual features to block text generation inertia during decoding. |
| [Watch Closely](https://arxiv.org/pdf/2512.19070v1) | arXiv'25 | 2025.12.22 | **Disentangled Decoding**: Decouples attention mechanisms and output probabilities for independent calibration. |
| [CoFi-Dec](https://arxiv.org/pdf/2512.23453v1) | arXiv'25 | 2025.12.29 | **Coarse-to-Fine Feedback Decoding**: Generates multi-granularity hierarchical feedback to dynamically correct outputs. |
| [Med-VCD](https://doi.org/10.1016/j.compbiomed.2025.111347) | **Computers in Biology and Medicine'26** | 2026.01 | **Sparse Visual Contrastive Decoding**: Selects visually informed tokens on the fly, removing redundant tokens while retaining critical medical image context. |
| [Structure-Disrupted Contrastive Decoding](https://arxiv.org/pdf/2601.03500v1) | arXiv'26 | 2026.01.07 | **Structure-Disrupted Contrastive Decoding**: Contrasts the original image with a structure-broken image to highlight entity logic. |
| [Context-Aware Decoding](https://arxiv.org/pdf/2601.05939v1) | arXiv'26 | 2026.01.09 | **Context-Aware Decoding**: Dynamically adjusts the fusion ratio of visual and language logits based on the generated context length. |
| [Attention-space Contrastive Guidance](https://arxiv.org/pdf/2601.13707v1) | arXiv'26 | 2026.01.20 | **Attention-Space Contrastive Guidance**: Shifts the scope of the contrastive mechanism from the output logit layer to the attention space. |
| [Residual Decoding](https://arxiv.org/pdf/2602.01047v1) | arXiv'26 | 2026.02.01 | **Residual Guidance Decoding**: Uses history-aware residual information to guide current token generation for consistency. |
| [Model-Aware Contrastive Decoding](https://arxiv.org/pdf/2602.01740v1) | arXiv'26 | 2026.02.02 | **Model-Aware Contrastive Decoding**: Uses counterfactual data as negative references to apply adaptive contrastive penalties based on the model's perception tendencies. |
| [SAKED](https://arxiv.org/pdf/2602.09825) | arXiv'26 | 2026.02.10 | **Stability-Aware Decoding**: Contrasts stability-aware and unstable layers to suppress fluctuating internal knowledge during token generation. |
| [Mask What Matters](https://arxiv.org/pdf/2602.11737) | arXiv'26 | 2026.02.12 | **Object-Aligned VCD**: Removes the most salient object evidence to create a stronger auxiliary contrastive view. |
| [Causal Decoding](https://arxiv.org/pdf/2602.21441) | arXiv'26 | 2026.02.24 | **Causal Logit Intervention**: Reshapes decoding dynamics to attenuate spurious dependencies that trigger unsupported object tokens. |
| [NoLan](https://arxiv.org/pdf/2602.22144) | arXiv'26 | 2026.02.25 | **Language-Prior Suppression**: Dynamically calibrates logits using the distribution gap between multimodal and text-only inputs. |
| [Entropy-Optimized Contrastive Decoding](https://doi.org/10.1016/j.neucom.2025.132507) | **Neurocomputing'26** | 2026.03 | **Entropy-Optimized Decoding**: Uses uncertainty-aware contrastive calibration to suppress hallucinated actions in vision-language-action generation. |
| [LEAD](https://arxiv.org/pdf/2603.13366) | arXiv'26 | 2026.03.09 | **Latent Entropy-Aware Decoding**: Switches high-entropy steps to probability-weighted latent embeddings and injects visual anchors. |
| [VCGD](https://doi.org/10.1609/aaai.v40i24.39089) | **AAAI'26** | 2026.03.14 | **Visual-Clue-Guided Decoding**: Uses a reinforcement-learned caption model as an auxiliary visual clue source and applies image-confidence constraints during generation. |
| [VGS-Decoding](https://arxiv.org/pdf/2603.20314) | arXiv'26 | 2026.03.19 | **Visual Grounding Score Decoding**: Reweights medical VLM tokens by their probability drop under visual degradation. |
| [VISAGE](https://arxiv.org/pdf/2603.25711) | arXiv'26 | 2026.03.26 | **Diffusion-Model Decoding Calibration**: Re-ranks parallel token commitments using cross-attention localization consensus. |
| [Divergent-Thinking Intervention](https://arxiv.org/pdf/2603.27201) | arXiv'26 | 2026.03.28 | **MCoT Step Intervention**: Localizes associative reasoning steps where fabricated content emerges and intervenes during decoding. |
| [SAGE](https://arxiv.org/pdf/2603.27898) | arXiv'26 | 2026.03.29 | **Sink-Aware Grounded Decoding**: Uses attention-sink triggers and spatial attribution agreement to recalibrate self-attention in real time. |
| [First Logit Boosting](https://arxiv.org/pdf/2604.00455) | arXiv'26 | 2026.04.01 | **Long-Term Visual Grounding**: Reuses the first-token logit in later predictions to counter visual-information decay. |
| [HaloProbe](https://arxiv.org/pdf/2604.06165) | arXiv'26 | 2026.04.07 | **Bayesian-Guided Decoding**: Estimates token-level hallucination posteriors from internal and description statistics to guide non-invasive decoding. |
| [DaID](https://arxiv.org/pdf/2604.10071) | arXiv'26 | 2026.04.11 | **Dual-Anchor Introspective Decoding**: Contrasts a visual-fact Spotlight layer with a text-inertia Shadow layer for token-specific calibration. |
| [HTDC](https://arxiv.org/pdf/2604.12115) | arXiv'26 | 2026.04.13 | **Hesitation-Triggered Calibration**: Activates visual- and semantic-nullification probes only when intermediate layers disagree. |
| [DeP](https://arxiv.org/pdf/2604.12424) | arXiv'26 | 2026.04.14 | **Textual-Perturbation Decoding**: Probes phrasing sensitivity to expose language-prior drift and stabilize evidence regions. |
| [PSRD](https://arxiv.org/pdf/2604.17982) | arXiv'26 | 2026.04.20 | **Phase-Wise Self-Reward Decoding**: Uses a distilled reward model to intervene at semantic-phase boundaries where hallucinations peak. |
| [PND](https://arxiv.org/pdf/2604.24396) | arXiv'26 | 2026.04.27 | **Positive-and-Negative Decoding**: Contrasts amplified salient evidence with a counterfactual branch whose core-object features are degraded. |
| [IECD²](https://arxiv.org/pdf/2604.25809) | arXiv'26 | 2026.04.28 | **Dual-Stream Decoding**: Adaptively fuses instruction-driven and evidence-driven token distributions with a symmetric-KL gate. |
| [SIRA](https://arxiv.org/pdf/2605.14621) | arXiv'26 | 2026.05.14 | **Internal Contrastive Decoding**: Forks a late-layer visual-masked branch from a shared multimodal prefix to isolate language priors. |
| [CHASD](https://arxiv.org/pdf/2605.23344) | arXiv'26 | 2026.05.22 | **On-Demand Contrastive Decoding**: Triggers localized negative-branch calibration only at uncertain token steps. |
| [YARD](https://arxiv.org/pdf/2605.31429) | arXiv'26 | 2026.05.29 | **Y-Architecture Register Decoding**: Shares shallow computation and replaces visual patches with register tokens only in an internal degraded branch. |
| [MGAP](https://arxiv.org/pdf/2606.09859) | arXiv'26 | 2026.05.31 | **Manifold-Guided Projection**: Selectively attenuates inconsistent language-prior subspace components while preserving orthogonal semantics. |
| [Fox](https://arxiv.org/pdf/2606.27596) | arXiv'26 | 2026.06.25 | **Causal Shortcut Decoding**: Locates risky attention mediators, severs prior-dominant paths, and gates interventional logits against fluent output. |
| [FADE](https://arxiv.org/pdf/2606.29431) | arXiv'26 | 2026.06.28 | **FFN Attenuation Decoding**: Weakens critical feed-forward layers identified as the source of language-prior dominance. |
| [CTDD](https://doi.org/10.1007/978-981-92-3432-5_49) | **LNCS'26** | 2026.07.14 | **Cumulative Trend-Divergence Decoding**: Tracks accumulated divergence in token-distribution trends and calibrates generation when visual and linguistic evidence separate. |

</details>

<details>
<summary><h3>🧩 Attention & Architecture Intervention</h3></summary>

*Basis: Completely training-free. Deep dives into the Transformer structure to edit the latent space, prune attention heads, or intervene in the KV Cache to cut off hallucination-inducing feature pathways.*

| Method | Pub | Date | Methodology |
| :--- | :--- | :--- | :--- |
| [OPERA](https://arxiv.org/pdf/2311.17911.pdf) | **CVPR'24** | 2024.1.1 | **Attention Penalty**: Extracts self-attention matrices to find and penalize attention flows overly reliant on summary tokens. |
| [AvisC](https://arxiv.org/pdf/2405.17820) | arXiv'24 | 2024.5.28 | **Attention Calibration**: Calibrates the weight allocation of attention heads to weaken the implicit coverage of visual inputs by language priors. |
| [AGLA](https://arxiv.org/pdf/2406.12718) | **CVPR'25** | 2024.6.18 | **Attention Fusion**: Fuses global and local attention feature matrices internally to enhance fine-grained perception. |
| [PAI](https://arxiv.org/pdf/2407.21771) | **ECCV'24** | 2024.7.31 | **Attention Amplification**: Adjusts cross-modal attention by forcefully amplifying the weights of visual tokens. |
| [PROJECTAWAY](https://arxiv.org/pdf/2410.02762) | arXiv'24 | 2024.10.3 | **Representation Editing**: Identifies and edits vision-language feature vectors representing hallucinations in intermediate layers. |
| [DAMRO](https://arxiv.org/pdf/2410.04514) | **EMNLP'24** | 2024.10.6 | **Attention Masking**: Dives into the MLLM to mask specific attention connections overly dominated by text. |
| [CAUSALMM](https://arxiv.org/pdf/2410.04780) | **ICLR'25** | 2024.10.7 | **Causal Attention Disconnection**: Uses causal analysis to block specific causal attention paths causing hallucinations during inference. |
| [FROM PIXELS TO TOKENS](https://arxiv.org/pdf/2410.06795) | arXiv'24 | 2024.10.9 | **Early Layer Intervention**: Locates the evolution of object features and corrects visual tokens via early layer interventions. |
| [CCA](https://arxiv.org/pdf/2410.15926) | **NIPS'24** | 2024.10.21 | **Concentric Causal Attention**: Strengthens the causal association between local visual features and global semantics in attention matrices. |
| [VTI](https://arxiv.org/pdf/2410.15778) | arXiv'24 | 2024.10.22 | **Latent Space Steering**: Injects pre-trained steering vectors into the latent space to guide generation away from hallucinations. |
| [EAH](https://arxiv.org/pdf/2411.09968) | arXiv'24 | 2024.11.15 | **Head Intervention**: Accurately locates key attention heads and specifically enhances or suppresses them during forward propagation. |
| [Looking Beyond Text](https://arxiv.org/pdf/2411.14279) | arXiv'24 | 2024.11.21 | **Dual-Attention Balancing**: Introduces dual-attention mechanisms to internally rebalance language priors and image feature flows. |
| [ICT](https://arxiv.org/pdf/2411.15268) | arXiv'24 | 2024.11.22 | **Cross-Level Blocking**: Proposes cross-level trusted intervention to block the drift of object representations toward false language priors. |
| [Devils in Middle Layers](https://arxiv.org/pdf/2411.16724) | arXiv'24 | 2024.11.23 | **Middle Layer Masking**: Uses an attention lens to locate hallucinated features in middle layers and masks them for correction. |
| [WhoBrings the Frisbee](https://arxiv.org/pdf/2412.02946) | arXiv'24 | 2024.12.3 | **Causal Attention Intervention**: Implements causal intervention to cut off spurious feature maps hidden in attention matrices. |
| [Nullu](https://arxiv.org/pdf/2412.13817) | **CVPR'25** | 2024.12.18 | **Latent Space Orthogonalization**: Projects hidden states into a hallucination space and strips them via orthogonalization to clear hallucinations. |
| [VHD](https://arxiv.org/pdf/2412.13949) | arXiv'24 | 2024.12.18 | **Attention Head Pruning**: Quantifies perception divergence and dynamically masks specific heads that lose visual alignment. |
| [VASparse](https://arxiv.org/pdf/2501.06553) | **CVPR'25** | 2025.1.11 | **Sparsification Dropping**: Introduces visual-aware sparsification to directly drop irrelevant visual tokens prone to inducing hallucinations. |
| [llava-fix-hallucination](https://arxiv.org/pdf/2501.12206) | arXiv'25 | 2025.1.21 | **Attention Rebalancing**: Corrects computation allocation to prevent long text prefixes from "hijacking" visual attention. |
| [MINT](https://arxiv.org/pdf/2502.00717) | arXiv'25 | 2025.2.2 | **Token Reduction**: Performs dynamic token reduction in deep layers to remove image features overly associated with the language model. |
| [UAC/DAC](https://arxiv.org/pdf/2502.01969) | arXiv'25 | 2025.2.4 | **Bidirectional Calibration**: Real-time bidirectional correction of attention shifts via Upward (UAC) and Downward (DAC) Attention Calibration. |
| [VISTA](https://arxiv.org/pdf/2502.03628) | arXiv'25 | 2025.2.5 | **Visual Steering Vector**: Uses visual information steering vectors to forcefully guide hidden states toward image fidelity. |
| [ADAVIB](https://arxiv.org/pdf/2502.20750) | **AAAI'25** | 2025.2.28 | **Information Flow Constraint**: Adaptively constrains inter-layer information flow to block false causal paths causing object hallucinations. |
| [TPC](https://arxiv.org/pdf/2503.04457) | arXiv'25 | 2025.3.6 | **Cross-Temporal Connection**: Establishes a cross-temporal network to pass early visual anchors to constrain subsequent tokens. |
| [EAZY](https://arxiv.org/pdf/2503.07772) | arXiv'25 | 2025.3.10 | **Activation Zeroing**: A minimalist intervention that directly zeros out the activation values of specific image tokens causing hallucinations. |
| [Attention Reallocation](https://arxiv.org/pdf/2503.08342) | arXiv'25 | 2025.3.12 | **Attention Reallocation**: Reallocates Attention Maps during inference to pull misplaced attention back to visual targets. |
| [Attention Hijackers](https://arxiv.org/pdf/2503.08216) | arXiv'25 | 2025.3.14 | **Hijack Disentanglement**: Detects and disentangles the attention "hijacking" phenomenon within the model architecture. |
| [Through the Magnifying Glass](https://arxiv.org/pdf/2503.10183) | arXiv'25 | 2025.3.14 | **Perception Magnification**: Adaptively magnifies the visual feature strength of target perception regions in the feature layer. |
| [TruthPrInt](https://arxiv.org/pdf/2503.10602) | arXiv'25 | 2025.3.14 | **Latent Truth Guidance**: Implements intervention before the first token is generated by injecting true visual vectors into deep layers. |
| [ClearSight](https://arxiv.org/pdf/2503.13107) | **CVPR'25** | 2025.3.14 | **Signal Enhancement**: Amplifies low-level visual signals in multimodal layers to combat dilution by deep language features. |
| [IAVA](https://arxiv.org/pdf/2503.18556) | arXiv'25 | 2025.3.24 | **Aligned Attention Masking**: Dynamically masks attention flows of irrelevant image patches based on instruction focus. |
| [TARAC](https://arxiv.org/pdf/2504.04099) | arXiv'25 | 2025.4.5 | **Accumulative Connection**: Establishes real-time accumulative connections of temporal attention to reinforce factual memory. |
| [DCLA](https://arxiv.org/pdf/2505.12343) | arXiv'25 | 2025.5.18 | **Inter-Layer Aggregation**: Implements inter-layer consistency aggregation to fuse expressions across depths to correct single-layer drift. |
| [SEVI](https://arxiv.org/pdf/2505.14257) | arXiv'25 | 2025.5.20 | **Flow Alignment**: Forces multimodal attention distributions to align with correct information flows to block fictitious feature mapping. |
| [SSL](https://arxiv.org/pdf/2505.16146) | arXiv'25 | 2025.5.22 | **SAE Steering**: Uses pre-trained Sparse Autoencoders (SAE) to extract and steer internal hidden states. |
| [SPIN](https://arxiv.org/pdf/2505.16411) | arXiv'25 | 2025.5.22 | **Dynamic Head Suppression**: Uses image features to precisely identify and dynamically suppress language-dominated heads. |
| [VaLSe](https://arxiv.org/pdf/2505.17812) | arXiv'25 | 2025.5.23 | **Latent Counterfactual Intervention**: Generates counterfactual vectors in the latent layer for subtractive intervention (Latent Steering). |
| [CGC](https://arxiv.org/pdf/2505.21547) | arXiv'25 | 2025.5.24 | **Discrete Mapping Editing**: Edits the mapping relationships of discrete visual tokens in the latent space to eliminate hallucinations. |
| [CAAC](https://arxiv.org/pdf/2505.21472) | arXiv'25 | 2025.5.27 | **Adaptive Calibration**: Adaptively triggers attention weight calibration mechanisms based on the degree of feature bias. |
| [CLAIM](https://arxiv.org/pdf/2506.11073) | arXiv'25 | 2025.6.3 | **Cross-Lingual Attention Intervention**: Cuts off implicit semantic biases introduced during cross-lingual transitions inside the model. |
| [Seeing Far and Clearly](https://arxiv.org/pdf/2505.16652) | arXiv'25 | 2025.6.7 | **Attention Causal Decoding**: Reconstructs causal connection chains of attention to enhance visual reliance. |
| [HalLoc](https://arxiv.org/pdf/2506.10286) | arXiv'25 | 2025.6.12 | **Token Localization & Pruning**: Pinpoints tokens sourcing hallucinations and excises them during forward propagation. |
| [TAI & HAI](https://arxiv.org/pdf/2506.12609) | arXiv'25 | 2025.6.14 | **Dual-Level Attention Intervention**: Performs attention intervention simultaneously at both the Token and Head granularity levels. |
| [HalluRNN](https://arxiv.org/pdf/2506.17587) | arXiv'25 | 2025.6.21 | **Recurrent Cross-Layer Intervention**: Builds a recurrent reasoning structure to repeatedly proofread feature vectors across Transformer layers. |
| [MDSAM](https://arxiv.org/pdf/2506.17664) | arXiv'25 | 2025.6.21 | **Memory-Driven Sparsification**: Constructs a sparse attention matrix using a memory-driven approach to mask redundant inputs. |
| [CAI](https://arxiv.org/pdf/2506.23590) | arXiv'25 | 2025.6.30 | **Sensitive Attention Interception**: Forcibly intercepts and truncates caption-sensitive attention branches. |
| [ONLY](http://arxiv.org/pdf/2507.00898) | arXiv'25 | 2025.7.1 | **Single-Layer Precise Intervention**: Proves that intervening on a specific single critical layer is sufficient to drastically suppress object hallucinations. |
| [EVA](https://arxiv.org/pdf/2507.15652) | arXiv'25 | 2025.7.21 | **Intermediate Feature Override**: Extracts true factual features at intermediate layers to forcibly override biased deep features. |
| [MCA-LLaVA](https://arxiv.org/pdf/2507.09184) | **ACMMM'25** | 2025.7.23 | **Manhattan Causal Replacement**: Reconstructs multimodal attention using a causal matrix based on Manhattan distance. |
| [LISA](https://arxiv.org/pdf/2507.19110) | arXiv'25 | 2025.7.25 | **Layer-wise Integration & Suppression**: Implements layer-wise feature accumulation and dynamic language prior suppression. |
| [MAP](https://arxiv.org/pdf/2508.01653) | arXiv'25 | 2025.8.3 | **Map-Level Smoothing**: Applies spatial smoothing filters to attention heatmaps to eliminate hallucination-inducing attention spikes. |
| [Modality Bias in LVLMs](https://arxiv.org/pdf/2508.02419) | arXiv'25 | 2025.8.4 | **Bias Lens Intervention**: Uses an attention lens to analyze modality biases and block underlying vectors. |
| [IKOD](https://arxiv.org/pdf/2508.03469) | arXiv'25 | 2025.8.5 | **Attention Degradation Recovery**: Recovers the model's visual attention that gradually degrades and gets lost during long-context generation. |
| [D-LEAF](https://arxiv.org/pdf/2509.07864) | arXiv'25 | 2025.9.9 | **Layer-to-Head Diagnostics**: Locates specific layers and heads causing hallucinations for dynamic interception during inference. |
| [VisionWeaver](https://arxiv.org/pdf/2509.13836) | **EMNLP'25** | 2025.9.17 | **Pure Vision Reinforcement**: Intervenes from the visual processing architecture to fundamentally alter how the model acquires visual information. |
| [Exposing Hallucinations](https://arxiv.org/pdf/2509.21997) | arXiv'25 | 2025.9.26 | **Latent Algebraic Editing**: Exposes latent space hallucination vectors via anchors and performs algebraic subtraction during forward passes. |
| [On Epistemic Uncertainty](https://arxiv.org/pdf/2510.09008v1) | arXiv'25 | 2025.10.10 | **Uncertainty Dropping**: Calculates the epistemic uncertainty of internal tokens to drop highly uncertain visual features. |
| [Hallu-Steer](https://arxiv.org/pdf/2510.11842v1) | arXiv'25 | 2025.10.13 | **Latent Steering Injection**: Injects pre-calculated anti-hallucination steering vectors into the hidden state space. |
| [Functional Attention Control](https://arxiv.org/pdf/2510.10285v1) | arXiv'25 | 2025.10.11 | **Functional Hardcoding**: Hardcodes specific multimodal reasoning functions into the attention control flow to block interference. |
| [Semantic Entanglement](https://arxiv.org/pdf/2510.12287v1) | arXiv'25 | 2025.10.14 | **Projector Disentanglement**: Analyzes and disentangles semantic entanglement in the visual projector to purify visual tokens. |
| [Suppressing Hallucinations](https://arxiv.org/pdf/2510.16596v1) | arXiv'25 | 2025.10.18 | **Encoder Low-Level Defense**: Deploys defense mechanisms at the visual encoder side to block hallucination source contamination. |
| [PruneHal](https://arxiv.org/pdf/2510.19183v1) | arXiv'25 | 2025.10.22 | **KV Cache Pruning**: Dynamically identifies and prunes KV Cache nodes representing pure language biases during inference. |
| [Refining Textual Embeddings](https://arxiv.org/pdf/2511.05017v1) | arXiv'25 | 2025.11.07 | **Input Purification**: Purifies textual embedding features at the architecture base to weaken their suppression of visual features. |
| [Causal Tracing](https://arxiv.org/pdf/2511.05923v3) | arXiv'25 | 2025.11.08 | **Causal Truncation**: Traces the flow of object representations across layers and implements precise mechanistic causal truncation. |
| [Causally-Grounded Dual-Path](https://arxiv.org/pdf/2511.09018v1) | arXiv'25 | 2025.11.12 | **Dual-Path Flow Separation**: Establishes dual attention paths to completely separate true visual information from false reasoning flows. |
| [Adaptive Residual-Update](https://arxiv.org/pdf/2511.10292v1) | arXiv'25 | 2025.11.13 | **Adaptive Residual Injection**: Injects adaptive steering vectors at Transformer residual connections with minimal computational overhead. |
| [Spectral Representation Filtering](https://arxiv.org/pdf/2511.12220v1) | arXiv'25 | 2025.11.15 | **High-Frequency Filtering**: Uses frequency-domain spectral analysis to filter hidden features and remove high-frequency hallucination noise. |
| [Tell Model Where to Look](https://arxiv.org/pdf/2511.20032v1) | arXiv'25 | 2025.11.25 | **Hard Mask Constraints**: Imposes hard attention masks to force the model to strictly follow salient image regions. |
| [Conscious Gaze](https://arxiv.org/pdf/2512.05546v1) | arXiv'25 | 2025.12.05 | **Simulated Gaze Refocusing**: Introduces an adaptive refocusing module simulating human gaze to converge scattered attention. |
| [Sparse Autoencoder-Driven](https://arxiv.org/pdf/2512.07730v2) | arXiv'25 | 2025.12.08 | **SAE Feature Enhancement**: Uses SAEs to extract visual activation features and amplifies their intensity during forward passes. |
| [VEGAS](https://arxiv.org/pdf/2512.12089v1) | arXiv'25 | 2025.12.12 | **Encoder-Guided Steering**: Directly uses the vision encoder's attention distribution to steer the generation direction of the LLM layers. |
| [Look Closer!](https://arxiv.org/pdf/2512.21999v1) | arXiv'25 | 2025.12.26 | **Adversarial Parameter Editing**: Locates parameters storing false associations and directly corrects weight distributions via adversarial editing. |
| [Adaptive Factual-Guided](https://arxiv.org/pdf/2601.01957v1) | arXiv'26 | 2026.01.05 | **Neuron Activation Editing**: Dynamically modifies and edits neuron activation values during forward propagation under factual guidance. |
| [Text-Guided Layer Fusion](https://arxiv.org/pdf/2601.03100v1) | arXiv'26 | 2026.01.06 | **Dynamic Layer Fusion**: Dynamically fuses multi-layer visual features guided by text instructions. |
| [Vision-Language Introspection](https://arxiv.org/pdf/2601.05159v1) | arXiv'26 | 2026.01.08 | **Bi-Causal Intervention**: Proposes an interpretable bi-causal introspection mechanism for latent space intervention to reduce overconfidence. |
| [VIB-Probe](https://arxiv.org/pdf/2601.05547v1) | arXiv'26 | 2026.01.09 | **Information Bottleneck Probe**: Inserts an information bottleneck probe to compress redundant multimodal mutual information that triggers hallucinations. |
| [One-shot Optimized Steering](https://arxiv.org/pdf/2601.23041v1) | arXiv'26 | 2026.01.30 | **One-Shot Steering Vector**: Calculates optimal anti-hallucination control vectors via few-shot data and injects them during inference. |
| [Contrastive Neuron Steering](https://arxiv.org/pdf/2602.00621v1) | arXiv'26 | 2026.01.31 | **Neuron Steering Vector**: Pinpoints individual neurons causing differences and applies vector steering. |
| [ClueTracer](https://arxiv.org/pdf/2602.02004) | arXiv'26 | 2026.02.02 | **Question-to-Vision Tracing**: Traces task clues through the reasoning path to suppress attention on irrelevant image regions. |
| [KVSmooth](https://arxiv.org/pdf/2602.04268v1) | arXiv'26 | 2026.02.04 | **Numerical Smoothing**: Applies smoothing operations to the KV Cache to mitigate attention collapse caused by extreme activation values. |
| [Visual-Aware Attention and Logits Enhancement](https://arxiv.org/pdf/2602.09521) | arXiv'26 | 2026.02.10 | **Task-Relevant Attention Reweighting**: Redistributes attention through vision-text similarity and injects visual scores into beam search. |
| [Scalpel](https://arxiv.org/pdf/2602.09541) | **WACV'26** | 2026.02.10 | **Attention Manifold Alignment**: Maps hallucination activations toward trusted attention regions with mixture-Gaussian bridges. |
| [REVIS](https://arxiv.org/pdf/2602.11824) | arXiv'26 | 2026.02.12 | **Sparse Latent Steering**: Orthogonally extracts pure visual directions and intervenes only where deep-layer suppression occurs. |
| [SAVAA](https://arxiv.org/pdf/2602.13600) | arXiv'26 | 2026.02.14 | **Adaptive Attention Amplification**: Estimates token-level grounding risk and adjusts visual attention strength step by step. |
| [PADE](https://arxiv.org/pdf/2602.15556) | arXiv'26 | 2026.02.17 | **Positive Attention Dynamics**: Locates core visual regions from internal attention motion and adaptively reinforces them per head. |
| [HIME](https://arxiv.org/pdf/2602.18711) | arXiv'26 | 2026.02.21 | **Layer-Adaptive Model Editing**: Uses hallucination-insensitivity scores to selectively edit vulnerable layers while preserving knowledge. |
| [Dynamic Multimodal Activation Steering](https://arxiv.org/pdf/2602.21704) | arXiv'26 | 2026.02.25 | **Context-Aware Activation Steering**: Selects semantic truthfulness vectors and applies them to influential perception heads. |
| [HulluEdit](https://arxiv.org/pdf/2602.22727) | arXiv'26 | 2026.02.26 | **Orthogonal Subspace Editing**: Separates visual evidence, conflicting priors, and residual uncertainty for single-pass selective suppression. |
| [AIR](https://arxiv.org/pdf/2602.24041) | arXiv'26 | 2026.02.27 | **Adaptive Visual Reinforcement**: Reduces redundant visual tokens and injects only patches aligned with current hidden states. |
| [ICLA](https://arxiv.org/pdf/2603.00437) | arXiv'26 | 2026.02.28 | **Cross-Layer Self-Correction**: Adds lightweight layer attention that retrieves preceding hidden states for internal refinement. |
| [AdaIAT](https://arxiv.org/pdf/2603.04908) | arXiv'26 | 2026.03.05 | **Generated-Text Attention Control**: Adaptively amplifies attention toward grounded prior text while avoiding repetition. |
| [CIPHER](https://arxiv.org/pdf/2603.10470) | arXiv'26 | 2026.03.11 | **Counterfactual Subspace Removal**: Learns vision-induced hallucination directions from diffusion-edited images and projects hidden states away from them. |
| [RFI](https://doi.org/10.1609/aaai.v40i5.37320) | **AAAI'26** | 2026.03.14 | **Rectified-Flow Intervention**: Predicts input-specific latent steering vectors with gradient correction in a single forward pass. |
| [Taming the Phantom](https://doi.org/10.1609/aaai.v40i10.37768) | **AAAI'26** | 2026.03.14 | **Token-Asymmetric Filtering**: Filters intermediate attention maps to isolate dominant phantom text tokens and strengthen visual anchor tokens. |
| [LTS-FS](https://arxiv.org/pdf/2603.16284) | arXiv'26 | 2026.03.17 | **Attribution-Guided Sparse Steering**: Scales layerwise steering according to causal hallucination-relevance scores. |
| [Segmentation-Based Attention Entropy](https://arxiv.org/pdf/2603.16558) | arXiv'26 | 2026.03.17 | **Object-Space Attention Adjustment**: Uses segmentation-derived attention entropy to detect risk and recalibrate visual attention. |
| [Attention Imbalance Rectification](https://arxiv.org/pdf/2603.24058) | arXiv'26 | 2026.03.25 | **Attention Redistribution**: Corrects modality- and token-level attention disparities linked causally to object hallucination. |
| [CLVA](https://arxiv.org/pdf/2603.25088) | arXiv'26 | 2026.03.26 | **Cross-Layer Visual Anchors**: Reinforces reliable middle-layer visual anchors while suppressing deep-layer regression to noise. |
| [HIRE](https://arxiv.org/pdf/2603.29405) | arXiv'26 | 2026.03.31 | **Dynamic Representation Editing**: Detects hallucination representations online and removes them with low-cost intermediate-state edits. |
| [IVE](https://arxiv.org/pdf/2604.01989) | arXiv'26 | 2026.04.02 | **Visual Inertia Intervention**: Promotes newly relevant regions and penalizes persistent localized attention during relational inference. |
| [MESA](https://arxiv.org/pdf/2604.07914) | arXiv'26 | 2026.04.09 | **Disentangled Latent Steering**: Suppresses hallucination-relevant representations while preserving the native generation distribution. |
| [DOP-OBC](https://arxiv.org/pdf/2604.09749) | arXiv'26 | 2026.04.10 | **Equitable Attention Control**: Penalizes dominant objects and boosts rare but confidently detected visual regions. |
| [MPD](https://arxiv.org/pdf/2604.20366) | arXiv'26 | 2026.04.22 | **Selective Parameter Editing**: Disentangles pure hallucination components and updates only the parameters most responsible for them. |
| [PTI](https://arxiv.org/pdf/2604.25642) | arXiv'26 | 2026.04.28 | **Prefill-Time KV Intervention**: Steers visual keys toward grounded objects and filters noisy values before autoregressive errors accumulate. |
| [LIME](https://arxiv.org/pdf/2605.01766) | arXiv'26 | 2026.05.03 | **Relevance-Propagation KV Updates**: Optimizes inference-time key-value states to increase contributions from vision and audio tokens. |
| [CAST](https://arxiv.org/pdf/2605.04641) | arXiv'26 | 2026.05.06 | **Caption-Guided Attention Steering**: Transfers factual caption-query activation patterns into selected visual attention heads. |
| [HAVAE](https://arxiv.org/pdf/2605.10622) | arXiv'26 | 2026.05.11 | **Vocabulary-Hijacking Intervention**: Excludes semantically collapsed inert tokens and strengthens non-hijacked visual attention heads. |
| [RVE](https://arxiv.org/pdf/2605.11808) | arXiv'26 | 2026.05.12 | **Relation-Aware Visual Enhancement**: Locates action-sensitive heads and amplifies image regions supporting object interactions. |
| [MHSA](https://arxiv.org/pdf/2605.14966) | arXiv'26 | 2026.05.14 | **Learned Attention Correction**: Replaces hallucination-prone cross-modal attention with lightweight discriminator-guided corrections. |
| [ILVAD](https://arxiv.org/pdf/2605.20965) | arXiv'26 | 2026.05.20 | **Inter-Layer Evidence Enhancement**: Builds saliency maps from recurring cross-layer attention and reinforces grounded visual and text tokens. |
| [Causal Route Gating](https://arxiv.org/pdf/2605.24024) | arXiv'26 | 2026.05.20 | **Decision-Aligned Route Suppression**: Separates visual and textual routes within heads and gates only prior-dominant text paths. |
| [Region-Aware Attention Recalibration](https://arxiv.org/pdf/2605.24957) | arXiv'26 | 2026.05.24 | **Continuous Attention Penalty**: Uses regional inter-head disagreement to allocate adaptive suppression budgets. |
| [CAS](https://arxiv.org/pdf/2605.27993) | arXiv'26 | 2026.05.27 | **Context-Preference Steering**: Applies signed residual vectors to control reliance on image, parametric knowledge, and textual context. |
| [TLVS](https://arxiv.org/pdf/2606.07647) | arXiv'26 | 2026.06.02 | **Token-Level Visual Steering**: Applies calibrated activation directions only at visually sensitive, hallucination-prone generation steps. |
| [MultiToP](https://arxiv.org/pdf/2606.11792) | arXiv'26 | 2026.06.10 | **Video Token Patching**: Learns to replace unreliable frame tokens with a dynamic global token before language generation. |
| [QK Product Steering](https://arxiv.org/pdf/2606.20419) | arXiv'26 | 2026.06.18 | **Spectral Weight Editing**: Suppresses dominant singular modes in selected query-key products with a closed-form query update. |
| [CAI](https://arxiv.org/pdf/2606.29847) | arXiv'26 | 2026.06.29 | **Context-Aware Attention Intervention**: Tilts only token-relevant regions at uncertainty spikes where deeper visual grounding degrades. |
| [SeeMe](https://arxiv.org/pdf/2607.04163) | arXiv'26 | 2026.07.05 | **Visual Token Engineering**: Restructures noisy visual tokens in three stages while retaining informative evidence. |
| [Look Before You Speak](https://doi.org/10.1007/978-981-92-3432-5_48) | **LNCS'26** | 2026.07.14 | **Visual Re-Focusing**: Reorients the model toward image evidence before response generation to reduce visually unsupported claims. |
| [SDPR](https://arxiv.org/pdf/2607.16841) | arXiv'26 | 2026.07.18 | **Perceptual Realignment**: Redistributes saliency, aligns spatial KV-cache structure, and constrains contrastive decoding with visual priors. |

</details>

<details>
<summary><h3>💡 External Augmentation & Prompting</h3></summary>

*Basis: Completely black-box without touching model weights or underlying architectures. Utilizes prompt engineering, Retrieval-Augmented Generation (RAG), external Agents, or self-reflection consistency to filter hallucinations.*

| Method | Pub | Date | Methodology |
| :--- | :--- | :--- | :--- |
| [LURE](https://arxiv.org/pdf/2310.00754.pdf) | **ICLR'23** | 2023.10.1 | **Post-hoc Revision**: Trains an independent Reviser model specifically to detect and reconstruct hallucinated entities in outputs. |
| [Woodpecker](https://arxiv.org/abs/2310.16045) | **SCIS'24** | 2023.10.24 | **Agent Correction**: Calls external visual foundation models to verify entity facts, finally using an LLM to rewrite and correct. |
| [Enhancing Multimodal Large Language Models with Vision Detection Models](https://arxiv.org/pdf/2401.17981.pdf) | arXiv'24 | 2024.1.31 | **External Visual Guidance**: Feeds information identified by external object detection models directly to the MLLM as context. |
| [SKIP \N](https://arxiv.org/pdf/2402.01345.pdf) | arXiv'24 | 2024.2.12 | **Prompt Interruption**: Inserts newline characters into the prompt to break context formatting and alleviate language inertia. |
| [LogicCheckGPT](https://arxiv.org/pdf/2402.11622.pdf) | arXiv'24 | 2024.2.18 | **Logical Loop Verification**: Uses external language models to ask questions about generated claims for self-verification. |
| [Evaluating and Mitigating Number Hallucinations](https://arxiv.org/pdf/2403.01373.pdf) | arXiv'24 | 2024.3.3 | **Multi-Sampling Verification**: Designs a prompt repair strategy based on multi-sampling consistency specifically for number hallucinations. |
| [DVP](https://arxiv.org/pdf/2403.13513.pdf) | arXiv'24 | 2024.3.20 | **Counterfactual Prompting**: Introduces "What if" prompting to compel the model to self-reflect on its initial judgments. |
| [PENSIEVE](https://arxiv.org/pdf/2403.14401.pdf) | arXiv'24 | 2024.3.21 | **Multi-Step Retrospective Prompting**: Adopts a "Retrospect-then-Compare" multi-step prompt to make the model review visual details for correction. |
| [ESREAL](https://arxiv.org/pdf/2403.16167.pdf) | arXiv'24 | 2024.3.26 | **Semantic Scoring & Reconstruction**: Extracts text for semantic reconstruction and uses external verifiers to score and block incorrect outputs. |
| [TVP](https://arxiv.org/pdf/2404.11207) | arXiv'24 | 2024.4.17 | **Original Image Overlay**: Overlays visual prompts (e.g., circles, bounding boxes) on the original image to force model attention. |
| [Visual Fact Checker](https://arxiv.org/pdf/2404.19752) | **CVPR'24** | 2024.4.30 | **Pipeline Agent**: Constructs a pipeline system containing claim extraction, external detection verification, and corrected generation. |
| [VDGD](https://arxiv.org/pdf/2405.15683) | arXiv'24 | 2024.5.24 | **Perception Detail Supplement**: Pre-supplements missing low-level visual perception details in the input prompt to bridge the gap. |
| [RITUAL](https://arxiv.org/pdf/2405.17821) | arXiv'24 | 2024.5.28 | **Multi-View Consistency**: Applies random geometric transformations to construct multiple views for consistency verification and correction. |
| [NoiseBoost](https://arxiv.org/pdf/2405.20081) | arXiv'24 | 2024.5.30 | **Noise Ensemble for Confidence Reduction**: Injects moderate noise and aggregates multiple outputs to lower model overconfidence. |
| [DBD](https://arxiv.org/pdf/2406.12663) | arXiv'24 | 2024.6.18 | **Prompt Detail Constraint**: Strictly controls the requested detail quantity via prompt to balance richness and hallucination rate. |
| [ARA](https://arxiv.org/pdf/2408.00555) | **TOMM'25** | 2024.8.1 | **Dynamic RAG Supplement**: Evaluates model uncertainty to actively trigger knowledge base retrieval for entity correction. |
| [Detect-then-Calibrate](https://arxiv.org/pdf/2408.09429) | arXiv'24 | 2024.8.18 | **External Detection Calibration**: Uses an external detector to locate relation errors, then applies template-based secondary correction. |
| [Look, Compare, Decide](https://arxiv.org/pdf/2408.17150) | arXiv'24 | 2024.8.30 | **Multi-Path Voting**: Adopts multi-view prompts and multi-path reasoning, aggregating and comparing answers. |
| [PACU](https://arxiv.org/pdf/2409.14484) | arXiv'24 | 2024.9.22 | **Joint Auxiliary Description**: Enhances prompt design and incorporates image auxiliary descriptions to provide richer visual anchors. |
| [Dentist](https://arxiv.org/pdf/2409.16494) | **TMLR'24** | 2024.9.24 | **External Discriminator System**: Builds a unified cross-modal diagnosis pipeline utilizing external discriminators to intercept and modify outputs. |
| [LOOK TWICE BEFORE YOU ANSWER](https://arxiv.org/pdf/2410.03577) | arXiv'24 | 2024.10.4 | **Memory Retracing Confirmation**: Uses prompts to guide the model to actively re-extract visual clues for confirmation during generation. |
| [VHExpansion](https://arxiv.org/pdf/2410.11242) | arXiv'24 | 2024.10.15 | **Adversarial Test Cases**: Automatically generates adversarial complex prompts to expand input diversity and force the model to evade hallucinations. |
| [Thinking Before Looking](https://arxiv.org/pdf/2411.12591) | arXiv'24 | 2024.11.15 | **Explicit CoT Constraint**: Introduces Chain-of-Thought prompting, forcing the model to explicitly write out reasoning steps. |
| [TPO: A Topic-level Self-Correctional Approach](https://arxiv.org/pdf/2411.17265) | arXiv'24 | 2024.11.26 | **Topic-Level Self-Scoring**: The model generates a draft, then independently reviews and self-scores sub-topics for correction. |
| [VisVM](https://arxiv.org/pdf/2412.03704) | arXiv'24 | 2024.12.6 | **External Scoring Search**: Introduces an external Vision Value Model to assist tree search, guiding autoregressive generation. |
| [DEHALL](https://arxiv.org/pdf/2412.11124) | arXiv'24 | 2024.12.15 | **Multi-Perspective Cross-Checking**: Utilizes a bottom-up holistic reasoning framework combined with multi-perspective prompt verification. |
| [Toward Robust Hyper-Detailed Image Captioning](https://arxiv.org/pdf/2412.15484) | arXiv'24 | 2024.12.20 | **Multi-Agent Debate**: Deploys a multi-agent system with different roles for generation and cross-debate correction. |
| [EAGLE](https://arxiv.org/pdf/2501.02699) | arXiv'25 | 2025.1.6 | **Structured Coordinate Requirement**: Modifies prompt structures to force the model to output attached visual grounding coordinates. |
| [Socratic Questioning](https://arxiv.org/pdf/2501.02964) | arXiv'25 | 2025.1.7 | **Multi-Round Socratic Inquiry**: Employs Socratic questioning prompts to filter hallucinations through iterative self-inquiry. |
| [MIAVLM](https://arxiv.org/pdf/2501.10011) | arXiv'25 | 2025.1.17 | **Negative Instruction Constraint**: Explicitly introduces negative constraint instructions in the system prompt combined with multi-view verification. |
| [Poison as Cure](https://arxiv.org/pdf/2501.19164) | arXiv'25 | 2025.1.31 | **Physical Noise Injection**: Explicitly injects specific visual noise into the original image to inversely stimulate the model's evasion capability. |
| [CAP](https://arxiv.org/pdf/2502.08317) | arXiv'25 | 2025.2.12 | **Spatial Logic Rule Prompting**: Explicitly adds spatial relation logic rules into the prompt to correct spatial confusion. |
| [API Cutoff](https://arxiv.org/pdf/2502.15389) | arXiv'25 | 2025.2.21 | **API Truncation Focus**: Uses specific Cutoff prompts to truncate background processing, forcing the model to only describe foreground targets. |
| [Treble Counterfactual VLMs](https://arxiv.org/pdf/2503.06169) | arXiv'25 | 2025.3.6 | **Counterfactual Reasoning Injection**: Adds a causal reasoning prompt framework at the input to help the model identify illusions. |
| [MFP](https://arxiv.org/pdf/2503.14895) | arXiv'25 | 2025.3.19 | **Multi-Frequency Consensus Check**: Applies multi-frequency perturbations at the input and achieves consensus by contrasting answers across frequencies. |
| [Generate, but Verify](https://arxiv.org/pdf/2504.13169) | arXiv'25 | 2025.4.17 | **Resampling Verification**: Performs targeted retrospective resampling verification to filter errors after initial generation. |
| [Hydra](https://arxiv.org/pdf/2504.14395) | arXiv'25 | 2025.4.19 | **Agent Interaction Defense**: Deploys an agent containing reasoning, questioning, and summarization to defend against input attacks. |
| [BBVPE](https://arxiv.org/pdf/2504.21559) | arXiv'25 | 2025.4.30 | **Automated Patch Search**: Uses black-box optimization to automatically search for "visual prompt patches" that suppress hallucinations. |
| [EVRB](https://arxiv.org/pdf/2505.19498) | arXiv'25 | 2025.5.26 | **Bayesian Probability Check**: Applies a Bayesian perspective to strengthen the verification of the model's reliance on visual features during generation. |
| [When Semantics Mislead Vision](https://arxiv.org/pdf/2506.05551) | arXiv'25 | 2025.6.5 | **Scene Text Special Handling**: Adds specific interception prompts against semantic misleading in OCR scenarios. |
| [LPS](https://arxiv.org/pdf/2506.06729) | arXiv'25 | 2025.6.7 | **External Local Locking**: Locks onto local factual details in the image using an external retrieval system before answering. |
| [PostAlign](https://arxiv.org/pdf/2506.17901) | arXiv'25 | 2025.6.22 | **Grounding Lens Correction**: Uses multimodal grounding as an external lens to replace entities before finalizing the text generation. |
| [ReCo](https://arxiv.org/pdf/2506.22636) | arXiv'25 | 2025.6.27 | **Reminder Composition Prompt**: Attaches a structured "memo" in the prompt forcing the model to check essential elements. |
| [Preemptive Hallucination Reduction](https://arxiv.org/pdf/2506.22636) | arXiv'25 | 2025.6.27 | **Preemptive Input Interception**: Sets up an interception mechanism during the preprocessing of prompts and initial inputs. |
| [SENTINEL](https://arxiv.org/pdf/2507.12455) | **ICCV'25** | 2025.7.16 | **Early Sentence Truncation**: Implements factual truncation prompts in early sentence stages of generation to prevent error propagation. |
| [ViHallu](https://arxiv.org/pdf/2507.22003) | arXiv'25 | 2025.7.30 | **Variant Input Cross-Checking**: Constructs image perturbation variants and cross-checks their outputs to filter non-factual content. |
| [Prompt-in-Image](https://arxiv.org/pdf/2508.01678) | arXiv'25 | 2025.8.3 | **Physical Pixel Embedding**: Renders and embeds text instructions directly into image pixels to force the model's compliance. |
| [SAVER](https://arxiv.org/pdf/2508.03177) | arXiv'25 | 2025.8.5 | **Style Advance Notice**: External modules pre-identify image styles and entities, feeding the correct info via prompt. |
| [Hacking Hallucinations](https://arxiv.org/pdf/2508.04182) | arXiv'25 | 2025.8.6 | **Causal Element Disentanglement Scoring**: Executes causal sufficiency and necessity scoring via external algorithms from the black-box input side. |
| [APASI](https://arxiv.org/pdf/2509.11287) | arXiv'25 | 2025.9.14 | **Trap Pre-embedding & Evasion**: Intentionally prompts the model to generate hallucination traps first, then uses instructions to make it self-evade. |
| [Self-Consistency as a Free Lunch](https://arxiv.org/pdf/2509.23236) | arXiv'25 | 2025.9.27 | **Consistency Self-Reflection**: Utilizes self-consistency voting for reflective judgments in a purely black-box setting. |
| [GACD](https://arxiv.org/pdf/2509.03113) | arXiv'25 | 2025.10.1 | **Gradient-Guided Reflection**: Feeds back externally calculated gradient information as a prompt to trigger deep self-correction. |
| [ChainMPQ](https://arxiv.org/pdf/2510.06292v1) | arXiv'25 | 2025.10.7 | **Interleaved Step Constraint**: Requires the model to output reasoning chains following strict text-image interleaved steps to verify relations. |
| [When Images Speak Louder](https://arxiv.org/pdf/2510.10466v1) | arXiv'25 | 2025.10.12 | **External Reference Constraint**: Provides strong cross-modal retrieved information as references at the input to constrain free generation. |
| [Why LVLMs Are More Prone to Hallucinations in Longer Responses](https://arxiv.org/pdf/2510.20229v1) | arXiv'25 | 2025.10.23 | **Memory Management Prompt**: Analyzes the snowball effect and proposes long-context truncation strategies via prompts. |
| [Capturing Gaze Shifts for Guidance](https://arxiv.org/pdf/2510.22067) | arXiv'25 | 2025.11.10 | **Human Gaze Trajectory Input**: Inputs human eye-tracking gaze trajectories as additional features to guide model attention. |
| [Taming Object Hallucinations](https://arxiv.org/pdf/2511.09228v1) | arXiv'25 | 2025.11.12 | **Atomic Granularity Decomposition**: Requires the model to dismantle answers atomically with attached confidence, using external tools for verification. |
| [Hallucination Mitigation via Introspection](https://arxiv.org/pdf/2512.02981v1) | arXiv'25 | 2025.12.02 | **Cross-Modal Introspective Debate**: Deploys a network of introspective and external verification agents for interactive debate. |
| [CRoPS](https://arxiv.org/pdf/2601.00659v1) | arXiv'26 | 2026.01.02 | **Black-Box Universal Framework**: Integrates multiple plug-and-play external training-free methods into a universal suppression framework. |
| [Ground What You See](https://arxiv.org/pdf/2601.06224) | arXiv'26 | 2026.01.09 | **Diversified External Feedback**: Combines diversity sampling and external feedback loops for black-box optimization at generation. |
| [Hallucination Begins Where Saliency Drops](https://arxiv.org/pdf/2601.20279v1) | arXiv'26 | 2026.01.28 | **Saliency Interception Gate**: Actively refuses to answer when image saliency calculated by external tools falls below a threshold. |
| [Countering the Over-Reliance Trap](https://arxiv.org/pdf/2601.22451v1) | arXiv'26 | 2026.01.30 | **Pipeline Self-Verification**: Designs a black-box self-verification pipeline including proposition extraction, re-checking, and logic judgment. |
| [See It, Say It, Sorted](https://arxiv.org/pdf/2602.21497) | arXiv'26 | 2026.02.25 | **Iterative Evidence Pooling**: Expands a textual visual-evidence pool until each reasoning step is sufficiently grounded. |
| [GroundCount](https://arxiv.org/pdf/2603.10978) | arXiv'26 | 2026.03.11 | **Detector-Augmented Counting**: Converts object-detector outputs into structured prompts that ground spatial instance counts. |
| [V3Fusion](https://arxiv.org/pdf/2603.12669) | arXiv'26 | 2026.03.13 | **Diversity-Aware Model Fusion**: Selects complementary VLMs from visual-embedding disagreement and fuses their predictions. |
| [Multi-Agent Undercover Gaming](https://doi.org/10.1609/aaai.v40i8.37613) | **AAAI'26** | 2026.03.14 | **Counterfactual Multi-Agent Gaming**: Modifies reference images to expose hallucinating agents and replaces consensus-only debate with evidence-based factual verification. |
| [Kestrel](https://arxiv.org/pdf/2603.16664) | arXiv'26 | 2026.03.17 | **Evidence-Verified Self-Refinement**: Converts grounding-tool outputs into structured evidence and iteratively revises claims after verification. |
| [Look Twice](https://arxiv.org/pdf/2604.01280) | arXiv'26 | 2026.04.01 | **Prompt-Level Evidence Highlighting**: Marks query-relevant image regions and retrieved text so the model re-attends before answering. |
| [Dialectic-Med](https://arxiv.org/pdf/2604.11258) | arXiv'26 | 2026.04.13 | **Adversarial Multi-Agent Debate**: Uses proponent, visual-falsification opponent, and mediator agents to challenge unsupported diagnoses. |
| [R-CoV](https://arxiv.org/pdf/2604.20696) | arXiv'26 | 2026.04.22 | **Region-Aware Chain-of-Verification**: Extracts entities, requests coordinates and region descriptions, then verifies and rewrites the response. |
| [Multi-Agent Guidance](https://doi.org/10.1109/icassp55912.2026.11463505) | **ICASSP'26** | 2026.05.03 | **Multi-Agent Verification**: Coordinates specialized agents to identify and correct unsupported object and relationship claims. |
| [TIGER](https://arxiv.org/pdf/2606.00232) | arXiv'26 | 2026.05.29 | **Graph-Based Evidence Routing**: Separately builds observation and claim graphs, ranks unsupported facts, and repairs only high-risk claims. |
| [Reliability-Aware Multimodal RAG](https://arxiv.org/pdf/2606.15782) | arXiv'26 | 2026.06.14 | **Retrieval-Gated Abstention**: Aggregates external visual-neighbor evidence into reliability scores for answer, caution, or fallback decisions. |
| [BCEA](https://arxiv.org/pdf/2606.16667) | arXiv'26 | 2026.06.15 | **Conformal Evidence Acquisition**: Re-examines images under a bounded budget before choosing whether to answer or abstain. |
| [CoEV](https://arxiv.org/pdf/2606.18609) | arXiv'26 | 2026.06.17 | **Counter-Evidence Verification**: Bidirectionally checks medical assertions against localized visual evidence and corrects unsupported claims. |
| [CEBC](https://aclanthology.org/2026.acl-long.2142/) | **ACL'26** | 2026.07 | **Conformal Evidence-Bounded Editing**: Calibrates an external detector on held-out data and minimally revises unsupported object mentions under explicit risk bounds. |
| [ESC](https://arxiv.org/pdf/2607.02089) | arXiv'26 | 2026.07.01 | **Emotional Self-Correction**: Uses an external verifier and emotional feedback cues to trigger training-free reflective revision. |

</details>

---

## 🎯 Evaluation Benchmark

<details open>
<summary><h3>Comprehensive Benchmark List</h3></summary>

| Benchmark | Pub | Date | Size | Task | Metric | Object | Attribute | Relation | Other | LLM Free | Human Annotation Free |
|-----------|-----|------|------|------|--------|--------|-----------|----------|-------|----------|------------------------|
| [CHAIR](https://arxiv.org/abs/1809.02156) | EMNLP'18 | 2018.09 | 5,000 | Gen | CHAIR | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ |
| [POPE](https://arxiv.org/pdf/2305.10355.pdf) | EMNLP'23 | 2023.05 | 3,000 | Dis | Acc/P/R/F1 | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ |
| [MME](https://arxiv.org/pdf/2306.13394.pdf) | NeurIPS’25 | 2023.06.23 | 1,457 | Dis | Acc/Score | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ |
| [M-HalDetect](https://arxiv.org/pdf/2308.06394.pdf) | AAAI'24 | 2023.08 | 16,000 | Dis | Reward Score | ✅ | ✅ | ✅ | Fine-grained | ❌ | ❌ |
| [CIEM](https://arxiv.org/pdf/2309.02301.pdf) | NeurIPS-W'23| 2023.09 | 40,367 | Dis | Acc/P/R/F1/Specificity | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| [HaELM](https://arxiv.org/pdf/2308.15126.pdf) | arXiv'23 | 2023.10.10 | 25,000 | Gen | LLM Rating | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ |
| [MMHal-Bench](https://arxiv.org/pdf/2309.14525.pdf) | ACL'24 | 2023.09.25 | 96 | Gen | LLM Rating | ✅ | ❌ | ❌ | Model Bias | ❌ | ✅ |
| [GAVIE](https://arxiv.org/pdf/2306.14565.pdf) | ICLR'24 | 2023.09.29 | 1,000 | Gen | LLM Rating | ✅ | ✅ | ✅ | Env/Action/Comp | ❌ | ✅ |
| [NOPE](https://arxiv.org/pdf/2310.05338.pdf) | ACL-W'24 | 2023.10.09 | 29,500 | Dis | Acc/METEOR | ✅ | ❌ | ❌ | Negative Pronoun | ❌ | ✅ |
| [FAITHSCORE](https://arxiv.org/pdf/2311.01477.pdf) | EMNLP'24 | 2023.11.02 | 2,000 | Gen | FaithScore | ✅ | ✅ | ✅ | Obj. Counting | ❌ | ❌ |
| [AMBER](https://arxiv.org/pdf/2311.07397.pdf) | arXiv'23 | 2023.11.13 | 15,202 | Dis & Gen | AMBER Score | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ |
| [Bingo](https://arxiv.org/pdf/2311.03287.pdf) | arXiv'23 | 2023.11.07 | 370 | Gen | Human Assessment | ❌ | ❌ | ❌ | Model Bias | ✅ | ❌ |
| [HallusionBench](https://arxiv.org/pdf/2310.14566.pdf) | CVPR'24 | 2023.11.28 | 1,129 | Gen | LLM Rating | ❌ | ❌ | ❌ | Visual Illusion | ✅ | ❌ |
| [RAH-Bench](https://arxiv.org/pdf/2311.16479.pdf) | arXiv'23 | 2023.11.27 | 3,000 | Dis | False Positive Rate | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| [CCeval](https://arxiv.org/pdf/2310.01779.pdf) | arXiv'23 | 2023.12.03 | 100 | Gen | CHAIR/Coverage | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ |
| [MERLIM](https://arxiv.org/pdf/2312.02219.pdf) | CVPR'25 | 2023.12.03 | 31,373 | Dis | Accuracy | ✅ | ❌ | ✅ | Visual Grounding | ✅ | ❌ |
| [FGHE](https://arxiv.org/pdf/2312.01701.pdf) | MMM'24 | 2023.12.04 | 200 | Dis | Acc/P/R/F | ✅ | ✅ | ✅ | Behaviour | ❌ | ❌ |
| [OpenCHAIR](https://arxiv.org/pdf/2312.03631.pdf) | EMNLP'24 | 2023.12.06 | 2,000 | Gen | OpenCHAIR | ✅ | ✅ | ❌ | Open-Vocabulary | ❌ | ✅ |
| [CorrelationQA](https://arxiv.org/pdf/2402.03757.pdf) | arXiv'24 | 2024.02.06 | 7,308 | Dis | Acc | ✅ | ❌ | ❌ | Spurious Images | ❌ | ✅ |
| [ViGoR](https://arxiv.org/pdf/2402.06118.pdf) | arXiv'24 | 2024.02.09 | 16,000 | Gen | Fine-Grained Reward| ✅ | ✅ | ✅ | Grounding | ❌ | ❌ |
| [VQAv2-IDK](https://arxiv.org/pdf/2402.09717.pdf) | ICASSP'24 | 2024.02.15 | 6,624 | Dis | Acc | ❌ | ❌ | ❌ | IDK (IK) | ✅ | ❌ |
| [MHaluBench](https://arxiv.org/pdf/2402.03190.pdf) | ACL'24 | 2024.02.20 | 1,860 | Gen | Acc/P/R/F | ✅ | ✅ | ❌ | T2I | ✅ | ✅ |
| [MAD-Bench](https://arxiv.org/pdf/2402.13220.pdf) | arXiv'24 | 2024.02.20 | 1,000 | Gen | Acc | ✅ | ✅ | ❌ | Deceptive Prompts | ✅ | ✅ |
| [VHTest](https://arxiv.org/pdf/2402.14683v1.pdf) | ACL'24 | 2024.02.22 | 1,200 | Dis & Gen | Acc | ✅ | ✅ | ❌ | Visual Hallucination | ❌ | ❌ |
| [Hal-Eval](https://arxiv.org/pdf/2402.15721.pdf) | ACMMM'24 | 2024.02.24 | 10,000 | Dis & Gen | Acc/Score | ✅ | ✅ | ✅ | Event Hallucination | ✅ | ❌ |
| [Number Hallucinations](https://arxiv.org/pdf/2403.01373.pdf) | arXiv'24 | 2024.03.03 | 20,000 | Dis | Acc / Consistency | ✅ | ✅ | ❌ | Object Counting | ❌ | ✅ |
| [EvalDial](https://arxiv.org/pdf/2403.10492.pdf) | arXiv'24 | 2024.03.15 | N/A | Dis & Gen| Acc | ✅ | ✅ | ❌ | Dialogue Hallucination| ❌ | ✅ |
| [PHD](https://arxiv.org/pdf/2403.11116.pdf) | CVPR'25 | 2024.03.17 | 102,564 | Dis | PhD Index | ✅ | ✅ | ✅ | Sentiment | ❌ | ❌ |
| [MM-UPD](https://arxiv.org/pdf/2403.20331) | arXiv'24 | 2024.03.29 | 2,095 | Dis | Acc | ❌ | ❌ | ❌ | Unsolvable (UPD) | ❌ | ❌ |
| [ALOHa](https://arxiv.org/pdf/2404.02904v1.pdf) | arXiv'24 | 2024.04.03 | N/A | Gen | ALOHa | ✅ | ❌ | ❌ | Captioning Metric | ❌ | ❌ |
| [VALOR-EVAL](https://arxiv.org/pdf/2404.13874) | ACL'24 | 2024.04.22 | 211 | Gen | Faithfulness & Coverage | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| [THRONE](https://arxiv.org/pdf/2405.05256) | CVPR'24 | 2024.05.08 | 5,000 | Gen | P/R/F | ✅ | ❌ | ❌ | Free-form Generations | ❌ | ✅ |
| [MRHal-Bench](https://arxiv.org/pdf/2405.11165) | NeurIPS'24 | 2024.05.18 | N/A | Gen | Preference Score | ✅ | ✅ | ❌ | Multi-round Conv | ❌ | ✅ |
| [VLind-Bench](https://arxiv.org/pdf/2406.08702) | arXiv'24 | 2024.06.13 | 2,576 | Dis | Acc (Y/N) | ✅ | ❌ | ❌ | Language Priors | ❌ | ✅ |
| [MMRel](https://arxiv.org/pdf/2406.09121) | arXiv'24 | 2024.06.13 | 22,500 | Dis & Gen | Acc | ✅ | ❌ | ✅ | Relation Understanding| ❌ | ❌ |
| [Med-HallMark](https://arxiv.org/pdf/2406.10185) | arXiv'24 | 2024.06.14 | 889,125 | Dis & Gen | MediHall Score | ✅ | ✅ | ❌ | Medical Context | ❌ | ✅ |
| [AutoHallusion](https://arxiv.org/pdf/2406.10900) | EMNLP'24 | 2024.06.16 | 5,000 | Dis | ASR/MASR/CASR | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ |
| [MFC Bench](https://arxiv.org/pdf/2406.11288) | arXiv'24 | 2024.06.17 | 35,000 | Dis & Gen | Acc/F1 | ❌ | ❌ | ❌ | Manipulation/OOC/Veracity | ❌ | ❌ |
| [CHAIR-MEN](https://arxiv.org/pdf/2406.14492) | arXiv'24 | 2024.06.20 | N/A | Gen | CHAIR-MEN / FaithScore | ✅ | ❌ | ❌ | Metric Method | ✅ | ✅ |
| [HQHBench](https://arxiv.org/pdf/2406.17115) | arXiv'24 | 2024.06.24 | 4,000 | Dis & Gen | Hallucination Rate | ✅ | ✅ | ✅ | OCR/Action/Counting | ❌ | ✅ |
| [VideoHallucer](https://arxiv.org/pdf/2406.16338) | arXiv'24 | 2024.06.24 | 1,800 | Dis & Gen | Acc | ✅ | ❌ | ✅ | Temporal/Extrinsic | ❌ | ❌ |
| [R-Bench](https://arxiv.org/pdf/2406.16449) | ICML'24 | 2024.06.24 | 8,030 | Dis | Acc/P/R/F1 | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ |
| [MMHalSnowball](https://arxiv.org/pdf/2407.00569) | arXiv'24 | 2024.06.30 | 4,973 | Dis | Acc | ✅ | ✅ | ❌ | Generated Distractions | ❌ | ✅ |
| [MedVH](https://arxiv.org/pdf/2407.02730) | arXiv'24 | 2024.07.03 | 2,000 | Dis & Gen | Characterization Score| ✅ | ✅ | ❌ | Medical Context | ❌ | ❌ |
| [ROPE](https://arxiv.org/abs/2407.06192) | NeurIPS'24 | 2024.07.08 | 5,000 | Gen | Accuracy | ✅ | ✅ | ✅ | Multi-Object | ✅ | ✅ |
| [BEAF](https://arxiv.org/pdf/2407.13442) | ECCV'24 | 2024.07.18 | 26,064 | Dis | TU/IG/SB/ID | ✅ | ❌ | ❌ | Before-After Changes | ❌ | ✅ |
| [HaloQuest](https://arxiv.org/pdf/2407.15680) | ECCV'24 | 2024.07.22 | 7,748 | Gen | Acc | ✅ | ❌ | ❌ | Synthetic Images / VQA | ❌ | ❌ |
| [MMINSTRUCT](https://arxiv.org/pdf/2407.15838) | arXiv'24 | 2024.07.22 | 973,000 | Gen | Acc | ✅ | ✅ | ✅ | Instruction Tuning | ❌ | ❌ |
| [Hallu-PI](https://arxiv.org/pdf/2408.01355) | arXiv'24 | 2024.08.02 | 1,260 | Dis | Acc | ✅ | ✅ | ✅ | Perturbed Inputs | ❌ | ✅ |
| [Reefknot](https://arxiv.org/pdf/2408.09429) | ACL'25 | 2024.08.18 | 21,880 | Dis & Gen | R-score | ❌ | ❌ | ✅ | Perceptive / Cognitive | ❌ | ✅ |
| [Pfram](https://arxiv.org/pdf/2409.01151) | arXiv'24 | 2024.09.02 | N/A | Dis | Pfram | ✅ | ❌ | ❌ | Alignment Method | ✅ | ✅ |
| [ODE](https://arxiv.org/abs/2409.09318) | CVPR'25 | 2024.09.14 | 8,786 | Dis & Gen | AMBER/Acc | ✅ | ✅ | ❌ | Open-Set | ✅ | ❌ |
| [LLSAVisionQA](https://arxiv.org/pdf/2409.09748) | arXiv'24 | 2024.09.15 | 4,989 | Gen | Acc | ❌ | ✅ | ❌ | Low-level Perception | ❌ | ❌ |
| [CAST](https://arxiv.org/pdf/2409.11007) | arXiv'24 | 2024.09.17 | 15,000 | Dis & Gen | Similarity | ✅ | ✅ | ✅ | Self-consistency | ❌ | ✅ |
| [FIHA](https://arxiv.org/pdf/2409.13612) | arXiv'24 | 2024.09.20 | N/A | Dis & Gen | Acc/P/R/F1 | ✅ | ✅ | ✅ | Eval Method | ✅ | ✅ |
| [EventHallusion](https://arxiv.org/pdf/2409.16597) | arXiv'24 | 2024.09.25 | 711 | Dis & Gen | Accuracy | ❌ | ❌ | ❌ | Video Event | ❌ | ❌ |
| [JourneyBench](https://arxiv.org/pdf/2409.12953) | arXiv'24 | 2024.09.25 | 13,500 | Dis & Gen | Acc | ✅ | ✅ | ❌ | Imaginary VQA | ❌ | ❌ |
| [TUBench](https://arxiv.org/pdf/2410.04107) | arXiv'24 | 2024.10.05 | 2,354 | Dis | Acc | ✅ | ❌ | ✅ | Unanswerable Qs | ❌ | ❌ |
| [LongHallGen](https://arxiv.org/pdf/2410.09962) | arXiv'24 | 2024.10.13 | 6,485 | Dis & Gen | Accuracy | ✅ | ✅ | ❌ | Long Context | ❌ | ✅ |
| [MM-SY](https://arxiv.org/pdf/2410.11302) | arXiv'24 | 2024.10.15 | N/A | Dis | Sycophancy Rate | ✅ | ✅ | ✅ | Sycophancy Eval | ❌ | ✅ |
| [Magnifier Prompt](https://arxiv.org/pdf/2410.11701) | arXiv'24 | 2024.10.15 | N/A | Gen | Acc | ✅ | ❌ | ❌ | Prompt Method | ✅ | ✅ |
| [DeCo](https://arxiv.org/pdf/2410.11779) | arXiv'24 | 2024.10.15 | N/A | Gen | Acc | ✅ | ❌ | ❌ | Decoding Method | ✅ | ✅ |
| [CMM](https://arxiv.org/pdf/2410.12787) | arXiv'24 | 2024.10.16 | 2,400 | Dis | PA/HR | ❌ | ❌ | ❌ | Modality Dominance | ✅ | ❌ |
| [Trust but Verify](https://arxiv.org/pdf/2410.13121) | arXiv'24 | 2024.10.17 | 10,500 | Gen | hscore/tscore | ✅ | ✅ | ❌ | In the Wild Eval | ❌ | ✅ |
| [Tri-HE](https://arxiv.org/pdf/2410.23114) | arXiv'24 | 2024.11.03 | 1,920 | Dis | Acc | ✅ | ❌ | ✅ | Triplet-Level Eval | ❌ | ❌ |
| [H-POPE](https://arxiv.org/pdf/2411.04077) | arXiv'24 | 2024.11.06 | 1,920 | Dis | Acc/P/R/F1 | ✅ | ✅ | ❌ | Coarse-to-fine | ✅ | ❌ |
| [VIDHAL](https://arxiv.org/pdf/2411.16771) | arXiv'24 | 2024.11.25 | 1,000 | Dis | NDCG | ✅ | ✅ | ❌ | Video Action | ❌ | ❌ |
| [HALLUCINOGEN](https://arxiv.org/pdf/2412.20622) | arXiv'24 | 2024.12.29 | 90,000 | Dis & Gen | Acc | ✅ | ❌ | ❌ | Object Hallucination | ❌ | ✅ |
| [CAOS](https://arxiv.org/pdf/2501.15046) | arXiv'25 | 2025.01.25 | 2,000 | Gen | CAOS Score | ✅ | ❌ | ❌ | Object Similarities | ❌ | ✅ |
| [Mirage in the Eyes](https://arxiv.org/pdf/2501.15269) | arXiv'25 | 2025.01.25 | 1,000 | Dis | Acc / HR | ✅ | ✅ | ✅ | Attack/Attention Sink | ✅ | ✅ |
| [LanP](https://arxiv.org/pdf/2502.12359) | arXiv'25 | 2025.02.17 | 340 | Dis | Acc | ✅ | ❌ | ❌ | Language Priors | ❌ | ❌ |
| [MedHallTune](https://arxiv.org/pdf/2502.20780) | arXiv'25 | 2025.02.28 | 1,000,000 | Dis & Gen | Acc | ✅ | ✅ | ❌ | Medical Context | ❌ | ✅ |
| [RePOPE](https://arxiv.org/pdf/2504.15707) | arXiv'25 | 2025.04.22 | 3,000 | Dis | Acc/F1 | ✅ | ❌ | ❌ | Annotation Errors | ✅ | ❌ |
| [Antidote](https://arxiv.org/pdf/2504.20468) | CVPR'25 | 2025.05.07 | N/A | Gen | Acc | ✅ | ❌ | ❌ | CP-Bench Mitigation | ✅ | ✅ |
| [QAVisualGenome & QA-FB15k](https://arxiv.org/pdf/2505.01958) | arXiv'25 | 2025.05.04 | N/A | Dis & Gen | Acc | ✅ | ✅ | ✅ | Visual Object Eval | ❌ | ❌ |
| [Localizing Before Answering](https://arxiv.org/pdf/2505.00744) | arXiv'25 | 2025.05.05 | 67,000 | Gen | Acc / Loc | ✅ | ❌ | ❌ | Grounded Medical | ❌ | ❌ |
| [EmotionHallucer](https://arxiv.org/pdf/2505.11405) | arXiv'25 | 2025.05.16 | 2,742 | Dis | Acc | ❌ | ✅ | ❌ | Emotion Psychology | ❌ | ❌ |
| [MIRAGE](https://arxiv.org/pdf/2505.24238) | arXiv'25 | 2025.06.02 | 1,329 | Dis & Gen | Acc / Factuality | ❌ | ❌ | ✅ | Reasoning Chains | ❌ | ❌ |
| [MMMC](https://arxiv.org/pdf/2507.07151) | arXiv'25 | 2025.07.09 | 5,000 | Dis & Gen | Acc | ✅ | ✅ | ✅ | Modality Conflict | ❌ | ✅ |
| [LOTUS](https://arxiv.org/pdf/2507.19362) | arXiv'25 | 2025.07.25 | N/A | Dis | Alignment/Bias| ❌ | ❌ | ❌ | Societal Bias/Pref | ❌ | ❌ |
| [MIHBench](https://arxiv.org/pdf/2508.00726) | arXiv'25 | 2025.08.01 | 3,000 | Dis & Gen | Acc | ✅ | ❌ | ❌ | Multi-Image Reasoning | ❌ | ❌ |
| [HOPE](https://arxiv.org/pdf/2508.06530) | arXiv'25 | 2025.08.03 | N/A | Gen | Precision Drop| ✅ | ✅ | ❌ | Misleading Distractors | ❌ | ✅ |
| [SHALE](https://arxiv.org/pdf/2508.09584) | arXiv'25 | 2025.08.14 | 30,100 | Dis & Gen | Acc | ✅ | ✅ | ✅ | Fine-grained | ❌ | ✅ |
| [HUmbleBench](https://arxiv.org/pdf/2509.09658) | arXiv'25 | 2025.09.11 | 22,831 | Dis | Rejection Acc | ✅ | ✅ | ✅ | Epistemic Humility | ❌ | ✅ |
| [VHBench-10](https://arxiv.org/pdf/2509.13836) | arXiv'25 | 2025.09.17 | 10,000 | Dis | Acc | ✅ | ✅ | ✅ | Vision Perspective | ❌ | ❌ |
| [ChartHal](https://arxiv.org/pdf/2509.17481) | arXiv'25 | 2025.09.22 | 1,062 | Dis & Gen | Acc | ❌ | ❌ | ❌ | Chart Understanding | ❌ | ❌ |
| [ColorBlindnessEval](https://arxiv.org/pdf/2509.19070) | arXiv'25 | 2025.09.23 | 500 | Dis & Gen | Acc | ❌ | ✅ | ❌ | Color Blindness Tests | ✅ | ❌ |
| [Common-O Bench](https://arxiv.org/pdf/2511.03768v1) | arXiv'25 | 2025.11.05 | 10,500 | Dis & Gen | Acc | ✅ | ❌ | ✅ | Reasoning Across Scenes| ❌ | ❌ |
| [Causal-HalBench](https://arxiv.org/pdf/2511.10268v1) | arXiv'25 | 2025.11.13 | N/A | Gen | Acc | ✅ | ❌ | ❌ | Causal Intervention | ❌ | ✅ |
| [What Color Is It](https://arxiv.org/pdf/2511.13400v2) | arXiv'25 | 2025.11.17 | N/A | Dis | Acc | ❌ | ✅ | ❌ | Text-Interference | ❌ | ✅ |
| [MVI-Bench](https://arxiv.org/pdf/2511.14159v1) | arXiv'25 | 2025.11.18 | 1,248 | Dis & Gen | MVI-Sensitivity | ✅ | ✅ | ✅ | Misleading Visual | ❌ | ❌ |
| [PIH](https://arxiv.org/pdf/2601.05201v1) | arXiv'26 | 2026.01.08 | N/A | Gen | PIH Ablation | ✅ | ❌ | ❌ | Prompt-Induced | ✅ | ✅ |
| [EH-Benchmark](https://doi.org/10.1016/j.inffus.2025.103631) | **Information Fusion'26** | 2026.02 | N/A | Dis & Gen | N/A | ❌ | ❌ | ❌ | Ophthalmology | ❌ | ❌ |
| [CFHR](https://arxiv.org/pdf/2602.05437v1) | arXiv'26 | 2026.02.05 | N/A | Dis | CFHR | ❌ | ❌ | ❌ | Counterfactual | ❌ | ❌ |
| [SPD-Faith Bench](https://arxiv.org/pdf/2602.07833) | arXiv'26 | 2026.02.08 | N/A | Dis & Gen | Faithfulness | ✅ | ✅ | ✅ | CoT Faithfulness | ❌ | ❌ |
| [VLM-UQBench](https://arxiv.org/pdf/2602.09214) | arXiv'26 | 2026.02.09 | 600 | Dis | UQ Sens./Corr. | ✅ | ✅ | ❌ | Multimodal Uncertainty | ✅ | ❌ |
| [RSHalluEval](https://arxiv.org/pdf/2602.10799) | arXiv'26 | 2026.02.11 | 2,023 | Dis & Gen | Hallucination-Free Rate | ✅ | ✅ | ✅ | Remote Sensing | ❌ | ❌ |
| [RSHBench](https://arxiv.org/pdf/2603.02754) | arXiv'26 | 2026.03.03 | N/A | Dis & Gen | Acc / Hallucination Rate | ✅ | ✅ | ✅ | Remote Sensing | ✅ | ❌ |
| [FINER](https://arxiv.org/pdf/2603.17662) | arXiv'26 | 2026.03.18 | N/A | Dis | Acc / Hallucination Rate | ✅ | ✅ | ✅ | Fine-Grained Negatives | ✅ | ❌ |
| [FREAK](https://arxiv.org/pdf/2603.19765) | arXiv'26 | 2026.03.20 | N/A | Dis | Accuracy | ✅ | ✅ | ✅ | Counter-Commonsense | ✅ | ❌ |
| [CDH-Bench](https://arxiv.org/pdf/2603.27982) | arXiv'26 | 2026.03.30 | N/A | Dis | CF-Acc/CFAD/CCR/RPD | ✅ | ✅ | ✅ | Commonsense Conflict | ✅ | ❌ |
| [M2-Verify](https://arxiv.org/pdf/2604.01306) | arXiv'26 | 2026.04.01 | 469,000+ | Dis | Micro-F1 | ✅ | ✅ | ✅ | Scientific Claims | ✅ | ❌ |
| [DetailVerifyBench](https://arxiv.org/pdf/2604.05623) | arXiv'26 | 2026.04.07 | 1,000 | Dis | Span/Token Localization | ✅ | ✅ | ✅ | Long Captions | ✅ | ❌ |
| [VLM-DeflectionBench](https://arxiv.org/pdf/2604.12033) | arXiv'26 | 2026.04.13 | 2,775 | Dis & Gen | Acc / Deflection | ✅ | ✅ | ✅ | Retrieval Conflict | ✅ | ❌ |
| [DO-Bench](https://arxiv.org/pdf/2604.22822) | arXiv'26 | 2026.04.18 | N/A | Dis | PriorRobust/PerceptionAbility | ✅ | ❌ | ❌ | Error Attribution | ✅ | ❌ |
| [VisualTextTrap](https://arxiv.org/pdf/2604.17375) | arXiv'26 | 2026.04.19 | 6,057 | Dis & Gen | TOIH Level / Acc | ✅ | ✅ | ✅ | Text-Overlay Video | ✅ | ❌ |
| [Med-StepBench](https://arxiv.org/pdf/2605.10002) | arXiv'26 | 2026.05.11 | 1,000,000+ | Dis | Step Acc / Hallucination | ✅ | ✅ | ✅ | 3D Medical Reasoning | ✅ | ❌ |
| [HalluCXR](https://arxiv.org/pdf/2605.20469) | arXiv'26 | 2026.05.19 | 15,408 | Gen | F1 / Hallucination Rate | ✅ | ✅ | ❌ | Chest Radiographs | ❌ | ❌ |
| [MM-Snowball](https://arxiv.org/pdf/2606.00622) | arXiv'26 | 2026.05.30 | N/A | Dis & Gen | Snowballing Rate | ✅ | ✅ | ✅ | Multi-Turn Dialogue | ❌ | ❌ |
| [ChronoPhyBench](https://arxiv.org/pdf/2606.07962) | arXiv'26 | 2026.06.06 | 10,000+ | Dis | Acc / Hallucination Rate | ✅ | ✅ | ✅ | Physical Dynamics | ✅ | ❌ |
| [ClinHallu](https://arxiv.org/pdf/2606.14697) | arXiv'26 | 2026.06.12 | 7,031 | Dis | Stage-Wise HR | ✅ | ✅ | ✅ | Medical Reasoning | ❌ | ❌ |
| [MotionHalluc](https://arxiv.org/pdf/2606.23061) | arXiv'26 | 2026.06.22 | 1,540 | Dis & Gen | Acc / Hallucination Rate | ❌ | ❌ | ✅ | Video Motion | ✅ | ❌ |
| [GI Hallucination Detection](https://arxiv.org/pdf/2606.24115) | arXiv'26 | 2026.06.23 | 4,392 | Dis | AUC | ✅ | ✅ | ❌ | GI Endoscopy | ✅ | ❌ |
| [MedBench v5](https://arxiv.org/pdf/2606.24155) | arXiv'26 | 2026.06.23 | N/A | Dis & Gen | Process Audit | ✅ | ✅ | ✅ | Clinical Stressors | ❌ | ❌ |
| [CRISP](https://arxiv.org/pdf/2606.26535) | arXiv'26 | 2026.06.25 | N/A | Dis | Consistency | ❌ | ❌ | ✅ | Spatial Intelligence | ✅ | ❌ |
| [GAVEL](https://arxiv.org/pdf/2606.26923) | arXiv'26 | 2026.06.25 | N/A | Dis & Gen | Verification/Localization | ✅ | ✅ | ✅ | Grounded Caption Errors | ❌ | ❌ |
| [HalluAudio](https://aclanthology.org/2026.acl-long.1797/) | **ACL'26** | 2026.07 | 5,000+ | Dis & Gen | Acc / Hallucination Rate | ❌ | ❌ | ❌ | Speech/Sound/Music | ✅ | ❌ |
| [MissingBench-Verified](https://arxiv.org/pdf/2607.18673) | arXiv'26 | 2026.07.21 | N/A | Dis | Accuracy | ✅ | ✅ | ❌ | Missing Object Parts | ✅ | ❌ |

</details>

---

## 📝 Citation

If you find our survey paper, this repository, or the hierarchical causes taxonomy useful for your research, please consider citing our work:

```bibtex

```
## 🤝 Contributing
We actively welcome contributions! The field of MLLM hallucinations is moving incredibly fast. If you find a new paper that fits into our taxonomy (especially elegant training-free methods, novel architecture interventions, or robust benchmarks), please feel free to open a Pull Request.

1.Format your addition strictly according to the existing tables.

2.Keep the Methodology description concise (one sentence limit).

3.Ensure the Date aligns with the initial arXiv release or conference acceptance.
