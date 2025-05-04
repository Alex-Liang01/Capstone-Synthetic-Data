# Capstone Project: Maintaining Data Governance through Synthetic Data

## Overview
Maintaining data governance is crucial in ensuring that sensitive data is handled responsibly when working in large cross-functional teams with varying levels of data access. This includes protection of personally identifiable information (PII), maintaining data quality, and ensuring compliance with privacy regulations.

The objective of this project is to investigate the feasibility of using synthetic data as a way to maintain data governance when working in these cross functional teams. Synthetic data is artifically generated datasets that are statistically similar to the real world datasets that it is trained on. Synthetic data has the potential to protect PII while enabling data-driven collaboration. 

To investigate the feasibility of synthetic data, data was simulated using Python with varying amounts of missing data, sample sizes, and association strengths to measure how different synthetic data synthesizers perform in different conditions. 

The synthesizers we used were from the Synthetic Data Vault Library where we used a statistical method Gaussian Copula (GC), and two neural network methods: Conditional Tabular GAN (CTGAN), Tabular Variational Autoencoder (TVAE). 

To measure the fidelity of the synthetic data compared to the simulated data they were trained on we investigated: marginal distributions, pairwise associations, and multivariate associations between the synthetic datasets compared to the simulated datasets. 

To measure the variance of the synthetic datasets trained with neural networks (CTGAN and TVAE), 100 synthetic datasets were generated from trained synthesizers across the different simulated datasets to measure if the fidelity of the synthetic data is consistent across different runs.

To measure the privacy protection of the synthetic datasets we applied several privacy protection metrics such as: Disclosure Protection (DP), Nearest Neighbor Distance Ratio (NNDR), Nearest Neighbor Adversarial Accuracy (NNAA) and Membership Inference Attack (MIA). 

This project aims to determine if synthetic data is a suitable alternative for real data that allows cross-functional teams to share real data insights without leaking PII.  

## Project Sections

- [Methodology](documents/Methodology.md)
- [Data Fidelity](documents/Data_Fidelity_Results.md)
- [Data Fidelity Variance (NN Methods)](documents/Data_Fidelity_Variance_NN_Methods.md)
- [Privacy Metric Results](documents/Privacy_Metrics_Results.md)

## Conclusion

### Data Fidelity
In terms of data fidelity of the synthetic data compared to the simulated datasets that they were trained on, GC performed the best at translating simple associations such as marginal distributions and correlations. However, TVAE and CTGAN performed much better in terms of more complex associations such as pariwise associations between categorical features with high cardinality as well as multivariate associations. CTGAN is heavily affected by sample size with it performing better at large sample sizes. 

### Data Fidelity Variance in Neural Network Methods
In terms of the variance of the synthetic datasets trained with neural netowrks (CTGAN and TVAE), it was found that CTGAN is less variable in terms of consistency with the boxplots of the tested metrics often being very small. This means that although the CTGAN fails to capture some of the relationships, it is consistent at not capturing the relatioship. In comparison, although TVAE was often closer to the simulated data's metrics, the boxplots of the tested metrics were much larger. This means that TVAE is unreliable in terms of consistency of synthesizing datasets with it performing very well on some instances while performing poorly in other iterations.

### Privacy of Synthetic Data
In terms of privacy of the synthetic data compared to the simulated datasets that they were trained on, GC performed the well with datasets synthesized using GC often having the best privacy across all metrics except for NNAA with small sample sizes meaning that adversaries can distinguish real data in the synthetic data. CTGAN performed by far the best with the privacy metrics tested; never leaking any privacy across any of the synthetic datasets. TVAE performed the worst with many of the synthetic datasets synthesized with the synthesizer having poor MIA results meaning that adversaries can determine that data points were a part of the training set used to create the synthetic data. 

### Overall 
There is a trade off between using different synthesizers. The simpler method tested of GC which uses Copulas performs better in terms of data fidelity of simple metrics such as marginal distributions but performs worst in more complex metrics such as pairwise associations between categorical features with large cardinalities. The CTGAN synthesizer performs best at transfering over complex relationships such as pairwise associations between cateogorical features with large cardinalities especially when the size of the simulated dataset increased.  The TVAE method performed the most similarly to the simulated data in terms of multivariate associations between variables. This leads the TVAE method to be the most similar to that of the simualated dataset leading to privacy issues in the synthetic dataset while GC and CTGAN perform much better in terms of privacy. Overall, if data similarity is the most important, TVAE performs the best while if a balance is needed CTGAN on average performs the best in terms of both privacy and data fidelity.


