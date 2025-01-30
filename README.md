# Key Point Analysis in Greek: A New Dataset and Baselines
This repo contains the code implementations for developing baseline solutions for the [Key Point Analysis Shared Tasks's subtasks](https://github.com/IBM/KPA_2021_shared_task) (Key Point Matching-KPM and Key Point Generation-KPG) in Greek, a low-resource language. 
The project is submitted in partial fulfillment of the requirements for the [MSc in “Language Technology”](https://www.di.uoa.gr/en/studies/graduate/lg) in the [Department of Informatics and Telecommunications of the National and Kapodistrian University of Athens (NKUA)](https://www.di.uoa.gr/en).
Each folder contains code related to specific project stages. 

# 1. ArgKP-2021 Dataset Translation (EN-GR)
- Zero-shot translation of the arguments, key points, topics of the [ArgKP-2021](https://github.com/IBM/KPA_2021_shared_task/tree/main/kpm_data) train set with Google's [madlad400-3b-mt](https://huggingface.co/google/madlad400-3b-mt).
- Human translation of the arguments, key points, topics of the [ArgKP-2021](https://github.com/IBM/KPA_2021_shared_task/tree/main/kpm_data) validation ad test sets.
- args_kps_labels: contain the translated argument, key points and labels .csv files, as provided in the original ArgKP-2021 dataset.
- Pred_dev_test folder: contains the human translated dev and test sets including the undecided pairs (refer to ArgKP-2021 dataset creation), required for the KPM evaluation setting. (refer to [Shared task's overview paper](https://aclanthology.org/2021.argmining-1.16.pdf)
- hf_dataset: contains the code for generating the Greek, labelled train, validation and test set for the HugginFace dataset upload. Each file is sorted in ascending order, based on the value of the arg_id column.
- The dataset has been made availalble in HugginFace under the title : [ArgKP_2021_GR](https://huggingface.co/datasets/Kleo/ArgKP_2021_GR)
- Greek data EDA: contains minimal data analysis steps, concering dataset class imbalance, average token number in arguments and key points.

# 2. KPM 
**Experiments**
- SMatchToPR re-implementation [1] with BERT and GreekBERT, with original (EN) and translated (GR) data respectively.
- Enigma re-implementation [2] with BERT and GreekBERT, with original (EN) and translated (GR) data respectively.
- Classification finetuning experiments with [ilsp/Meltemi-7B-v1](https://huggingface.co/ilsp/Meltemi-7B-v1) with Quantization(4bit) QLoRa on the translated data (GR)

**Metrics**
- mAP(mean Average Precision): strict and relaxed. For details refer to my [MSc Thesis Text](https://pergamos.lib.uoa.gr/uoa/dl/object/3456844/file.pdf) or [IBM/KPA Shared Task repo](https://github.com/IBM/KPA_2021_shared_task)
# 3. KPG
Argument Clustering (BERTopic) and KPG with Representation tuning [3]

**Experiments**
- BERTopic hyperparameter tuning (for UMAP: n_nighbors, num_target_dimensions, for HDBSCAN: min_samples, cluster_selection_method) with [Optuna](https://optuna.org/) and [DBCV index](https://permetrics.readthedocs.io/en/latest/pages/clustering/DBCVI.html) as maximization metric
- Zero- and Few-shot Representation tuning experiments with LLMs [3]: [IMISLab/GreekWiki-umt5-base](https://huggingface.co/IMISLab/GreekWiki-umt5-base), [ilsp/Meltemi-7B-v1.5](https://huggingface.co/ilsp/Meltemi-7B-v1.5), [ilsp/Meltemi-7B-Instruct-v1.5](https://huggingface.co/ilsp/Meltemi-7B-Instruct-v1.5)
  
**Metrics**
- [ROUGE](https://huggingface.co/spaces/evaluate-metric/rouge) + Greek Stemmer [4]
- [BERTScore](https://huggingface.co/spaces/evaluate-metric/bertscore)
For implementation details refer to [Thesis' text](https://pergamos.lib.uoa.gr/uoa/dl/object/3456844/file.pdf)

# 4. Final Display
- Examples of generated key points and extraction of matching scores with the [developed Meltemi-7b-base Key Point Matcher model](https://huggingface.co/Kleo/meltemi_base_finetuning_kpm_kp_arg)
- Load with adapters: Kleo/meltemi_base_finetuning_kpm_kp_arg

  
# Hardware used 
- Number of nodes: 1
- Number of GPUs per node: 1
- GPU type: Tesla P100
- GPU memory: 16GB
# Development Environment and Libraries
The code has been run in Jupyter notebooks to be easily replicable. Google Colab and Kaggle were used for model finetuning and zero-/few-shot inference
- Python > 3.6
- PyTorch
- sentence-transformers


# Contributor Expectations/ Future Work
 **KPM**
1. More PEFT methods (p-tuning, prompt-tuning)
2. Classification as NLG task
   
  **KGP**
1. Improve Argument clustering methods: Iterative clustering (refer to Li et al. [5] and relevant repo:https://github.com/HaoBytes/KeyPoint-Analysis)
2. Improve embedding quality (with a Greek Sentence-transformer model, notyet available)
3. Meltemi-finetuning
4. Establish a more clear evaluation framework

# References
[1] M. Alshomary et al., *ArgMining 2021 Key Point Analysis Shared Task Code*. GitHub repository. [Online]. Available: https://github.com/webis-de/argmining-21-keypoint-analysis-sharedtask-code

[2] M. Kapadnis, S. Patnaik, S. Panigrahi, V. Madhavan, and A. Nandy, *Team Enigma at ArgMining-EMNLP 2021: Leveraging Pre-trained Language Models for Key Point Matching*, GitHub repository. [Online]. Available: https://github.com/manavkapadnis/Enigma_ArgMining

[3] M. Grootendorst, "LLM representation for BERTopic," *BERTopic Documentation*. [Online]. Available: https://maartengr.github.io/BERTopic/getting_started/representation/llm.html.

[4] “GreekStemmer.ipynb,” GitHuB Gist, Dec. 07, 2023. [Online]. Available: https://gist.github.com/Patelis-GM/e1f8cf553f27ff40ed49db8c310611b3

[5] H. Li, V. Schlegel, R. Batista-Navarro, and G. Nenadic, “Do You Hear The People Sing? Key Point Analysis via Iterative Clustering and Abstractive Summarisation,” vol. 1, p. 14064, 1408, [Online]. Available: https://aclanthology.org/2023.acl-long.786.pdf
