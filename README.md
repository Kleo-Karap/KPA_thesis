# Key Point Analysis in Greek: A New Dataset and Baselines
This repo contains the code implementations for developing baseline solutions for the [Key Point Analysis Shared Tasks's subtasks](https://github.com/IBM/KPA_2021_shared_task) (Key Point Matching-KPM and Key Point Generation-KPG) in Greek, a low-resource language. 
The project is submitted in partial fulfillment of the requirements for the [MSc in “Language Technology”](https://www.di.uoa.gr/en/studies/graduate/lg) in the [Department of Informatics and Telecommunications of the National and Kapodistrian University of Athens (NKUA)](https://www.di.uoa.gr/en).
Each folder contains code related to specific project stages. 

# 1. ArgKP-2021 Dataset Translation (EN-GR)
- Zero-shot translation of the arguments, key points, topics of the [ArgKP-2021](https://github.com/IBM/KPA_2021_shared_task/tree/main/kpm_data) train set with Google's [madlad400-3b-mt](https://huggingface.co/google/madlad400-3b-mt).
- 
The dataset has been made availalble in HugginFace: https://huggingface.co/datasets/Kleo/ArgKP_2021_GR

# 2. Experiments KPM 

# 3. Experiments KPG
# Hardware used 
- Number of nodes: 1
- Number of GPUs per node: 1
- GPU type: NVIDIA P100
- GPU memory: 16GB
# Development Environment and Libraries
The code has been run in Jupyter notebooks to be easily replicable.
Google Colab and Kaggle were used for model finetuning and zero-/few-shot inference
Python > 3.6
PyTorch
sentence-transformers

# Main Findings
![image](https://github.com/user-attachments/assets/325b792d-c712-4d85-80b0-82d752c51677)
![image](https://github.com/user-attachments/assets/eb7d4a0e-d966-4c90-bbd2-30dd702b4aca)

# Contributor Expectations/ Future Work

# References
[1] M. Kapadnis, S. Patnaik, S. Panigrahi, V. Madhavan, and A. Nandy, *Team Enigma at ArgMining-EMNLP 2021: Leveraging Pre-trained Language Models for Key Point Matching*, GitHub repository. [Online]. Available: https://github.com/manavkapadnis/Enigma_ArgMining

[2] M. Alshomary et al., *ArgMining 2021 Key Point Analysis Shared Task Code*. GitHub repository. [Online]. Available: https://github.com/webis-de/argmining-21-keypoint-analysis-sharedtask-code

[3] M. Grootendorst, "LLM representation for BERTopic," *BERTopic Documentation*. [Online]. Available: https://maartengr.github.io/BERTopic/getting_started/representation/llm.html.

- Code for Greek Stemming: https://gist.github.com/Patelis-GM/e1f8cf553f27ff40ed49db8c310611b3
