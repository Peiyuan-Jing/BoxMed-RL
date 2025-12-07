# BoxMed-RL

**Official repository for:**

**_“Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation”_**  
_Medical Image Analysis, 2025_

BoxMed-RL is a unified training framework designed to make vision–language models generate radiology reports that are both **clinically coherent** and **spatially verifiable**. The system couples medical chain-of-thought reasoning with reinforcement learning driven by bounding-box rewards, enabling the model to reason explicitly and justify findings in a manner closer to radiologist behavior.

This repository will host the **full implementation** of the BoxMed-RL pipeline, including:

- Medical Concept Learning (MCL)  
- Spatially Verifiable Reinforcement (SVR)  
- LoRA-based downstream report-generation adapters  
- Evaluation scripts for localization, CheXbert, GEMA/GreenScore, and NLG metrics  

Code release is ongoing. Dataset documentation for the included materials is already available inside each folder.

---

## 🚩 Repository Status

| Component | Status |
|----------|---------|
| Dataset documentation (CheXpert Plus, filtered subsets) | ✅ Included |
| Core training code (MCL, SVR) | 🔧 In progress |
| LoRA adapter training | 🔧 In progress |
| Evaluation suite | 🔧 In progress |
| Full release w/ instructions | 📅 Planned |

The current repository primarily provides dataset splits and metadata referenced in the paper, with training code to follow.


---

## 🧠 Method Overview (High-Level)

BoxMed-RL trains a radiology-capable VLM through three coordinated stages.  
All details below are based on the official publication.

---

### **1️⃣ Medical Concept Learning (MCL)**

MCL teaches the model to reason explicitly by generating a structured chain-of-thought:

