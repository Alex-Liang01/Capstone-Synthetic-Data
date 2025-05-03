# Data Fidelity Results
To compare the similarity of the properties of the synthetic dataset compared to the simulated datasets that they were trained on, marginal distributions, pairwise associations, and multivariate associations were used to compare the performance of the synthesizers.

## Marginal Distributions Comparison

To compare the marginal distributions of the synthetic datasets to the training set, we used KSComplement and TVComplement to look at each of the variables individually. In KSComplement and TVComplement, higher values closer to 1 indicate that the marginal distribution of the simulated dataset is transfered over well to the synthetic dataset.

### Simulated Data from Marginal Distributions

![image](https://github.com/user-attachments/assets/2f7005ea-a7eb-4d99-b83e-f237da02d16b)
Looking at the results of the KSComplements and TVComplements for the synthetic dataset that was created using simulated data with provided marginal distributions, it is observed that GC does pretty well across the board at all sample sizes and all percent missings. Looking at CTGAN, it is observed that Language and Country Code perform worst with values around 0.70 across the board. These two features Lanaguage and Country Code are categorical features with high cardinality which shows that CTGAN performs poorly at transfering over marginal distributions when there is high cardinality in categorical features. Looking at TVAE, it is observed that Language is now more inline with the other features with smaller cardinality but Country Code still struggled meaning that TVAE is better at transfering marginal distributions of categorical featuures with large cardinality but struggles with extremly large cardinalities as in the training dataset, the languange had a smaller cardinality than that of the Country Code. Overall, GC performed the best at transfering over marginal distributions when the training data was a simulated data with varying amount of association between variables. 

### High Association Data

![image](https://github.com/user-attachments/assets/c83dcf29-bde3-47a6-94d0-7d6ae6c38bd2)
Looking at the results of the KSComplements and TVComplements for the synthetic dataset that was created using simulated data with artifically enforced high association between variables, it is observed that GC does pretty well across the board at all sample sizes and all percent missings with rating performing the worst. Looking at CTGAN, it is observed that Language and Country Code once again performed the worst. Looking at TVAE, it is observed that it performs better than that of CTGAN with Country Code still performing the worst. Overall, GC and TVAE performed pretty similarly at transfering over marginal distributions when the training data was a simulated data with enforced high dependencies between variables. 

### Moderate Association Data
![image](https://github.com/user-attachments/assets/927d2219-4e2d-4f9f-a2a3-f2f392c337f1)

Looking at the results of the KSComplements and TVComplements for the synthetic dataset that was created using simulated data with artifically enforced moderate association between variables, it is observed that GC does pretty well again with rating performing the worst. Looking at CTGAN, it is observed that the results are quite consistent with Language and Country Code once again performing worst than those features with smaller cardinality. Looking at TVAE, it is observed that it performs quite poorly when the dataset gets larger with more missing values with langugage and country code performing very poorly at 50000 rows and 20% missing data. Overall, GC performed the best at transfering over marginal distributions when the training data was a simulated data with enforced moderate dependencies between variables. 

### Low Association Data

![image](https://github.com/user-attachments/assets/471666d7-746b-40f2-97ac-0cc3b6d57359)

Looking at the results of the KSComplements and TVComplements for the synthetic dataset that was created using simulated data with artifically enforced low association between variables, it is observed that GC does pretty well. Looking at CTGAN, it is observed that the results are quite consistent with Language and Country Code once again performing worst than those features with smaller cardinality. Looking at TVAE, it is observed that it performs quite poorly when the dataset gets larger with more missing values with langugage and country code performing very poorly at 50000 rows and 20% missing data. Overall, GC performed the best at transfering over marginal distributions when the training data was a simulated data with enforced low dependencies between variables. 

### Overall
Overall, when looking at the marginal distributions of the synthetic datasets, GC performed the best across all features at all levels of samples sizes, missing data, and association strengths. The other two synthesizers performed quite poorly when handling categorical features with high cardinality.

## Pairwise Association Tests
To compare the pairwise associations of the synthetic datasets to the simulated dataset, we used Pearson's correlation for numeric features and Cramer's V for categorical features.

### Pearson's Correlation

For the Pearson's Correlation tests between the synthetic dataset and simulated datasets, we compared the age and rating of the datasets. The importance here is the correlation of the synthetic datasets relative to that of the simulated dataset.

#### Simulated Data from Marginal Distributions
![image](https://github.com/user-attachments/assets/1253e3af-2b4d-4ec9-ab60-292bb8c978db)

Looking at the results of the correlation between age and rating for the synthetic dataset that was created using simulated data with provided marginal distributions, it is observed that the GC method performs quite well across the board with it most consistently being close to that of the correlation for the simulated dataset. Looking at CTGAN, it is observed that it requires a larger sample size to perform well with it performing quite poorly at 10,000 rows. Looking at TVAE, it is observed that it's results are quite inconsistent with it performing really well at 10,000 row and 50,000 rows but performing quite poorly at 25,000 rows. Overall, in the synthetic dataset that was trained using simulated data with provided marginal distributions, GC performed the most consistently.

#### High Association Data

![image](https://github.com/user-attachments/assets/2464c60f-cec8-4ed1-b26f-44b570a3596b)

Looking at the results of the correlation between age and rating for the synthetic dataset that was created using simulated data with enforced high associations between variables, it is observed that the GC method once again performs quite well across the board. Looking at CTGAN, it is observed that it performed the worst out of the three methods with it's correlation being very different from that of the simulated data across the board. Looking at TVAE, it is observed that it performs worst when there are more rows in the training set. Overall, in the synthetic dataset that was trained using simulated data with enforced high associations between variables, GC performed the most consistently.

#### Moderate Association Data
![image](https://github.com/user-attachments/assets/e9dfb565-0175-4bc0-9af7-9dc19087c11c)

Looking at the results of the correlation between age and rating for the synthetic dataset that was created using simulated data with enforced moderate associations between variables, it is observed that the GC method once again performs quite well across the board. Looking at CTGAN and TVAE, it is observed that they both performed very poorly with CTGAN's performance being consistently bad while TVAE sometimes performed more similarly to the simulated dataset when the training set had 10% missing data in the rows. Overall, in the synthetic dataset that was trained using simulated data with enforced moderate associations between variables, GC performed the most consistently while TVAE and CTGAN performed quite poorly.

#### Low Association Data
![image](https://github.com/user-attachments/assets/80bee48b-fc32-408b-afb5-b6fb41b612a5)

Looking at the results of the correlation between age and rating for the synthetic dataset that was created using simulated data with enforced low associations between variables, it is observed that the GC method once again performs quite well across the board. Looking at CTGAN and TVAE, it is observed that they both performed very poorly with both of their results being inconsistent across varying amounts of missing data and sample sizes. Overall, in the synthetic dataset that was trained using simulated data with enforced low associations between variables, GC performed the most consistently while TVAE and CTGAN performed quite poorly.

#### Overall

Overall, across all dataset sizes, missing percentages, and strength associations, GC performed by far the best with it's correlation being very consistent with that of the simulated dataset that it was trained on. The other two methods, consistently performed very poorly except for CTGAN on the training dataset that was simulated from marginal distributions. 

### Cramer's V

For the Cramer's V tests between the synthetic dataset and simulated datasets, we compared the Country Code and Language of the datasets. Both of these features have high cardinality. The importance here is the Cramer's V of the synthetic datasets relative to that of the simulated dataset.

#### Simulated Data from Marginal Distributions
![image](https://github.com/user-attachments/assets/19a1b87c-2238-4043-b2ca-391a4817210e)

Looking at the results of Cramer's V between Country Code and Language for the synthetic dataset that was created using simulated data with provided marginal distributions, it is observed that the GC performed very poorly with it's Cramer's V being very far from that of the simulated dataset. Looking at CTGAN, it too performed quite poorly, especially when the sample size was smaller at 10,000 rows. Looking at TVAE, it performed the best with it's Cramer's V being fairly similar to the simulated dataset across all missing percentagers and sample sizes except at 50,000 rows where the CTGAN method performed better than it. Overall, in the synthetic dataset that was trained using simulated data with provided marginal distributions, TVAE performed the most consistently.

#### High Association Data
![image](https://github.com/user-attachments/assets/b8f4ae8d-f266-4b21-ae01-157e27ccff8f)

Looking at the results of Cramer's V between Country Code and Language for the synthetic dataset that was created using simulated data with enforced high associations between variables, it is observed that GC once again performed very poorly with it's Cramer's V being very far from that of the simulated dataset. Looking at CTGAN, it performed quite well but only at higher sample sizes of greater than 25,000 rows. Looking at TVAE, it performed quite consistently across the board with it's Cramer's V performing moderately close to that of the simulated dataset at all amounts of missing data and sample sizes. Overall, in the synthetic dataset that was trained using simulated data  with enforced high associations between variables, TVAE performed the most consistently but was surpassed by CTGAN at sample sizes of greater than 25,000 rows.

#### Moderate Association Data
![image](https://github.com/user-attachments/assets/46d443d9-fecc-4ad4-bd73-7af5d1119cd5)

Looking at the results of Cramer's V between Country Code and Language for the synthetic dataset that was created using simulated data with enforced moderate associations between variables, it is observed that GC once again performed very poorly with it's Cramer's V being very far from that of the simulated dataset. Looking at CTGAN, it once again performed poorly at small sample sizes with it performing very well at 50,000 rows. Looking at TVAE, it performed quite consistently across the board with it's Cramer's V being moderately close to that of the simulated dataset at all amounts of missing data and sample sizes. Overall, in the synthetic dataset that was trained using simulated data with enforced moderate associations between variables, TVAE once again performed the most consistently but was surpassed by CTGAN at sample sizes of greater than 25,000 rows.

#### Low Association Data
![image](https://github.com/user-attachments/assets/25391386-41fb-46bf-93f7-01986fee926c)

Looking at the results of Cramer's V between Country Code and Language for the synthetic dataset that was created using simulated data with enforced low associations between variables, it is observed that GC once again performed very poorly with it's Cramer's V being very far from that of the simulated dataset. Looking at CTGAN, it once again performed poorly at small sample sizes with it performing very well at 50,000 rows. Looking at TVAE, it performed quite well at lower sample sizes with it doing well at 10,000 rows but it failed to capture the association between the variables when there were larger sample sizes of greater than 25,000 rows with it performing more similarly to GC: the worst synthesizers at translating the assocciations between the tested categorical featue of Country Code and Language across the other association strengths test. Overall, in the synthetic dataset that was trained using simulated data with enforced low associations between variables, CTGAN performed the best but only at large sample sizes. 

#### Overall

Overall, GC consistently performed the worst out of the three methods across all association strengths, sample sizes and missing percentages. CTGAN performed the best especially at large sample sizes across all association strengths and missing percentages. TVAE performed quite consistently across the board but failed to capture the association between Country Code and Language when the association strength was weak. Overall, the neural network methods of CTGAN and TVAE performed much better than that of the statistical method of GC when translating over associations between categorical features. This may be a result of the tested association being between two features with large cardinality, Country Code and Language which as stated before has large cardinality showing that GC fails to transfer over associations when the cardinality of the two categorical features is large.

## Machine Learning Fidelity (Multivariate Associations)

For the multivariate tests between the synthetic dataset and simulated datasets, we used random forests to make predictions on rating. The importance here is the mean absolute error (MAE) of the synthetic datasets relative to that of the simulated dataset.

### Simulated Data from Marginal Distributions
![image](https://github.com/user-attachments/assets/f2d235df-d7bd-4d58-86b8-f6044a2f808a)

Looking at the results of predicting rating from the random forest regression model for the synthetic dataset that was created using simulated data with provided marginal distributions, GC performed quite poorly with it's MAE being quite different from that of the simulated dataset across the board. Looking at CTGAN, like with GC, it performed quite poorly with it's MAE being quite different from that of the simulated dataset as well. It is observed that both of these datasets don't really get effected by missing data in the training data. Looking at TVAE, it is observed that it performs most similarly to that of the simulated dataset at 10,000 rows and 50,000 rows across all missing percentages. At 25,000 rows, it is observed that the TVAE method performed well at lower amounts of missing of less than 10% but performed very poorly at 25,000 rows with 20% missing. Overall, in the synthetic dataset that was trained using simulated data with provided marginal distributions, TVAE performed the best while CTGAN and GC failed to capture the multivariate associations in the simulated dataset. 

### High Association Data
![image](https://github.com/user-attachments/assets/4f5890b7-a89f-4404-9379-a27e86d556a4)

Looking at the results of predicting rating from the random forest regression model for the synthetic dataset that was created using simulated data with enforced high associations between variables, GC once again performed quite poorly with it's MAE being quite different from that of the simulated dataset across the board. Looking at CTGAN, it performs slightly better than that of GC. Looking at TVAE, it is observed that it performs most similarly to that of the simulated dataset across all missing percentages and sample sizes. Overall, in the synthetic dataset that was trained using simulated data with enforced high associations between variables, TVAE performed the best while CTGAN and GC failed to capture the multivariate associations in the simulated dataset. 

### Moderate Association Data
![image](https://github.com/user-attachments/assets/407f42f0-cd7f-4ae0-99a2-6672dae450f9)

Looking at the results of predicting rating from the random forest regression model for the synthetic dataset that was created using simulated data with enforced moderate associations between variables, GC once again performed quite poorly with it's MAE being quite different from that of the simulated dataset across the board. Looking at CTGAN, it performs just as poorly as that of GC. Looking at TVAE, it is observed that it performs most similarly to that of the simulated dataset across all missing percentages and sample sizes. Overall, in the synthetic dataset that was trained using simulated data with enforced moderate associations between variables, TVAE performed the best while CTGAN and GC failed to capture the multivariate associations in the simulated dataset. 

### Low Association Data
![image](https://github.com/user-attachments/assets/3eb9fbe5-f151-4ee0-aa16-592d290023b0)

Looking at the results of predicting rating from the random forest regression model for the synthetic dataset that was created using simulated data with enforced low associations between variables, GC once again performed quite poorly with it's MAE being quite different from that of the simulated dataset across the board. Looking at CTGAN, it performs just as poorly as that of GC. Looking at TVAE, it is observed that it performs most similarly to that of the simulated dataset across all missing percentages and sample sizes. Overall, in the synthetic dataset that was trained using simulated data with enforced low associations between variables, TVAE performed the best while CTGAN and GC failed to capture the multivariate associations in the simulated dataset. 


### Overall
Overall, when looking at the MAE of the different synthetic datasets, it is observed that TVAE consistently performed by far the best at transfering over multivariate associations between variables that were observed in the simulated dataset. GC and CTGAN consistently performed quite poorly with neither of the two synthesizers being really affected by different sample sizes and missing percentages.

## Data Fidelity Results Overall

Overall, in terms of transfering over marginal distributions GC performed the best out of the three methods: GC, CTGAN, and TVAE. When transfering pairwise associations, GC performed the best at transfering over associations between numeric features but performed quite poorly at transfering over associations between categories with high cardinality. When transfering over associations with high cardinalities, CTGAN performed the best but only at larger sample sizes of greater than 25,000 rows. Looking at the transfer of multivariate associations between variables, TVAE performed the best with it's prediciton of rating having the most similar MAE to that of the simulated dataset. Overall, the GC was the best at transfering over simple properties but the neural network methods performed much better on more complex properties of the orignal dataset.

