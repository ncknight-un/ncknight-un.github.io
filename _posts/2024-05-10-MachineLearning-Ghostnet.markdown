---
layout: post
title:  "GhostNet-CBAM: Enhancing Lightweight CNNs"
date:   2024-05-10 09:00:00 +0300
image: ghost_stats.jpeg
tags:   Attention_Mechanisms Machine_Learning Python Pytorch TensorFlow
---

This project explores the integration of the **Convolutional Block Attention Module (CBAM)** into the **GhostNet** architecture to enhance feature representation while preserving computational efficiency.

GhostNet is a lightweight convolutional neural network designed to generate rich feature maps using inexpensive operations. In this work, I extend GhostNet by introducing both **channel and spatial attention** through CBAM, enabling the model to selectively emphasize informative regions of feature maps during inference. The standard GhostNet architecture employs Squeeze-and-Excitation (SE) modules, which apply channel attention only. This project therefore investigates the effect of introducing spatial attention into the GhostNet architecture.

The primary goal of this work was to evaluate whether spatial attention mechanisms could improve **inferential quality** without significantly compromising GhostNet’s efficiency, particularly in resource-constrained settings. Experimental results showed that incorporating CBAM into GhostNet resulted in reduced accuracy while increasing model complexity, suggesting that spatial attention did not provide a net benefit in this context.

As a secondary study, I investigated the trade-off between the linear transformation ratio used in GhostNet and its impact on model accuracy and FLOPs. The results indicate the existence of an optimization point where sufficient accuracy can be maintained while substantially reducing computational cost.

---

## Motivation

Lightweight CNN architectures often trade representational power for speed and efficiency. While GhostNet reduces redundancy in feature generation, it does not explicitly model attention.

By integrating CBAM, this project investigates:

- Whether the addition of spatial attention improves feature discrimination  
- The performance–efficiency trade-offs introduced by spatial attention
- The impact of spatial attention on inference performance across datasets  

---

## Approach

- Extended the original GhostNet architecture with **CBAM attention modules**
- Implemented all models using **PyTorch**
- Trained and evaluated models on:
  - **CIFAR-10**
  - A subset of **ImageNet**
- Conducted **accuracy vs. efficiency trade-off analysis**

Both the baseline GhostNet and the proposed **GhostNet-CBAM** models were trained and evaluated under consistent conditions to ensure fair comparison.

---

## Results & Analysis

- Observed that the addittion of spatial attention to GhostNet through CBAM reduced inferential accuracy
- Analyzed trade-offs between accuracy, inference cost, and model complexity  

---

## Implementation Details

- **Framework:** PyTorch  
- **Python Version:** 3.11.12  
- **PyTorch Version:** 2.6.0 + CUDA 12.4  

### Repository Structure

The GitHub repository includes the following directories:

- `ProjectCode` — Training and testing notebooks (Colab-compatible)
- `Models` — Model definitions and variants
- `StateDirectory` — Training state and checkpoint paths for pretrained models
- `Video` — Project explanation and results overview

Pretrained models for both **GhostNet** and **GhostNet-CBAM** are included in StateDirectory.

---

## References

- **GhostNet**  
  *GhostNet: More Features from Cheap Operations*  
  Kai Han, Yunhe Wang, Qi Tian, Jianyuan Guo, Chunjing Xu, Chang Xu  
  CVPR 2020  

- **CBAM**  
  *Convolutional Block Attention Module*  
  Jonghyun Woo, Donghyun Lee, Choonsik Park, Joon-Young Lee, In So Kweon  
  ECCV 2018  

---

**School:** Purdue University - Main Campus  
**Location:** - West Laffayete, IN  
**Duration:** March 2024 - May 2025  
 
---

## Project Gallery


**Github Link:** <a href="https://github.com/ncknight-un/GhostNet-Extended-CBAM" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/GhostNet-Extended-CBAM
</a>

### Enclosure & CAD Designs:

<div class="project-gallery">
  <div class="gallery-item">
    <h4 style="margin-bottom: -2.5em;">Results</h4>
    <img src="/images/ghost_stats.jpeg" alt="Stats">
  </div>

  <div class="gallery-item">
    <h4 style="margin-bottom: -2.5em;">CBAM Method</h4>
    <img src="/images/CBAM.jpeg" alt="CBAM">
  </div>

  <div class="gallery-item">
    <h4>Transform Ratio vs Accuracy</h4>
    <img src="/images/transform_ratio.jpeg" alt="Accuracy">
  </div>

  <div class="gallery-item">
    <h4>Transform Ratio vs Flops</h4>
    <img src="/images/flops.jpeg" alt="Flops">
  </div>
</div>

---


## Skills Gained:  

- Implemented and modified lightweight CNN architectures using PyTorch
- Integrated attention mechanisms (CBAM, Squeeze-and-Excitation) into existing models
- Analyzed channel vs. spatial attention effects on feature representation
- Evaluated performance across CIFAR-10 and ImageNet datasets
- Performed accuracy vs. computational cost (FLOPs) trade-off analysis
- Designed reproducible experiments using Jupyter/Colab notebooks
- Interpreted negative results and translated them into actionable insights

---


## Key Takeaway:  

This project highlights that architectural improvements do not always translate into performance gains, particularly in efficiency-focused models. While spatial attention via CBAM increased model complexity and additional attention mechanisms, it did not improve accuracy within the constraints of GhostNet’s design. Furthermore, my findings emphasized that careful trade-off analysis can uncover optimization points that balance accuracy and computational efficiency more effectively than adding complexity alone.