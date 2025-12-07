# Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation

[![Paper Accepted](https://img.shields.io/badge/Journal-Medical%20Image%20Analysis-blue.svg?style=for-the-badge)](https://www.elsevier.com/locate/media)
[![GitHub Repository](https://img.shields.io/badge/GitHub-BoxMed--RL-green.svg?style=for-the-badge)](https://github.com/Peiyuan-Jing/BoxMed-RL/tree/main)

## Overview

This repository hosts the official code for **BoxMed-RL**, a novel two-phase framework for automated chest X-ray report generation that unifies structured reasoning and spatially verifiable reinforcement learning.

Current report generation models often lack the **structured reasoning** of a radiologist and struggle to **explicitly ground findings** in anatomical evidence, limiting clinical trust and explainability. BoxMed-RL addresses these critical challenges by approximating the cognitive workflow of radiologists.

The paper, "**Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation**," has been accepted for publication in *Medical Image Analysis*.

---

## Key Innovations (BoxMed-RL Framework)

The BoxMed-RL framework consists of two integrated phases to generate spatially verifiable and explainable reports:

1.  **Pretraining Phase:** Integrates two core modules:
    * **Medical Concept Learning (MCL):** Forces the model to internalize the diagnostic logic of radiologists through a hierarchical Chain-of-Thought (CoT) reasoning dataset. This bridges the gap between free-form generation and clinically structured workflows.
    * **Spatially Verifiable Reinforcement (SVR):** Explicitly aligns textual descriptions with anatomical regions using Intersection-over-Union (**IoU-based rewards**). This ensures that generated phrases correspond to pixel-level anatomical evidence, enforcing textual-visual alignment.
2.  **Downstream Adapter Phase:** A lightweight adapter is fine-tuned on raw reports while the pretrained weights are frozen. This step refines linguistic fluency and clinical phrasing, ensuring the final output is a fluent and coherent report while preserving the learned reasoning and alignment.



---

## Performance Highlights

BoxMed-RL demonstrates significant improvements over state-of-the-art methods on standard chest X-ray benchmarks.

* Achieves an average **7% improvement** in both **METEOR** and **ROUGE-L** natural language generation metrics.
* Shows an average **5% improvement** in large language model-based metrics, further underscoring its robustness in generating high-quality reports.
* Consistently outperforms state-of-the-art methods across language quality, clinical accuracy, and composite evaluation metrics.

---

## Citation
If you find this work useful for your research, please consider citing our paper:

```
@article{jing2025reason,
  title={Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation},
  author={Jing, Peiyuan and Lee, Kinhei and Zhang, Zhenxuan and Zhou, Huichi and Yuan, Zhengqing and Gao, Zhifan and Zhu, Lei and Papanastasiou, Giorgos and Fang, Yingying and Yang, Guang},
  journal={Medical Image Analysis},
  year={2025},
  publisher={Elsevier}
}
```
