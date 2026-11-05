# Gossip Learning for Distributed Training of Performance Models in Edge FaaS Systems

Master’s thesis in **Data Science** at the **University of Milano-Bicocca**, academic year **2025–2026**.

**Author:** Adonis Kingsley Granita  
**Supervisor:** Prof. Michele Ciavotta  
**Co-supervisor:** Dr.ssa Federica Filippini

📄 **[Read the full thesis (PDF)](./Gossip_learning_for_edge_faas.pdf)**

## Overview

How can heterogeneous edge nodes learn to predict resource usage and overload without collecting their training data in a central location?

This thesis investigates **Gossip Learning** for training performance models in **decentralized Function-as-a-Service (DFaaS)** systems. Nodes train on local observations and exchange model parameters with peers, without a central training coordinator.

The goal is to improve predictions beyond each node’s local data distribution, providing a predictive component that could support future workload-offloading decisions.

## Methodology

- Adopt a **permutation-invariant, multi-task model** that jointly predicts node-level resource usage and overload status.
- Evaluate **four existing model-merging strategies**.
- Introduce a **node-type-aware approach** that uses received models to generate synthetic targets for local workloads represented on remote node types.
- Compare parameter-update rules and synthetic-data management configurations.
- Run simulations with **9 and 18 nodes** in fully connected networks.
- Compare decentralized learning with **local-only** and **centralized** training.

## Key Results

In the 18-node experiments, parameter interpolation combining **70% of local parameters and 30% of received parameters** before each training update delivered the best overall results among the evaluated configurations.

The following results compare a selected Gossip Learning configuration with the reference training settings:

| Training setting | Accuracy ↑ | MSE on scaled targets ↓ |
|---|---:|---:|
| Local-only | 0.5553 | 0.20081 |
| Selected Gossip Learning configuration | 0.8950 | 0.02346 |
| Centralized | 0.9666 | 0.00693 |

The selected Gossip Learning configuration also achieved an **overloaded-class F1-score of 0.6147**. Decentralized results are averaged across the 18 nodes and evaluated on a common test set.

These findings show a substantial improvement over local-only training in the evaluated setting, while training records remain on their originating nodes. Centralized training retains the strongest predictive performance.


