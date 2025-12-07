Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation
Overview
This repository hosts the official code for BoxMed-RL, a novel two-phase framework for automated chest X-ray report generation that unifies structured reasoning and spatially verifiable reinforcement learning.

Current report generation models often lack the structured reasoning of a radiologist and struggle to explicitly ground findings in anatomical evidence, limiting clinical trust and explainability. BoxMed-RL addresses these critical challenges by approximating the cognitive workflow of radiologists.

The paper, "Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation," has been accepted for publication in Medical Image Analysis.

Key Innovations (BoxMed-RL Framework)
The BoxMed-RL framework consists of two integrated phases to generate spatially verifiable and explainable reports:

Pretraining Phase: Integrates two core modules:


Medical Concept Learning (MCL): Forces the model to internalize the diagnostic logic of radiologists through a hierarchical Chain-of-Thought (CoT) reasoning dataset. This bridges the gap between free-form generation and clinically structured workflows.


Spatially Verifiable Reinforcement (SVR): Explicitly aligns textual descriptions with anatomical regions using Intersection-over-Union (IoU-based rewards). This ensures that generated phrases correspond to pixel-level anatomical evidence, enforcing textual-visual alignment.


Downstream Adapter Phase: A lightweight adapter is fine-tuned on raw reports while the pretrained weights are frozen. This step refines linguistic fluency and clinical phrasing, ensuring the final output is a fluent and coherent report while preserving the learned reasoning and alignment.

Performance Highlights
BoxMed-RL demonstrates significant improvements over state-of-the-art methods on standard chest X-ray benchmarks.

Achieves an average 7% improvement in both METEOR and ROUGE-L natural language generation metrics.

Shows an average 5% improvement in large language model-based metrics, further underscoring its robustness in generating high-quality reports.

Consistently outperforms state-of-the-art methods across language quality, clinical accuracy, and composite evaluation metrics.

Installation
Prerequisites
Python 3.x

PyTorch (tested with a recent version, e.g., 2.x)

CUDA-compatible GPU (recommended for training)

Setup
Clone the repository:

Bash

git clone https://github.com/Peiyuan-Jing/BoxMed-RL.git
cd BoxMed-RL
Create a virtual environment (recommended):

Bash

python -m venv venv
source venv/bin/activate # On Windows use `venv\Scripts\activate`
Install dependencies:

Bash

pip install -r requirements.txt
Datasets
The model was extensively evaluated on two widely used public benchmarks:


MIMIC-CXR


IU X-Ray

Detailed instructions on dataset preprocessing and the construction of the structured Chain-of-Thought (CoT) reasoning dataset used for MCL can be found in the supplementary materials and documentation within the repository.

Usage (Training & Testing)
This section provides a high-level overview. Please refer to the documentation in the main branch for specific configuration and script details.

1. Pretraining (MCL & SVR)
The pretraining phase is critical for teaching the model the structured diagnostic logic and spatial grounding.

Bash

# Run the MCL and SVR sequential training phase
python run_pretrain.py --config config/pretrain_mimic.yaml
2. Downstream Adapter Fine-Tuning
Once the backbone is pretrained, the lightweight adapter is fine-tuned to ensure linguistic fluency.

Bash

# Run the downstream adapter training phase
python run_adapter_finetune.py --config config/adapter_finetune_mimic.yaml --pretrained_weights /path/to/pretrain_weights
3. Inference
To generate reports on a test set:

Bash

python run_inference.py --config config/inference_mimic.yaml --adapter_weights /path/to/adapter_weights
Citation
If you find this work useful for your research, please consider citing our paper:

Code snippet

@article{jing2025reason,
  title={Reason Like a Radiologist: Chain-of-Thought and Reinforcement Learning for Verifiable Report Generation},
  author={Jing, Peiyuan and Lee, Kinhei and Zhang, Zhenxuan and Zhou, Huichi and Yuan, Zhengqing and Gao, Zhifan and Zhu, Lei and Papanastasiou, Giorgos and Fang, Yingying and Yang, Guang},
  journal={Medical Image Analysis},
  year={2025},
  publisher={Elsevier}
}
