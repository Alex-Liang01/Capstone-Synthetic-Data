# Multiple Iterations of Synthetic Datasets 

The neural network methods CTGAN and TVAE have inherent randomness in them when sampling data from trained synthesizers. To investigate if these heavily affect the results of the synthetic datasets, 100 iterations of synthetic datasets were generated for each of the explored features of different sample sizes, association strength, and missing data.

## Pearson's Correlation Boxplots

Boxplots were done on the Pearson's Correlation between age and rating from each of the different datasets to see if the variance of CTGAN, and TVAE is too large to be used. The real correlation from the dataset the synthetic datasets were trained on are in Orange to compare the performance of the synthetic datasets to the real dataset. 

### Simulated Data from Marginal Distributions
<img width="704" alt="image" src="https://github.com/user-attachments/assets/6c7f8b82-c102-4326-b0fe-d51c69a4d895" />

Looking at the boxplot of the Pearson's Correlation between age and rating across 100 synthetic datasets trained on the simulated data that was created using provided marginal distributions, it is observed that the CTGAN method consistently performs poorly at small sample sizes with the whiskers of the boxplots never being near the simulated data's correlation. At sample sizes greater than 25,000 rows, it is observed that the CTGAN method performs much closer to that of the simulated dataset indicating that sample size is very important for CTGAN. Looking at the correlation of the TVAE methods, it is observed that generally it is much more inline with that of the simulated dataset except at 20% missing across all tested sample sizes where it performed quite poorly especially at 20% 25,000 rows.  

### High Association Data
<img width="712" alt="image" src="https://github.com/user-attachments/assets/e97b1649-c2e6-4c4f-91b8-d53d75418191" />

Looking at the boxplot of the Pearson's Correlation between age and rating across 100 synthetic datasets trained on the simulated data that was created with enforced high associations between variables, it is observed that both the CTGAN and TVAE method consistently performs poorly with the whiskers of the boxplots often being far from the simulated data's correlation. The only time the synthesizers performed well was TVAE at 10% missing 10,000 rows where it is observed that the boxplot of the TVAE method is in line with that of the simulated dataset.

### Moderate Association Data
<img width="709" alt="image" src="https://github.com/user-attachments/assets/f219c43a-0cc5-45ef-80a7-446226304d27" />

Looking at the boxplot of the Pearson's Correlation between age and rating across 100 synthetic datasets trained on the simulated data that was created with enforced moderate associations between variables, it is observed that the CTGAN method consistently performs poorly with the whiskers of the boxplots never being near the simulated data's correlation. Looking at the correlation of the TVAE methods, it is observed that it is much more inline with that of the simulated dataset at smaller sample sizes. At larger sample sizes the TVAE synthesized datasets' correlation deviates further away from that of the simulated dataset. 

### Low Association Data
<img width="716" alt="image" src="https://github.com/user-attachments/assets/a68f36ea-a49b-4393-8a59-94d8a98328ce" />

Looking at the boxplot of the Pearson's Correlation between age and rating across 100 synthetic datasets trained on the simulated data that was created with enforced low associations between variables, it is observed that the CTGAN method generally performs poorly with the whiskers of the boxplots only being near the simulated data's correlation at 0% missing 50,000 rows. Looking at the correlation of the TVAE methods, it is observed that like CTGAN method, it performs much worst than the other datasets with stronger association with it's boxplot's whiskers only being near the simulated dataset at 20% missing, 10,000 rows. Overall, it is observed that at low dependency between variables in the simulated dataset, the CTGAN and TVAE perform much worst with the whiskers of the boxplots becoming larger.

###  Pearson's Correlation Boxplots Overall
Overall, the CTGAN method perfomed quite poorly at transfering over the correlation between age and rating with the corelation in the synthetic datasets often being drastically different than that of the simulated dataset across different associations. TVAE often perfomed poorly as well with it only performing well at high dependencies and low sample sizes of 10,000 rows.


## Cramer's V Boxplots

### Simulated Data from Marginal Distributions
<img width="716" alt="image" src="https://github.com/user-attachments/assets/3829b5dc-5624-4744-ad79-ba24756570fe" />

Looking at the boxplot of Cramer's V between Country Code and Language across 100 synthetic datasets trained on the simulated data that was created using provided marginal distributions, it is observed that both methods generally fail to get Cramer's V similar to the simulated dataset. The CTGAN method is quite consistent with it's whiskers generally being very small but it still has a fair number of outliers. It is observed that CTGAN performs much better once the sample size increases from 10,000 rows to 25,000 rows. TVAE is quite inconsistent with the whiskers often being quite long.

### High Association Data
<img width="714" alt="image" src="https://github.com/user-attachments/assets/4c42cfd4-9cdb-462a-a9bb-63d6b70f363a" />

Looking at the boxplot of Cramer's V between Country Code and Language across 100 synthetic datasets trained on the simulated data that was created with enforced high associations between variables, it is observed that once again CTGAN is very dependent on sample size with it performing very similarly to that of the simulated dataset at high sample sizes. CTGAN's whiskers are very small but their are still outliers meaning that the sampled datasets are often very similar to each other in terms of Cramer's V. Looking at TVAE, it is observed that it's whiskers are much larger meaning that it is quite inconsistent when sampling synthesized datasets from a trained synthesizer. Overall, CTGAN performance is much more consistent with smaller whiskers and closer Cramer's V to the simulated dataset than TVAE.

### Moderate Association Data
<img width="718" alt="image" src="https://github.com/user-attachments/assets/862fed11-5a62-4e72-8997-93dce149ec4d" />

Looking at the boxplot of Cramer's V between Country Code and Language across 100 synthetic datasets trained on the simulated data that was created with enforced moderate associations between variables, it is observed that once again CTGAN is very dependent on sample size with it performing very similarly to that of the simulated dataset at high sample sizes. Looking at TVAE, it is observed that it's whiskers are much larger with it's whiskers being even larger than that of the high association simulated dataset meaning that TVAE is very inconsistent when working with datasets that have moderate associations between categorical features. Furthermore, it is observed that TVAE has a lot of outliers with some being very far away from the whiskers of their respective boxplot showing that TVAE is not reliable when synthesizing from a dataset that has moderate associations between variables.
### Low Association Data
<img width="719" alt="image" src="https://github.com/user-attachments/assets/f7279259-897b-4920-9c01-6661997e81e5" />
Looking at the boxplot of Cramer's V between Country Code and Language across 100 synthetic datasets trained on the simulated data that was created with enforced low associations between variables, it is observed that once again CTGAN is very dependent on sample size with it performing very similarly to that of the simulated dataset at high sample sizes. Looking at TVAE, it is observed that it's whiskers are much larger with it's whiskers being even larger than that of the high association simulated dataset meaning that TVAE is very inconsistent when working with datasets that have moderate associations between categorical features. Furthermore, it is observed that TVAE has a lot of outliers with some being very far away from the whiskers of their respective boxplot showing that TVAE is not reliable when synthesizing from a dataset that has low associations between variables.

###  Cramer's V Boxplots Overall

Overall, the CTGAN method needs a large sample size in order to accurately transfer over the association between categories with high cardinality with it performing quite poorly at smaller sample sizes of 10,000 rows. The TVAE method is quite inconsistent when sampling synthetic datasets from a trained synthesizer with the whisker's of it's boxplots often being very wide especially at low and moderate dependencies making it unreliable if the dataset that needs to be synthesized has columns with multiple high cardinality features with low or moderate association. 

## Machine Learning Fidelity Boxplots

### Simulated Data from Marginal Distributions
<img width="710" alt="image" src="https://github.com/user-attachments/assets/2e65213c-c625-4d7e-a4d6-c19f711b30d3" />

Looking at the boxplot of MAE from the prediction on ratings using Random Forest Regression across 100 synthetic datasets trained on the simulated data that was created from the provided marginal distributions, it is observed that CTGAN performs quite poorly but is very consistent with its whiskers being quite small. Looking at TVAE it is observed that it's MAE is often quite similar to that of the simulated data. Like with CTGAN, the boxplots of the TVAE synthetic datasets has quite small whiskers showing that they both are consistent in sampling synthetic datasets with consistent multivariate properties from a trained synthesizer. Overall the CTGAN method often fails to transfer over the multivariate properties of the simulated data over to the synthetic data while the TVAE method is better at transfering over the multivariate properties of the simulated data over to the synthetic data.

### High Association Data
<img width="713" alt="image" src="https://github.com/user-attachments/assets/436d4dbc-5cbe-4d3c-84f4-d15481313a31" />

Looking at the boxplot of MAE from the prediction on ratings using Random Forest Regression across 100 synthetic datasets trained on the simulated data that was created with enforced high associations between variables, it is observed that CTGAN performs quite poorly but is very consistent with its whiskers being quite small. Looking at TVAE it is observed that it's MAE is often quite similar to that of the simulated data. Like with CTGAN, the boxplots of the TVAE synthetic datasets has quite small whiskers showing that it is they both are consistent in sampling synthetic datasets with consistent multivariate properties from a trained synthesizer. Overall the CTGAN method often fails to transfer over the multivariate properties of the simulated data over to the synthetic data while the TVAE method is better at transfering over the multivariate properties of the simulated data over to the synthetic data.

### Moderate Association Data
<img width="712" alt="image" src="https://github.com/user-attachments/assets/f55436a6-b605-412f-8666-0053950133aa" />

Looking at the boxplot of MAE from the prediction on ratings using Random Forest Regression across 100 synthetic datasets trained on the simulated data that was created with enforced moderate associations between variables, it is observed that CTGAN performs quite poorly but is very consistent with its whiskers being quite small. Looking at TVAE it is observed that it's MAE is often quite similar to that of the simulated data. Like with CTGAN, the boxplots of the TVAE synthetic datasets has quite small whiskers showing that it is they both are consistent in sampling synthetic datasets with consistent multivariate properties from a trained synthesizer. Overall the CTGAN method often fails to transfer over the multivariate properties of the simulated data over to the synthetic data while the TVAE method is better at transfering over the multivariate properties of the simulated data over to the synthetic data. 

### Low Association Data
<img width="711" alt="image" src="https://github.com/user-attachments/assets/d665044a-5fd5-4e5e-90d1-b9eb9bf9be66" />

Looking at the boxplot of MAE from the prediction on ratings using Random Forest Regression across 100 synthetic datasets trained on the simulated data that was created with enforced moderate associations between variables, it is observed that CTGAN performs quite poorly but is very consistent with its whiskers being quite small. Looking at TVAE it is observed that it's MAE is often quite similar to that of the simulated data. Like with CTGAN, the boxplots of the TVAE synthetic datasets has quite small whiskers showing that it is they both are consistent in sampling synthetic datasets with consistent multivariate properties from a trained synthesizer. Looking at the difference when there is no missing data in the simulated dataset compared to when there is missing data in the simulated data, it is observed that TVAE performs worst when there is no missing data in the simulated dataset. Overall the CTGAN method often fails to transfer over the multivariate properties of the simulated data over to the synthetic data while the TVAE method is better at transfering over the multivariate properties of the simulated data over to the synthetic data.

###  Machine Learning Fidelity Boxplots Overall

Overall, it is observed that the CTGAN method is worst than the TVAE method when it comes to transfering over multivariate properties from the simulated dataset to the synthetic dataset with the CTGAN method performing worst across all association strengths. Looking at the whiskers of the boxplots, CTGAN and TVAE often have small whiskers meaning that they manage to transfer over the multivariate properies across different samples from a trained dataset consistently. 

## Overall Findings from Multiple Iterations of Synthetic Data

Overall, the CTGAN method performed quite poorly at transfering over the correlations between rating and age, as well as multivariate properties used to predict rating across all association levels, sample sizes and missing data percentages. It performed quite well at transfering over categorical relationships between features with high cardinality but only when it had a large sample size of at least 50,000 rows. The TVAE method performance is unreliable in transfering over categorical relationships between features with high cardinality as the boxplots of the method was quite large. However, there is a trade off with it performing very well in terms of transfering over multivariate properties from the simulated dataset over to the synthetic datasets. This shows that the TVAE method is decent in terms of data fidelity but leads into issues with the synthetic dataset being too similar to that of the simulated dataset leading to privacy issues.


