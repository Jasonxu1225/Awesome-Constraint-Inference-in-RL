# Awesome-Constraint-Inference-in-RL

A collection of research papers on constraint inference within the field of Reinforcement Learning (RL), with a primary focus on **Inverse Constrained Reinforcement Learning (ICRL)**. Our survey paper *[A Comprehensive Survey on Inverse Constrained Reinforcement Learning: Definitions, Progress and Challenges](https://openreview.net/pdf?id=WUQsBiJqyP)* has been accepted to TMLR 2025.

This repository will be continuously updated. Welcome to follow and star it!



## Importance of Inferring Constraints

To ensure the reliability of a Reinforcement Learning (RL) algorithm within safety-critical applications, it is crucial for the agent to have knowledge of the underlying constraints. However, in many real-world tasks, the constraints are often unknown and difficult to specify mathematically, particularly when these constraints are time-varying, context-dependent, and inherent to the expert’s own experience. For example, the following figure shows a contemporary example of a highway merging task, where the ideal constraints depend on the traffic or road conditions as well as the weather. 

![introduction](./figures/example.png)

An example of the context-sensitive car distance constraint between vehicles during a merge on the highway. Under proper weather conditions, when vehicle speed is relatively low and traffic congestion is high, the distance between cars can be reduced. However, in adverse weather conditions, when vehicles are moving fast and traffic is sparse, it becomes necessary to increase the distance between cars to ensure safety.

## Procedure of ICRL

An effective approach to resolve the above challenges is Inverse Constrained Reinforcement Learning (ICRL), which infers the implicit constraints respected by expert agents, utilizing experience collected from both the environment and the observed demonstration dataset. These constraints, learned through a data-driven approach, can effectively generalize across multiple environments, thereby providing a more comprehensive explanation of the expert agents’ behavior and facilitating safety control in downstream applications.

In the typical preference modeling approach, the agent must first recover the rewards optimized and constraints respected by expert agents, and imitate experts by optimizing the Constrained Reinforcement Learning (CRL) objective under these constraints. This is a challenging task since there might be various equivalent combinations of reward distributions and constraints that can explain the same expert demonstrations. Striving for identifiability, ICRL algorithms simplify the problem by assuming that rewards are observable, and the goal is to recover only the constraints that best explain the expert data. The inference process of ICRL often involves alternating between updating an imitating policy and updating a constraint function. The following figure summarizes the main procedure of ICRL.

<p align="center">
  <img src="./figures/flowchart.png" alt="flowchart" style="width:50%;"/>
</p>

## Papers

### Constraint Inference in Inverse Optimal Control

- [Learning constraints from demonstrations](https://arxiv.org/pdf/1812.07084) [Workshop 2018]
  - Glen Chou, Dmitry Berenson, Necmiye Ozay
  - Address the forward problem with the hit-and-run sampling algorithm
  - ` General Constraints` `Discrete`

- [Learning parametric constraints in high dimensions from demonstrations](http://proceedings.mlr.press/v100/chou20a/chou20a.pdf) [CoRL 2019]
  - Glen Chou, Necmiye Ozay, Dmitry Berenson
  - Extend to continuous state spaces by employing parametric constraint functions
  - ` Parametric Constraints` `Continuous`

- [Uncertainty-aware constraint learning for adaptive safe motion planning from demonstrations](https://proceedings.mlr.press/v155/chou21a/chou21a.pdf) [CoRL 2020]
  - Glen Chou, Necmiye Ozay, Dmitry Berenson
  - Devise uncertainty-aware constraints driven by Bayesian inference
  - ` Uncertainty-aware Constraints` `Continuous`

- [Constraint inference in control tasks from expert demonstrations via inverse optimization](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10383197) [CDC 2023]
  - Dimitris Papadimitriou, Jingqi Li
  - Propose an incremental greedy constraint inference algorithm
  - `Constraint Set`

- [Efficient learning of constraints and generic null space policies](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7989181) [ICRA 2017]
  - Leopoldo Armesto, Jorren Bosga, Vladimir Ivan, Sethu Vijayakumar
  - Focus on learning geometric constraints
  - `Geometric Constraints`

- [C-learn: Learning geometric constraints from demonstrations for multi-step manipulation in shared autonomy](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7989466) [ICRA 2017]
  - Leopoldo Armesto, Jorren Bosga, Vladimir Ivan, Sethu Vijayakumar
  - Learn multi-step manipulation tasks from demonstrations as a sequence of key frames and a set of geometric constraints
  - `Geometric Constraints`

- [Isoperimetric constraint inference for discrete-time nonlinear systems based on inverse optimal control](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10471228) [IEEE Transactions on Cybernetics 2024]
  - Qinglai Wei, Tao Li, Jie Zhang, Hongyang Li, Xin Wang, Jun Xiao
  - Infer the unknown isoperimetric constraints given optimal state and control trajectories
  - `Isoperimetric Constraints`

- [Learning object orientation constraints and guiding constraints for narrow passages from one demonstration](https://web.cs.wpi.edu/~rich/heres_how/pub/LiBerenson2016_ISER.pdf) [ISER 2016]
  - Changshuo Li, Dmitry Berenson
  - Explore the area around the demonstration trajectory through sampling in task space, and learn constraints by segmenting and analyzing the feasible samples
  - `Trajectory-oriented Constraints`

- [Inferring and assisting with constraints in shared autonomy](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7799299) [CDC 2016]
  - Negar Mehr, Roberto Horowitz, Anca D. Dragan
  - Introduce a method for inferring constraints from operator input, along with a confidence-based way of assisting the user in maintaining them, and evaluate in a user study
  - `Trajectory-oriented Constraints`

### Constraint Inference from Human Interventions

- [Learning Constraints on Autonomous Behavior from Proactive Feedback](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10341801) [IROS 2023]
  - Connor Basich, Saaduddin Mahmud, Shlomo Zilberstein
  - Assume access only to sparse interventions, and infer constraints from human interventions without full or partial demonstration trajectories
  - `Constraint Set`

- [Expert intervention learning: An online framework for robot learning from explicit and implicit human feedback](https://personalrobotics.cs.washington.edu/publications/spencer2022eil.pdf) [Autonomous Robots 2022]
  - Jonathan Spencer, Sanjiban Choudhury, Matthew Barnes, Matthew Schmittle, Mung Chiang, Peter Ramadge, Sidd Srinivasa
  - Formalize interventions as action-value constraints
  - `Intervention Constraints`

### Inverse Constrained Reinforcement Learning

#### ICRL in Deterministic Environments

- [Maximum Likelihood Constraint Inference for Inverse Reinforcement Learning](https://arxiv.org/pdf/1909.05477) [ICLR 2020]
  - Dexter R.R. Scobee, S. Shankar Sastry
  - Infer the maximum likelihood constraint to best explain observed behavior under the maximum entropy principle
  - `Maximum Entropy` `Discrete`

- [Inverse Constrained Reinforcement Learning](http://proceedings.mlr.press/v139/malik21a/malik21a.pdf) [ICML 2021]
  - Shehryar Malik, Usman Anwar, Alireza Aghasi, Ali Ahmed
  - Propose learning a binary classifier as a feasibility function approximator to determine the probability that performing one action under one state is feasible
  - `Maximum Entropy` `Continuous`

- [Positive-Unlabeled Constraint Learning for Inferring Nonlinear Continuous Constraints Functions From Expert Demonstrations](http://proceedings.mlr.press/v139/malik21a/malik21a.pdf) [RAL 2024]
  - Baiyu Peng, Aude Billard
  - Propose a two-step Positive-Unlabeled Constraint Learning (PUCL) method to identify reliable infeasible data and then train a binary feasibility classifier as a constraint function
  - `Positive-Unlabeled Learning`

#### ICRL in Stochastic Environments

- [Maximum likelihood constraint inference from stochastic demonstrations](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9658862) [CCTA 2021]
  - David L. McPherson, Kaylene C. Stocking, S. Shankar Sastry
  - Generalize maximum entropy ICRL to stochastic environments by modeling the causal entropy
  - `Maximum Causal Entropy` `Discrete`

- [Maximum causal entropy inverse constrained reinforcement learning](https://arxiv.org/pdf/2305.02857) [Arxiv 2023]
  - Mattijs Baert, Pietro Mazzaglia, Sam Leroux, Pieter Simoens
  - Generalize maximum causal entropy ICRL to continuous environments by utilizing a feasibility neural network
  - `Maximum Causal Entropy` `Continuous`

- [Learning soft constraints from constrained expert demonstrations](https://arxiv.org/pdf/2206.01311) [ICLR 2023]
  - Ashish Gaurav, Kasra Rezaee, Guiliang Liu, Pascal Poupart
  - Employ the Deep Constraint Correction framework to learn soft constraints, which transforms a constrained problem into an unconstrained problem by introducing a non-differentiable ReLU term
  - `Soft Constraints` `Continuous`

#### ICRL from Limited Demonstrations

- [Bayesian methods for constraint inference in reinforcement learning](https://openreview.net/pdf?id=oRjk5V9eDp) [TMLR 2023]
  - Dimitris Papadimitriou, Usman Anwar, Daniel S. Brown
  - Apply the Maximum-A-Posteriori (MAP) approach to address the epistemic uncertainty during constraint inference
  - `Bayesian Posterior` `Uncertainty-aware`

- [Benchmarking constraint inference in inverse reinforcement learning](https://arxiv.org/pdf/2206.09670) [ICLR 2023]
  - Guiliang Liu, Yudong Luo, Ashish Gaurav, Kasra Rezaee, Pascal Poupart
  - Infer the approximated posterior distributions of constraints to capture uncertainty in the demonstration dataset through Dirichlet VAE
  - `Variational Inference` `Uncertainty-aware`

- [Confidence aware inverse constrained reinforcement learning](https://arxiv.org/pdf/2406.16782) [ICML 2024]
  - Sriram Ganapathi Subramanian, Guiliang Liu, Mohammed Elmahgiubi, Kasra Rezaee, Pascal Poupart
  - Ensure that only those constraints that meet a desired confidence threshold are utilized by incorporating a confidence level alongside a set of expert demonstrations
  -  `Confidence-aware`

- [Uncertainty-aware Constraint Inference in Inverse Constrained Reinforcement Learning](https://openreview.net/pdf?id=ILYjDvUM6U) [ICLR 2024]
  - Sheng Xu, Guiliang Liu
  - Propose expanding the training dataset by adding generated trajectories through flow-based trajectory generation based on GFlowNets
  -  `Data-augmented` `Uncertainty-aware`

- [Learning Constraints from Offline Demonstrations via Superior Distribution Correction Estimation](https://openreview.net/pdf?id=Ax90jQPbgF) [ICML 2024]
  - Guorui Quan, Guiliang Liu
  - Consider the offline setting where the agent has no access to the environment for interactions, which transfer the constraint inference problem to the problem of estimating the superior distributions set
  -  `Offline`

- [Bayesian Constraint Inference from User Demonstrations Based on Margin-Respecting Preference Models](https://arxiv.org/pdf/2403.02431) [ICRA 2024]
  - Dimitris Papadimitriou, Daniel S. Brown
  - Explore an alternative scenario in which preferences among demonstrations are available by extending the Bradley-Terry model to the context of constraint inference
  -  `Preference-based`

#### ICRL for Both Rewards and Constraints
- [Inferring task goals and constraints using bayesian nonparametric inverse reinforcement learning](http://proceedings.mlr.press/v100/park20a/park20a.pdf) [CoRL 2019]
  - Daehyung Park, Michael Noseworthy, Rohan Paul, Subhro Roy, Nicholas Roy
  - Propose a Constraint-based Bayesian Nonparametric IRL (CBN-IRL) algorithm that learns multiple local rewards/goals and local constraints from different expert trajectory segments
  - `Bayesian Posterior`

- [Distributed inverse constrained reinforcement learning for multi-agent systems](https://proceedings.neurips.cc/paper_files/paper/2022/file/d842425e4bf79ba039352da0f658a906-Paper-Conference.pdf) [NeurIPS 2022]
  - Shicheng Liu, Minghui Zhu
  - Formulate the problem as a distributed bi-level optimization problem and propose a novel bi-level algorithm to estimate reward functions and constraints
  - `Multi-agent` `Bi-level`

- [Learning multi-agent behaviors from distributed and streaming demonstrations](https://proceedings.neurips.cc/paper_files/paper/2023/file/a7affe50ab177b9a7f0a05f07a9ca205-Paper-Conference.pdf) [NeurIPS 2023]
  - Shicheng Liu, Minghui Zhu
  - Propose a novel “multi-agent behavior inference from distributed and streaming demonstrations" (MA-BIRDS) algorithm that allows the learners to solve the bi-level problem
  - `Multi-agent` `Bi-level`

- [Meta inverse constrained reinforcement learning: Convergence guarantee and generalization analysis](https://openreview.net/pdf?id=bJ3gFiwRgi) [ICLR 2024]
  - Shicheng Liu, Minghui Zhu
  - Formulate a bi-level optimization problem where the upper level aims to learn a meta-prior over reward functions and the lower level is to learn a meta-prior over constraints
  - `Meta-learning` `Bi-level`

- [Inverse Constraint Learning and Generalization by Transferable Reward Decomposition](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10319083) [RA-L 2024]
  - Jaehwi Jang, Minjae Song, Daehyung Park
  - Propose decomposing the reward function into task reward and the constraint-related residual reward, given the constrained demonstrations and the task reward space
  - `Reward Decomposition`

#### ICRL from Multiple Expert Agents
- [Learning safety constraints from demonstrations with unknown rewards](https://proceedings.mlr.press/v238/lindner24a/lindner24a.pdf) [AISTATS 2024]
  - David Lindner, Xin Chen, Sebastian Tschiatschek, Katja Hofmann, Andreas Krause
  - Study a setting where the expert agents optimize different rewards under a shared constraint, and define the safe set as the convex hull of the feature expectations of the expert demonstrations
  - `Shared Constraint`

- [Learning shared safety constraints from multi-task demonstrations](https://proceedings.neurips.cc/paper_files/paper/2023/file/124dde499d62b58e97e42a45b26d7369-Paper-Conference.pdf) [NeurIPS 2023]
  - Konwoo Kim, Gokul Swamy, Zuxin Liu, Ding Zhao, Sanjiban Choudhury, Zhiwei Steven Wu
  - Additionally leverage side information in the form of a reasonable set of constraints, enabling policy performance guarantees.
  - `Shared Constraint`

- [Multi-modal inverse constrained reinforcement learning from a mixture of demonstrations](https://proceedings.neurips.cc/paper_files/paper/2023/file/bdc48324d6158a7edef88d673855a3f4-Paper-Conference.pdf) [NeurIPS 2023]
  - Guanren Qiao, Guiliang Liu, Pascal Poupart, Zhiqiang Xu
  - Study expert data that record demonstrations from multiple experts who respect different kinds of constraints, and propose a Multi-Modal Inverse Constrained Reinforcement Learning (MM-ICRL) algorithm that performs unsupervised agent identification and multi-modal policy optimization to learn agent-specific constraints
  - `Multi-modal Constraint`