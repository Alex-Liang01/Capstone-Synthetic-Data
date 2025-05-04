# Methodology
To investigate the feasability of synthetic data as a way to handle data goveranance in cross-functional teams we tested three synthetic data synthesizers across various different simulated datasets. 

## Simulation
The dataset we simulated contains the following features: Id, HashedId, ArcsId, Country Code, date of birth, email addresses, language, rating, and gender. Most of these features can be directly linked to an individual (Id, HashedId, ArcsId, email addresses) as they are unique identifiers while some of the other features could be possibly combined to identify an individual (date of birth, language, gender, and rating) showing the importance of privacy protection in these features. 

The datasets we simulated were a dataset based on marginal distributions, a dataset with artificially enforced high dependencies between features, a dataset with artificially enforced moderate dependencies between features, and a dataset with artificially enforced low dependencies between features. For the high, moderate, and low dependency datasets, we enforced one to one mappings between variables before randomly replacing a specified percentage of values based on the dependency strength of the dataset with other existing values from the same column to simulate varying levels of association.

To verify the importance of sample size in the synthetic data synthesizers we sampled each of the above datasets to test how the synthesizers would perform in terms of data fidelity and privacy with a training sample size of 10,000 rows, 25,000 rows and 50,000 rows. To verify how the synthesizers perform when there is missing data we tested different training sets with various amounts of missing data of 0%, 10%, and 20% in the rows. For the missing data, we enforced the missing data to only exist in the features: Country Code, date of birth and gender.

This results in simulated datasets with 3 factors: dataset types (marginal distribution, high dependency, moderate dependency, and low dependency), missing percentages (0%, 10%, 20%), and sample sizes (10000 rows, 25000 rows, and 50000 rows). Overall, there are 36 different datasets that were created in order to test the data fidelity and privacy protection of three different synthetic data synthesizers 

## Synthetic Data Generation
With the 36 different datasets with varying amounts of missing values, sample sizes, and asssociation strengths we tested 3 synthetic data synthesizers from the Synthetic Data Vault library: Gaussian Copula (GC), Conditional Tabular GAN (CTGAN) and Tabular Variational Autoencoder (TVAE). 

Gaussian Copula is a statistical method that uses copulas to model marginal distributions while maintaining correlations among variables. To handle categorical features, the Synthetic Data Vault uses reversible data transformations. GC synthesizes data using three steps. First, it generates values for variables using multivariate normal distributions and a desired correlation. Then, it converts these distirbutions to a uniform distribution using a cumulative distirbution functions. Finally, it maps the values of the uniform distribution back to the original distribution of the variables.

Conditional Tabular GAN is a generative adversial network where two neural networks compete against each other. One neural network is a generator and the other is a discriminator. The objective of the generator is to create synthetic data that resembles the training data while the objective of the discriminator is to distinguish between synthetic and training data. The process of the two synthesizers are compete against each other iteratively until a dataset is generated where the synthetic dataset looks realistic enough to the point where the discriminator cannot tell the two sets apart.   

Tabular Variational Autoencoder is a neural network that uses an encoder and decoder. It first encodes the training data into a smaller, abstract representation called the latent vector. Then, it introduces randomness into the latent vector. Then the decoder, decompresses the latent vector with noise to reconstruct the original dimensions of the training data resulting in a new synthetic dataset that follows the dimensions of the original dataset with added noise.

With these three synthetic data synthesizers, we then fed in the 36 different datasets with varying amounts of missing data, sample sizes, and association strengths resulting in 108 synthetic datasets each of which have a varying amounts of missing data, sample sizes, and association strengths. To test the data fidelity of the synthetic datasets, we then tested the marginal distribution of the synthetic data sets compared to the simulated datasets it was trained on.

## Data Fidelity Tests
### Marginal Distributions of Synthetic data

To test the marginal distribution of the synthetic data compared to the simulated datasets it was trained on, we used two metrics for numeric features and categorical features respectively: the KSComplement and TVComplement. This means that we used the TVComplement to benchmark the performance for the numeric features of Rating and Date Of Birth while KSComplement was used to measure the performance for the categorical features: Gender, Country Code, and Language. 

KSComplement compares the marginal distribution of the numeric features of the synthetic data compared to the simulated dataset that it was trained on. It computes two cumulative distribution functions: one for the synthetic data and one for the simulated data that it was on. Then it takes the maximum difference between the two cumulative distribution functions to get the Kolmogorov-Smirnov statistic. The Kolmogorov-Smirnov statistic is then inverted resulting in the KSComplement where the metric is bounded from 0 to 1 with values closer to 1 meaning that the preservation of the marginal distribution was preserved very well. 

The TVComplement computes the total variation distance between the synthetic data compared to the simulated dataset that it was trained on. The total variation distance is the largest difference in probablities across the levels in the category. The total variation distance is then inverted resulting in the TVComplement where the metric is bounded from 0 to 1 with values closer to 1 meaning that the preservation of the marginal distribution was preserved very well. 

To further test the data fideility of the synthetic datasets, we then tested the pairwise associations between the features in the synthetic dataset compared to the simulated datasets.

### Pairwise Association Tests

To compare the pairwise assocations between the synthetic datasets compared to the simulated datasets, we used the common Pearson's Correlation for numeric features, and Cramer's V for categorical features. For Pearson's Correlation, we used the features of rating and age while for Cramer's V, we compared Country Code and language for the synthetic dataset compared to simulated datasets.

Pearson's Correlation is a metric bounded from -1 to 1 where values closer to 0 means weaker association while values closer to 1 means stronger association. The sign of the association measures a positive correlation and a negative correlation between the two variables respectively.

Cramer's V is a metric bounded from 0 to 1 where values closer to 0 means weaker association while values closer to 1 means stronger association.

To further test the data fidelity of the synthetic datasets, we then used machine learning to make predictions on rating to measure the multivariate associations between the synthetic data and simulated data.

### Machine Learning Fidelity

To test the multivariate assocations between the synthetic data and simulated data, we used machine learning as if the synthetic data carries over the properties of the simulated dataset well, the results of the synthetic dataset should be similar to the simulated dataset.

To do this, we used random forest regression using the LightGBM package. Random forests are an ensemble of trees where each individual tree is trained using bootstraping and a random subset of features. As a result, each individual tree will make slightly different predictions which is then averaged out to get the prediction for the entire random forest. The loss function we used was the mean absolute error so that the results are easily interpreable. We used cross validation with five folds to prevent overfitting while utilizing the entire dataset in order to train the tree. No hyperparameter optimization was done so that the results can be compared fairly between the synthetic datasets and the simulated datasets that they were trained on with varying amounts of missing data, sample sizes and asssociation strengths.

Now with all of the data fidelity metrics described, we used four privacy metrics to measure the privacy of the synthetic data compared to the simulated data. 

## Privacy Metrics
The four privacy metrics we used to test the privacy protection of PII in the synthetic datasets are: Disclosure Protection (DP), Nearest Neighbor Distance Ratio (NNDR), Nearest Neighbor Adversarial Accuracy (NNAA) and Membership Inference Attack (MIA).

Disclosure protection measures the risk of sensitive information being disclosed in the synthetic data. DP is a score bounded from 0 to 1 with higher scores closer to 1 indicating strong privacy while values close to 0 have high disclosure risk.

Nearest Neighbor Distance Ratio evaluates how close synthetic data points are compared to the simulated data points by comparing distances. NNDR is a ratio from score 0 to 1 with higher scores indicating stronger privacy while values close to 0 have higher disclosure risk. It compares distances to the nearest vs. the distance to the second nearest neighbor.

Nearest Neighbor Adversial Accuracy evaluates how well an adversary can distinguish real and synthetic data using a nearest neighbor classifier. NNAA is a score from 0 to 1 with lower scores closer to 0 indicating better privacy. Values greater than or equal to 0.5 indicate high privacy loss. 

Membership Inference Attack evaluates whether an adversary can determine if a specific dat point was part of the training set used to create the synthetic data. MIA is a score from 0 to 1 with lower scores less than 0.5 indicating excellent privacy but poor accuracy. Values that are greater than or equal to 0.5 indicate poor privacy and excellent accuracy.

Each of these privacy metrics was ran on the different synthetic datasets to see if any of the synthetic data synthesizers perform better or worst in terms of privacy when there are varying amounts of missing data, sample sizes and association strengths in the simulated dataset that it was trained on.
