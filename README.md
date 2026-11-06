# O-RAN Energy Consumption Modeling and Explainability using XAI

## 📌 Overview

Energy efficiency is an important challenge in 5G Open Radio Access Networks (O-RAN). Understanding which network parameters contribute most to power consumption can help build more efficient and sustainable RAN architectures.

As part of my Master's research, I explored how Machine Learning (ML) and Explainable AI (XAI) can be used to model and understand energy consumption in virtualized 5G base stations (gNBs).

The project focuses on predicting power consumption using ML models and explaining their predictions using XAI techniques. Rather than treating ML models as black boxes, the goal was to understand which network parameters have the greatest influence on energy usage.

## 🏗️ System Architecture and Experimental Setup

The experiments were conducted using a 5G O-RAN testbed designed around standard O-RAN interfaces.

The architecture includes:

- **O-RAN Interfaces:** O1, A1, and E2 interfaces for monitoring, data collection, and policy-driven control.
- **RIC Components:** Non-RT RIC and Near-RT RIC for AI/ML model management and intelligent network control.
- **Data Collection:** Real-time network performance and power consumption measurements collected from the testbed.
- **Communication:** ZeroMQ sockets used for data exchange between system components.

Two datasets were considered:
- `dataset_ul` – Uplink measurements.
- `dataset_dlul` – Downlink and uplink measurements.

## 📊 Machine Learning and Explainable AI

Three ML models were explored to predict power consumption:

- Gradient Boosting
- Random Forest
- XGBoost

To understand how these models make predictions, I integrated two model-agnostic explainability techniques:

**1. SHAP (SHapley Additive exPlanations)**

SHAP helps identify how individual network parameters contribute to model predictions. It provides both global feature importance and explanations for individual predictions.

**2. LIME (Local Interpretable Model-agnostic Explanations)**

LIME explains individual predictions by slightly changing the input features and observing how the model output changes. This helps understand the local behaviour of otherwise complex ML models.

## 🔍 Key Findings

The explainability analysis helped identify the network parameters that have the strongest influence on power consumption.

**Most influential parameters:**
- Airtime
- Average Buffer Status Report (BSR)
- Average Goodput (GPUT)
- Selected Airtime

Some important observations from the experiments:

- **Airtime:** Higher airtime generally indicates increased radio resource usage and network activity, which can contribute to higher energy consumption.
- **Buffer Status Report (BSR):** Higher BSR values indicate more data waiting for transmission, often reflecting increased traffic demand.
- **Goodput:** Goodput represents the successfully delivered data rate. More efficient data transfer can improve energy efficiency per unit of data.
- **Selected Airtime:** The amount of airtime allocated for transmission also plays an important role in determining power consumption.

These findings demonstrate how XAI can help move beyond power consumption prediction and provide meaningful insights into the factors influencing energy usage in 5G O-RAN systems.

## 🛠️ Technologies and Tools

- **RAN:** 5G OpenAirInterface (OAI), O-RAN
- **Architecture:** Non-RT RIC, Near-RT RIC
- **Machine Learning:** Python, Scikit-learn, XGBoost
- **Explainable AI:** SHAP, LIME
- **Communication:** ZeroMQ
- **Environment:** Linux, Docker

## 📁 Repository Status

The complete source code and experimental setup are currently private due to academic publication restrictions.
This repository provides an overview of the research, system architecture, methodology, and key experimental findings from my Master's thesis.

