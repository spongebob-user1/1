# Awesome CoT for Autonomous Driving

![License](https://img.shields.io/badge/license-MIT-blue.svg)
[![arXiv](https://img.shields.io/badge/arXiv-2505.20223-<COLOR>.svg)](https://arxiv.org/abs/2505.20223)

This is the repository of **Chain-of-Thought for Autonomous Driving: A Comprehensive Survey and Future Prospects**. We warmly welcome contributions from everyone to this repository. Please feel free to submit issues or pull requests for any missing papers, datasets, or methodologies. Our team is committed to maintaining and updating the repository regularly.

# Contents

- [Introduction](#introduction)
- [Methods](#methods)
  - [Modular Driving CoT](#modular-driving-cot)
  - [Logical Driving CoT](#logical-driving-cot)
  - [Reflective Driving CoT](#reflective-driving-cot)
- [Datasets](#datasets)
- [Citation](#citation)

# Introduction

Chain-of-Thought reasoning empowers autonomous driving systems with human-like logical processing for complex scenarios. Our review analyzes CoT implementations and maintains a live repository.


# Tables

### TABLE I: 

### Summary of Implicit World Models in Autonomous Driving

| **Method**                                                   | **Latent Representation**                  | **Dynamics Architecture**      | **Training Objective**         | **Inference Mechanism** |                           **Code**                           |
| :----------------------------------------------------------- | :----------------------------------------- | :----------------------------- | :----------------------------- | :---------------------- | :----------------------------------------------------------: |
| <br>***Feature Alignment***                                  |                                            |                                |                                |                         |                                                              |
| [**I-JEPA**](https://arxiv.org/pdf/2301.08243)               | Continuous Patch                           | ViT Block                      | Latent Distance                | Masked Prediction       |     [GitHub](https://github.com/facebookresearch/ijepa)      |
| [**Dense-JEPA**](https://openreview.net/pdf?id=bc0fa51d9e)   | Continuous Patch                           | ViT Block (Dense)              | Latent Distance                | Masked Prediction       |                              x                               |
| [**C-JEPA**](https://arxiv.org/pdf/2410.19560)               | Continuous Patch                           | ViT Block                      | Latent Dist + Reg              | Masked Prediction       |       [GitHub](https://github.com/galilai-group/cjepa)       |
| [**AD-L-JEPA**](https://arxiv.org/pdf/2501.04969)            | BEV Embeddings                             | Transformer (BEV)              | Latent Distance                | Masked Prediction       |                              x                               |
| [**Point-JEPA**](https://arxiv.org/pdf/2404.16432)           | Point Embeddings                           | Transformer (Point)            | Latent Distance                | Masked Prediction       |      [GitHub](https://github.com/Ayumu-J-S/Point-JEPA)       |
| [**V-JEPA**](https://arxiv.org/pdf/2404.08471)               | Spatiotemporal Clips                       | Video Transformer              | Latent Distance                | Masked Prediction       |     [GitHub](https://github.com/facebookresearch/vjepa)      |
| [**V-JEPA 2**](https://arxiv.org/pdf/2506.09985)             | Spatiotemporal Emb.                        | Video Transformer              | Latent Distance                | Masked Prediction       |    [GitHub](https://github.com/facebookresearch/jepa-wms)    |
| [**Drive-JEPA**](https://arxiv.org/pdf/2601.22032)           | Planning-aligned Spatiotemporal Embeddings | Video ViT Predictor            | Task-aligned Latent Distance   | Masked Pretraining      |      [GitHub](https://github.com/linhanwang/Drive-JEPA)      |
| [**DINO-WM**](https://arxiv.org/pdf/2411.04983)              | Patch Features                             | ViT Block                      | Latent Distance                | Forward Prediction      |                              x                               |
| [**UnO**](https://openaccess.thecvf.com/content/CVPR2024/papers/Agro_UnO_Unsupervised_Occupancy_Fields_for_Perception_and_Forecasting_CVPR_2024_paper.pdf) | Continuous 4D Field                        | Neural ODE / 4D Func           | Occupancy Prob                 | Querying 4D Field       |          [GitHub](https://github.com/waabi-ai/uno)           |
| [**MC-JEPA**](https://arxiv.org/pdf/2307.12698)              | Decoupled (Motion/Content)                 | Decoupled Transformer          | Latent Distance                | Masked Prediction       |                              x                               |
| [**PanDora**](https://arxiv.org/pdf/2406.09455)              | Video States + Lang                        | Hybrid Transformer             | Latent Distance                | Autoregressive Gen.     |      [GitHub](https://github.com/Jiannan-Xiang/PanDora)      |
| [**LAW**](https://arxiv.org/pdf/2406.08481)                  | Action-aware Visual Latents                | Action-conditioned Transformer | Action-aligned Latent Distance | Forward Prediction      |         [GitHub](https://github.com/BraveGroup/LAW)          |
| [**T-JEPA**](https://arxiv.org/pdf/2406.12913) / [**HiT-JEPA**](https://arxiv.org/pdf/2507.00028) | Trajectory Segments                        | Trajectory Transformer         | Latent Distance                | Masked Prediction       |                              x                               |
| <br>***Value Alignment***                                    |                                            |                                |                                |                         |                                                              |
| [**MuZero**](https://arxiv.org/pdf/1911.08265)               | Continuous                                 | Recurrent Network              | Value+Policy+Reward            | MCTS                    |                              x                               |
| [**EfficientZero**](https://arxiv.org/pdf/2111.00210)        | Continuous                                 | Recurrent Network              | Value+Policy+Consist           | MCTS                    |       [GitHub](https://github.com/YeWR/EfficientZero)        |
| [**Think2Drive**](https://arxiv.org/pdf/2402.18221)          | Sequence of Tokens                         | World Model Transformer        | Value / Reward                 | MCTS                    |  [GitHub](https://github.com/Thinklab-SJTU/CornerCaseRepo)   |
| [**L3P**](https://arxiv.org/pdf/2108.03223)                  | Graph of Landmarks                         | Topological Graph              | Reachability (Value)           | Graph Search            | [GitHub](https://github.com/LunjunZhang/world-model-as-a-graph) |
| [**MILE**](https://arxiv.org/pdf/2210.13877)                 | Continuous                                 | Probabilistic Imagination      | Action Regression              | Gradient Optimization   |          [GitHub](https://github.com/wayveai/mile)           |
| [**UniAD**](https://arxiv.org/pdf/2212.10156)                | Queries (Cont.)                            | Transformer (Query-based)      | Planning Loss                  | Gradient Optimization   |       [GitHub](https://github.com/OpenDriveLab/UniAD)        |
| [**SafeDreamer**](https://arxiv.org/pdf/2307.07176)          | Continuous                                 | RSSM (Dreamer)                 | Reward+Safety Penalty          | Lagrangian Optimization |    [GitHub](https://github.com/PKU-Alignment/SafeDreamer)    |
| <br>***Behavior Alignment***                                 |                                            |                                |                                |                         |                                                              |
| [**MultiPath++**](https://arxiv.org/pdf/2111.14973)          | Object-centric Latents                     | Interaction Graph              | Trajectory Dist.               | Anchor-based Inference  |                              x                               |
| [**TrafficBots**](https://arxiv.org/pdf/2303.04116)          | Latent Personality Embeddings              | CVAE (Scene-centric)           | ELBO / Prediction              | Conditioned Sampling    |    [GitHub](https://github.com/Zhejun-Zhang/TrafficBots)     |
| [**CCE-MASAC**](https://scholar.google.com/scholar?q=Modelling+competitive+behaviors+in+autonomous+driving+under+generative+world+model) | Multi-agent Game Latents                   | Markov Game Dynamics           | Nash Equilibrium Objective     | Game-theoretic Rollout  |                              x                               |
| [**CarFormer**](https://scholar.google.com/scholar?q=Carformer:+Self-driving+with+learned+object-centric+representations) | Implicit Object Slots                      | Autoregressive Trans.          | Trajectory Alignment           | Slot Attention Decoding |      [GitHub](https://github.com/shadihamdan/CarFormer)      |
| [**Wayformer**](https://arxiv.org/pdf/2207.05844)            | Scene Tokens                               | Multi-axis Attention           | Trajectory Alignment           | Scene-centric Decoding  |                              x                               |
| [**Forecast-MAE**](https://scholar.google.com/scholar?q=Forecast-mae:+Self-supervised+pre-training+for+motion+forecasting+with+masked+autoencoders) | Trajectory Context Tokens                  | Masked Autoencoder             | Trajectory Recon.              | Mask-Predict Decoding   |      [GitHub](https://github.com/jchengai/forecast-mae)      |





### TABLE II: 

### Comprehensive Summary of Datasets and Benchmarks Driving the Evolution of Latent World Models

| **Dataset / Benchmark**                                | **Year** | **Size (Scale)** | **Input Modality** | **Key Annotations for LWMs**    | **Supported Evaluation**   |                           **Code**                           |
| :----------------------------------------------------- | :------- | :--------------- | :----------------- | :------------------------------ | :------------------------- | :----------------------------------------------------------: |
| <br>***I. Foundation Datasets for Dynamics Learning*** |          |                  |                    |                                 |                            |                                                              |
| [**nuScenes**](https://arxiv.org/pdf/1903.11027)       | 2020     | 40K frames       | Cam, LiDAR, Rad    | 3D BBox, Map, Ego-pose          | Open-loop Planning         |    [GitHub](https://github.com/nutonomy/nuscenes-devkit)     |
| [**Waymo Open**](https://arxiv.org/pdf/1912.04838)     | 2020     | 104K frames      | Cam, LiDAR         | 3D BBox, Map, High-freq Traj.   | Open-loop Planning         | [GitHub](https://github.com/waymo-research/waymo-open-dataset) |
| [**Argoverse 2**](https://arxiv.org/pdf/2301.00493)    | 2023     | 250K logs        | Cam, LiDAR         | HD Map, Multi-agent Traj.       | Open-loop Planning         |        [GitHub](https://github.com/argoverse/av2-api)        |
| [**WOMD-E2E**](https://arxiv.org/pdf/2104.10133)       | 2024     | 4,021 clips      | Cam, LiDAR         | Multi-agent Traj., Ego-action   | Reactive Closed-loop       |                              x                               |
| <br>***II. Large-Scale Video Pre-training Corpus***    |          |                  |                    |                                 |                            |                                                              |
| [**OpenDV-2K**](https://arxiv.org/pdf/2403.03182)      | 2024     | 65.1M frames     | Camera-only        | Ego-trajectory (Pseudo)         | Latent Representation      |          [GitHub](https://github.com/wzzheng/GenAD)          |
| [**BDD100K**](https://arxiv.org/pdf/1805.04687)        | 2020     | 100K videos      | Camera-only        | 2D Box, Action (Lane/Turn)      | Domain Adaptation          |         [GitHub](https://github.com/bdd100k/bdd100k)         |
| [**SHIFT**](https://arxiv.org/pdf/2206.08347)          | 2022     | 5M frames        | Multi-modal        | Dense Depth, Segmentation       | Domain Adaptation          |       [GitHub](https://github.com/SysCV/shift-dataset)       |
| [**DrivePhysica**](https://arxiv.org/pdf/2412.08410)   | 2024     | 10M frames       | Camera-only        | Unannotated physics evolution   | Video Pre-training         |          [GitHub](https://github.com/DrivePhysica)           |
| <br>***III. Closed-Loop Planning & Decision Making***  |          |                  |                    |                                 |                            |                                                              |
| [**nuPlan**](https://arxiv.org/pdf/2106.11810)         | 2021     | 1,500 hours      | Cam, LiDAR, Map    | Human Driving Traj., Ego-action | Reactive Closed-loop       |     [GitHub](https://github.com/motional/nuplan-devkit)      |
| [**Bench2Drive**](https://arxiv.org/pdf/2406.03877)    | 2024     | 10K clips        | Multi-modal        | Dense Action, Ego-state         | CARLA Closed-loop          |    [GitHub](https://github.com/Thinklab-SJTU/Bench2Drive)    |
| [**NAVSIM**](https://arxiv.org/pdf/2406.15349)         | 2024     | 1M+ frames       | Cam, LiDAR         | Action-trajectory alignment     | Non-reactive Closed-loop   |     [GitHub](https://github.com/autonomousvision/navsim)     |
| <br>***IV. Reasoning & Instruction Following (VLA)***  |          |                  |                    |                                 |                            |                                                              |
| [**DriveLM**](https://arxiv.org/pdf/2312.14150)        | 2024     | 445K QA pairs    | Cam, LiDAR         | Graph QA, Logical reasoning     | Instruction Fidelity       |      [GitHub](https://github.com/OpenDriveLab/DriveLM)       |
| [**LMDrive**](https://arxiv.org/pdf/2312.07488)        | 2024     | 120K traj.       | Camera, Text       | Navigation Prompts, Action      | Language-guided Control    |        [GitHub](https://github.com/opendilab/LMDrive)        |
| [**Rank2Tell**](https://arxiv.org/pdf/2309.01428)      | 2024     | 50K traj.        | Cam, LiDAR         | Importance ranking, Ego-action  | Reasoning Interpretability |                              x                               |
| [**AutoVLA**](https://arxiv.org/pdf/2506.13757)        | 2024     | 80K episodes     | Multi-modal        | Multimodal QAs, Policy steps    | VLA Reasoning              |      [GitHub](https://github.com/ucla-mobility/AutoVLA)      |

### TABLE III: 

### Multidimensional Evaluation Metrics Tailored for Latent World Models

| **Category / Metric**                                        | **Dir.** | **Definition / Mathematical Form**                           | **Target Capability Evaluated** |                        **Code**                         |
| :----------------------------------------------------------- | :------: | :----------------------------------------------------------- | :------------------------------ | :-----------------------------------------------------: |
| <br>***Latent Representation Quality***                      |          |                                                              |                                 |                                                         |
| [**Linear Probing (LP-mIoU/mAP)**](https://arxiv.org/pdf/2402.11502) |    ↑     | Accuracy of frozen encoder on downstream tasks               | Semantic Disentanglement        |       [GitHub](https://github.com/wzzheng/GenAD)        |
| [**Latent Prediction Error (LPE)**](https://arxiv.org/pdf/2210.13877) |    ↓     | $\Vert z_{t+1} - \hat{z}_{t+1}\Vert_2^2$ or $1 - \cos(z_{t+1}, \hat{z}_{t+1})$ | Dynamics Consistency            |        [GitHub](https://github.com/wayveai/mile)        |
| [**Long-Horizon Consistency (LHC)**](https://arxiv.org/pdf/2210.13877) |    ↑     | Error decay rate over unrolled multi-step predictions        | Temporal Stability              |        [GitHub](https://github.com/wayveai/mile)        |
| [**Disentanglement Score (DS)**](https://arxiv.org/pdf/2312.07488) |    ↑     | InfoNCE loss measuring action-environment independence       | Action-Conditioned Fidelity     |     [GitHub](https://github.com/opendilab/LMDrive)      |
| [**Temporal Consistency (TCS)**](https://arxiv.org/pdf/2309.09777) |    ↑     | Variance of latent state transitions across adjacent frames  | Motion Smoothness               | [GitHub](https://github.com/XiaofengWang7/DriveDreamer) |
| [**Normalized Mutual Info. (NMI)**](https://arxiv.org/pdf/2312.14150) |    ↑     | Mutual information between latent clusters and labels        | Feature Interpretability        |    [GitHub](https://github.com/OpenDriveLab/DriveLM)    |
| [**Feature-level LPIPS (LPIPS-F)**](https://arxiv.org/pdf/2309.09777) |    ↓     | Perceptual similarity calculated purely in feature space     | Perceptual Preservation         | [GitHub](https://github.com/XiaofengWang7/DriveDreamer) |
| <br>***Open-Loop Planning***                                 |          |                                                              |                                 |                                                         |
| [**Avg. / Final Disp. Error (ADE/FDE)**](https://arxiv.org/pdf/1903.11027) |    ↓     | $\frac{1}{T} \sum \Vert p_t - \hat{p}_t\Vert_2$ (ADE) and $\Vert p_T - \hat{p}_T\Vert_2$ (FDE) | Trajectory Accuracy             |  [GitHub](https://github.com/nutonomy/nuscenes-devkit)  |
| [**Collision Rate (CR)**](https://arxiv.org/pdf/2106.11810)  |    ↓     | Percentage of predicted trajectories intersecting obstacles  | Spatial Safety Awareness        |   [GitHub](https://github.com/motional/nuplan-devkit)   |
| [**Miss Rate (MR)**](https://arxiv.org/pdf/2106.11810)       |    ↓     | Rate that ground-truth is not covered by predictions         | Scenario Coverage               |   [GitHub](https://github.com/motional/nuplan-devkit)   |
| [**Predictive Driver Score (PDMS)**](https://arxiv.org/pdf/2406.15349) |    ↑     | Consistency of predicted behavior with human patterns        | Human-like Interaction          |  [GitHub](https://github.com/autonomousvision/navsim)   |
| <br>***Closed-Loop Simulation & Reasoning***                 |          |                                                              |                                 |                                                         |
| [**Driving Score (DS)**](https://arxiv.org/pdf/1711.03938)   |    ↑     | $\text{Route Completion} \times (1 - \text{Infraction Penalty})$ | Comprehensive Policy            |   [GitHub](https://github.com/carla-simulator/carla)    |
| [**Success Rate (SR)**](https://arxiv.org/pdf/1711.03938)    |    ↑     | Percentage of episodes completed without collision           | Safe Navigation Limit           |   [GitHub](https://github.com/carla-simulator/carla)    |
| [**Infraction Score (IS)**](https://arxiv.org/pdf/1711.03938) |    ↓     | Cumulative penalty from traffic rule violations              | Long-tail Safety                |   [GitHub](https://github.com/carla-simulator/carla)    |
| [**Route Completion (RC)**](https://arxiv.org/pdf/1711.03938) |    ↑     | Percentage of planned route distance successfully traversed  | Goal-directed execution         |   [GitHub](https://github.com/carla-simulator/carla)    |
| [**Instruction Fidelity (IF)**](https://arxiv.org/pdf/2312.07488) |    ↑     | Execution alignment with natural language prompts            | LLM-guided Control              |     [GitHub](https://github.com/opendilab/LMDrive)      |
| [**Reasoning Interpretability (RI)**](https://arxiv.org/pdf/2309.01428) |    ↑     | Consistency of Chain-of-Thought output with human logic      | Action Explainability           |                            x                            |

# Datasets

With technological advancements, datasets now encompass not only perceptual and behavioral data but also progressively integrate semantic cognitive information, driving the development of CoT based models.

# Citation

If you find this repository useful for your research, please consider citing the following paper:

```bibtex
@article{cui2025chain,
  title={Chain-of-Thought for Autonomous Driving: A Comprehensive Survey and Future Prospects},
  author={Cui, Yixin and Lin, Haotian and Yang, Shuo and Wang, Yixiao and Huang, Yanjun and Chen, Hong},
  journal={arXiv preprint arXiv:2505.20223},
  year={2025}
}
```



