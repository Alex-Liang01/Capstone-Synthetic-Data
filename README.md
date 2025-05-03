# Capstone Project: Maintaining Data Governance through Synthetic Data

## Overview
Maintaining data governance is crucial in ensuring that sensitive data is handled responsibly when working in large cross-functional teams with varying levels of data access. This includes protection of personally identifiable information (PII), maintaining data quality, and ensuring compliance with privacy regulations.

The objective of this project is to investigate the feasibility of using synthetic data as a way to maintain data governance when working in these cross functional teams. Synthetic data is artifically generated datasets that are statistically similar to the real world datasets that it is trained on. Synthetic data has the potential to protect PII while enabling data-driven collaboration. 

To investigate the feasibility of synthetic data, data was simulated using Python with varying amounts of missing data, sample sizes, and association strengths to measure how different synthetic data synthesizers perform in different conditions. The synthesizers we used were from the Synthetic Data Vault Library where we used a statistical method Gaussian Copula (GC), and two neural network methods: Conditional Tabular GAN (CTGAN), Tabular Variational Autoencoder (TVAE). We used LightGBM classifiers as well as pairwise correlation and Cramer's V tests to measure the fidelity of the synthetic data compared to the simulated data they were trained on. To measure the privacy protection of the synthetic datasets we applied several privacy protection metrics such as: Disclosure Protection (DP), Nearest Neighbor Distance Ratio (NNDR), Nearest Neighbor Adversarial Accuracy (NNAA) and Membership Inference Attack (MIA). 

This project aims to determine if synthetic data is a suitable alternative for real data that allows cross-functional teams to share real data insights without leaking PII.     

