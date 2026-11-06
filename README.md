# Integrating Explainable AI for Energy-Efficient Open Radio Access Networks

## 📌 Overview

Energy consumption is one of the major challenges in 5G and Beyond 5G (B5G) networks. With increasing network traffic and connected devices, understanding how different Radio Access Network (RAN) parameters affect power consumption is important for building energy-efficient networks.

In this work, we explored the use of Explainable Artificial Intelligence (XAI) to understand the factors influencing energy consumption in Open Radio Access Networks (O-RAN).

Machine Learning models can predict power consumption, but understanding why a model makes a particular prediction is often difficult. To address this, we investigated two explainability techniques, SHAP and LIME, to identify the RAN parameters that contribute to power consumption.

The study uses real-time RAN datasets to evaluate different ML models and understand the relationship between network performance parameters and energy consumption.

## 🎯 Research Objectives

- Study the relationship between RAN performance parameters and energy consumption.
- Evaluate ML models for predicting RAN power consumption.
- Apply SHAP and LIME to interpret ML predictions.
- Identify the network parameters that have the greatest influence on energy consumption.
- Explore how XAI insights can support energy-aware resource management in O-RAN.

## 🏗️ System Architecture

The proposed architecture considers the O-RAN framework with two intelligent controllers:

**1. Non-Real-Time RIC (Non-RT RIC)**

- Handles AI/ML model training and management.
- Stores collected network data.
- Supports policy generation and energy-efficiency strategies.
- Hosts the XAI framework to interpret model predictions.

**2. Near-Real-Time RIC (Near-RT RIC)**

- Supports time-sensitive network operations.
- Hosts AI/ML inference applications.
- Uses network information and control mechanisms to support RAN optimization.

**O-RAN Interfaces:**

- **O1:** Management and orchestration of RAN components.
- **A1:** Policy-driven guidance and AI/ML feedback between RIC components.
- **E2:** Communication and control between the Near-RT RIC and RAN components.

The architecture explores how explainability insights can help network operators understand AI/ML predictions and make informed energy-management decisions.

## 📊 Dataset Description

The evaluation uses real-time RAN energy measurement datasets collected from an O-RAN testbed.

Two datasets were considered:

| Dataset | Description |
|---|---|
| `dataset_ul` | Uplink-only performance and power consumption measurements. |
| `dataset_dlul` | Combined downlink and uplink performance and power consumption measurements. |

The datasets contain several network-related parameters, including:

- Airtime and selected airtime
- Throughput and Goodput
- Buffer Status Report (BSR)
- Number of Resource Blocks (nRBs)
- Modulation and Coding Scheme (MCS)
- Block Error Rate (BLER)
- Signal-to-Noise Ratio (SNR)
- Decoding time and clock speed
- Power consumption

Dataset source: [O-RAN Experimental Evaluation Datasets](https://dx.doi.org/10.21227/64s5-q431).

## 🤖 Machine Learning Models

Three ensemble-based ML models were evaluated for power consumption prediction.

**1. Gradient Boosting**

Builds predictive models sequentially, with each new model attempting to reduce the errors made by previous models.

**2. Random Forest**

Uses multiple decision trees trained on different samples of the dataset and combines their predictions to improve generalization.

**3. XGBoost**

An optimized gradient boosting algorithm that uses regularization and efficient optimization techniques to improve prediction performance.

### Model Evaluation

The datasets were divided into 80% training and 20% testing data. Mean Squared Error (MSE) was used to evaluate prediction performance.

**Downlink/Uplink dataset**

| Model | Train MSE | Test MSE |
|---|---:|---:|
| Gradient Boosting | 0.05733 | 0.06710 |
| Random Forest | 0.00897 | 0.06806 |
| XGBoost | 0.01672 | 0.07021 |

**Uplink-only dataset**

| Model | Train MSE | Test MSE |
|---|---:|---:|
| Gradient Boosting | 0.0290 | 0.0307 |
| Random Forest | 0.0020 | 0.0143 |
| XGBoost | 0.0085 | 0.0191 |

## 🔍 Explainable AI Techniques

To understand the factors influencing the ML predictions, two model-agnostic XAI techniques were investigated.

### 1. SHAP (SHapley Additive exPlanations)

SHAP uses Shapley values from game theory to estimate the contribution of individual features to a model prediction.

In this work, SHAP was used to:
- Understand global feature importance.
- Analyze how individual RAN parameters influence power predictions.
- Identify positive and negative feature contributions.
- Compare feature importance across different ML models.

### 2. LIME (Local Interpretable Model-agnostic Explanations)

LIME explains individual predictions by generating perturbed samples around a particular input and observing changes in model predictions.

In this work, LIME was used to:
- Understand individual power consumption predictions.
- Identify the parameters influencing specific predictions.
- Analyze how changes in network parameters affect model outputs.

Both techniques were evaluated across Gradient Boosting, Random Forest, and XGBoost models.

## 📈 Key Findings

The explainability analysis identified several important RAN parameters influencing power consumption.

**Important parameters identified:**

| Parameter | Significance |
|---|---|
| Airtime | Higher airtime indicates increased radio activity and can contribute to higher energy consumption. |
| Buffer Status Report (BSR) | Indicates the amount of data waiting for transmission and can reflect network traffic demand. |
| Goodput | Represents successfully delivered useful data; efficient data transfer can reduce energy consumption per unit of data. |
| Selected Airtime | Represents the allocated channel transmission time and influences energy consumption. |
| Number of Resource Blocks (nRBs) | Indicates allocated radio resources and affects network utilization. |
| Throughput | Represents the rate of successful data transmission and influences energy consumption. |

**Key observations:**

- For the DL/UL dataset, airtime, average BSR, average uplink Goodput, and selected airtime were identified as the top four influential parameters across the evaluated models and XAI techniques.
- Longer airtime generally indicates increased network activity, which can lead to higher energy consumption.
- Higher BSR values indicate more data waiting for transmission.
- Goodput and throughput provide insights into data transfer efficiency and their relationship with energy consumption.
- For the UL-only dataset, airtime, selected airtime, and nRBs were among the important influencing parameters. Their relative importance varied across models and explanation techniques.

The analysis demonstrates how XAI can provide meaningful insights into the relationship between network activity and RAN power consumption.

## 💡 Research Significance

This work demonstrates how explainability can make ML-based power consumption predictions more understandable to network operators.

By identifying the RAN parameters influencing energy consumption, the study provides useful insights for:

- Designing energy-aware RAN resource allocation strategies.
- Understanding the impact of network traffic on power consumption.
- Developing intelligent energy-management policies.
- Supporting future AI-driven optimization in O-RAN.

## 🛠️ Technologies and Techniques

- **Architecture:** 5G, O-RAN, Non-RT RIC, Near-RT RIC
- **Machine Learning:** Gradient Boosting, Random Forest, XGBoost
- **Explainable AI:** SHAP, LIME
- **Evaluation:** Mean Squared Error (MSE)
- **Data:** Real-time O-RAN energy measurement datasets

## 💻 Code Availability

The complete source code and experimental implementation are currently private due to academic publication restrictions.

This repository provides an overview of the research, including the O-RAN system architecture, dataset description, ML models, XAI methodology, experimental evaluation, and key findings.

The implementation and experimental scripts are maintained separately.

## 📄 Publication

**Integrating Explainable AI for Energy Efficient Open Radio Access Networks**

Published in: 2024 IEEE Future Networks World Forum (FNWF).

Authors: Lavanya Malakalapalli, V. Gudepu, B. Chirumamilla, S. J. Yadhunandan, and Koteswararao Kondepu.

DOI: [10.1109/FNWF63303.2024.11028856](https://doi.org/10.1109/FNWF63303.2024.11028856)

